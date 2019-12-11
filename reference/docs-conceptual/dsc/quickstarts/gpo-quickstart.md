---
ms.date: 07/09/2019
keywords: DSC, GPO, PowerShell, configuración, instalación
title: 'Inicio rápido: Conversión de directiva de grupo en DSC'
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953472"
---
> <span data-ttu-id="5bbc6-103">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5bbc6-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="5bbc6-104">Inicio rápido: Conversión de directiva de grupo en DSC</span><span class="sxs-lookup"><span data-stu-id="5bbc6-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="5bbc6-105">Puede generar una configuración de DSC a partir de una directiva de grupo o una línea de base de Azure Security Center.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="5bbc6-106">En el módulo [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) se incluyen los comandos siguientes para llevar a cabo esta tarea.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="5bbc6-107">`ConvertFrom-GPO`: convierte directivas de grupo, almacenadas como archivos.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="5bbc6-108">También puede especificar un directorio que contenga varias directivas que se combinarán en una configuración.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="5bbc6-109">Para exportar las directivas de grupo en el entorno, use el cmdlet [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps), o bien siga las instrucciones de [Exportación de un GPO a un archivo](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="5bbc6-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="5bbc6-110">`ConvertFrom-SCM`: convierte las líneas de base del Administrador de cumplimiento de normas de seguridad, almacenadas como archivos `.xml`.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="5bbc6-111">`ConvertFrom-ASC`: convierte las líneas de base de Azure Security Center, almacenadas como archivos `.json`.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="5bbc6-112">`Merge-GPOs`: convierte las directivas de grupo aplicadas a un equipo de destino.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="5bbc6-113">Los cmdlets enumerados anteriormente convierten una línea de base en un archivo `.mof` de DSC.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="5bbc6-114">También puede optar por generar un script de configuración (`.ps1`), que puede editar y volver a compilar.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="5bbc6-115">Los cmdlets detectan errores de compilación para los recursos que faltan, o bien duplican bloques de recursos.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="5bbc6-116">Los bloques de recursos que puedan provocar errores de compilación están comentados.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="5bbc6-117">En el ejemplo siguiente se convierte una [línea de base de seguridad de Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=55319) en un script de configuración de DSC (`.ps1`) y un archivo `.mof`.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="5bbc6-118">Después de ejecutar los comandos, verá dos archivos en el directorio "Output" predeterminado que se ha creado en la ruta de acceso actual.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

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

<span data-ttu-id="5bbc6-119">Cada nodo administrado también necesitará los dos módulos siguientes:</span><span class="sxs-lookup"><span data-stu-id="5bbc6-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="5bbc6-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="5bbc6-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="5bbc6-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="5bbc6-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="5bbc6-122">**BaselineManagement** es una solución desarrollada por la comunidad para que DSC sea más reconocible para obtener soporte técnico para las soluciones de la comunidad que proceden de los encargados del mantenimiento del proyecto y no de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bbc6-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="5bbc6-123">Puede abrir una nueva incidencia para **BaselineManagement** en [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="5bbc6-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5bbc6-124">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="5bbc6-124">Next steps</span></span>

- <span data-ttu-id="5bbc6-125">Para cargar el script de configuración en la configuración de estado de Azure Automation, vea [Introducción](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="5bbc6-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="5bbc6-126">Agregue los módulos **SecurityPolicyDSC** y **AuditPolicyDSC** a la [cuenta de Automation](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="5bbc6-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="5bbc6-127">Encuentre las configuraciones y los recursos de DSC en la [Galería de PowerShell](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="5bbc6-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
