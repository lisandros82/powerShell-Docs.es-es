---
title: Cómo agregar notas a un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862271"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="282fa-102">Cómo agregar notas a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="282fa-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="282fa-103">En esta sección se describe cómo agregar una sección de notas a un tema de Ayuda de cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="282fa-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="282fa-104">La sección Notas se utiliza para explicar los detalles que no se ajustan fácilmente a las demás secciones estructuradas, como una explicación más detallada de un parámetro.</span><span class="sxs-lookup"><span data-stu-id="282fa-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="282fa-105">Este contenido puede incluir comentarios acerca de cómo funciona el cmdlet con un proveedor concreto, algunos usos únicos, aunque importantes, del cmdlet o las formas de evitar posibles condiciones de error.</span><span class="sxs-lookup"><span data-stu-id="282fa-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="282fa-106">No hay ningún límite al número de notas de la que se pueden agregar a una sección de notas.</span><span class="sxs-lookup"><span data-stu-id="282fa-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="282fa-107">Para cada nota, agregue un par de \<maml:alert > etiquetas para el \<maml:alertset > nodo.</span><span class="sxs-lookup"><span data-stu-id="282fa-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="282fa-108">Se agrega el contenido de cada nota dentro de un conjunto de \<maml: para > etiquetas.</span><span class="sxs-lookup"><span data-stu-id="282fa-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="282fa-109">Use espacio en blanco \<maml: para > etiquetas para el espaciado.</span><span class="sxs-lookup"><span data-stu-id="282fa-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="282fa-110">El siguiente XML muestra un \<maml:alertset > nodo con dos nodos.</span><span class="sxs-lookup"><span data-stu-id="282fa-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="282fa-111">Tenga en cuenta que todas las notas tiene un elemento opcional \<maml: Title > etiqueta (títulos pueden utilizarse para agrupar cualquier conjunto de \<maml:alert > etiquetas), y que todas las notas tiene una línea en blanco que siguen al contenido para el espaciado.</span><span class="sxs-lookup"><span data-stu-id="282fa-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



