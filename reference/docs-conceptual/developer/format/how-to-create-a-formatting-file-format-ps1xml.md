---
title: Cómo crear un archivo de formato (. Format. ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363624"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="694e7-102">Cómo crear un archivo de formato (. format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="694e7-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="694e7-103">En este tema se describe cómo crear un archivo de formato (. Format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="694e7-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="694e7-104">También puede crear un archivo de formato si realiza una copia de uno de los archivos proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="694e7-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="694e7-105">Si realiza una copia de un archivo existente, elimine la firma digital existente y agregue su propia firma al nuevo archivo.</span><span class="sxs-lookup"><span data-stu-id="694e7-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="694e7-106">Para crear un archivo. Format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="694e7-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="694e7-107">Cree un archivo de texto (. txt) mediante un editor de texto como el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="694e7-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="694e7-108">Copie las líneas siguientes en el archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="694e7-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="694e7-109">Las etiquetas de configuración de \<\</Configuración > definen el nodo raíz `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="694e7-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="694e7-110">Todas las etiquetas XML adicionales se incluirán dentro de este nodo.</span><span class="sxs-lookup"><span data-stu-id="694e7-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="694e7-111">Las <ViewDefinitions></ViewDefinitions> etiquetas definen el nodo de `ViewDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="694e7-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="694e7-112">Todas las vistas se definen dentro de este nodo.</span><span class="sxs-lookup"><span data-stu-id="694e7-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="694e7-113">Guarde el archivo en la carpeta de instalación de Windows PowerShell, en la carpeta del módulo o en una subcarpeta de la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="694e7-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="694e7-114">Use el siguiente formato de nombre al guardar el archivo: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="694e7-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="694e7-115">Los archivos de formato deben utilizar la extensión `.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="694e7-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="694e7-116">Ahora está listo para agregar vistas al archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="694e7-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="694e7-117">No hay ningún límite en el número de vistas que se pueden definir en un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="694e7-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="694e7-118">Puede Agregar una vista única para cada objeto, varias vistas para el mismo objeto o una vista única que utilicen varios objetos.</span><span class="sxs-lookup"><span data-stu-id="694e7-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="694e7-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="694e7-119">See Also</span></span>

[<span data-ttu-id="694e7-120">Escribir un archivo de formato y tipos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="694e7-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
