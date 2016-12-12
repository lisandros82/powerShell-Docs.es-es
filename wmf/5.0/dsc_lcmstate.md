# <a name="detailed-information-about-lcm-state"></a>Información detallada acerca del estado de LCM

Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM. El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.
