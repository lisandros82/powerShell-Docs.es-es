---
title: Cómo crear un archivo de formato (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862971"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="f7fca-102">Cómo crear un archivo de formato (. format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="f7fca-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="f7fca-103">Este tema describe cómo crear un archivo de formato (. format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="f7fca-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="f7fca-104">También puede crear un archivo de formato mediante la realización de una copia de uno de los archivos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7fca-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="f7fca-105">Si realiza una copia de un archivo existente, elimine la firma digital existente y agregar su propia firma para el nuevo archivo.</span><span class="sxs-lookup"><span data-stu-id="f7fca-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="f7fca-106">Para crear una. archivo format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="f7fca-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="f7fca-107">Cree un archivo de texto (.txt) con un texto editor como Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="f7fca-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="f7fca-108">Copie las líneas siguientes en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f7fca-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="f7fca-109">El \<configuración >\</Configuration > etiquetas definen la raíz `Configuration` nodo.</span><span class="sxs-lookup"><span data-stu-id="f7fca-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="f7fca-110">Todas las etiquetas XML adicionales está incluidas en este nodo.</span><span class="sxs-lookup"><span data-stu-id="f7fca-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="f7fca-111">El <ViewDefinitions> </ViewDefinitions> etiquetas definen el `ViewDefinitions` nodo.</span><span class="sxs-lookup"><span data-stu-id="f7fca-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="f7fca-112">Todas las vistas se definen dentro de este nodo.</span><span class="sxs-lookup"><span data-stu-id="f7fca-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="f7fca-113">Guarde el archivo a la carpeta de instalación de Windows PowerShell, la carpeta del módulo o en una subcarpeta de la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="f7fca-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="f7fca-114">Use el siguiente formato de nombre cuando guarde el archivo: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="f7fca-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="f7fca-115">Archivos de formato deben usar el `.format.ps1xml` extensión.</span><span class="sxs-lookup"><span data-stu-id="f7fca-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="f7fca-116">Ahora está listo para agregar vistas en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f7fca-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="f7fca-117">No hay ningún límite al número de vistas que se pueden definir en un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="f7fca-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="f7fca-118">Puede agregar una vista única para cada objeto, varias vistas para el mismo objeto o una vista única que sirve para varios objetos.</span><span class="sxs-lookup"><span data-stu-id="f7fca-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7fca-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="f7fca-119">See Also</span></span>

[<span data-ttu-id="f7fca-120">Escribir un formato de Windows PowerShell y los tipos de archivo</span><span class="sxs-lookup"><span data-stu-id="f7fca-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
