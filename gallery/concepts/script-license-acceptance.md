---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Requerir aceptación de licencia para scripts
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="requiring-license-acceptance-for-scripts"></a>Requerir aceptación de licencia para scripts

No se admite la aceptación de la licencia para los scripts. Sin embargo, sí se admite el escenario en que un script depende de un módulo que requiere la aceptación de la licencia.

Los comandos de script (Install-Script/Save-Script/Update-Script) admiten un parámetro nuevo, -AcceptLicense, que se comporta como si el usuario hubiese visto la licencia. Si no se especifica -AcceptLicense, el usuario verá el archivo license.txt para el módulo dependiente y se le pedirá que acepte la licencia.

## <a name="examples"></a>EJEMPLOS

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Ejemplo 1: instalación de un script con dependencias que requiere la aceptación de la licencia

El script "ScriptRequireLicenseAcceptance" depende del módulo "ModuleRequireLicenseAcceptance". Se solicita al usuario que acepte la licencia.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Ejemplo 2: instalación de un script con dependencias que requiere la aceptación de la licencia y -AcceptLicense

El script "ScriptRequireLicenseAcceptance" depende del módulo "ModuleRequireLicenseAcceptance". No se le pide al usuario que acepte la licencia porque se especifica -AcceptLicense.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Más detalles

- [Compatibilidad de Requerir la aceptación de la licencia para los módulos](module-license-acceptance.md)
- [Compatibilidad de Requerir la aceptación de la licencia en PowerShellGallery](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [Requerir la aceptación de licencia de Implementar en Azure Automation](../how-to/working-with-items/deploy-to-azure-automation.md)