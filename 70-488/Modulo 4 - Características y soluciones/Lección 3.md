# Trabajando con Soluciones Sandboxed

Las soluciones *Sandboxed* fueron introducidas en *SharePoint 2010* para que el administrador pudiera desplegar soluciones sin necesidad de ingresar al servidor o la intervención del administrador de la granja.

Las soluciones *Sandboxed* se ejecutan con los permisos mínimos y no tienen acceso a los archivos del sistema.

## Despliegue 

las soluciones *Sandboxed* se despliegan a nivel de *sitios de colección* y esto permite que se puedan desplegar en *SharePoint Online*, además este tipo de soluciones se almacena en la base de datos y no en el sistema de archivos de *SharePoint*.

## Alcance 

Esto define el limite de accesos a los recursos dentro del sistema, para este caso, las soluciones *Sandboxed* tienen acceso a las características de *Sitio de colección* y de *sitio web*.

## Ejecución de código

Los ensamblados de este tipo de soluciones se almancenan en la base de datos de contenido, cuando se requieren se cargan y son ejecutados por el proceso *SPCUWorkeProcess.exe*, este proceso corre con restricciones muy altas sobre los privilegión para evitar la ejecución de código malicioso o código cree problemas de ejecución en la granja.

## Restricciones

*   No puede acceder a los archivos del sistema
*   No puede llamar servicios web o tener acceso a la red
*   No puede llamar ensamblados globales o que no sean marcados como seguros
*   No puede usar tipos del ensamblado *Microsoft.SharePoint.Administration*