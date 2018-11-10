---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Introducción a la Galería de PowerShell
ms.openlocfilehash: 85b0a754aba25d850dc918024419318554f92b33
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225682"
---
# <a name="getting-started-with-the-powershell-gallery"></a>Introducción a la Galería de PowerShell

La manera adecuada para instalar paquetes desde la Galería de PowerShell es usar los cmdlets en el módulo [PowerShellGet](/powershell/module/powershellget). No es necesario iniciar sesión para descargar los elementos de la Galería de PowerShell.

> [!NOTE]
> Es posible descargar un paquete desde la Galería de PowerShell directamente, pero este no es un enfoque recomendado.
> Para más información, vea [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download) (Descargar paquete de forma manual).

## <a name="discovering-packages-from-the-powershell-gallery"></a>Detectar paquetes de la Galería de PowerShell

Puede buscar paquetes en la Galería de PowerShell mediante el control de **búsqueda** en este sitio web o la exploración de las páginas Scripts y Módulos. También puede buscar paquetes de la Galería de PowerShell al ejecutar los cmdlets [Find-Module][] y [Find-Script][], en función del tipo de paquete, con `-Repository PSGallery`.

Puede filtrar los resultados de la Galería mediante los siguientes parámetros:

- Nombre
- AllVersions
- MinimumVersion
- RequiredVersion
- Etiqueta
- Includes
- DscResource
- RoleCapability
- Comando
- Filtro

Si solo le interesa detectar recursos de DSC específicos en la Galería, puede ejecutar el cmdlet [Find-DscResource]. Find-DscResource devuelve datos sobre los recursos de DSC contenidos en la Galería.
Dado que los recursos de DSC siempre se entregan como parte de un módulo, debe ejecutar [Install-Module][] para instalar dichos recursos de DSC.

## <a name="learning-about-packages-in-the-powershell-gallery"></a>Obtener información sobre los paquetes de la Galería de PowerShell

Una vez identificado un paquete de su interés, tal vez quiera obtener más información. Puede hacerlo examinando la página específica de ese paquete en la Galería. En la página, podrá ver todos los metadatos cargados con el paquete. El autor del paquete es quien proporciona estos metadatos, que Microsoft no comprueba. El propietario del paquete está estrechamente ligado a la cuenta de la Galería que se usa para publicar el paquete, y es más confiable que el campo Autor.

Si cree que un paquete no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese paquete.

Si está ejecutando [Find-Module][] o [Find-Script][], puede ver estos datos en el objeto PSGetModuleInfo devuelto. Por ejemplo, la ejecución de `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
devuelve datos en el módulo PSReadLine de la galería.

## <a name="downloading-packages-from-the-powershell-gallery"></a>Descargar paquetes de la Galería de PowerShell

Se recomienda el proceso siguiente al descargar paquetes de la Galería de PowerShell:

### <a name="inspect"></a>Inspeccionar

Para descargar un paquete de la Galería para su inspección, ejecute el cmdlet [Save-Module][] o [Save-Script][], en función del tipo de paquete. Esto le permite guardar el paquete localmente sin instalarlo e inspeccionar su contenido. Recuerde eliminar el paquete guardado manualmente.

Algunos de estos paquetes los crea Microsoft y otros los crea la comunidad de PowerShell.
Microsoft recomienda que se revisen el contenido y el código de los paquetes de esta Galería antes de la instalación.

Si cree que un paquete no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese paquete.

### <a name="install"></a>Instalar

Para instalar un paquete desde la Galería para su uso, ejecute el cmdlet [Install-Module][] o [Install-Script][], en función del tipo de paquete.

[Install-Module][] instala el módulo en `$env:ProgramFiles\WindowsPowerShell\Modules` de manera predeterminada.
Para ello es necesaria una cuenta de administrador. Si agrega el parámetro `-Scope CurrentUser`, el módulo se instala en `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[Install-Script][] instala el script en `$env:ProgramFiles\WindowsPowerShell\Scripts` de manera predeterminada.
Para ello es necesaria una cuenta de administrador. Si agrega el parámetro `-Scope CurrentUser`, el script se instala en `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

De forma predeterminada, [Install-Module][] e [Install-Script][] instalan la última versión de un paquete.
Para instalar una versión anterior del paquete, agregue el parámetro `-RequiredVersion`.

### <a name="deploy"></a>Implementar

Para implementar un paquete desde la Galería de PowerShell en Azure Automation, haga clic en **Deploy to Azure Automation** (Implementar en Azure Automation) en la página de detalles del paquete. Se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure. Tenga en cuenta que si se implementan paquetes con dependencias, se implementarán todas las dependencias en Azure Automation. El botón Deploy to Azure Automation (Implementar en Azure Automation) se puede deshabilitar mediante la adición de la etiqueta **AzureAutomationNotSupported** a los metadatos del paquete.

Para obtener más información sobre Azure Automation, consulte la documentación de [Azure Automation](/azure/automation).

## <a name="updating-packages-from-the-powershell-gallery"></a>Actualizar paquetes desde la Galería de PowerShell

Para actualizar paquetes instalados desde la Galería de PowerShell, ejecute los cmdlets [Update-Module][] o [Update-Script][]. Cuando se ejecuta sin parámetros adicionales, [Update-Module][] intenta actualizar cada módulo instalado mediante la ejecución de [Install-Module][]. Para actualizar módulos de forma selectiva, agregue el parámetro `-Name`.

Del mismo modo, cuando se ejecuta sin parámetros adicionales, [Update-Script][] también intenta actualizar cada script instalado mediante la ejecución de [Install-Script][]. Para actualizar scripts de forma selectiva, agregue el parámetro `-Name`.

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a>Enumerar los paquetes instalados desde la Galería de PowerShell

Para averiguar qué módulos ha instalado desde la Galería de PowerShell, ejecute el cmdlet [Get-InstalledModule][]. Este comando enumera todos los módulos del sistema que se instalaron directamente desde la Galería de PowerShell.

Del mismo modo, para averiguar qué scripts ha instalado desde la Galería de PowerShell, ejecute el cmdlet [Get-InstalledScript][]. Este comando enumera todos los scripts del sistema que se instalaron directamente desde la Galería de PowerShell.

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
