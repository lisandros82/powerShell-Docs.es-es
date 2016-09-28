---
title: "Problemas conocidos de WMF 5.1 (versión preliminar)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 3dde62efa7ba595ed5160cc81b4e2b17a54e52a2
ms.openlocfilehash: d4c9e88ddd6cfaec611527d19d00cbd4db9f5d1d

---

#Problemas conocidos de WMF 5.1 (versión preliminar) #

> Nota: Esta información es preliminar y está sujeta a cambios.

##Inicio del acceso directo de PowerShell como administrador
Al instalar WMF, si intenta iniciar PowerShell como administrador desde el acceso directo, puede obtener el mensaje "Error no especificado".
Vuelva a abrir el acceso directo como no administrador y dicho acceso directo funcionará ahora incluso como administrador.

##Pester
En esta versión, hay dos problemas que deben tenerse en cuenta cuando se utilice Pester en Nano Server:

* La realización de pruebas en el propio Pester puede provocar errores debido a las diferencias entre FULL CLR y CORE CLR. En concreto, el método Validate no está disponible en el tipo XmlDocument. Se sabe que seis pruebas que intentan validar el esquema de los registros de salida de NUnit generan un error. 
* En la actualidad, una prueba de cobertura de código genera un error porque el recurso de DSC *WindowsFeature* no existe en Nano Server. Sin embargo, estos errores suelen ser poco preocupantes y pueden ignorarse.

##Validación de operaciones 

* Se producirá un error de Update-Help para el módulo Microsoft.PowerShell.Operation.Validation porque el URI de ayuda no funciona.



<!--HONumber=Sep16_HO4-->


