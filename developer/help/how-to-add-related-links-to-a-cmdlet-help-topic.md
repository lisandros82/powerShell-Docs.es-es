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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083355"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Cómo agregar vínculos relacionados a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar referencias a otro contenido que está relacionado con un tema de Ayuda de cmdlet Windows PowerShell®. Dado que estas referencias aparecen en una ventana de comandos, no vincular directamente al contenido que se hace referencia.

En los temas de Ayuda de cmdlet que se incluyen en Windows PowerShell®, estos vínculos hacen referencia a otros cmdlets, el contenido conceptual ("about_") y otros documentos y archivos de ayuda que no están relacionadas con Windows PowerShell®.

El siguiente XML muestra cómo agregar un nodo RelatedLinks que contiene dos referencias a los temas relacionados.

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



