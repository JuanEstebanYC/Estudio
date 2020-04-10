# Git en entornos empresariales 

## Flujo de trabajo con ramas

La creación de ramas es una estrategia que garantiza un ambiente aislado para cada una de las nuevas características requeridas, esto es que por cada nueva característica que se vaya a desarrollar se crea una rama donde se trabajará y con esto se evita que todo el equipo trabaje sobre la rama principal, además que se suba código que afecte el funcionamiento de la rama principal y con esto todo el desarrollo.

Además, permite crear pull request y con esto iniciar una discusión sobre las mejoras hechas, permite hacer revisiones pares y validar el código antes de ser unido con la rama principal.

## Pasos del flujo de trabajo

*   Crear una rama: Para trabajar una nueva característica o reparar un problema, se crea una rama a partir de la rama principal y se le crea con un nombre descriptivo.
*   Crear un commit: Con la creación del commit se garantiza que se haga un correcto seguimiento de los cambios hechos, cada commit tiene asociado un mensaje y se considera una unidad de cambio lo cual permite hacer un rollback de ser necesario.
*   Crear un pull request: Esto se hace para abrir una discusión y pedir ayuda cuando se requiere o hacer la validación de las modificaciones antes de ser unidas a la rama principal.
*   Revisión y discusión: Esto permite hacer los comentarios que sean necesarios para el pull request.
*   Despliegue: Se puede hacer un despliegue a un ambiente intermedio (pruebas) con el fin de validar completamente la funcionalidad o la corrección de bugs.
*   Merge (unión): Este es el último paso y se hace cuando todas las anteriore fases ya están completas y se pasaron satisfactoriamente. Este paso une la rama de trabajo con la rama principal.

## Colaboración con Pull Request

Pull request permite avisas a los demás compañeros de equipo que un trabajo se ha finalizado y esto permite que sea revisado antes de ser integrado a una rama principal.

La revisión que permite el pull request garantiza que el código escrito tenga todos los estandares que se exigen en el equipo además permite hacer discusiones del porqué se hicieron esos cambios y ayuda a mejorar el código de ser necesario.

Los pull request permiten proteger las ramas principales ya que se puede bloquear los push a dichas ramas y solo se puede hacer merge por medio de pull request que son aprobados por las personas responsables de mantener el código.

## Importancia de los Hooks de git

Teniendo en mente los despliegues continuos y una calidad de código minima, git ofrece hook que permiten ejecutar scripts o tareas de validación en todo su ciclo de vida y de esta forma garantizamos que el código sea validado antes de ser deplegado a las ramas correspondientes.

Un ejemplo de esto es la validación del mensaje de commit que cumpla con estandares predefinidos por la empresa como un prefijo inicial, un link al item relacionado etc... para más información consultar el siguiente [link][git_hooks]

Algunos ejemplos de githooks se encuentran en la ruta .git\hooks del repositorio local.

## Promoviendo la colaboración interna entre proyectos.

Para colaborar con otros proyectos, git ofrece una opción de crear un Fork, esto es un copia del proyecto dentro de tu perfil, ya con esto se puede iniciar la colaboración y al momento de finalizar lo que se tenía previsto hacer se crea un pull request con el repositorio origina para que las personas que lo mantienen puedan revisar la colaboración y hacer el posterior merge con el proyecto principal y así tener las mejoras hechas.



## Laboratorios
*   [Pull request lab][pullrequest_lab]

[pullrequest_lab]:https://azuredevopslabs.com/labs/azuredevops/githubpullrequests/
[git_hooks]:https://git-scm.com/docs/githooks