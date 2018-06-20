---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Canalización de objetos
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 6102ec6e8fbf38fdc2bc5fa9c583244ef639dec8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30948217"
---
# <a name="object-pipeline"></a>Canalización de objetos
Las canalizaciones actúan como una serie de segmentos de canalización conectados. Los elementos que se mueven por la canalización pasan a través de cada segmento. Para crear una canalización en Windows PowerShell, se conectan comandos con el operador de canalización "|". La salida de cada comando se usa como entrada para el siguiente.

Las canalizaciones son sin duda el concepto más valioso usado en las interfaces de línea de comandos. Si se usan correctamente, la canalizaciones no solo reducen el esfuerzo que implica escribir comandos complejos, sino que también facilitan la visualización del flujo de trabajo en los comandos. Una característica útil relacionada de las canalizaciones es que, dado que operan en cada elemento por separado, no tienen que modificarse según la ausencia de elementos o la presencia de uno o muchos elementos en la canalización. Además, cada comando de una canalización (denominado un elemento de canalización) suele pasar la salida al siguiente comando de la canalización elemento por elemento. Normalmente, esto reduce la demanda de recursos de comandos complejos y permite empezar a obtener la salida inmediatamente.

En este capítulo, se describe cómo la canalización de Windows PowerShell difiere de las canalizaciones de los shells más populares y, luego, se muestran algunas herramientas básicas que puede usar para simplificar el control de la salida de la canalización y para ver cómo funciona la canalización.