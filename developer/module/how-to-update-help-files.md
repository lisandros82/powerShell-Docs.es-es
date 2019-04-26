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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082321"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="c0a35-102">Cómo actualizar los archivos de Ayuda</span><span class="sxs-lookup"><span data-stu-id="c0a35-102">How to Update Help Files</span></span>

<span data-ttu-id="c0a35-103">En este tema se explica cómo actualizar los archivos de ayuda para un módulo que admite la Ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="c0a35-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="c0a35-104">Actualizar los archivos de ayuda</span><span class="sxs-lookup"><span data-stu-id="c0a35-104">Updating Help Files</span></span>

<span data-ttu-id="c0a35-105">Hay muchas razones para actualizar los archivos de ayuda, como la corrección de errores, aclarar un concepto, responder una pregunta más frecuentes, agregar nuevos archivos o agregar nuevos y mejores ejemplos.</span><span class="sxs-lookup"><span data-stu-id="c0a35-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="c0a35-106">Para actualizar un archivo de ayuda:</span><span class="sxs-lookup"><span data-stu-id="c0a35-106">To update a help file:</span></span>

1. <span data-ttu-id="c0a35-107">Cambiar los archivos.</span><span class="sxs-lookup"><span data-stu-id="c0a35-107">Change the files.</span></span>

2. <span data-ttu-id="c0a35-108">Los archivos se traducen en otras referencias culturales de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="c0a35-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="c0a35-109">Recopilar todos los archivos de ayuda (nuevas, cambiados y sin cambios) para el módulo en cada referencia cultural de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="c0a35-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="c0a35-110">Valide los archivos con respecto al esquema XML.</span><span class="sxs-lookup"><span data-stu-id="c0a35-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="c0a35-111">Vuelva a generar los archivos .cab para cada referencia cultural de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="c0a35-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="c0a35-112">En el archivo XML HelpInfo, incrementar los números de versión del archivo .cab para cada referencia cultural de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="c0a35-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="c0a35-113">Cargue los archivos CAB de nuevo en la ubicación especificada por el valor de la **HelpContentUri** elemento en el archivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="c0a35-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="c0a35-114">Reemplazar los antiguos archivos CAB con los nuevos archivos CAB.</span><span class="sxs-lookup"><span data-stu-id="c0a35-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="c0a35-115">Cargue el archivo XML HelpInfo actualizado en la ubicación especificada por el **HelpInfoUri** clave en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="c0a35-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="c0a35-116">Reemplace el archivo XML HelpInfo anterior con el nuevo archivo.</span><span class="sxs-lookup"><span data-stu-id="c0a35-116">Replace the older HelpInfo XML file with the new file.</span></span>