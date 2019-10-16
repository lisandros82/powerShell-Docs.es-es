---
title: Cómo actualizar los archivos de ayuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367144"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="46b06-102">Cómo actualizar los archivos de Ayuda</span><span class="sxs-lookup"><span data-stu-id="46b06-102">How to Update Help Files</span></span>

<span data-ttu-id="46b06-103">En este tema se explica cómo actualizar los archivos de ayuda de un módulo que admite la ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="46b06-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="46b06-104">Actualizar archivos de ayuda</span><span class="sxs-lookup"><span data-stu-id="46b06-104">Updating Help Files</span></span>

<span data-ttu-id="46b06-105">Hay muchas razones para actualizar los archivos de ayuda, como corregir errores, aclarar un concepto, responder a preguntas frecuentes, agregar nuevos archivos o agregar nuevos y mejores ejemplos.</span><span class="sxs-lookup"><span data-stu-id="46b06-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="46b06-106">Para actualizar un archivo de ayuda:</span><span class="sxs-lookup"><span data-stu-id="46b06-106">To update a help file:</span></span>

1. <span data-ttu-id="46b06-107">Cambie los archivos.</span><span class="sxs-lookup"><span data-stu-id="46b06-107">Change the files.</span></span>

2. <span data-ttu-id="46b06-108">Traduzca los archivos a otras referencias culturales de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="46b06-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="46b06-109">Recopilar todos los archivos de ayuda (nuevos, modificados y sin cambios) para el módulo en cada referencia cultural de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="46b06-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="46b06-110">Valide los archivos con el esquema XML.</span><span class="sxs-lookup"><span data-stu-id="46b06-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="46b06-111">Recompile los archivos. CAB para cada referencia cultural de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="46b06-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="46b06-112">En el archivo XML HelpInfo, incremente los números de versión del archivo. CAB para cada referencia cultural de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="46b06-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="46b06-113">Cargue los nuevos archivos. CAB en la ubicación especificada por el valor del elemento **HelpContentUri** en el archivo XML de HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="46b06-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="46b06-114">Reemplace los archivos CAB antiguos por los nuevos archivos. CAB.</span><span class="sxs-lookup"><span data-stu-id="46b06-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="46b06-115">Cargue el archivo XML HelpInfo actualizado en la ubicación especificada por la clave **HelpInfoUri** en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="46b06-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="46b06-116">Reemplace el archivo XML HelpInfo anterior por el nuevo archivo.</span><span class="sxs-lookup"><span data-stu-id="46b06-116">Replace the older HelpInfo XML file with the new file.</span></span>