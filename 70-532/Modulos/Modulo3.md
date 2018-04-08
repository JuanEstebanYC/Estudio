# Hosting Web Applications on the Azure Plataform

*   Web Apps es PaaS (Pataforma como servicio por sus siglas en inglés) y permite una configuración rápida de servicios como Always On, custom domain, escalabilidad entre otros.
*   La flexibilidad es una oportunidad que se brinda al utilizar Web Apps ya que permite varios frameworks, no solo .Net, sino Java, PHP, Node.js o Python, tambien tiene la versatilidad de poder desplegar con Git o Kudu aplicaciones Node.js y PHP.
*   La escalabilidad es otro punto a tener en cuenta ya que es fácil de implementar y dejar que Azure cree una cantidad adecuadad de instancias de la aplicación y por medio de un balanceador de carga distribuir el trabajo sin tener problemas con el servicio.
*   App Service Plan es una agrupación lógica de aplicaciones que comparten características como capacidad y capas entre otra.
*   Multiples Wen Apps pueden estar en un mismo App Service Plan y multiplies App Services Plan pueden estar en un Resource Group.
*   Cuando se requiera, es posible hacer un escalamiento de un App Service Plan y con esto todas las aplicaciones que estas dentro del Plan, esto es cuando se hace el escalamiento del Plan las aplicaciones dentro de este se clonan según la cantidad de instancias y comienza a funcionar un balanceador de cargas interno para dar el soporte necesario a las peticiones de los usuarios.


## AlwaysOn

Si se hospeda una aplicación en IIS, esta se reinicia cada 'X' tiempo por medio de un calendario de tareas programadas y solo se ejecutan las tareas iniciales de la aplicación cuando se hace una nueva petición. 

Esto se puede solucionar, dentro de IIS, con un modo de inicio Always Running. Para las Web Apps en Azure esta característica se puede usar activando la característica Always On. 
Esto evita que se recicle la aplicación y con esto que siempre este en ejecución y en el caso de un reinicio, esta característica inicia de inmediato la aplicación ejecutando las tareas iniciales.

## Domain Names

Es posible usar nombres de nominio para las aplicaciones, esto se hace desde la característica 'Manage Domains' dentro del portal de Azure. 
Luego es necesario matricular el CNAME dentro del DNS que apunte a la dirección de la aplicación en Azure (appname.azurewebsite.net) y posterior a eso se debe matricular la dirección IP (A).