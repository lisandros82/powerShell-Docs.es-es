---
ms.date: 08/25/2017
keywords: powershell, cmdlet
title: El objeto ObjectModelRoot
ms.openlocfilehash: 0b04bdb3127edaac7b504556843efb64ee65ed13
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736035"
---
# <a name="the-objectmodelroot-object"></a>El objeto ObjectModelRoot

El objeto `$psISE`, que es el objeto raíz de entidad de seguridad en Windows PowerShell® ISE, es una instancia de la clase Microsoft.PowerShell.Host.ISE.ObjectModelRoot. En este tema se describen las propiedades del objeto **ObjectModelRoot**.

## <a name="properties"></a>Propiedades

### <a name="currentfile"></a>CurrentFile

> Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene el archivo, que está asociado a este objeto host que tiene actualmente el foco.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene de la pestaña de PowerShell que tiene el foco.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene la herramienta de complemento de Windows PowerShell ISE actualmente visible que se encuentra en el panel de herramientas horizontal en la parte inferior del editor.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene la herramienta de complemento de Windows PowerShell ISE actualmente visible que se encuentra en el panel de herramientas vertical en el lado derecho del editor.

### <a name="options"></a>Opciones

> Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene las distintas opciones que pueden cambiar la configuración de Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs

> Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.

La propiedad de solo lectura que obtiene la colección de las pestañas de PowerShell que están abiertas en Windows PowerShell ISE. De forma predeterminada, este objeto contiene una pestaña de PowerShell. Sin embargo, puede agregar más pestañas de PowerShell a este objeto mediante scripts o mediante los menús de Windows PowerShell ISE.

## <a name="see-also"></a>Consulte también

- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)