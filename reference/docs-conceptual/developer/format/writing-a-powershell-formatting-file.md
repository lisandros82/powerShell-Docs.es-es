---
title: Escribiendo un archivo de formato de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361414"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="e6255-102">Escritura de un archivo de formato de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e6255-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="e6255-103">"Escribir un archivo de formato de PowerShell" es para los desarrolladores de comandos que están escribiendo cmdlets o funciones que envían objetos a la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="e6255-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="e6255-104">Los archivos de formato definen cómo PowerShell muestra esos objetos en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="e6255-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="e6255-105">En esta documentación se proporciona información general sobre los archivos de formato, una explicación de los conceptos que debe comprender al escribir estos archivos, ejemplos de XML que se usan en estos archivos y una sección de referencia para los elementos XML.</span><span class="sxs-lookup"><span data-stu-id="e6255-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e6255-106">En esta sección</span><span class="sxs-lookup"><span data-stu-id="e6255-106">In This Section</span></span>

<span data-ttu-id="e6255-107">[Información general sobre el formato de archivo](./formatting-file-overview.md) Describe qué es un archivo de formato y los componentes generales de un archivo de formato, incluidas las características comunes que se pueden definir en el archivo, los distintos tipos de vistas de formato que se pueden definir para los objetos .NET y un ejemplo simplificado del XML que se usa para definir una vista de tabla.</span><span class="sxs-lookup"><span data-stu-id="e6255-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="e6255-108">[Conceptos del archivo de formato](./formatting-file-concepts.md) Incluye información que podría necesitar saber al crear sus propios archivos de formato, como los diferentes tipos de vistas que puede definir y componentes especiales de esas vistas.</span><span class="sxs-lookup"><span data-stu-id="e6255-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="e6255-109">[Ejemplos de archivos de formato](./examples-of-formatting-files.md) Proporciona ejemplos XML de varios archivos de formato, incluidos ejemplos de una vista de tabla, una vista de lista y una vista amplia, así como ejemplos que muestran cómo definir características como conjuntos de selección, condiciones de selección y controles comunes.</span><span class="sxs-lookup"><span data-stu-id="e6255-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="e6255-110">[Referencia de formato XML](./format-schema-xml-reference.md) Incluye temas de referencia para los elementos XML utilizados en un archivo de formato.</span><span class="sxs-lookup"><span data-stu-id="e6255-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
