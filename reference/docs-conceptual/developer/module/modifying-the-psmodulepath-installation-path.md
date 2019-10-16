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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360674"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Cambio de la ruta de instalación de PSModulePath

La variable de entorno `PSModulePath` almacena las rutas de acceso a las ubicaciones de los módulos que están instalados en el disco. Windows PowerShell usa esta variable para buscar módulos cuando el usuario no especifica la ruta de acceso completa a un módulo. Las rutas de acceso de esta variable se buscan en el orden en que aparecen.

Cuando Windows PowerShell se inicia, se crea `PSModulePath` como una variable de entorno del sistema con el siguiente valor predeterminado: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Para ver la variable PSModulePath

Para ver las rutas de acceso especificadas en la variable `PSModulePath`, escriba el siguiente comando:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Para agregar ubicaciones a la variable PSModulePath

Para agregar rutas de acceso a esta variable, use uno de los métodos siguientes:

- Para agregar un valor temporal que solo está disponible para la sesión actual, ejecute el siguiente comando en la línea de comandos:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Para agregar un valor persistente que esté disponible cada vez que se abra una sesión, agregue el siguiente comando a un perfil de Windows PowerShell:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Para obtener más información acerca de los perfiles, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) en la biblioteca de Microsoft TechNet.

- Para agregar una variable persistente al registro, cree una nueva variable de entorno de usuario llamada `PSModulePath` mediante el editor de variables de entorno en el cuadro de diálogo **propiedades del sistema** .

- Para agregar una variable persistente mediante un script, use el método **SetEnvironmentVariable** en la clase Environment. Por ejemplo, el siguiente script agrega la ruta de acceso "C:\Archivos de Files\Fabrikam\Module al valor de la variable de entorno PSModulePath para el equipo. Para agregar la ruta de acceso a la variable de entorno User PSModulePath, establezca el destino en "User".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Para quitar ubicaciones de PSModulePath

Puede quitar rutas de acceso de la variable mediante métodos similares: por ejemplo, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` quitará la ruta de acceso **c:\ModulePath** de la sesión actual.

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
