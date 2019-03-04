---
title: Nomenclatura de archivos de ayuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856671"
---
# <a name="naming-help-files"></a>Asignación de un nombre a los archivos de ayuda

En este tema se explica cómo asignar un nombre de un archivo de ayuda basado en XML para que la [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet puede encontrarlo. Los requisitos de nombre varían para cada tipo de comando.
En este tema se explica cómo asignar un nombre de un archivo de ayuda basado en XML para que la [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet puede encontrarlo. Los requisitos de nombre varían para cada tipo de comando.

## <a name="cmdlet-help-files"></a>Archivos de Ayuda de cmdlet

El archivo de ayuda para un C# cmdlet debe tener el nombre del ensamblado donde se define el cmdlet. Use el siguiente formato de nombre de archivo:

```
<AssemblyName>.dll-help.xml
```

El formato de nombre de ensamblado es necesario incluso si el ensamblado es un módulo anidado.

Por ejemplo, el [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet se define en el ensamblado Microsoft.PowerShell.Diagnostics.dll. El `Get-Help` cmdlet busca un tema de ayuda para el `Get-WinEvent` cmdlet solo en el archivo Microsoft.PowerShell.Diagnostics.dll help.xml en el directorio del módulo.
Por ejemplo, el [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet se define en el ensamblado Microsoft.PowerShell.Diagnostics.dll. El `Get-Help` cmdlet busca un tema de ayuda para el `Get-WinEvent` cmdlet solo en el archivo Microsoft.PowerShell.Diagnostics.dll help.xml en el directorio del módulo.

## <a name="provider-help-files"></a>Archivos de Ayuda de proveedor

El archivo de ayuda para un proveedor de Windows PowerShell debe llamarse para el ensamblado en el que se define el proveedor. Use el siguiente formato de nombre de archivo:

```
<AssemblyName>.dll-help.xml
```

El formato de nombre de ensamblado es necesario incluso si el ensamblado es un módulo anidado.

Por ejemplo, el proveedor de certificados se define en el ensamblado Microsoft.PowerShell.Security.dll. El `Get-Help` cmdlet busca un tema de ayuda para el proveedor de certificados solo en el archivo Microsoft.PowerShell.Security.dll help.xml en el directorio del módulo.

## <a name="function-help-files"></a>Archivos de Ayuda de función

Se pueden documentar las funciones mediante el uso de [Ayuda basada en comentarios](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentados en un archivo de ayuda XML. Cuando la función está documentada en un archivo XML, la función debe tener un `.ExternalHelp` comentar la palabra clave que asocia la función con el archivo XML. En caso contrario, el `Get-Help` cmdlet no encuentra el archivo de ayuda.
Se pueden documentar las funciones mediante el uso de [Ayuda basada en comentarios](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentados en un archivo de ayuda XML. Cuando la función está documentada en un archivo XML, la función debe tener un `.ExternalHelp` comentar la palabra clave que asocia la función con el archivo XML. En caso contrario, el `Get-Help` cmdlet no encuentra el archivo de ayuda.

No hay ningún requisito técnico para el nombre de un archivo de Ayuda de la función. Sin embargo, una práctica recomendada es un nombre al archivo de ayuda para el módulo de script en el que se define la función. Por ejemplo, la siguiente función se define en el archivo MyModule.psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Archivos de Ayuda de comandos CIM

El archivo de ayuda para un comando CIM debe llamarse para el archivo CDXML en el que se define el comando CIM. Use el siguiente formato de nombre de archivo:

```
<FileName>.cdxml-help.xml
```

Los comandos CIM se definen en los archivos CDXML que pueden incluirse en módulos como módulos anidados. Cuando se importa el comando CIM en la sesión como una función, Windows PowerShell agrega un `.ExternalHelp` comentario palabra clave para la definición de función que se asocia un ayuda XML a la función de archivo que se denomina para el archivo CDXML en el que se define el comando CIM.

## <a name="script-workflow-help-files"></a>Archivos de Ayuda de flujo de trabajo de script

Los flujos de trabajo que se incluyen en los módulos pueden documentarse en archivos de ayuda basado en XML. No hay ningún requisito técnico para el nombre del archivo de ayuda. Sin embargo, una práctica recomendada es un nombre al archivo de ayuda para el módulo de script en el que se define el flujo de trabajo de script. Por ejemplo:

```
<ScriptModule>.psm1-help.xml
```

A diferencia de otros archivos de comandos, los flujos de trabajo no requieren un `.ExternalHelp` comentar la palabra clave para asociarlos a un archivo de ayuda. En su lugar, Windows PowerShell busca los subdirectorios específicos de la referencia cultural de interfaz de usuario del directorio de módulo para los archivos de ayuda basado en XML y busca ayuda para el flujo de trabajo de script en todos los archivos. `.ExternalHelp` se omite la palabra clave de comentario.

Dado que el `.ExternalHelp` se omite la palabra clave de comentario, el `Get-Help` cmdlet puede encontrar ayuda para los flujos de trabajo solo cuando se incluyen en los módulos.