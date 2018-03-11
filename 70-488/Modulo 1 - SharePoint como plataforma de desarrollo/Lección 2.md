# Seleccionando el medio adecuado para el desarrollo en SharePoint

Para el desarrollador, existen diversas formas de implementar la lógica del negocio dentro de SharePoint.

## Componentes declarativos
Se puede utilizar *(CAML)* para crear y configurar los siguientes elementos:

*   *Definiciones de campos. (site columns)*
*   *Content type definition.*
*   *List template:* permite que los usuarios instancien desde una lista especifica.
*   *List instance.*
*   *Content type binding:* asocia un tipo de contenido con una lista existente.
*   *Modules:* para desplegar archivos junto con sus metadatos.
*   *Event registration:* registra el assembly del *event receiver* a un evento especifico.
*   *Custom actions:* acciones dentro del menú contextual.
*   *Workflow definition*

### Cuando usar componentes declarativos

Se pueden usar cuando estos ayudan a cumplir con la lógica del negio, pero se debe tener en cuenta que no ejecutan código y que las personas normalmente no estan familiarizadas con la sintaxis. Este componente es el acertacmiento más flexible a la personalización de SharePoint, se pueden desplegar componentes declarativos en las caracteristicas de SharePoint sin necesidad de una solución o un App y los componentes sirven tanto para SharePoint Online y para SharePoint 2013.

## Código del lado del cliente (Client-Site Code)
Es posible hacer el llamado al servicio *client.svc* para hacer peticiones *REST y OData*.
Por medio del servicio *client.svc* se puede interactuar con:

*   Sitio, listas, documentos, tipos de contenido y archivos
*   Administrador de carcterísticas de sitios y colección de sitios
*   Interactuar con el *user profile* y las *social features*
*   Interactuar con el servicio de busqueda
*   Interactuar con el *Business Data Conectivity component(BDC)*
*   Interactuar con Workflows

El scope de las soluciones implementadas con *CLient-Site Code* son solamente de la colección de sitios y no de la arquitectura lógica de las aplicaciones web ni de la granja.

### Cuando usar componentes Client-Site Code

Es una aproximación adecuada cuando se va a implementar un desarrollo para la plataforma, una de sus ventajas es que todo se ejecuta del lado del cliente, esto hace que no se requiera hacer un despliegue y ejecución de código del lado del servidor evitando asi problemas con restricciones administrativas en el componente construido.

Otra ventaja es que para los casos de SharePoint Online y SharePoint OnPremise el manejo y uso del Client-Site Code es el mismo.

## WebParts

Es un tipo de control ASP.NET que se construye con el framework *ASP.NET WebPart* y sirve para modificar el contenido y el comportamiento de los páginas adicionando controles personalizados. Tambien es posible conectar WebParts entre sí.

Visual Studio 2012 presenta 3 tipos de plantillas para los webparts:

*   *Regular Webpart*: en este se puede sobre escribir el modo de renderización.
*   *Visual Webpart*: permite controlar el diseño del webpart.
*   *Silverlight Webpart*: es contenido en un control de Solverlight.

La clase base de la cual heredan la mayoría de los webparts es **System.Web.UI.WebControls.WebParts.WebPart** que expone los siguientes métodos que component el ciclo de vida de un webpart:
*   *Init*
*   *Load*
*   *PreRender*
*   *Unload*

### Cuando crear WebParts

Los webparts se pueden crear cuando se requiera un mayor control de conectividad con lógica del negocio y cuando se requiera conectar dos o más webparts.

## Páginas de aplicación (Application Pages)

Las páginas de aplicación se usan para exponer funcionalidades administrativas.

Para utilizar una Página de Aplicación simplemente se debe crear una página *ASP.NET forms (aspx)* y desplegarla en el directorio *15/Template/Layouts*. Esta nueva página es accesible desde cualquier sitio desde el directorio virtual *_layouts*

Estas páginas corren con los permisos máximos y tienen acceso al modelo de objetos del servidor.

