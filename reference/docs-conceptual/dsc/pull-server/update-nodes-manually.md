---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Actualización de nodos a partir de un servidor de extracción
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955102"
---
# <a name="update-nodes-from-a-pull-server"></a>Actualización de nodos a partir de un servidor de extracción

En las secciones siguientes se supone que ya ha configurado un servidor de extracción. De no ser así, puede usar las siguientes guías:

- [Configuración de un servidor de extracción SMB de DSC](pullServerSmb.md)
- [Configuración de un servidor de extracción HTTP de DSC](pullServer.md)

Cada nodo de destino puede configurarse para descargar configuraciones y recursos, e incluso para notificar de su estado. Este artículo le mostrará cómo cargar recursos para que estén disponibles para su descarga, así como configurar clientes para descargar automáticamente los recursos. Cuando el nodo recibe una configuración asignada, a través de **extracción** o **inserción** (v5), descarga automáticamente todos los recursos requeridos por la configuración de la ubicación especificada en el LCM.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Uso del cmdlet Update-DSCConfiguration

A partir de PowerShell 5.0, el cmdlet [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) obliga a un nodo a actualizar su configuración desde el servidor de extracción configurado en el LCM.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Uso de Invoke-CimMethod

En PowerShell 4.0, aún puede forzar manualmente a un cliente de extracción para que actualice su configuración usando [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). El ejemplo siguiente crea una sesión CIM con credenciales especificadas, invoca el método adecuado de CIM y quita la sesión.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Véase también

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
