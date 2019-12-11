---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Galería de PowerShell
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327866"
---
# <a name="the-powershell-gallery"></a>Galería de PowerShell

La Galería de PowerShell es el repositorio central del contenido de PowerShell. En ella, encontrará módulos útiles de PowerShell que contienen comandos de PowerShell y los recursos de configuración de estado deseado (DSC).
También encontrará scripts de PowerShell (algunos de los cuales pueden contener flujos de trabajo de PowerShell), que describen un conjunto de tareas y proporcionan la secuenciación de dichas tareas. Algunos de estos paquetes los crea Microsoft y otros los crea la comunidad de PowerShell.

## <a name="powershellget-overview"></a>Información general de PowerShellGet

El módulo PowerShellGet contiene cmdlets para detectar, instalar, actualizar y publicar paquetes de PowerShell que contienen artefactos como módulos, recursos de DSC, funcionalidades de rol y scripts desde la [Galería de PowerShell](https://www.PowerShellGallery.com) y otros repositorios privados.

## <a name="getting-started-with-the-gallery"></a>Introducción a la Galería

Para instalar paquetes de la Galería, se necesita la última versión del módulo PowerShellGet.
Vea [Instalación de PowerShellGet](installing-psget.md) para ver las instrucciones completas.

Consulte la página [Introducción](getting-started.md) para obtener más información sobre el uso de comandos PowerShellGet con la Galería. También puede ejecutar *Update-Help -Module PowerShellGet* para instalar la Ayuda local para estos comandos.

## <a name="supported-operating-systems"></a>Sistemas operativos compatibles

El módulo **PowerShellGet** requiere **Windows PowerShell 3.0 o posterior**, o bien **PowerShell Core 6.0 o posterior**.

Una versión adecuada de **Windows PowerShell** está disponible para estos sistemas operativos:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** requiere .NET Framework 4.5 o una versión posterior. Puede instalar .NET Framework 4.5 o posterior desde [aquí](https://msdn.microsoft.com/library/5a4x27ek.aspx).

Puesto que **PowerShell Core** es multiplataforma y eso significa que funciona en Windows, Linux y MacOS, permite que **PowerShellGet** esté disponible en esos sistemas. Para obtener una lista completa de sistemas compatibles con **PowerShell Core**, vea [Instalación de distintas versiones de PowerShell](/powershell/scripting/setup/installing-powershell).

Muchos módulos hospedados en la galería admitirán diferentes sistemas operativos y tendrán requisitos adicionales. Consulte la documentación de los módulos para obtener más información.

## <a name="got-a-question-have-feedback"></a>¿Tiene alguna pregunta? ¿Tiene comentarios?

Encontrará más información sobre la Galería de PowerShell y PowerShellGet en la página [Introducción](getting-started.md). Proporcione comentarios e informe de problemas mediante [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).
