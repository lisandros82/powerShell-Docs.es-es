---
title: Asignar nombres a los archivos de ayuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367014"
---
# <a name="naming-help-files"></a>Asignación de un nombre a los archivos de ayuda

En este tema se explica cómo asignar un nombre a un archivo de ayuda basado en XML para que el cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) pueda encontrarlo. Los requisitos de nombre difieren para cada tipo de comando.

## <a name="cmdlet-help-files"></a>Archivos de ayuda de cmdlet

El archivo de ayuda de C# un cmdlet se debe denominar para el ensamblado en el que se define el cmdlet. Use el siguiente formato de nombre de archivo:

```
<AssemblyName>.dll-help.xml
```

El formato del nombre del ensamblado es necesario incluso cuando el ensamblado es un módulo anidado.

Por ejemplo, [Get-WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) se define en el ensamblado Microsoft. PowerShell. Diagnostics. dll. El cmdlet `Get-Help` busca un tema de ayuda para el cmdlet `Get-WinEvent` solo en el archivo Microsoft. PowerShell. Diagnostics. dll-help. XML en el directorio del módulo.

## <a name="provider-help-files"></a>Archivos de ayuda del proveedor

El archivo de ayuda de un proveedor de Windows PowerShell debe tener un nombre para el ensamblado en el que se define el proveedor. Use el siguiente formato de nombre de archivo:

```
<AssemblyName>.dll-help.xml
```

El formato del nombre del ensamblado es necesario incluso cuando el ensamblado es un módulo anidado.

Por ejemplo, el proveedor de certificados se define en el ensamblado Microsoft. PowerShell. Security. dll. El cmdlet `Get-Help` busca un tema de ayuda para el proveedor de certificados solo en el archivo Microsoft. PowerShell. Security. dll-help. XML en el directorio del módulo.

## <a name="function-help-files"></a>Archivos de ayuda de función

Las funciones se pueden documentar mediante [la ayuda basada en comentarios](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentada en un archivo de ayuda XML. Cuando la función está documentada en un archivo XML, la función debe tener una palabra clave `.ExternalHelp` comment que asocie la función con el archivo XML. De lo contrario, el cmdlet `Get-Help` no puede encontrar el archivo de ayuda.

No hay ningún requisito técnico para el nombre de un archivo de ayuda de función. Sin embargo, se recomienda asignar un nombre al archivo de ayuda para el módulo de script en el que se define la función. Por ejemplo, la siguiente función se define en el archivo MyModule. psm1.

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a>Archivos de ayuda de comandos CIM

El archivo de ayuda de un comando CIM debe tener el nombre del archivo CDXML en el que se define el comando CIM. Use el siguiente formato de nombre de archivo:

```
<FileName>.cdxml-help.xml
```

Los comandos CIM se definen en los archivos CDXML que se pueden incluir en los módulos como módulos anidados. Cuando el comando CIM se importa en la sesión como una función, Windows PowerShell agrega una palabra clave de comentario `.ExternalHelp` a la definición de función que asocia la función a un archivo de ayuda XML denominado para el archivo CDXML en el que se define el comando CIM.

## <a name="script-workflow-help-files"></a>Archivos de ayuda del flujo de trabajo de script

Los flujos de trabajo de script que se incluyen en los módulos se pueden documentar en archivos de ayuda basados en XML. No hay ningún requisito técnico para el nombre del archivo de ayuda. Sin embargo, se recomienda asignar un nombre al archivo de ayuda para el módulo de script en el que se define el flujo de trabajo de script. Por ejemplo:

```
<ScriptModule>.psm1-help.xml
```

A diferencia de otros comandos scripts, los flujos de trabajo de scripts no requieren una palabra clave `.ExternalHelp` comment para asociarlos con un archivo de ayuda. En su lugar, Windows PowerShell busca en los subdirectorios específicos de la referencia cultural de la interfaz de usuario del directorio de módulos para los archivos de ayuda basados en XML y busca ayuda para el flujo de trabajo de script en todos los archivos. `.ExternalHelp` palabra clave comment se omiten.

Dado que se omite la palabra clave `.ExternalHelp` comment, el cmdlet `Get-Help` puede buscar ayuda para flujos de trabajo de scripts solo cuando se incluyen en módulos.