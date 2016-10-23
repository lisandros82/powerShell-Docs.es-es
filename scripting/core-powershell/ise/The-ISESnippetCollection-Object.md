---
title: El objeto ISESnippetCollection
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: 410cd4503883ea2cc02936044d7357b9cb029274

---

# El objeto ISESnippetCollection
  El objeto **ISESnippetCollection** es una colección de objetos **ISESnippet**. La colección de archivos que está asociada con un objeto **PowerShellTab** es un miembro de esta clase. Un ejemplo es la colección **$psISE.CurrentPowerShellTab.Files**.

## Métodos

### Load\( FilePathName \)
  Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores. 

 Carga un archivo .snippets.ps1xml que contiene fragmentos de código definidos por el usuario. La manera más fácil de crear fragmentos de código es usar el cmdlet New\-IseSnippet, que los almacena automáticamente en la carpeta de perfil para que se carguen cada vez que inicie Windows PowerShell ISE.

 **FilePathName** (cadena). La ruta de acceso y el nombre de un archivo .snippets.ps1xml que contiene las definiciones de fragmento de código.

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## Véase también
- [ISESnippetObject](The-ISESnippetObject.md) 
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Oct16_HO3-->


