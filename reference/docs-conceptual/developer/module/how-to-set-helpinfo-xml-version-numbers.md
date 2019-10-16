---
title: Cómo establecer los números de versión XML de HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360684"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="98ebe-102">Cómo establecer números de versión de HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="98ebe-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="98ebe-103">En este tema se explica cómo establecer y aumentar los números de versión en un archivo de información de ayuda actualizable, conocido comúnmente como "archivo XML de HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="98ebe-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="98ebe-104">Cómo establecer números de versión de HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="98ebe-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="98ebe-105">Los números de versión de un archivo XML HelpInfo son fundamentales para el funcionamiento de la ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="98ebe-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="98ebe-106">Los cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) descargan nuevos archivos de ayuda solo cuando el número de versión de una referencia cultural de la interfaz de usuario en el archivo XML HelpInfo remoto es mayor que el número de versión de esa referencia cultural de la interfaz de usuario en el XML de HelpInfo local o no hay ningún HelpInfo local. Archivo XML.</span><span class="sxs-lookup"><span data-stu-id="98ebe-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="98ebe-107">El archivo XML HelpInfo usa el número de versión de 4 partes que se define en la clase **System. version** del marco de Microsoft .net.</span><span class="sxs-lookup"><span data-stu-id="98ebe-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="98ebe-108">El formato es `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="98ebe-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="98ebe-109">Los autores de módulos pueden usar cualquier esquema de numeración de versiones permitido por la clase **System. version** .</span><span class="sxs-lookup"><span data-stu-id="98ebe-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="98ebe-110">La ayuda actualizable solo requiere que el número de versión de una referencia cultural de la interfaz de usuario aumente cuando se cargue una nueva versión del archivo. CAB para esa referencia cultural de la interfaz de usuario en la ubicación especificada por el elemento **HelpContentURI** en el archivo XML de HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="98ebe-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="98ebe-111">En el ejemplo siguiente se muestran los elementos del archivo XML HelpInfo para la referencia cultural de la interfaz de usuario alemana (de-DE) cuando la versión es 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="98ebe-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="98ebe-112">El número de versión de una referencia cultural de la interfaz de usuario refleja la versión del archivo. CAB para esa referencia cultural de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="98ebe-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="98ebe-113">El número de versión se aplica a todo el archivo. CAB.</span><span class="sxs-lookup"><span data-stu-id="98ebe-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="98ebe-114">No se pueden establecer números de versión diferentes para los distintos archivos del archivo. CAB.</span><span class="sxs-lookup"><span data-stu-id="98ebe-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="98ebe-115">El número de versión de cada referencia cultural de la interfaz de usuario se evalúa de forma independiente y no debe estar relacionado con los números de versión de otras referencias culturales de la interfaz de usuario que admite el módulo.</span><span class="sxs-lookup"><span data-stu-id="98ebe-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>