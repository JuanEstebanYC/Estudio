# Trabajando con Site y Web

## Ciclo de vida de los objetos

Los problemas en el rendimiento de los desarrollos a la medida hechos en *SharePoint* se pueden presentar por cargar la memoria con objetos que no se usan, por esta razón es importante saber cuando y cómo es adecuado hacer el *Dispose* de un objeto *SPSite* o *SPWeb*.

Para hacer un dispose adecuado, es requerido hacerlo sobre los objetos creados y no los objetos asignados desde propiedades estaticas como lo son por ejemplo *SPContext.Current.Web* o *SPContext.Current.SPSite*.

Para un correcto *Dispose* es recomendable usar bloques *Try - Catch - Finally* y en el *Finally* hacer el dispose del objeto requerido o un bloque *Using* con el fin de hacer el *Dispose* automaticamente cuando se finalice la ejecución de la sección de código.