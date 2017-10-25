---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: "Cmdlets del catálogo"
ms.openlocfilehash: f0869e8c174ab127996866775ad20d056f877345
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2017
---
# <a name="catalog-cmdlets"></a>Cmdlets del catálogo  

Hemos agregado dos nuevos cmdlets en el módulo [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) para generar y validar los archivos de catálogo de Windows.  

## <a name="new-filecatalog"></a>New-FileCatalog 
--------------------------------

`New-FileCatalog` crea un archivo de catálogo de Windows para un conjunto de carpetas y archivos. El archivo de catálogo contiene hashes para todos los archivos de las rutas de acceso especificadas. Los usuarios pueden distribuir el conjunto de carpetas junto con el correspondiente archivo de catálogo que representa a esas carpetas. El destinatario del contenido puede usar el archivo de catálogo para validar si se realizaron cambios en las carpetas después de la creación del catálogo.    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Se admite la creación de catálogos de las versiones 1 y 2. La versión 1, utiliza el algoritmo hash SHA1 para crear los hashes de archivo y la versión 2 utiliza SHA256. La versión 2 del catálogo no es compatible con *Windows Server 2008 R2* y *Windows 7*. Se recomienda utilizar la versión 2 del catálogo si utiliza las plataformas *Windows 8*, *Windows Server 2012* y versiones posteriores.  

Para utilizar este comando en un módulo existente, especifique las variables CatalogFilePath y Path de modo que coincidan con la ubicación del manifiesto del módulo. En el ejemplo siguiente, el manifiesto del módulo se encuentra en la ruta C:\Program Files\Windows PowerShell\Modules\Pester. 

![](../images/NewFileCatalog.jpg)

Esto crea el archivo de catálogo. 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

Para comprobar la integridad del archivo de catálogo (Pester.cat en el ejemplo anterior) debe firmarse mediante el cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).   


## <a name="test-filecatalog"></a>Test-FileCatalog 
--------------------------------

`Test-FileCatalog` valida el catálogo que representa un conjunto de carpetas. 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Este cmdlet compara los valores hash de todos los archivos y de sus rutas de acceso relativas que se encuentran en el archivo de catálogo con los guardados en el disco. Si se detecta cualquier error de coincidencia entre los hashes y las rutas de acceso de los archivos devuelve el estado `ValidationFailed`. Los usuarios pueden recuperar toda esta información mediante el modificador `Detailed`. Se muestra el estado de firma del catálogo en el campo `Signature`, lo que es igual que llamar al cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) en el archivo de catálogo. El usuario también puede omitir cualquier archivo durante la validación mediante el parámetro `FilesToSkip`. 

