---
title: "Información general sobre la configuración de estado deseado de Windows PowerShell"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: ec773688540a3f4a2f128f66d311926fd5b9a935
ms.sourcegitcommit: 6d27d6db5ab0e2d5b6c7229e2e2d2e57915ea22d
translationtype: HT
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Información general sobre la configuración de estado deseado de Windows PowerShell 

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC es una plataforma de administración de PowerShell que le permite administrar su infraestructura de desarrollo y TI con configuración como código.

- Para información general de las ventajas empresariales de usar DSC, consulte [Información general sobre la configuración de estado deseado para responsables de toma de decisiones](decisionMaker.md).
- Para obtener información general de las ventajas de ingeniería de usar DSC, consulte [Información general sobre la configuración de estado deseado para ingenieros](DscForEngineers.md).
- Para empezar a usar DSC rápidamente, consulte [Inicio rápido de la configuración de estado deseado](quickStart.md).

## <a name="key-concepts"></a>Conceptos clave

DSC es una plataforma declarativa que se usa para la configuración, implementación y administración de sistemas. Consta de tres componentes principales:

- Las [configuraciones](configurations.md) son scripts de PowerShell declarativos que definen y configuran instancias de recursos.
    Cuando ejecuta la configuración, DSC (y los recursos a los que llama la configuración) simplemente "hará que sea así", asegurándose de que el sistema exista en el estado que disponga la configuración. 
    Las configuraciones DSC también son idempotentes: el administrador de configuración local (LCM) seguirá garantizando que las máquinas estén configuradas en el estado que la configuración declare.
- Los recursos son la parte "hacer que sea así" de DSC. Contienen el código que coloca y mantiene el destino de una configuración en el estado especificado. 
    Los recursos residen en los módulos de PowerShell y pueden escribirse para modelar algo tan genérico como un archivo o un proceso de Windows, o algo tan específico como un servidor IIS o una VM que se ejecuta en Azure.
- El administrador de configuración local (LCM) es el motor mediante el que DSC facilita la interacción entre recursos y configuraciones. 
    El LCM sondea periódicamente el sistema mediante el flujo de control que han implementado los recursos para asegurarse de que se mantiene el estado que ha definido una configuration. 
    Si el sistema está fuera del estado, el LCM llama al código de los recursos para "hacer que sea así" según la declaración de la configuration. 

## <a name="see-also"></a>Véase también

- [Configuraciones DSC](configurations.md)
- [Recursos de DSC](resources.md)
- [Configuración del administrador de configuración local](metaConfig.md)

