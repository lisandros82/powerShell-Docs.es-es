---
title: Problemas conocidos de WMF 5.1
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 8f1b550e92c3c280b84664e0b1f9695172370522
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="known-issues-in-wmf-51"></a>Problemas conocidos de WMF 5.1 #

> Nota: Esta información está sujeta a cambios.

## <a name="starting-powershell-shortcut-as-administrator"></a>Inicio del acceso directo de PowerShell como administrador
Al instalar WMF, si intenta iniciar PowerShell como administrador desde el acceso directo, puede obtener el mensaje "Error no especificado".
Vuelva a abrir el acceso directo como no administrador y dicho acceso directo funcionará ahora incluso como administrador.

## <a name="pester"></a>Pester
En esta versión, hay dos problemas que deben tenerse en cuenta cuando se utilice Pester en Nano Server:

* La realización de pruebas en el propio Pester puede provocar errores debido a las diferencias entre FULL CLR y CORE CLR. En concreto, el método Validate no está disponible en el tipo XmlDocument. Se sabe que seis pruebas que intentan validar el esquema de los registros de salida de NUnit generan un error. 
* En la actualidad, una prueba de cobertura de código genera un error porque el recurso de DSC *WindowsFeature* no existe en Nano Server. Sin embargo, estos errores suelen ser poco preocupantes y pueden ignorarse.

## <a name="operation-validation"></a>Validación de operaciones 

* Se producirá un error de Update-Help para el módulo Microsoft.PowerShell.Operation.Validation porque el URI de ayuda no funciona.

## <a name="dsc-after-uninstall-wmf"></a>DSC después de desinstalar WMF 
* La desinstalación de WMF no elimina los documentos MOF de DSC desde la carpeta de configuración. DSC no funcionará correctamente si los documentos MOF contienen propiedades más recientes que no están disponibles en los sistemas más antiguos. En este caso, ejecute el siguiente script desde la consola de PowerShell con privilegios elevados para limpiar los estados de DSC.
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  