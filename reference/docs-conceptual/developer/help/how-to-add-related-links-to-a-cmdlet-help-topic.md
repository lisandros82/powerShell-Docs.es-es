---
title: Cómo agregar vínculos relacionados a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361224"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="070e7-102">Cómo agregar vínculos relacionados a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="070e7-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="070e7-103">En esta sección se describe cómo agregar referencias a otro contenido relacionado con un tema de ayuda del cmdlet de® de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="070e7-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="070e7-104">Dado que estas referencias aparecen en una ventana de comandos, no se vinculan directamente al contenido al que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="070e7-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="070e7-105">En los temas de ayuda de los cmdlets que se incluyen en Windows PowerShell®, estos vínculos hacen referencia a otros cmdlets, contenido conceptual ("about_") y otros documentos y archivos de ayuda que no están relacionados con® de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="070e7-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="070e7-106">El siguiente XML muestra cómo agregar un nodo RelatedLinks que contiene dos referencias a temas relacionados.</span><span class="sxs-lookup"><span data-stu-id="070e7-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```



