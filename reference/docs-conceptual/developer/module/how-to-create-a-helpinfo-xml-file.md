---
title: Cómo crear un archivo XML de HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367324"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="6e663-102">Cómo crear un archivo HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="6e663-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="6e663-103">En los temas de esta sección se explica cómo crear y rellenar un archivo de información de ayuda, conocido comúnmente como "archivo XML de HelpInfo", para la característica de ayuda actualizable de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e663-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="6e663-104">Información general sobre el archivo XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="6e663-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="6e663-105">El archivo XML HelpInfo es la fuente principal de información sobre la ayuda actualizable para el módulo.</span><span class="sxs-lookup"><span data-stu-id="6e663-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="6e663-106">Incluye la ubicación de los archivos de ayuda de los módulos, las referencias culturales de la interfaz de usuario admitidas y los números de versión que la ayuda actualizable usa para determinar si el usuario tiene los archivos de ayuda más recientes.</span><span class="sxs-lookup"><span data-stu-id="6e663-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="6e663-107">Cada módulo tiene solo un archivo XML HelpInfo, aunque el módulo incluya varios archivos de ayuda para varias referencias culturales de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="6e663-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="6e663-108">El autor del módulo crea el archivo XML HelpInfo y lo coloca en la ubicación de Internet especificada por la clave **HelpInfoUri** en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="6e663-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="6e663-109">Cuando se actualizan y se cargan los archivos de ayuda del módulo, el autor del módulo actualiza el archivo XML HelpInfo y reemplaza el archivo XML HelpInfo original con la nueva versión.</span><span class="sxs-lookup"><span data-stu-id="6e663-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="6e663-110">Es fundamental mantener cuidadosamente el archivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="6e663-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="6e663-111">Si carga nuevos archivos pero olvida incrementar los números de versión, la ayuda actualizable no descargará los nuevos archivos en los equipos de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="6e663-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="6e663-112">Si agrega archivos de ayuda para una nueva referencia cultural de la interfaz de usuario, pero no actualiza el archivo XML HelpInfo o lo coloca en la ubicación correcta, la ayuda actualizable no descargará los archivos nuevos.</span><span class="sxs-lookup"><span data-stu-id="6e663-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6e663-113">En esta sección</span><span class="sxs-lookup"><span data-stu-id="6e663-113">In this section</span></span>

<span data-ttu-id="6e663-114">Esta sección incluye los temas siguientes.</span><span class="sxs-lookup"><span data-stu-id="6e663-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="6e663-115">Esquema XML de HelpInfo</span><span class="sxs-lookup"><span data-stu-id="6e663-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="6e663-116">Archivo de ejemplo XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="6e663-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="6e663-117">Cómo asignar un nombre a un archivo XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="6e663-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="6e663-118">Cómo establecer números de versión XML de HelpInfo</span><span class="sxs-lookup"><span data-stu-id="6e663-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="6e663-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="6e663-119">See Also</span></span>

[<span data-ttu-id="6e663-120">Compatibilidad con la ayuda actualizable</span><span class="sxs-lookup"><span data-stu-id="6e663-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)