El namespace **Microsoft.SharePoint.WebControls** incluye dos clases utiles para la creación de Páginas de Aplicación:
*   *LayoutsPageBase:* se utiliza cuando solo unos pocos usuarios privilegiados pueden tener acceso a esta.
*   *UnsecuredLayoutsPageBase:* se utiliza cuando la página es abierta para todo tipo de usuarios.

### Cuando crear una Páginas de Aplicación (Application Page)

Las páginas de aplicación se utilizan para interactuar con recursos de una aplicación web o de una granja, esto es, este tipo de páginas tiene acceso al modelo de objetos del servidor y debe ser desplegado en una solución confiable para la granja (*full-trust farm solution*), la debe desplegar un adminitrados de la granja o *Farm Administrator*.
Este tipo de páginas no se pueden desplegar en un SharePoint Online ya que requieren ser desplegadas a nivel de la granja.

## Timer Jobs

Un *Timer Job* se utiliza para ejecutar tareas en el BackGround de la aplicación que no requieren interacción de una persona y no se espere un retorno de información para alguien.
Los *Timer Jobs* se ejecutan en un proceso aparte del del IIS *(w3wp.exe)*, esto quiere decir, que los *Timer Jobs* no deben intervenir en el performance de la aplicación y que no se afectan cuando se recicla el pool de la aplicación web.

SharePoint 2013 soporta dos tipos de *Timer Job*:

*   *Regular Timer Job:* Este tipo de *Timer Job* heredan de la clase **SPJobDefinition** y sirven para configurar una tarea especifica en el calendario, el cual es administrador puede configurar cuando puede correr la tarea.
*   *Work Item Timer Job:* Sirve para encolar una tarea en el calendario. Para crear un *Work Item Timer Job* es necesario  crear una clase que herede de **SPWorkItemJobDefinition** y se debe crear un objeto del tipo **SPWorkItem** para representar la tarea.

Los *Timer Jobs* se ejecutan con máximos privilegios y tienen acceso completo al *Modelo de objetos del servidor*.

### Cuando crear un Timer Jobs

Los *Timer Jobs* son utiles cuando se requieren hacer tareas de larga duración o que consuman muchos recursos, siempre y cuando no requieren del ingreso de información por parte del usuario y que finalmente no sea necesario retornar información al usuario.

## Event Receivers

Es posible crer un *Event Receiver* para responder a alguna acción dentro de SharePoint.
Las siguientes son las categorías que existen:

*   *Site Collection*
*   *Web*
*   *List*
*   *Field*
*   *Item*
*   *WorkFlow*
*   *Feature*

Para mayor información sobre estas categorías, [leér][EventReceiverLin]

Existen dos tipos de *Event Receiver*:
*   Antes del evento:  ocurre justo antes del evento, se representa con los verbos terminados en *ing*. Estas acciones son sincronas.
*   Después del evento: ocurre justo después del evento, se presenta con los verbos terminados en pasado. Ejemplo *ed*. Estas acciones pueden ser sincronas o asincronas.

Exite una clase base para cada una de las categorias de los eventos, por ejemplo *SPListEventReceiver*.

### Cuando crear Event Receiver

Generalmente los *Events Receivers* se crean cuando es requerido manejar una acción del ambiente de SharePoint antes o durante su ejecución.
Por ejemplo: se quiere llevar un log de los elementos de una lista que son eliminados.

## WorkFlow

Un *WorkFlow* es una forma de automatizar un proceso donde intervienen varios actores. Los *WorkFlows* estan activos solamente cuando el usuario realiza una acción que es pre-requisito para que el flujo de negocio continue o inicie. El alcance de los flujos es de Web o de lista.

### Cuando crear un WorkFlow

Los *WorkFlow* se crean cuando se requiere que un proceso sea llevado acabo por más de un autor y además el proceso tenga lógica interna que valide información del negocio.

Para SharePoint 2013 los *WorkFlow* son declarativos, esto es se pueden hacer *SharePoint Apps* o *Sandbox solution* para su despliegue tanto OnPremise como Online.

[EventReceiverLin]:https://msdn.microsoft.com/en-us/library/office/ff408183(v=office.14).aspx