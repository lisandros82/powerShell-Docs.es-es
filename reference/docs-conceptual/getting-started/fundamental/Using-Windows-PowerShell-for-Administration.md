---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Usar Windows PowerShell para la administración
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954337"
---
# <a name="using-windows-powershell-for-administration"></a>Usar Windows PowerShell para la administración
El objetivo fundamental de Windows PowerShell es ofrecer un control administrativo mejor y más fácil sobre los sistemas, ya sea de manera interactiva o desde un script. En este capítulo se presentan soluciones a muchos problemas específicos de la administración de sistemas de Windows con Windows PowerShell. Aunque no hemos hablado de los scripts ni las funciones en la Guía de usuario de Windows PowerShell, las soluciones pueden usarse desde scripts o funciones posteriormente. Le mostraremos ejemplos que incluyen funciones como parte de la solución de problemas.

En las descripciones de la solución, verá una combinación de soluciones que usan cmdlets específicos, el cmdlet Get-WmiObject general e incluso herramientas externas que forman parte de las infraestructuras de Windows y .NET Framework. El uso de herramientas externas es parte de la intención de diseño a largo plazo de Windows PowerShell. Incluso cuando el sistema crece, los usuarios encontrarán continuamente situaciones en las que los conjuntos de herramientas disponibles no hacen todo lo que necesitan. En lugar de fomentar la dependencia en las implementaciones de cmdlet solamente, Windows PowerShell trata de admitir soluciones de integración de cada escenario alternativo posible.