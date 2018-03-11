# Configurando Características y Soluciones

## Escenarios de dependencia

*   **Agrupación (Grouping)**: Esto se da cuando se requiere que se activen características "ocultas" cuando activo una característica principal.
*   **Recursos Garantizados (Resource guarantees)**: Se utiliza cuando se requiere que exista una característica o un recurso activado antes de activar la característica principal.

## [Reglas de dependencia][Reglas]

Reglas hechas para evitar las dependencias circulares y problemas de performance.

*   **Cadena de dependencias (Dependency Chains)**: Sí la característica A depende de la B, esta última no debe tener dependencias con otra característica.
*   **Características Ocultas (Hidden Features)**: Estas características estan destinadas ha ser usadas por otras características. Las características ocultas no deben tener dependencia.
*   **Dependencias de igual alcance (Same-Scope Dependencies)**: Si la característica A depende de la B y ambas tienen el mismo alcance (scope), la B se activa automaticamente cuando la A sea activada.
*   **Dependencias de varios alcances**: Las características solo dependen de otra característica de un alcance menos restrictivo.

## Creando Feature Receivers

Para crear un *Feature Receiver* es necesario heredar de la clase **SPFeatureReceiver**, con esto se tiene la posibilidad de sobreescribir los métodos de la clase base que responden a los siguientes eventos
*   *FeatureInstalled*
*   *FeatureActivated*
*   *FeatureUpgrading*
*   *FeatureDeactivating*
*   *FeatureUninstalling*



[Reglas]:https://msdn.microsoft.com/library/aa543162.aspx