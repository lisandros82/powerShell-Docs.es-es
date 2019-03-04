---
title: Los parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853851"
---
# <a name="cmdlet-parameters"></a>Parámetros del cmdlet

Los parámetros de cmdlet proporcionan el mecanismo que permite que un cmdlet Aceptar la entrada. Los parámetros pueden aceptar directamente desde la línea de comandos o desde los objetos pasados al cmdlet a través de la canalización, los argumentos de entrada (también conocido como *valores*) de estos parámetros, puede especificar la entrada que el cmdlet acepta, el modo cmdlet debe realizar las acciones y los datos que el cmdlet devuelve a la canalización.

## <a name="in-this-section"></a>En esta sección

[Declarar propiedades como parámetros](./declaring-properties-as-parameters.md) proporciona información básica que debe conocer antes de declarar los parámetros de un cmdlet.

[Tipos de parámetros de Cmdlet](./types-of-cmdlet-parameters.md) describe los diferentes tipos de parámetros que se pueden declarar en los cmdlets.

[Nombre del parámetro de cmdlet y directrices de funcionalidad](./standard-cmdlet-parameter-names-and-types.md) analiza los nombres, se recomienda el tipo de datos y la funcionalidad de los parámetros estándar.

[Alias de parámetro](./parameter-aliases.md) se describen los alias que se pueden definir para los parámetros.

[Los nombres de parámetro comunes](./common-parameter-names.md) en este tema se describe los parámetros que Windows PowerShell agrega a los cmdlets.

[Conjuntos de parámetros de cmdlet](./cmdlet-parameter-sets.md) explica cómo conjuntos de parámetros le permiten escribir un solo cmdlet que puede realizar acciones diferentes para distintos escenarios.

[Los parámetros dinámicos de cmdlet](./cmdlet-dynamic-parameters.md) explica los parámetros que están disponibles para el usuario bajo condiciones especiales.

[Compatibilidad con caracteres comodín en los parámetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md) se describe cómo proporcionar compatibilidad con caracteres comodín cuando se diseña un cmdlet que se va a ejecutar en un grupo de recursos.

[Validar la entrada del parámetro](./validating-parameter-input.md) se describe cómo Windows PowerShell valida los argumentos pasados a los parámetros de cmdlet.

[Parámetros de filtro de entrada](./input-filter-parameters.md) trata la `Filter`, `Include`, y `Exclude` los parámetros que filtran el conjunto de objetos de entrada que afecta el cmdlet.

## <a name="related-sections"></a>Secciones relacionadas

[Cómo validar entrada de parámetros](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Véase también

[Declaración de atributo de parámetro](./parameter-attribute-declaration.md)

[Cmdlets de Windows PowerShell](./cmdlet-overview.md)
