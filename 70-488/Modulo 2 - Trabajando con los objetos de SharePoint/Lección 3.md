# Contexto de ejecución

Es posible obtener el sitio actual, la web actual, el usuario actual entre otra información con el objeto **SPContext**, este objeto representa la instancia actual de ejecución de Sharepoint y almacena información util para trabajar.

La propiedad para acceder a toda esta información es el **SPContext.Current**. Cabe aclarar que la propiedad solo tiene datos cuando se ejecuta una acción que involucre llamados HTTP.

## Usuarios y permisos

Es requerido tener un control de los usuarios y sus permisos dentro del *Web* con el fin de que al momento de ingresar a una página, solo si tiene el nivel de permisos requerido puede ver el contenido.

Para esta tarea, se puede utilizar dentro del código una validación y obtener el usuarios actual y comprobar desde el web actual si este tiene o no los permisos suficientes. [Leer][PermisosWebUsuarioActual]

Los permisos en Sharepoint estan enunciados en el *enum* **SPBasePermissions**

Tambien es posible desde la creación de las páginas crear secciónes que solo algunos usuarios con permisos especiales puedan ver, este es el caso del control 
*SPSecurityTrimmedControl*. [Leer][SPSecurityTrimmedControl]

En ocasiones es requerido ejecutar fragmentos de código que requieren permisos elevados de usuario, es aquí cuando entra en funcionamiento el método **SPSecurity.RunWithElevatedPrivileges** esto hace que se ejecute el código con la cuenta del *Application Pool* y no con el usuario actual.

Solo es posible ejecutar procesos con permisos elevados cuando es una *Farm Solution*.


[PermisosWebUsuarioActual]:https://social.msdn.microsoft.com/Forums/office/en-US/80c6a4cb-efa9-4d4b-8d6e-517175e4ba69/sharepoint-checking-if-current-user-has-permissions-for-site?forum=sharepointdevelopmentlegacy

[SPSecurityTrimmedControl]:https://sharepoint.stackexchange.com/questions/72774/how-to-use-spsecuritytrimmedcontrol-to-check-if-current-user-has-edit-rights-to