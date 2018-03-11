# Introducción al desarrollo en SharePoint

## Áreas de trabajo dentro de SharePoint 2013

Como desarrollador, las siguientes son áreas donde puedo trabajar.

*   **Portales y colaboración:** permite la creación y manipulación de sitios, librerías y listas.
*   **Busquedas**: componente flexible y de alta extensibilidad, que permite al usuario encontrar información en las diversas fuentes de recursos de la organización.
*   **Administrador de contenido empresarial:** provee funcionalidades que soportan procesos de negocio como los flujos de trabajo.
*   **Administrador de componentes web:** provee un administrador de contenido o CMS.
*   **Social y comunicaciones:** permite a los usuarios conectarse con otros, compartir información y crear grupos al rededor de un tema en común.
*   **Servicios de conectividad empresarial:** (Business conectivity services) permite conectar sistemas externos en soluciones de sitios o de aplicaciones de *Microsoft Office 365*.
*   **Inteligencia de negocios:** permite la integración con el servicio de Excel, SQL server 2012 Analysis Services y SQL 2012 Reporting Services.

## Herramientas de desarrollo para SharePoint 2013

Como desarrollador, hay diferentes herramientas y formas de interactuar con la plataforma, las más comunes son:

*   **Visual Studio**
*   **Sharepoint Designer**
*   **Microsoft Office Tools para VS:** este plugin provee, para Visual Studio, plantillas para SharePoint 2013 que incluye apps para SharePoint y para Office además de componentes como listas, recibidores de eventos entre otros.

## Que hay de nuevo para desarrolladores en SharePoint 2013

*   **Apps para el modelo de SharePoint:** Las apps proveen un nuevo modelo de desarrollo, empaquetado y despliegue de características funcionales para SharePoint; esencialmente apps que corren fuera del servidor, en Azure o en una plataforma diferente o ejecutando JavaScript del lado del cliente o ambos escenarios.
Las apps proveen las siguientes ventajas:
    *   Menor impacto en el rendimiento de la granja: no ejecutan ningún código en el servidor.
    *   Mejor encapsulamiento de la funcionalidad: cuando se instala un app, esta solamente afecta el sitio donde fue activada, guardando la información en páginas, listas, tipos de contenido, columnas de sitio entre otros.
    *   Mejora el manejo de permisos: puede especificar los permisos requeridos para el funcionamiento del app.
    *   Consistencia entre plataformas: se ejecutan de igual forma las apps en la SharePoint Online y en SharePoint on premise.

*   **Nuevo modelo de desarrollo del lado del cliente:** SharePoint 2013 incluye novedades y mejoras en su modelo de objetos.
    *   Modelo de objetos de JavaScript: también conocido como *client-site object model*  para JavaScript, fue introducido desde SharePoint 2010 pero para esta nueva versión trae muchas mejoras y un API más completa.
    *   Modelo de objetos .NET Framework: también conocido como *object model for managed clients* fue introducido en SharePoint 2010 pero para esta nueva versión fue mejorado y ahora cuenta con nuevas funcionalidades que permiten interactuar con core de SharePoint.
    *   Modelo de objetos de Silverlight y Modelo de objetos Mobile.
    *   REST/[OData][ODataUrl]: SharePoint 2010 incluye REST API para realizar el CRUD, pero SharePoint 2013 incluye REST/OData que permite extender las operaciones básicas del CRUD.

*   **Nuevo modelo de diseño:** con esta nueva mejora, se pueden crear páginas con herramientas comerciales para tal fin, HTML5, CSS3 y JS, y para convertir este diseño a una master page, por ejemplo, se pueden utilizar utilidades como Design Manager que permite generar los fragmentos de código que SharePoint debe administrar como la navegación y el titulo del sitio.

*   **Nuevo modelo de Flujos de trabajo (WorkFlkows):** Incluye un nuevo modelo de flujos de trabajo basado en *Workflow Manager 1.0* basado en .NET Framework 4.5 y Windows WorkFlow Foundation. Estas nuevas características permiten mayor escalabilidad a a las granjas de flujos de trabajo on-premise o basada en Azure. El desarrollo es completamente declarativo y brinda mayor flexibilidad sobre el desarrollo, y se puede hacer el despliegue en Apps o en soluciones Sandboxed.


Para mayor información, visitar el siguiente [link][NuevoEnSharePointUrl]

## Proceso de renderización de las páginas

hay dos tipos de páginas: 
*   **Application Pages (Páginas de aplicación):** páginas ASPX que se encuentras en los archivos del servidor front-end de SharePoint, estas páginas se utilizan para encapsular funcionalidad y no contenido.
*   **Content Pages (Páginas de contenido):** páginas que se construyen dinamicamente cuando son requeridas. Estas páginas combinan una plantilla con un contenido proveniente de la base de datos, la plantilla contiene Web Part Zones donde se inyectos el contenido y los controles cuando se construyen este tipo de páginas.

## Puntos de ingreso a SharePoint 2013 para los desarrolladores

SharePoint provee varias funcionalidades para los desarrolladores:

*   **Server-site object model:** Su principal contenedor es el assembly *Microsoft.Sharepoint.dll* y permite interactuar con la mayoria de elementos de SharePoint, tambien es posible interactuar por medio de este componente con *powershell*.

*   **Client.svc:** por cada sitio de colección expone un servicio *WCF*, cuando se usa *REST/OData* se interactua directamente con este servicio.
La ruta relativa para cada servicio es *vti_bin/client.svc*.

*   **Personalización declarativa:** se puede personalizar muchos aspectos de SharePoint utilizando *Collaborative Application Markup Language (CAML)*


[ODataUrl]:http://www.odata.org
[NuevoEnSharePointUrl]: http://go.microsoft.com/fwlink/?LinkID=306774
