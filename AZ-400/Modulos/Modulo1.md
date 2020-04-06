# Control de versiones

DevOps es una metodología que permite generar despliegues más eficientes, rápidos además de ayudar con el mantenimiento de aplicaciones y su seguridad.

Todo se basa en el control de versiones y el almacenamiento del código fuente de las aplicaciones y esto ayuda a las empresas a generar Workflow consistentes entre sus empleados, ayuda al momento de hacer merge entre los diferentes trabajos realizados y finalmente da soporte y un histórico de cambios de las aplicaciones.

## ¿Qué es el versionamiento de código?

El versionamiento del código es una práctica que permite hacer un seguimiento de los cambios del código, permite almacenar un histórico y ayuda al momento de resolver conflictos por múltiples interversiones de los equipos de trabajo.

Además, el versionamiento no solo ayuda evitando degradación del código por múltiples fuentes de cambios, también sirve como resguardo en caso de una catástrofe.

### Valores del desarrollo de software
*   Reusabilidad: No repetir código.
*   Trazabilidad: Tener un histórico de cambios y saber por qué se hicieron dichas modificaciones.
*   Manejabilidad: Se pueden ejecutar reglas de código, ejecutar pruebas y garantizar que todo el ciclo de vida del desarrollo este en perfecto estado.
*   Eficiencia: ¿Se están utilizando las herramientas adecuadas?
*   Colaboración.
*   Aprendizaje: El equipo de trabajo mejora día a día con las nuevas experiencias y conocimientos.

Las herramientas y procesos solos no son suficientes para el mejoramiento de la industria, es por eso que se adoptan metodologías como CI (Integración continua) y DevOps.

El versionamiento del código permite tener un histórico de los cambios del código, ayuda en caso de tener que volver atrás en el tiempo, permite que múltiples personas/equipos colaboren con la construcción de software y garantiza que su trabajo quede almacenado de forma segura.

## Beneficios de control de versiones

*   Crear flujos de trabajo predecibles para los miembros del equipo.
*   Los cambios se guardan como paquetes de cambios y no como un cambio por archivo, así se mantiene la estabilidad y la consistencia del software.
*   La colaboración es importante y con el versionamiento permite hacer una sincronización de cambios previos.
*   Almacena un histórico de cambios.
*   Permite automatizar tareas como las pruebas, las revisiones de código y el despliegue.

### Buenas prácticas del control de versiones

*   Hacer cambios pequeños.
*   No almacenar archivos personales como configuraciones de ambientes, llaves, tokens, cadenas de conexión etc.
*   Verificar los cambios, la compilación de la aplicación y su correcto funcionamiento antes de guardar la versión.
*   Prestar mucha atención a los mensajes ya que estos indican los cambios hechos.
*   Hacer referencia a las tareas realizadas y resueltas con los cambios.

## Tipos de control de versiones

*   Centralizados: Solo existe una copia del código en un repositorio.
    *   Idea para dar permisos granulares.
    *   Exclusividad al modificar un archivo.

*   Distribuidos: Cada desarrollador tiene una copia del código y su historial.
    *   Se pueden almacenar cambios localmente para luego subirlos al repositorio.
    *   Se habilita el trabajo offline ya que al clonar se tiene toda el histórico de los archivos.

### Beneficios del control de versiones descentralizado

*   Uso de ramas para trabajo aislado por nuevas características de producto.
*   Cada desarrollador tiene el historial completo del código esto habilita el trabajo offline lo cual ayuda a crear y almacenar cambios localmente, poder hacer diff de los archivos y ver su cambio en el tiempo
*   Pull request, con esto se busca que al momento de hacer un merge se haga una revisión previa del código y se abran discusiones sobre el porqué de los cambios.


## Laboratorios
*   [Azure Repos][azure_repos]
    
    
[azure_repos]:https://www.azuredevopslabs.com/labs/azuredevops/git/
