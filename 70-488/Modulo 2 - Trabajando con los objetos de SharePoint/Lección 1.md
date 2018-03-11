# Gerarquía de objetos de SharePoint (Para más información, [leer][SharepointObjectHierarchy])

Las clases base del modelo de *SharePoint* son:
*   **SPFarm**
*   **SPService**
*   **SPServiceApplication**
*   **SPWebApplication**
*   **SPSite**
*   **SPWeb**
*   **SPList**

## SPFarm
Representa logicamente la granja, no tiene constructor y representa la las propiedades de la graja actual.
Se encuentra en el namespace *Microsoft.SharePoint.Administration*.

No se puede usar esta clase dentro de un *Sandbox Solution* por tema de permisos y tampoco se puede usar en una *App* ya que no existe una entidad similar para trabajar desde JavaScript.

## Servicios

*   **SPService** Esta clase representa los servicios que estan disponibles en la granja.
*   **SPServiceIntance** Esta clase representa una instancia de los servicios que estan disponibles en la granja.

[**SPWebService**][SPWebServiceInfo] es una clase muy util en cuando a la administración de los *Web Applications* ya que es un contenedor de los mismos y permite hacer modificaciones y creación/eliminación de estos elementos.

Tiene dos propiedades muy importantes:
*   *ContentService*: retorna un objeto de tipo *SPWebService*.
*   *AdministrationService*: Devuelve un objeto de tipo *SPWebService* del *Web Application* del *Central Admin*.

No es posible interactuar con los servicios de *SharePoint Online* ya que no se tiene acceso a estas clases, además solo se pueden desplegar soluciones *Sandobox* o *Apps*, adicional a esto no existen los objetos *SPService* o *SPServerInstance* en los objetos del modelo de cliente.

## Trabajando con servicios (Para más información, [leer][Servicios]) 
*SharePoint* utiliza servicios para usos especificos.

Hay 3 componentes principales dentro de la arquitectura de Servicios:
*   *Service Application*: Encapsulan funcionalidades especificas.
*   *Service Application Proxies*
*   *Service Application Proxies Group*

## Web Applications

Contenedor principal dentro de los objetos de *SharePoint* y se aloja en el *IIS*.
Se representa por la clase **SPWebApplication** y no es muy utilizada para el desarollo ya que el tema de crear *Web Applications* es más de administradores que utilizan el *Central Administration* o *PowerShell*. De parte de desarrollo, la clase *SPWebApplication* se utiliza para modificar propiedades.

## Site Collection

Esta representado por la clase **SPSite**.
Es común utilizar este objeto ya que en él se definen los usuarios, grupos, permisos entre otras caracteristicas, además hay muchos componentes que se despliegan sobre los *Site Colllection* como lo son *Content Type*, *Web Parts* entre otros.

Utilizando *JavaScript*, el objeto que representa un *SPSite* es *SP.Site* y esta representado por la clase *Microsoft.SharePoint.Cliente.Site*. (Para más información, [Leer][SPSiteClient])

## Site

Un sito es representado por la clase **SPWeb**.
Este es el objeto más utilizado ya es el contenedor de las listas con las que finalmente se tiene más interacción.
Cada objeto de tipo *SPSite* contiene un *Root web* que comparte la URL con el *Site Collection*. Dentro de la jerarquía de los objetos, el *SPWeb* es el único que puede tener dentro de sí mismo otros objetos *SPWeb* siendo estos SubSite - Sub-Subsite y así sucesivamente.

Utilizando *JavaScript*, el objeto que representa un *SPWeb* es *SP.Web* que se encuentra en la clase *Microsoft.SharePoint.Client.Web*. (Para más información, [Leer][SPWebClient])

[SPWebClient]:https://msdn.microsoft.com/en-us/library/office/jj245288.aspx
[SPSiteClient]:https://msdn.microsoft.com/en-us/library/office/jj246828.aspx
[Servicios]:https://sharepoint.stackexchange.com/questions/24001/sharepoint-service-applications-purpose-of-each-component
[SPWebServiceInfo]:https://msdn.microsoft.com/en-us/library/microsoft.sharepoint.administration.spwebservice.aspx
[SharepointObjectHierarchy]:https://msdn.microsoft.com/en-us/library/ms473633(v=office.14).aspx