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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Cómo agregar vínculos relacionados a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar referencias a otro contenido relacionado con un tema de ayuda del cmdlet de® de Windows PowerShell. Dado que estas referencias aparecen en una ventana de comandos, no se vinculan directamente al contenido al que se hace referencia.

En los temas de ayuda de los cmdlets que se incluyen en Windows PowerShell®, estos vínculos hacen referencia a otros cmdlets, contenido conceptual ("about_") y otros documentos y archivos de ayuda que no están relacionados con® de Windows PowerShell.

El siguiente XML muestra cómo agregar un nodo RelatedLinks que contiene dos referencias a temas relacionados.

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



