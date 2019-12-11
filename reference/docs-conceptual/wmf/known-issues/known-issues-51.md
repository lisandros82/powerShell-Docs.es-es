---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Problemas conocidos de WMF 5.1
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147955"
---
# <a name="known-issues-in-wmf-51"></a>Problemas conocidos de WMF 5.1

## <a name="starting-powershell-shortcut-as-administrator"></a>Inicio del acceso directo de PowerShell como administrador

Al instalar WMF, si intenta iniciar PowerShell como administrador desde el acceso directo, puede obtener el mensaje "Error no especificado". Vuelva a abrir el acceso directo como no administrador y este ya funcionará incluso como administrador.

## <a name="pester"></a>Pester

En esta versión, hay dos problemas que deben tenerse en cuenta cuando se utilice Pester en Nano Server:

- La realización de pruebas en el propio Pester puede provocar errores debido a las diferencias entre FULL CLR y CORE CLR. En concreto, el método **Validate** no está disponible en el tipo **XmlDocument**. Se sabe que seis pruebas que intentan validar el esquema de los registros de salida de NUnit generan un error.
- Una prueba de cobertura de código genera un error porque el recurso de DSC **WindowsFeature** no existe en Nano Server. Sin embargo, estos errores suelen ser poco preocupantes y pueden ignorarse.

## <a name="operation-validation"></a>Validación de operaciones

- Se produce un error de `Update-Help` para el módulo Microsoft.PowerShell.Operation.Validation porque el URI de ayuda no funciona.

## <a name="dsc-after-uninstall-wmf"></a>DSC después de desinstalar WMF

- La desinstalación de WMF no elimina los documentos MOF de DSC desde la carpeta de configuración. DSC no funcionará correctamente si los documentos MOF contienen propiedades más recientes que no están disponibles en los sistemas más antiguos. En este caso, ejecute el siguiente script desde la consola de PowerShell con privilegios elevados para limpiar los estados de DSC.

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>Cuentas virtuales de JEA

Los puntos de conexión de JEA y las configuraciones de sesión configuradas para usar las cuentas virtuales de WMF 5.0 no se configurará para utilizar una cuenta virtual después de actualizar a WMF 5.1. Esto significa que los comandos que se ejecutan en sesiones de JEA se ejecutarán bajo la identidad del usuario que se conecta en lugar de una cuenta de administrador temporal, impidiendo posiblemente que el usuario ejecute comandos que requieren privilegios elevados. Para restaurar las cuentas virtuales, debe anular el registro y volver a registrar las configuraciones de sesión que utilizan las cuentas virtuales.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```