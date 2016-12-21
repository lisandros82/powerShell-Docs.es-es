---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: El objeto ObjectModelRoot
ms.technology: powershell
ms.assetid: 13fcf7ee-b18f-4499-a2b4-ccfc4484cd88
ms.openlocfilehash: f25dfea23ba865d98f09ae9b1604ade8b1c4f72a
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-objectmodelroot-object"></a>El objeto ObjectModelRoot
  El objeto **$psISE**, que es el objeto raíz de entidad de seguridad en el Entorno de scripting integrado (ISE) de Windows PowerShell®, es una instancia de la clase Microsoft.PowerShell.Host.ISE.ObjectModelRoot. En este tema se describen las propiedades del objeto **ObjectModelRoot**.

## <a name="properties"></a>Propiedades

### <a name="currentfile"></a>CurrentFile
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene el archivo, que está asociado a este objeto host que tiene actualmente el foco.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene de la pestaña de PowerShell que tiene el foco.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene la herramienta de complemento de Windows PowerShell ISE actualmente visible que se encuentra en el panel de herramientas horizontal en la parte inferior del editor.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene la herramienta de complemento de Windows PowerShell ISE actualmente visible que se encuentra en el panel de herramientas vertical en el lado derecho del editor.

### <a name="options"></a>Options
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene las distintas opciones que pueden cambiar la configuración de Windows PowerShell ISE.

### <a name="powershelltabs"></a>PowerShellTabs
  Se admite en Windows PowerShell ISE 2.0 y versiones posteriores. 

 La propiedad de solo lectura que obtiene la colección de las pestañas de PowerShell que están abiertas en Windows PowerShell ISE. De forma predeterminada, este objeto contiene una pestaña de PowerShell. Sin embargo, puede agregar más pestañas de PowerShell a este objeto mediante scripts o mediante los menús de Windows PowerShell ISE.

## <a name="see-also"></a>Véase también
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)

  
