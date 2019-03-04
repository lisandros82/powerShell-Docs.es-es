---
title: Cómo agregar vínculos relacionados a un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855401"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="885fa-102">Cómo agregar vínculos relacionados a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="885fa-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="885fa-103">En esta sección se describe cómo agregar referencias a otro contenido que está relacionado con un tema de Ayuda de cmdlet Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="885fa-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="885fa-104">Dado que estas referencias aparecen en una ventana de comandos, no vincular directamente al contenido que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="885fa-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="885fa-105">En los temas de Ayuda de cmdlet que se incluyen en Windows PowerShell®, estos vínculos hacen referencia a otros cmdlets, el contenido conceptual ("about_") y otros documentos y archivos de ayuda que no están relacionadas con Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="885fa-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="885fa-106">El siguiente XML muestra cómo agregar un nodo RelatedLinks que contiene dos referencias a los temas relacionados.</span><span class="sxs-lookup"><span data-stu-id="885fa-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



