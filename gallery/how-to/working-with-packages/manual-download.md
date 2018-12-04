---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery
title: Descarga del paquete manual
ms.openlocfilehash: 57baa14089b803f58c42ccb54553ecace841e34b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742829"
---
# <a name="manual-package-download"></a>Descarga del paquete manual

La Galería de Powershell admite descargar un paquete directamente desde el sitio web, sin usar los cmdlets de PowerShellGet. Puede descargar cualquier paquete como un archivo de paquete (archivo .nupkg) de NuGet, que, a continuación, puede copiar en un repositorio interno.

> [!NOTE]
> La descarga del paquete manual **no** está pensada como un sustituto del cmdlet Install-Module.
> La descargar del paquete no instala el módulo o el script. Las dependencias no se incluyen en el paquete NuGet descargado. Las instrucciones siguientes se proporcionan únicamente con fines de referencia.

## <a name="using-manual-download-to-acquire-a-package"></a>Usar la descarga manual para obtener un paquete

Cada página tiene un vínculo para de descarga manual, como este:

![Descarga manual](../../Images/packagedisplaypagewithpseditions.png)

Para descargar manualmente, haga clic en **Download the raw nupkg file** (Descargar el archivo nupkg sin formato). Se descarga una copia del paquete se copia en la carpeta de descargas del explorador con el nombre `<name>.<version>.nupkg`.

Un paquete de NuGet es un archivo ZIP con archivos adicionales que contienen información sobre el contenido del paquete. Algunos exploradores, como Internet Explorer, reemplazan automáticamente la extensión del archivo `.nupkg` por `.zip`. Para expandir el paquete, cambie el nombre del archivo `.nupkg` a `.zip`, si es necesario, y luego extraiga el contenido en una carpeta local.

Un archivo de paquete de NuGet incluye los siguientes elementos de NuGet específicos que no forman parte del código empaquetado original:

- Una carpeta denominada `_rels` que contiene un archivo `.rels` que enumera las dependencias
- Una carpeta denominada `package` que contiene los datos específicos de NuGet
- Un archivo denominado `[Content_Types].xml` que describe cómo funcionan las extensiones como PowerShellGet con NuGet
- Un archivo denominado `<name>.nuspec` que contiene el grueso de los metadatos

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Instalar módulos de PowerShell desde un paquete de NuGet

> [!NOTE]
> Estas instrucciones **NO** ofrecen los mismos resultados que si se ejecuta `Install-Module`. Estas instrucciones cumplen los requisitos mínimos. No pretenden ser un sustituto de `Install-Module`. No se incluyen algunos pasos realizados por `Install-Module`.

El enfoque más sencillo consiste en quitar los elementos específicos de NuGet de la carpeta. Esto deja el código de PowerShell creado por el autor del paquete. Los pasos son:

1. Extraiga el contenido del paquete de NuGet en una carpeta local.
2. Elimine los elementos específicos de NuGet de la carpeta.
3. Cambie el nombre de la carpeta. El nombre de carpeta predeterminado suele ser `<name>.<version>`. La versión puede incluir "-versión preliminar" si el módulo se etiqueta como una versión preliminar. Cambie el nombre de la carpeta para que sea solo el nombre del módulo. Por ejemplo, "azurerm.storage.5.0.4-preview" pasa a ser "azurerm.storage".
4. Copie la carpeta en una de las carpetas en el `$env:PSModulePath value`. `$env:PSModulePath` es un conjunto de delimitada por puntos y de las rutas de acceso debe ser los módulos de PowerShell.

> [!IMPORTANT]
> La descarga manual no incluye todas las dependencias que necesita el módulo. Si el paquete tiene dependencias, deben instalarse en el sistema para que este módulo funcione correctamente. La Galería de PowerShell muestra todas las dependencias que necesita el paquete.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Instalar los scripts de PowerShell desde un paquete de NuGet

> [!NOTE]
> Estas instrucciones **NO** ofrecen los mismos resultados que si se ejecuta `Install-Script`. Estas instrucciones cumplen los requisitos mínimos. No pretenden ser un sustituto de `Install-Script`.

El enfoque más sencillo consiste en extraer el paquete NuGet y, después, usar el script directamente. Los pasos son:

1. Extraiga el contenido del paquete de NuGet.
2. El archivo `.PS1` de la carpeta puede usarse directamente desde esta ubicación.
3. Puede eliminar los elementos específicos de NuGet de la carpeta.

> [!IMPORTANT]
> La descarga manual no incluye todas las dependencias que necesita el módulo. Si el paquete tiene dependencias, deben instalarse en el sistema para que este módulo funcione correctamente. La Galería de PowerShell muestra todas las dependencias que necesita el paquete.
