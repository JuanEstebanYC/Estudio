# Entendiendo el despliegue y el modelo de ejecución en SharePoint 2013

## SharePoint Features

Las caracteristicas estan contenidas en carpetas, los nombres de estas son muy importantes ya que es así como SharePoint las reconoce. Dentro de cada carpeta existe un archivo llamado *Feature.xml* donde se describe el contenido de la característica, como debe ser desplegado cuando se instale y se active.

Basicamente, el archivo *Feature.xml* contiene 3 etiquetas importantes:
*   *Scope:* indica el nivel donde se va desplegar la solución:
    *   **Farm**
    *   **WebApplication**
    *   **Site** (Site Collection)
    *   **Web** (Sitio individual)
*   *Element Manifest:*  Indica la ubicación de los archivos de configuración y su localización dentro de la carpeta contenedora.
*   *Element file*: Indica la estructura/árbol de carpetas que se van a desplegar en el servidor archivos como carpetas, documentos *CCS*, *JS*, documentos *.aspx* entre otros.

Normalmente los archivos de cada caracteristica se almacenan en la carpeta **15/Template/Features** de cada servidor front-end de SharePoint, pero normalmente no se copia y se pega sino que se crear soluciones tipo *Farm Solution*, *Sandbox Solution* o *SharePoint App* donde contenga la información necesaria y se automatice el proceso del despliegue.

Solo cuando se crea una solución *Farm Solution* la información y contenido de la característica se copia dentro de *15/Template/Features* de lo contrarios se guarda en la base de datos.

## Farm Solution

Solución que desplieguea la caracteristica además de *.ddl's* dentro del GAC o dentro de la carpeta del *IIS* correspondiente al *Web Application*, este tipo de soluciones deben ser deplegadas por un administrador por medio de *PowerShell* o *Central Admin*.

Las soluciones estan empaquetadas en un archivo con extensión *.wsp* y contienen un archivo *Manifest.xml* que describe el contenido del paquete.

Las soluciones contienen:

*   *Assemblies:* Deben ser ingresados dentro del *Web.config* como seguiros. Se despliegan en el *GAC* o en el directorio del *Web Application*.
*   *Files:* Archivos que complementan la solución, como pueden ser archivos *JS*, *CSS* entre otros. Pueden ser desplegados en una carpeta física o en una carpeta virtual dentro de la base de datos.
*   *Features:* La solución tambien puede contener características que se despliegan de acuerdo a lo indicado dentro del archivo *Manifest.xml*

Para crear una *Farm Solution* es necesario que la funcionalidad requiera para su correcto funcionamiento privilegios elevados y requiere ser instalado por un *Administrador*. Se pueden crear *Farm Solution* que contengan:
*   *Timer Jobs*
*   *Application Pages*
*   *Server-Side Code* que requiere de máximos provilegios.

## Sandboxed Solution

Las soluciones *Sandbox* pueden ser desplegadas por el administrador del *Site Collection*, estas soluciones se ejecutan con los permisos necesarios y con acceso limitado al modelo de objetos de servidor.

Las soluciones *Sandbox* se empaquetan en archivos *.wsp* y pueden contener lo mismo que las *Farm Solutions*. Estas se despliegan en la galeria de características y no se almacenan en carpetas físicas sino en la base de datos de contenido.

El código de las soluciones *Sandbox* es ejecutado en un proceso diferente al del *application pool de IIS*.

## Apps para SharePoint

Las *Apps* no ejecutan código en el servidor, todo lo hacen desde el cliente (JavaScript) o desde la nube (Windows Azure u otro servicio) y consultan a *SharePoint* por medio del modelo de cliente *REST/OData*.

Las *App* se empaquetan en un archivo *.app* y se pueden habilitar dentro del *App Catalog Site* o en el *Microsoft office MarketPlace*.

Cuando se instala un *App* se crea un subsitio donde se hostea la aplicación, además las columnas, tipos de contenido y demás se crean dentro de este subsitio, lo que hace que todo el funcionamiento este aislado y no interfiera con *SharePoint*, además esto ayuda a que cuando se desinstale el *App* todo sea más fácil.

Existen dos categorias para las *Apps*: (Para ampliar la información, [leer][AutoHosted-CloudHosted])
*   *Sharepoint-Hosted App*: es cuando el *App* se hostea directamente en *SharePoint*.
*   *Romete Hosted App*: es cuando el *App* se hostea en otro servidor.

Se puede implementar el *App* para que el usuario interactue con ella de las siguientes formas: (Para ampliar la información, [leer][FormasVerApp])

*   *Full Pages App*: Usa la ventana completa.
*   *App Parts: Es un tipo de *webpart* que se renderiza en un *IFrame*
*   *Command Extention:* Crea un botón dentro de la barra de menú especifico que adiciona funcionalidades a la interface del usuarios.

[AutoHosted-CloudHosted]:https://sharepoint.stackexchange.com/questions/58479/is-there-a-difference-between-a-sharepoint-hosted-app-and-a-cloud-hosted-app

[FormasVerApp]:https://dev.office.com/sharepoint/docs/sp-add-ins/sharepoint-add-ins