---
ms.date: 07/09/2019
keywords: DSC, GPO, PowerShell, configuración, instalación
title: 'Inicio rápido: Conversión de directiva de grupo en DSC'
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953472"
---
> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Inicio rápido: Conversión de directiva de grupo en DSC

Puede generar una configuración de DSC a partir de una directiva de grupo o una línea de base de Azure Security Center. En el módulo [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) se incluyen los comandos siguientes para llevar a cabo esta tarea.

- `ConvertFrom-GPO`: convierte directivas de grupo, almacenadas como archivos. También puede especificar un directorio que contenga varias directivas que se combinarán en una configuración.
  - Para exportar las directivas de grupo en el entorno, use el cmdlet [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps), o bien siga las instrucciones de [Exportación de un GPO a un archivo](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM`: convierte las líneas de base del Administrador de cumplimiento de normas de seguridad, almacenadas como archivos `.xml`.
- `ConvertFrom-ASC`: convierte las líneas de base de Azure Security Center, almacenadas como archivos `.json`.
- `Merge-GPOs`: convierte las directivas de grupo aplicadas a un equipo de destino.

Los cmdlets enumerados anteriormente convierten una línea de base en un archivo `.mof` de DSC. También puede optar por generar un script de configuración (`.ps1`), que puede editar y volver a compilar. Los cmdlets detectan errores de compilación para los recursos que faltan, o bien duplican bloques de recursos. Los bloques de recursos que puedan provocar errores de compilación están comentados.

En el ejemplo siguiente se convierte una [línea de base de seguridad de Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=55319) en un script de configuración de DSC (`.ps1`) y un archivo `.mof`.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Después de ejecutar los comandos, verá dos archivos en el directorio "Output" predeterminado que se ha creado en la ruta de acceso actual.

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

Cada nodo administrado también necesitará los dos módulos siguientes:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** es una solución desarrollada por la comunidad para que DSC sea más reconocible para obtener soporte técnico para las soluciones de la comunidad que proceden de los encargados del mantenimiento del proyecto y no de Microsoft. Puede abrir una nueva incidencia para **BaselineManagement** en [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Pasos siguientes

- Para cargar el script de configuración en la configuración de estado de Azure Automation, vea [Introducción](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Agregue los módulos **SecurityPolicyDSC** y **AuditPolicyDSC** a la [cuenta de Automation](/azure/automation/shared-resources/modules).
- Encuentre las configuraciones y los recursos de DSC en la [Galería de PowerShell](https://www.powershellgallery.com/).
