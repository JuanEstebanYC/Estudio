# Building Application Infraestructure in Azure

*   Es posible transferir discos entre hyper-v y azure solo si los discos son de formato Vhd - Vhdx.
*   Las máquinas virtuales estan aisladas de todo el tráfico público excepto del trafico predefinido por los puestos especificados.
*   Las máquinas virtuales se pueden escalar dependiendo de las necesidades del negocio.
* 'Migration Accelerator' es una herramienta que analiza una aplicación existente y facilita la migración con las configuraciones ya listas.
* Backup y Site Recovery Service son servicios de Azure que ayudar con la generación de backups incrementales y restauración de desastres.
*   Las replicas o backps se almacenan en una cuenta Azure Storage que permite la geo-replicación.
*   Site Recovery provee una monitorización de servicios y usa tecnología como System Center, Hyper-V replica y SQL Always On.
*   Por medio del portal se puede configurar una vpn de tipo Site-to-Site o una de tipo Point-to-Site, además esta configuración se puede hacer por medio de una archivo XML que tenga toda la configuración predefinida.
*   Es posible exportar la configuración de una red y modificarla por medio de una archivo XML que tiene como extención .netcfg.
*   Cuando se crea un recurso que necesite acceso a la red virtual, esta se debe especificar cuando se crea el recurso ya que luego no es posible cambiar la red.
Es posible utilizar NSGs o Network Security Groups para aplicar políticas de acceso.
*   Update domine es una unidad lógica qe agrupa multiples maquinas virtuales y permite hacer actualizaciones en masa.
*   Escalamiento:
    
    -   Vertical: es cambiar el tamaño de la máquina.
    -   Horizontal: es aumentar el número de las instancias.

*   Es posible hacer un escalamiento dependiendo del uso de la CPU y el número de peticiones al servidos, para definir el escalamiento se necesita:

    -   Un calendario definido.
    -   Métricas de uso de CPU y mensajería soportada.
    -   Número de instancias a usar.

*   Todas las máquinas se comunican por medio de una red nterna virtual y si se requiere acceso desde el exterior es necesario habilitar un endpoint.
*   Cuando se crea una máquina virtual por medio de Networtk Access Control List se habilitan o deshabilitan los accesos desde el exterior y el interior de la red.

    -   ACL (Access Control List): Habilita el tráfico hacia la máquina virtual.
    -   NGS (Network Security Group): Habilita el acceso desde la red (Vnet).