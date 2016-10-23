
DSC usa la clave de registro <b>DSCAutomationHostEnabled </b> de <b>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System</b> para configurar automáticamente la máquina en el arranque inicial.
DSCAutomationHostEnabled admite tres modos:

|  Valor de DSCAutomationHostEnabled  |  Descripción   | 
|---|---| 
0 | Deshabilita la configuración de la máquina en el arranque. |
1 | Habilita la configuración de la máquina en el arranque. |
2 | Habilita la configuración de la máquina solo si DSC está en estado pendiente o actual. Este es el valor predeterminado. |




<!--HONumber=Oct16_HO2-->


