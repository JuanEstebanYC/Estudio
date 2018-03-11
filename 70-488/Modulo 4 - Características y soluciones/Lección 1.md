# Entendiendo Características y soluciones (**Features and Solutions**)

## Característica

Una característica (**Feature**) es un conjunto de archivos que adicionan a Sharepoint nuevas funcionalidades o componentes.
Estas características tiene un alcance (**Scope**) que va desde toda la granja, pasando por la aplicación web, la colección de sitios y finalmente llegando al sitio, para activar una característica lo debe hacer el administrador del cada uno de estos niveles.

Para el ambiente de *Sharepoint*, una característica es un conjunto de archivos *.xml* que se conocen como *Element Manifest* que usa *CAML* para definir los componentes. 

Cada característica tiene un archivo *feature.xml* que lista cada uno de los archivos que componen la característica y el alcance  que esta tiene.

## Alcance de las características

Este atributo se configura dentro del archivo *manifest* y puede tomar 4 valores:

*   **Farm**: esta característica queda habilitada para todas las aplicaciones web, las colecciones de sitios y los sitios dentro de la granja y debe ser activada por el *administrador de la granja*.

*   **WebApplication**: aplica para todos las colecciones de sitios y todos los sitios dentro de la aplicación web donde se active la característica, esta característica debe ser activada por el *administrador de la granja*.

*   **Site**: esta característica aplica para los sitios de colección y debe ser activada por el *administrador del sitio de colección*.

*   **Web**: esta característica aplica solamente para el sitio web especifico donde se activa y debe ser activado por el *administrador del sitio*.

## Solución

Es un archivo *cabinet* con extensión *.wsp* que se utiliza para empaquetar, hacer despliegues y manejar el ciclo de vida de varios componentes de SharePoint.

Hay tres tipos:
*   **Farm Solution**: solución desplegada en la granja por el *Farm Administrator*.
*   **Sandboxed Solutions**: conocida como solución de usuario, tiene un alcance de *Site Collection*, todo código que se ejecute dentro de esta solución será ejecutado en un contexto seguro. 
*   **Solutions within app for SharePoint**: solución en la que todo el código debe ser *Client Site* y no puede contener ninguna código que se requiera ejecutar del lado del servidor.

### Qué se puede incluír en la Solución?

Dentro de las soluciones se pueden empaquetar dos tipos de componentes:
*   *Características*
*   *Ensamblados*

Cada solución incluye un archivo **Manifest.xml** que indica el contenido.