---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery,psget
title: "Galería de PowerShell"
ms.openlocfilehash: 83a1f4e20b985a502637aee9d50ecc1d3f9a4616
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/29/2017
---
# <a name="the-powershell-gallery"></a>Galería de PowerShell

La Galería de PowerShell es el repositorio central del contenido de PowerShell. En la Galería encontrará nuevos comandos de PowerShell o recursos de configuración de estado deseado (DSC).

## <a name="powershellget-overview"></a>Información general de PowerShellGet

El módulo PowerShellGet contiene cmdlets para detectar, instalar, actualizar y publicar los artefactos de PowerShell como módulos, recursos de DSC, funcionalidades de rol y scripts desde https://www.PowerShellGallery.com y otros repositorios privados.

## <a name="getting-started-with-the-gallery"></a>Introducción a la Galería

Para instalar elementos desde la Galería se requiere la versión más reciente del módulo PowerShellGet, que está disponible en Windows 10, en Windows Management Framework (WMF) 5.0 o en el programa de instalación basado en MSI (para PowerShell 3 y 4).

- [**Obtener Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**Obtener WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) u
- [**Obtener el instalador MSI**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Con la última versión del módulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), puede:

-   Buscar elementos en la Galería con [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) y [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)
-   Guardar los elementos en el sistema desde la Galería con [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) y [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)
-   Instalar elementos desde la Galería con [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) e [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)
-   Cargar elementos en la Galería con [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) y [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)
-   Agregue su propio repositorio personalizado con [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)

Consulte la página [Introducción](psgallery/psgallery_gettingstarted.md) para obtener más información sobre el uso de comandos PowerShellGet con la Galería. También puede ejecutar *Update-Help -Module PowerShellGet* para instalar la Ayuda local para estos comandos.

## <a name="supported-operating-systems"></a>Sistemas operativos compatibles

El módulo **PowerShellGet** requiere **PowerShell 3.0 o posterior**.

Por lo tanto, **PowerShellGet** requiere uno de los siguientes sistemas operativos:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** también requiere .NET Framework 4.5 o posterior. Puede instalar .NET Framework 4.5 o posterior desde [aquí](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).


## <a name="got-a-question-have-feedback"></a>¿Tiene alguna pregunta? ¿Tiene comentarios?

Encontrará más información sobre la Galería de PowerShell y PowerShellGet en la página [Introducción](psgallery/psgallery_gettingstarted.md). Proporcione comentarios e informe de problemas mediante [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).

