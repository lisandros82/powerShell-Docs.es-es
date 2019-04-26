---
title: Cómo establecer números de versión XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: b98e6879bbfe0e3ec1a9ab37496dde44caf523a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082284"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="9e06c-102">Cómo establecer números de versión de HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="9e06c-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="9e06c-103">En este tema se explica cómo establecer y aumentar los números de versión en un archivo de información de ayuda actualizable, conocido comúnmente como "archivo XML HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="9e06c-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="9e06c-104">Cómo establecer números de versión de HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="9e06c-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="9e06c-105">Los números de versión en un archivo XML HelpInfo son fundamentales para el funcionamiento de la Ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="9e06c-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span>
<span data-ttu-id="9e06c-106">El [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets descargar nuevos archivos de ayuda solo cuando el número de versión para una referencia cultural de interfaz de usuario en el archivo XML HelpInfo remoto es mayor que el número de versión para esa referencia cultural de interfaz de usuario en el XML HelpInfo local, o no hay ningún archivo XML HelpInfo local.</span><span class="sxs-lookup"><span data-stu-id="9e06c-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="9e06c-107">El archivo XML HelpInfo utiliza el número de versión de 4 partes que se define en el **System.Version** clase de Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e06c-107">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="9e06c-108">El formato es `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="9e06c-108">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="9e06c-109">Los autores del módulo pueden usar cualquier versión de esquema que está permitido por la numeración del **System.Version** clase.</span><span class="sxs-lookup"><span data-stu-id="9e06c-109">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="9e06c-110">La Ayuda actualizable requiere solo que el número de versión para un aumento de la referencia cultural de interfaz de usuario cuando se cargue una nueva versión del archivo CAB para esa referencia cultural de interfaz de usuario en la ubicación especificada por el **HelpContentURI** elemento en el archivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="9e06c-110">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="9e06c-111">El ejemplo siguiente muestra los elementos del archivo XML HelpInfo para el alemán (de-DE) la interfaz de usuario de la referencia cultural cuando la versión es 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="9e06c-111">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="9e06c-112">El número de versión para una referencia cultural de interfaz de usuario refleja la versión del archivo CAB para esa referencia cultural de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e06c-112">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="9e06c-113">El número de versión se aplica a todo el archivo CAB.</span><span class="sxs-lookup"><span data-stu-id="9e06c-113">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="9e06c-114">No se puede establecer números de versión diferentes para distintos archivos en el archivo CAB.</span><span class="sxs-lookup"><span data-stu-id="9e06c-114">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="9e06c-115">El número de versión para cada referencia cultural de interfaz de usuario se evalúa de forma independiente y no necesita estar relacionado con los números de versión para otras referencias culturales de interfaz de usuario que admite el módulo.</span><span class="sxs-lookup"><span data-stu-id="9e06c-115">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>