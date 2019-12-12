---
title: Cómo agregar notas a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361274"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="57547-102">Cómo agregar notas a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="57547-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="57547-103">En esta sección se describe cómo agregar una sección Notas a un tema de ayuda del cmdlet de® de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57547-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="57547-104">La sección Notas se usa para explicar los detalles que no se ajustan a las demás secciones estructuradas, como una explicación más detallada de un parámetro.</span><span class="sxs-lookup"><span data-stu-id="57547-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="57547-105">Este contenido podría incluir comentarios sobre cómo funciona el cmdlet con un proveedor específico, algunos usos únicos, pero importantes, del cmdlet o formas de evitar posibles condiciones de error.</span><span class="sxs-lookup"><span data-stu-id="57547-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="57547-106">No hay ningún límite en el número de notas que puede Agregar a una sección Notas.</span><span class="sxs-lookup"><span data-stu-id="57547-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="57547-107">Por cada nota, agregue un par de etiquetas \<maml: Alert > al nodo \<maml: alertset >.</span><span class="sxs-lookup"><span data-stu-id="57547-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="57547-108">El contenido de cada nota se agrega dentro de un conjunto de etiquetas \<maml: para >.</span><span class="sxs-lookup"><span data-stu-id="57547-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="57547-109">Use las etiquetas en blanco \<maml: para > para el espaciado.</span><span class="sxs-lookup"><span data-stu-id="57547-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="57547-110">El siguiente código XML muestra un nodo \<maml: alertset > con dos notas.</span><span class="sxs-lookup"><span data-stu-id="57547-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="57547-111">Tenga en cuenta que cada nota tiene una etiqueta opcional \<maml: title > (los títulos se pueden usar para agrupar cualquier conjunto de \<maml: Alert > Tags) y que cada nota tiene una línea en blanco que sigue el contenido para el espaciado.</span><span class="sxs-lookup"><span data-stu-id="57547-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



