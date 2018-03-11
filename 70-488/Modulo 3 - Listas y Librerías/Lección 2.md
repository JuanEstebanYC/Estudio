# Consultando y buscando datos en una lista.

## Clases de consultas

Para consultar datos en las listas existen dos clases:

*   **SPQuery** que busca datos en una lista.
*   [**SPSiteDataQuery**][spsitedataquery] que sirve para hacer busquedas en multiples listas de multiples sitios de la misma colección de sitios.

Ambas clases de busqueda requeren de una consulta que se crea usando *(Collaborative Application Markup Language)* [**CAML**][CAMLTutorial] que es un lenguaje basado en la sintaxis de *xml*

## LINQ para Sharepoint

Existe una versión de *LINQ* para Sharepoint que sirve para hacer busquedas en las listas, pero requiere una clase base sobre la cual buscar, para esto Sharepoint tiene una herramienta llamada [**SPMetal**][SPMetal] que genera clases de las listas a utilizar.

## Usando la clase SPQuery

Es posible ejecutar consultas *CAML* desde el código utilizando la clase **SPQuery**:
*   Se debe construir una instancia de la clase *SPQuery*.
*   Se anexa el string que contiene el Query en la propiedad *Query* en la instancia creada anteriormente.
*   Se llama el método *GetItems* del objeto *SPList* pasando como parámetro el objeto de tipo *SPQuery*.

## Usando la clase SPSiteDataQuery

Esta clase se usa cuando se quiere hacer consultas entre sitios dentro del mismo *Site Collection*:
*   Se debe crear una instancia de la clase *SPSiteDataQuery*.
*   Se ingresan los parámetros necesarios para realizar la consulta.
*   Se llama el método *GetSiteData* del objeto *SPWeb* y se le pasa como parámetro el objeto de tipo *SPSiteDataQuery*.

## LINQ para Sharepoint

Para utilizar *LINQ* en *Sharepoint* es necesario primero generar clases que representen las listas y los tipos de contenido con los que se va a trabajar, para esto se puede utilizar la herramienta [*SPMetal*][SPMetal]

[spsitedataquery]:https://msdn.microsoft.com/en-us/library/microsoft.sharepoint.spsitedataquery.aspx
[SPMetal]: https://msdn.microsoft.com/es-es/library/office/ee538255(v=office.14).aspx

[CAMLTutorial]: http://sharepoint-works.blogspot.com.co/2012/05/caml-query-tutorial-for-sharepoint.html