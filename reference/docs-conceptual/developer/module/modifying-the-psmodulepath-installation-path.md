---
title: Modificando la ruta de instalación de PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953847"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Cambio de la ruta de instalación de PSModulePath

La variable de entorno `PSModulePath` almacena las rutas de acceso a las ubicaciones de los módulos que están instalados en el disco. PowerShell usa esta variable para buscar módulos cuando el usuario no especifica la ruta de acceso completa a un módulo. Las rutas de acceso de esta variable se buscan en el orden en que aparecen.

Cuando se inicia PowerShell, `PSModulePath` se crea como una variable de entorno del sistema con el siguiente valor predeterminado: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` o `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` para Windows PowerShell.

## <a name="to-view-the-psmodulepath-variable"></a>Para ver la variable PSModulePath

Para ver las rutas de acceso que se especifican en la variable `PSModulePath`, escriba el siguiente comando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Para agregar ubicaciones a la variable PSModulePath

Para agregar rutas de acceso a esta variable, use uno de los métodos siguientes:

- Para agregar un valor temporal que solo está disponible para la sesión actual, ejecute el siguiente comando en la línea de comandos:

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Para agregar un valor persistente que esté disponible cada vez que se abra una sesión, agregue el comando anterior a un archivo de Perfil de PowerShell (`$PROFILE`) >

  Para obtener más información sobre los perfiles, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

- Para agregar una variable persistente al registro, cree una nueva variable de entorno de usuario denominada `PSModulePath` mediante el editor de variables de entorno en el cuadro de diálogo **propiedades del sistema** .

- Para agregar una variable persistente mediante un script, use el método .net [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) en la clase [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) . Por ejemplo, el siguiente script agrega el `C:\Program Files\Fabrikam\Module` ruta de acceso al valor de la variable de entorno `PSModulePath` para el equipo. Para agregar la ruta de acceso a la variable de entorno User `PSModulePath`, establezca el destino en "User".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Para quitar ubicaciones de PSModulePath

Puede quitar rutas de acceso de la variable mediante métodos similares: por ejemplo, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` quitará la ruta de acceso **c:\ModulePath** de la sesión actual.

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
