---
ms.date: 2017-06-09
schema: 2.0.0
keywords: powershell
title: RequireLicenseAcceptance
ms.openlocfilehash: 260ccc1ee52d09a640e88203c5644f20f9723d6f
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2017
---
# <a name="modules-requiring-license-acceptance"></a>Módulos que requieren la aceptación de la licencia

## <a name="synopsis"></a>SINOPSIS
Los departamentos jurídicos de los publicadores de algunos módulos requieren que los clientes acepten la licencia de manera explícita antes de instalar el módulo desde la Galería de PowerShell. Si un usuario instala, actualiza o guarda un módulo con PowerShellGet, ya sea directamente o como una dependencia de otro elemento, y ese módulo requiere que el usuario acepte una licencia, el usuario debe indicar que acepta la licencia o la operación generará un error.

## <a name="publish-requirements-for-modules"></a>Requisitos de publicación de los módulos

Los módulos que requieran que los usuarios acepten la licencia deberán cumplir los requisitos siguientes:
    
- La sección PSData del manifiesto del módulo debe incluir RequireLicenseAcceptance = $True.
- El módulo debe incluir el archivo license.txt en el directorio raíz.
- El manifiesto del módulo debe incluir el URI de la licencia.
- El módulo se debe publicar con la versión 2.0 de PowerShellGet Format o una versión superior.

## <a name="impact-on-installsaveupdate-module"></a>Impacto en Install/Save/Update-Module

- Los cmdlets Install/Save/Update admitirán un parámetro nuevo, –AcceptLicense, que se comportará como si el usuario hubiese visto la licencia.
- Si RequiredLicenseAcceptance es True y no se especifica –AcceptLicense, el usuario verá el archivo license.txt y se le preguntará: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot; (¿Acepta estos términos de licencia? [Sí/No/SíATodo/NoATodo]).
  - Si se acepta la licencia
    - **Save-Module:** el módulo se copiará en el sistema del usuario.
    - **Install-Module:** el módulo se copiará en el sistema del usuario, en la carpeta correspondiente (según el ámbito).
    - **Update-Module:** el módulo se actualizará.
  - Si se rechaza la licencia 
    - Se cancelará la operación.
- Todos los cmdlets buscarán los metadatos (requireLicenseAcceptance y Format Version) que indican que se requiere aceptar la licencia
  - Si la versión del formato de cliente es anterior a 2.0, la operación presentará un error y le pedirá al usuario que actualice el cliente.
  - Si el módulo se publicó con una versión del formato anterior a 2.0, se omitirá la marca requireLicenseAcceptance.

    
 ## <a name="module-dependencies"></a>Dependencias de módulo
- Durante la operación Install/Save/Update, si un módulo dependiente (si algo más depende del módulo) requiere aceptar la licencia, se requerirá el comportamiento de aceptación de la licencia (ya mencionado).
- Si la versión del módulo ya aparece en el catálogo local como instalada en el sistema, se omitirá la comprobación de la licencia.
- Durante la operación Install/Save/Update, si un módulo dependiente requiere una licencia y no se produce la aceptación de esta, la operación presentará un error y seguirá los procesos normales del elemento que no se instaló, guardó o actualizó.

 ## <a name="impact-on--force"></a>Impacto en -Force

Especificar –Force NO es suficiente para aceptar una licencia. Se requiere –AcceptLicense para tener permiso para realizar la instalación. Si se especifica –Force, RequiredLicenseAcceptance es True y NO se especifica –AcceptLicense, no se realizará la operación.

## <a name="examples"></a>EJEMPLOS

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Ejemplo 1: actualización del manifiesto del módulo para requerir la aceptación de la licencia
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable
    
 } # End of PrivateData hashtable
```
Este comando actualiza el archivo de manifiesto y establece la marca RequireLicenseAcceptance en true.
### <a name="example-2-install-module-requiring-license-acceptance"></a>Ejemplo 2: instalación de un módulo que requiere la aceptación de la licencia
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 

```
Este comando muestra la licencia del archivo license.txt y le pide al usuario que acepte la licencia.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Ejemplo 3: instalación de un módulo que requiere la aceptación de la licencia con -AcceptLicense
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
El módulo se instala sin que aparezca ningún mensaje que pida aceptar la licencia.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Ejemplo 4: instalación de un módulo que requiere la aceptación de la licencia con -Force
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Ejemplo 5: instalación de un módulo con dependencias que requiere la aceptación de la licencia
El módulo "ModuleWithDependency" depende del módulo "ModuleRequireLicenseAcceptance". Se solicita al usuario que acepte la licencia.
```PowerShell
PS C:\> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Ejemplo 6: instalación de un módulo con dependencias que requiere la aceptación de la licencia y -AcceptLicense
El módulo "ModuleWithDependency" depende del módulo "ModuleRequireLicenseAcceptance". No se le pide al usuario que acepte la licencia porque se especifica -AcceptLicense.
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Ejemplo 7: instalación de un módulo que requiere la aceptación de la licencia en un cliente anterior a PSGetFormatVersion 2.0
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a>Ejemplo 8: guardado de un módulo que requiere la aceptación de la licencia
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 
```
Este comando muestra la licencia del archivo license.txt y le pide al usuario que acepte la licencia.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Ejemplo 9: guardado de un módulo que requiere la aceptación de licencia con -AcceptLicense
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
El módulo se guarda sin que aparezca ningún mensaje que pida aceptar la licencia.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Ejemplo 10: actualización de un módulo que requiere la aceptación de la licencia
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance

License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): 
```
Este comando muestra la licencia del archivo license.txt y le pide al usuario que acepte la licencia.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Ejemplo 11: actualización de un módulo que requiere la aceptación de licencia con -AcceptLicense
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
El módulo se actualiza sin que aparezca ningún mensaje que pida aceptar la licencia.

## <a name="more-details"></a>Más detalles
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[Requerir la aceptación de la licencia para Scripts](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[Compatibilidad de Requerir la aceptación de la licencia en PowerShellGallery](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[Requerir la aceptación de licencia de Implementar en Azure Automation](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
