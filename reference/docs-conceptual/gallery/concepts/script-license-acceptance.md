---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Requerir aceptación de licencia para scripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328086"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="d22b8-103">Requerir aceptación de licencia para scripts</span><span class="sxs-lookup"><span data-stu-id="d22b8-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="d22b8-104">No se admite la aceptación de la licencia para los scripts.</span><span class="sxs-lookup"><span data-stu-id="d22b8-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="d22b8-105">Sin embargo, sí se admite el escenario en que un script depende de un módulo que requiere la aceptación de la licencia.</span><span class="sxs-lookup"><span data-stu-id="d22b8-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="d22b8-106">Los comandos de script (Install-Script/Save-Script/Update-Script) admiten un parámetro nuevo, -AcceptLicense, que se comporta como si el usuario hubiese visto la licencia.</span><span class="sxs-lookup"><span data-stu-id="d22b8-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="d22b8-107">Si no se especifica -AcceptLicense, el usuario verá el archivo license.txt para el módulo dependiente y se le pedirá que acepte la licencia.</span><span class="sxs-lookup"><span data-stu-id="d22b8-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="d22b8-108">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="d22b8-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="d22b8-109">Ejemplo 1: instalación de un script con dependencias que requiere la aceptación de la licencia</span><span class="sxs-lookup"><span data-stu-id="d22b8-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="d22b8-110">El script "ScriptRequireLicenseAcceptance" depende del módulo "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="d22b8-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="d22b8-111">Se solicita al usuario que acepte la licencia.</span><span class="sxs-lookup"><span data-stu-id="d22b8-111">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="d22b8-112">Ejemplo 2: instalación de un script con dependencias que requiere la aceptación de la licencia y -AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="d22b8-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="d22b8-113">El script "ScriptRequireLicenseAcceptance" depende del módulo "ModuleRequireLicenseAcceptance".</span><span class="sxs-lookup"><span data-stu-id="d22b8-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="d22b8-114">No se le pide al usuario que acepte la licencia porque se especifica -AcceptLicense.</span><span class="sxs-lookup"><span data-stu-id="d22b8-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="d22b8-115">Más detalles</span><span class="sxs-lookup"><span data-stu-id="d22b8-115">More details</span></span>

- [<span data-ttu-id="d22b8-116">Compatibilidad de Requerir la aceptación de la licencia para los módulos</span><span class="sxs-lookup"><span data-stu-id="d22b8-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="d22b8-117">Compatibilidad de Requerir la aceptación de la licencia en PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="d22b8-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="d22b8-118">Requerir la aceptación de licencia de Implementar en Azure Automation</span><span class="sxs-lookup"><span data-stu-id="d22b8-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
