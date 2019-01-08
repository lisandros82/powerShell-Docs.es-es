---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Actualización de nodos a partir de un servidor de extracción
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402153"
---
# <a name="update-nodes-from-a-pull-server"></a>Actualización de nodos a partir de un servidor de extracción

Las secciones siguientes se suponen que ya ha configurado un servidor de extracción. Si no ha configurado el servidor de incorporación de cambios, puede usar a las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar las configuraciones, recursos e incluso notificado su estado. En este artículo le mostrará cómo cargar recursos para que estén disponibles para descargarse y configurar clientes para descargar automáticamente los recursos. Cuando el nodo recibe una configuración asignada, a través de **extraer** o **Push** (v5), se descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Mediante el cmdlet Update-DSCConfiguration

A partir de PowerShell 5.0, el [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, fuerza un nodo para actualizar su configuración desde el servidor de incorporación de cambios configurado en el LCM.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Uso de Invoke-CIMMethod

En PowerShell 4.0, puede forzar manualmente un cliente de incorporación de cambios para actualizar su configuración mediante [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). El ejemplo siguiente crea una sesión CIM con credenciales especificadas, invoca el método adecuado de CIM y quita la sesión.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Véase también

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
