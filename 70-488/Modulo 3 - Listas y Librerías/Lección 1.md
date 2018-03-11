# Listas y librerías

Todas las listas y las librerías documentales estan representadas por una instancia de **SPList**, las librerias documentales son una especialización de lista como consecuencia de esto implementan la clase **SPDocumentLibrary** que hereda de *SPlist*.

Cada instancia de *SPList* tiene entre sus propiedades colecciones de *Field*, *Folders* e *Items*.

**SPListItem** representa un item de lista que puede contener archivos que se representan con la clase **SPFile** y si la lista contien carpetas,estas se representan con al clase **SPFolder**.

Para trabajar con una lista, es necesario obtenerla desde el objeto *SPWeb* ya que no tiene un constructor, para tal fin el objeto los siguientes métodos y la siguiente propiedad:

*   *(Propiedad) Lists*: colección de tipo **SPListCollection** donde, por medio de un indice, se puede obtener la lista deseada.
*   *(Método)  GetList*: permite obtener una lista/librería especifica por medio de la ruta relativa.
*   *(Método) GetListOfType*:  retorna una colección de tipo **SPListCollection** y requiere un parámetro de tipo **SPBaseType**
*   *(Método) GetListFromWebPartPageUrl*

Tambien es posible busca las listas por medio del objeto **SPListCollection** que expone dos métodos:
*   *GetList*: cuando no encuentra una lista devuelve una excepción.
*   *TryGetList*: cuando no encuentra una lista devuelve null.


*List Definition* es un termino que se utiliza para designar la forma como está definida la lista, esto se hace con un XML que se despliega en el servidor e indica los campos que la lista debe contener, los formularios y las vistas entre otros. Este XML debe indicar que tipo de lista es deacuerdo con el enumerado **SPBaseType**.

*List Template* es la forma como se muestra la lista al usuario, esto se despliega desde una característica. Es posible crear una nueva lista guardardo la actual como una plantilla.

## Crear una lista

Para crear una lista solo basta con llamar el método **Add** de la colección **SPListCollection** que expone la propiedad **SPWeb.Lists**, cuando se crea la lista se devuelve un *GUID* que identifica la nueva lista.

## Eliminar una lista

Para eliminar una lista es necesario primero buscar la Lista dentro del sitio web, posteriormente con el objeto *SPList* instanciado se llama el método **Delete** que elimina la lista o el método **Recycle** que envía la lista a la papelera del usuario.

## Trabajando con Items

Cada item de lista se representa por la clase **SPListItem**, los items esta almacenados en la collección **SPListItemCollection** que esta representada en la propiedad **SPLit.Items**.

Para crear un item dentro de la lista se deben seguir los siguientes tres pasos [CrearItemLista]:
    
1. Llamar el método **Add** del objeto *SPListItemsCollection* que se obtiene desde *SPList.Items*, este devuelve una instancia de tipo *SPListItem*
2. Especificar los campos y sus valores.
3. Llamar el método **Update** del objeto *SPListItem*.

##  Buscando y modificando Items

El objeto de tipo *SPListItem* incluye dos propiedades:
*   **SPListItem.ID** devuelve el ID incremental del registro dentro de la lista.
*   **SPListItem.UniqueId** devuelve el *GUID* que identifica el registro de manera *única*.

Los objetos de tipo *SPList* tienen un método por cada uno de los identificadores que se obtuvieron anteriormente:
*   **SPList.GetItemById** que requiere el *ID* del registro dentro de la lista.
*   **SPList.GetItemByUniqueId** que require el *GUID* único del registro dentro de la lista.

Tambien se puede buscar items de lista con la propiedad *Items* del objeto **SPLit.Items** ingresando un *GUID* o un *ID*.


## Eliminando items

Para eliminar los items de una lista se pueden utilizar las siguientes formas:

*   **SPListItem.Delete**
*   **SPListItemCollection.Delete** requiere que se especifique un index.
*   **SPListItemCollection.DeleteItemById** requiere un identificador del item dentro de la lista.

## Trabajando con campos

Los campos estan definidos por el enumarado [**SPFieldType**][SPFieldType], al momento de buscarlos dentro del registro se retorna un objeto de tipo *System.Object*, para estos casos se debe hacer un casteo explicito al tipo de dato que se requiera.

En algunos casos, cuando el objeto es muy complejo, se debe usar el método **SPField.GetFieldValue**.


## Trabajando con archivos

Los archivos estan representados por la clase **SPFile**. Para trabajar con las propiedades del documento se utiliza **SPListItem** y para trabajar directamente con el documento se utiliza la clase **SPFile**.
Para buscar un archivo, no es necesario ir hasta el objeto *SPListItem* dentro de la lista, los objetos *SPWeb* o *SPFolder* exponen una propiedad llamada **Files** que expone una colección de tipo *SPFile*.

### Checking y CheckOut

Para trabajar con archivos, y hacer check in o out, se usa el objeto [**SPFile.CheckOut**][CheckOut] o [**SPFile.CheckIn**][CheckIn]

### Añadiendo y Actualizando archivos

Para añadir un archivo se puede utilizar el método *Add* sobre la propiedad *SPFileCollection*.


[CrearItemLista]:https://msdn.microsoft.com/en-us/library/office/ms467435(v=office.14).aspx
[SPFieldType]:https://msdn.microsoft.com/en-us/library/microsoft.sharepoint.spfieldtype.aspx
[CheckOut]:https://msdn.microsoft.com/en-us/library/microsoft.sharepoint.spfile.checkout.aspx
[CheckIn]: https://msdn.microsoft.com/en-us/library/office/ms467428.aspx