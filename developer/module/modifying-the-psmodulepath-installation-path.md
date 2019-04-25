---
title: Modificar la ruta de instalación PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082216"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Cambio de la ruta de instalación de PSModulePath

El `PSModulePath` variable de entorno almacena las rutas de acceso a las ubicaciones de los módulos que están instalados en el disco. Windows PowerShell usa esta variable para buscar módulos cuando el usuario no especifica la ruta de acceso completa a un módulo. Las rutas de acceso en esta variable se buscan en el orden en que aparecen.

Cuando se inicia Windows PowerShell, `PSModulePath` se crea como una variable de entorno del sistema con el siguiente valor predeterminado: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Para ver la variable PSModulePath

Para ver las rutas de acceso que se especifican en el `PSModulePath` variable, escriba el siguiente comando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Agregar ubicaciones a la variable PSModulePath

Para agregar las rutas de acceso a esta variable, use uno de los métodos siguientes:

- Para agregar un valor temporal que sólo está disponible para la sesión actual, ejecute el siguiente comando en la línea de comandos:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Para agregar un valor persistente que está disponible cada vez que se abre una sesión, agregue el siguiente comando para un perfil de Windows PowerShell:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Para obtener más información acerca de los perfiles, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) en la biblioteca TechNet de Microsoft.

- Para agregar una variable persistente en el registro, cree una nueva variable de entorno de usuario denominada `PSModulePath` con el Editor de Variables de entorno en el **las propiedades del sistema** cuadro de diálogo.

- Para agregar una variable persistente mediante un script, use el **SetEnvironmentVariable** método en la clase de entorno. Por ejemplo, el script siguiente agrega el "C:\Program Files\Fabrikam\Module ruta de acceso al valor de la variable de entorno PSModulePath para el equipo. Para agregar la ruta de acceso a la variable de entorno PSModulePath de usuario, establecer el destino en "Usuario".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Para quitar las ubicaciones de PSModulePath

Puede quitar las rutas de acceso de la variable mediante métodos similares: por ejemplo, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` quitará el **c:\ModulePath** ruta de acceso de la sesión actual.

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
