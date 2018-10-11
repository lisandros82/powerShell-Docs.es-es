---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Introducción a la Galería de PowerShell
ms.openlocfilehash: 39998df1a2bf9363dd008dc96a802157c8d691d7
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523066"
---
# <a name="get-started-with-the-powershell-gallery"></a>Introducción a la Galería de PowerShell

La manera adecuada para instalar elementos desde la Galería de PowerShell es usar los cmdlets en el módulo [PowerShellGet](/powershell/module/powershellget). No es necesario iniciar sesión para descargar los elementos de la Galería de PowerShell.

> [!NOTE]
> Es posible descargar un paquete desde la Galería de PowerShell directamente, pero este no es un enfoque recomendado. Para más información, vea [Manual Package Download](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/how-to/working-with-items/manual-download.md) (Descargar paquete de forma manual).  


## <a name="discovering-items-from-the-powershell-gallery"></a>Detectar elementos de la Galería de PowerShell

Puede buscar elementos en la Galería de PowerShell mediante el control de **búsqueda** en este sitio web o la examinación de las páginas Scripts y Módulos. También puede buscar elementos de la Galería de PowerShell al ejecutar los cmdlets [Find-Module][] y [Find-Script][], en función del tipo de elemento, con `-Repository PSGallery`.

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

## <a name="learning-about-items-in-the-powershell-gallery"></a>Obtener información sobre los elementos de la Galería de PowerShell

Una vez que haya identificado el elemento que le interesa, tal vez quiera obtener más información. Puede hacerlo examinando la página específica de ese elemento en la Galería. En la página, podrá ver todos los metadatos cargados con el elemento. El autor del elemento es quien proporciona estos metadatos del elemento, que Microsoft no comprueba. El propietario del elemento está estrechamente ligado a la cuenta de la Galería que se usa para publicar el elemento, y es más confiable que el campo Autor.

Si cree que un elemento no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese elemento.

Si está ejecutando [Find-Module][] o [Find-Script][], puede ver estos datos en el objeto PSGetModuleInfo devuelto. Por ejemplo, la ejecución de `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`
devuelve datos en el módulo PSReadLine de la galería.

## <a name="downloading-items-from-the-powershell-gallery"></a>Descargar elementos de la Galería de PowerShell

Se recomienda el proceso siguiente al descargar elementos de la Galería de PowerShell:

### <a name="inspect"></a>Inspeccionar

Para descargar un elemento de la Galería para su inspección, ejecute el cmdlet [Save-Module][] o [Save-Script][], en función del tipo de elemento. Esto le permite guardar el elemento localmente sin instalarlo e inspeccionar su contenido. Recuerde eliminar el elemento guardado manualmente.

Algunos de estos elementos son creación de Microsoft y otros son creación de la comunidad de PowerShell.
Microsoft recomienda que se revisen el contenido y el código de los elementos de esta Galería antes de la instalación.

Si cree que un elemento no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese elemento.

### <a name="install"></a>Instalar

Para instalar un elemento desde la Galería para su uso, ejecute el cmdlet [Install-Module][] o [Install-Script][], en función del tipo de elemento.

[Install-Module][] instala el módulo en `$env:ProgramFiles\WindowsPowerShell\Modules` de manera predeterminada.
Para ello es necesaria una cuenta de administrador. Si agrega el parámetro `-Scope CurrentUser`, el módulo se instala en `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`.

[Install-Script][] instala el script en `$env:ProgramFiles\WindowsPowerShell\Scripts` de manera predeterminada.
Para ello es necesaria una cuenta de administrador. Si agrega el parámetro `-Scope CurrentUser`, el script se instala en `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`.

De forma predeterminada, [Install-Module][] e [Install-Script][] instalan la versión más reciente de un elemento.
Para instalar una versión anterior del elemento, agregue el parámetro `-RequiredVersion`.

### <a name="deploy"></a>Implementar

Para implementar un elemento desde la Galería de PowerShell en Automatización de Azure, haga clic en **Deploy to Azure Automation** (Implementar en Automatización de Azure) en la página de detalles del elemento. Se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure. Tenga en cuenta que si se implementan elementos con dependencias, se implementarán todas las dependencias en Automatización de Azure. El botón Deploy to Azure Automation (Implementar en Automatización de Azure) se puede deshabilitar agregando la etiqueta **AzureAutomationNotSupported** a los metadatos del elemento.

Para obtener más información sobre Azure Automation, consulte la documentación de [Azure Automation](/azure/automation).

## <a name="updating-items-from-the-powershell-gallery"></a>Actualizar elementos de la Galería de PowerShell

Para actualizar elementos instalados desde la Galería de PowerShell, ejecute el cmdlet [Update-Module][] o [Update-Script][]. Cuando se ejecuta sin parámetros adicionales, [Update-Module][] intenta actualizar cada módulo instalado mediante la ejecución de [Install-Module][]. Para actualizar módulos de forma selectiva, agregue el parámetro `-Name`.

Del mismo modo, cuando se ejecuta sin parámetros adicionales, [Update-Script][] también intenta actualizar cada script instalado mediante la ejecución de [Install-Script][]. Para actualizar scripts de forma selectiva, agregue el parámetro `-Name`.

## <a name="list-items-that-you-have-installed-from-the-powershell-gallery"></a>Enumerar los elementos instalados desde la Galería de PowerShell

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