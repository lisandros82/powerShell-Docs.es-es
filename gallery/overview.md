---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Galería de PowerShell
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482937"
---
# <a name="the-powershell-gallery"></a>Galería de PowerShell

La Galería de PowerShell es el repositorio central del contenido de PowerShell. En ella, encontrará módulos útiles de PowerShell que contienen comandos de PowerShell y los recursos de configuración de estado deseado (DSC).
También encontrará scripts de PowerShell (algunos de los cuales pueden contener flujos de trabajo de PowerShell), que describen un conjunto de tareas y proporcionan la secuenciación de dichas tareas. Algunos de estos elementos son creación de Microsoft y otros son creación de la comunidad de PowerShell.

## <a name="powershellget-overview"></a>Información general de PowerShellGet

El módulo PowerShellGet contiene cmdlets para detectar, instalar, actualizar y publicar los artefactos de PowerShell como módulos, recursos de DSC, funcionalidades de rol y scripts desde la [Galería de PowerShell](https://www.PowerShellGallery.com) y otros repositorios privados.

## <a name="getting-started-with-the-gallery"></a>Introducción a la Galería

Para instalar elementos de la Galería es necesaria la versión más reciente del módulo PowerShellGet.
Vea [Instalación de PowerShellGet](installing-psget.md) para ver las instrucciones completas.

Consulte la página [Introducción](getting-started.md) para obtener más información sobre el uso de comandos PowerShellGet con la Galería. También puede ejecutar *Update-Help -Module PowerShellGet* para instalar la Ayuda local para estos comandos.

## <a name="supported-operating-systems"></a>Sistemas operativos compatibles

El módulo **PowerShellGet** requiere **Windows PowerShell 3.0 o posterior**, o bien **PowerShell Core 6.0 o posterior**.

Una versión adecuada de **Windows PowerShell** está disponible para estos sistemas operativos:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** también requiere .NET Framework 4.5 o una versión posterior. Puede instalar .NET Framework 4.5 o posterior desde [aquí](https://msdn.microsoft.com/library/5a4x27ek.aspx).

**PowerShell Core** admite muchos sistemas operativos. Consulte [este artículo](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) para ver una lista completa.

Muchos módulos hospedados en la galería admitirán diferentes sistemas operativos y tendrán requisitos adicionales. Consulte la documentación de los módulos para obtener más información.

## <a name="got-a-question-have-feedback"></a>¿Tiene alguna pregunta? ¿Tiene comentarios?

Encontrará más información sobre la Galería de PowerShell y PowerShellGet en la página [Introducción](getting-started.md). Proporcione comentarios e informe de problemas mediante [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).
