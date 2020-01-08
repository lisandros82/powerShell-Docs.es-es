---
ms.date: 10/11/2019
keywords: dsc,powershell,configuration,setup
title: Información general sobre la configuración de estado deseado para responsables de toma de decisiones
ms.openlocfilehash: b6d483d105c2d3b9be7215be36397d452338c7f1
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737260"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Información general sobre Desired State Configuration para responsables de toma de decisiones

En este documento se describen los beneficios de negocio del uso de Desired State Configuration (DSC) de PowerShell, además de una guía técnica.

## <a name="what-is-dsc"></a>¿Qué es DSC?

DSC de PowerShell ofrece una plataforma de administración de configuración integrada en Windows que se basa en estándares abiertos. DSC es lo suficientemente flexible como para funcionar de forma confiable y coherente en cada una de las etapas del ciclo de vida de implementación (desarrollo, prueba, preproducción, producción), así como durante el escalado horizontal.

Centros de DSC alrededor de [configuraciones](../configurations/configurations.md). Una configuración es un script de PowerShell que describe un entorno compuesto por equipos (o nodos) con características específicas. Estas características pueden ser tan sencillas como garantizar que una característica concreta de Windows está habilitada o tan complejas como la implementación de SharePoint.

DSC tiene supervisión y generación de informes integradas. Si un sistema ya no es conforme, DSC puede generar una alerta y actuar para corregir el sistema.

## <a name="benefits-of-using-dsc"></a>Ventajas del uso de DSC

El diseño de la configuración simplifica el modo en que se leen, almacenan y actualizan. Las configuraciones declaran el estado de los dispositivos de destino, en lugar de escribir instrucciones sobre cómo colocar los dispositivos en ese estado. Estos factores reducen los costos de aprender, adoptar, implementar y mantener la configuración a través de DSC.

La creación de configuraciones implica que se capturen los pasos de implementación complejos como un **origen único de verdad** en una ubicación única. Las configuraciones hacen que las implementaciones repetidas de un conjunto de máquinas en concreto sean mucho menos propensas a errores. Y las implementaciones son más rápidas y confiables, lo que permite un tiempo de entrega rápido en las implementaciones complejas.

Las configuraciones se pueden compartir a través de la [Galería de PowerShell](https://powershellgallery.com). Es posible que ya existan escenarios comunes y procedimientos recomendados para el trabajo que necesita hacer.

## <a name="dsc-and-devops"></a>DSC y DevOps

DSC se diseñó con [DevOps](/archive/blogs/ashleymcglone/devops-for-n00bs-ie-windows-people-like-me) en mente. Una combinación de personas, procesos y herramientas que permiten una rápida implementación e iteración centrada en la entrega de valor a los usuarios finales, ya sean internos o externos. Una configuración única que define un entorno significa que los desarrolladores pueden codificar sus requisitos en una configuración y comprobar esa configuración en el control de código fuente. Después, los equipos de operaciones pueden implementar código sin pasar por procesos manuales propensos a errores.

Las configuraciones están [orientadas a los datos](../configurations/configData.md). Los datos definidos facilitan que las operaciones identifiquen y cambien los entornos sin intervención del desarrollador.

## <a name="dsc-on-premises-and-off-premises"></a>DSC dentro y fuera del entorno local

DSC puede administrar implementaciones locales y fuera de las instalaciones. Para las soluciones locales, DSC tiene un [servidor de extracción](../pull-server/pullServer.md) que se usa para centralizar la administración de máquinas e informar sobre su estado. En el caso de las soluciones en la nube fuera de las instalaciones, DSC se puede usar en cualquier lugar en el que se pueda usar Windows.
Hay ofertas específicas de Azure basadas en DSC, como [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), que centraliza la generación de informes de DSC.

## <a name="dsc-and-compatibility"></a>DSC y la compatibilidad

DSC se introdujo en Windows Server 2012 R2, pero está disponible para los sistemas operativos inferiores mediante Windows Management Framework (WMF). Para más información sobre WMF, consulte [Windows Management Framework](/powershell/scripting/wmf/overview).

DSC se puede usar para administrar Linux. Para más información, consulte [Introducción a la configuración de estado deseado (DSC) para Linux](../getting-started/lnxGettingStarted.md).
