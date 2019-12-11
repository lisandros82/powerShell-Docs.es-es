---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery
title: Descarga del paquete manual
ms.openlocfilehash: c0a96e866dfd27f9b2170ea540ec6dd0c67701fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327896"
---
# <a name="manual-package-download"></a>Descarga del paquete manual

La Galería de PowerShell admite descargar un paquete directamente desde el sitio web, sin usar los cmdlets de PowerShellGet. Puede descargar cualquier paquete como un archivo de paquete NuGet (`.nupkg`), que posteriormente puede copiar a un repositorio interno.

> [!NOTE]
> La descarga del paquete manual **no** está pensada como un sustituto del cmdlet `Install-Module`.
> La descargar del paquete no instala el módulo o el script. Las dependencias no se incluyen en el paquete NuGet descargado. Las instrucciones siguientes se proporcionan únicamente con fines de referencia.

## <a name="using-manual-download-to-acquire-a-package"></a>Usar la descarga manual para obtener un paquete

Cada página tiene un vínculo para de descarga manual, como este:

![Descarga manual](../../Images/packagedisplaypagewithpseditions.png)

Para descargar manualmente, haga clic en **Download the raw nupkg file** (Descargar el archivo nupkg sin formato). Una copia del paquete se copia en la carpeta de descargas del explorador con el nombre `<name>.<version>.nupkg`.

Un paquete de NuGet es un archivo ZIP con archivos adicionales que contienen información sobre el contenido del paquete. Algunos exploradores, como Internet Explorer, reemplazan automáticamente la extensión del archivo `.nupkg` por `.zip`. Para expandir el paquete, cambie el nombre del archivo `.nupkg` a `.zip`, si es necesario, y luego extraiga el contenido en una carpeta local.

Un archivo de paquete de NuGet incluye los siguientes **elementos de NuGet específicos** que no forman parte del código empaquetado original:

- Una carpeta denominada `_rels` que contiene un archivo `.rels` que enumera las dependencias
- Una carpeta denominada `package` que contiene los datos específicos de NuGet
- Un archivo denominado `[Content_Types].xml` que describe cómo funcionan las extensiones como PowerShellGet con NuGet
- Un archivo denominado `<name>.nuspec` que contiene el grueso de los metadatos

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Instalación de módulos de PowerShell desde un paquete de NuGet

> [!NOTE]
> Estas instrucciones **NO** ofrecen los mismos resultados que si se ejecuta `Install-Module`. Estas instrucciones cumplen los requisitos mínimos. No pretenden ser un sustituto de `Install-Module`.
> No se incluyen algunos pasos realizados por `Install-Module`.

El enfoque más sencillo consiste en quitar los elementos específicos de NuGet de la carpeta. Esto deja el código de PowerShell creado por el autor del paquete.
Para obtener la lista de elementos específicos de NuGet, consulte [Usar la descarga manual para obtener un paquete](#using-manual-download-to-acquire-a-package).

Los pasos son los siguientes:

1. Extraiga el contenido del paquete de NuGet en una carpeta local.
2. Elimine los elementos específicos de NuGet de la carpeta.
3. Cambie el nombre de la carpeta. El nombre de carpeta predeterminado suele ser `<name>.<version>`. La versión puede incluir `-prerelease` si el módulo se etiqueta como una versión preliminar. Cambie el nombre de la carpeta para que sea solo el nombre del módulo. Por ejemplo, `azurerm.storage.5.0.4-preview` se convierte en `azurerm.storage`.
4. Copie la carpeta en una de las carpetas de `$env:PSModulePath value`. `$env:PSModulePath` es un conjunto delimitado por punto y coma de las rutas de acceso en las cuales PowerShell debe buscar módulos.

> [!IMPORTANT]
> La descarga manual no incluye todas las dependencias que necesita el módulo. Si el paquete tiene dependencias, deben instalarse en el sistema para que este módulo funcione correctamente. La Galería de PowerShell muestra todas las dependencias que necesita el paquete.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Instalación de los scripts de PowerShell desde un paquete de NuGet

> [!NOTE]
> Estas instrucciones **NO** ofrecen los mismos resultados que si se ejecuta `Install-Script`. Estas instrucciones cumplen los requisitos mínimos. No pretenden ser un sustituto de `Install-Script`.

El enfoque más sencillo consiste en extraer el paquete NuGet y, después, usar el script directamente.

Los pasos son los siguientes:

1. Extraiga el contenido del paquete de NuGet.
2. El archivo `.PS1` de la carpeta puede usarse directamente desde esta ubicación.
3. Puede eliminar los elementos específicos de NuGet de la carpeta.

Para obtener la lista de elementos específicos de NuGet, consulte [Usar la descarga manual para obtener un paquete](#using-manual-download-to-acquire-a-package).

> [!IMPORTANT]
> La descarga manual no incluye todas las dependencias que necesita el módulo. Si el paquete tiene dependencias, deben instalarse en el sistema para que este módulo funcione correctamente. La Galería de PowerShell muestra todas las dependencias que necesita el paquete.
