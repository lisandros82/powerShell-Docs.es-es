---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Información general sobre la configuración de estado deseado para responsables de toma de decisiones
ms.openlocfilehash: 70fc5c55266970165dc16eac85f6b850cf409d64
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189880"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Información general sobre la configuración de estado deseado para responsables de toma de decisiones

En este documento se describen los beneficios de negocio del uso de la configuración de estado deseado (DSC) de PowerShell. No se trata de una guía técnica.

## <a name="what-is-desired-state-configuration"></a>¿Qué es la configuración de estado deseado?

La configuración de estado deseado (DSC) de Windows PowerShell ofrece una plataforma de administración de configuración integrada en Windows que se basa en estándares abiertos. DSC es lo suficientemente flexible como para funcionar de forma confiable y coherente en cada una de las etapas del ciclo de vida de implementación (desarrollo, prueba, preproducción, producción), así como durante el escalado horizontal.

Centros de DSC alrededor de "[configuraciones](https://msdn.microsoft.com/powershell/dsc/configurations)".
Una configuración es un documento fácil de leer que describe un entorno compuesto por equipos ("nodos") con características específicas.
Estas características pueden ser tan sencillas como garantizar que una característica concreta de Windows está habilitada o tan complejas como la implementación de SharePoint.

DSC también tiene supervisión y generación de informes integradas.
Si un sistema ya no es conforme, DSC puede generar una alerta y actuar para corregir el sistema.

## <a name="benefits-of-using-desired-state-configuration"></a>Ventajas de usar la configuración de estado deseado

Las configuraciones están diseñadas para que se puedan leer, almacenar y actualizar fácilmente.
Las configuraciones declaran el estado en que deberían estar los dispositivos de destino, en lugar de escribir instrucciones sobre cómo hacer que lleguen a ese estado.
Esto permite que la configuración mediante DSC sea mucho menos costosa de aprender, adoptar, implementar y mantener.

La creación de configuraciones implica que se capturen los pasos de implementación complejos como un "origen único de verdad" en una ubicación única.
Esto hace que las implementaciones repetidas de un conjunto concreto de máquinas sean mucho menos propensas a errores.
A su vez, hace que las implementaciones sean más rápidas y confiables, lo que permite un tiempo de entrega rápido en las implementaciones complejas.

Las configuraciones también se pueden compartir mediante la [Galería de PowerShell](https://powershellgallery.com), lo que significa que es posible que ya existan escenarios comunes y procedimientos recomendados para el trabajo que necesita realizar.


## <a name="desired-state-configuration-and-devops"></a>Configuración de estado deseado y DevOps

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) es una combinación de personas, procesos y herramientas que permiten una rápida implementación e iteración centrada en la entrega de valor a los usuarios finales, ya sean internos o externos.
DSC se diseñó con DevOps en mente.
Que una sola configuración defina un entorno significa que los desarrolladores pueden codificar sus requisitos en una configuración, incorporar esa configuración en el control de código fuente, y los equipos de operaciones pueden implementar fácilmente el código sin tener que realizar procesos manuales propensos a errores.

Las configuraciones también están [controladas por datos](https://msdn.microsoft.com/powershell/dsc/configdata), lo que facilita que los equipos de operaciones identifiquen y cambien los entornos sin intervención del programador.

## <a name="desired-state-configuration-on--and-off-premises"></a>Desired State Configuration local y remota

DSC se puede usar para administrar implementaciones locales y remotas.
Para las soluciones locales, DSC tiene un [servidor de extracción](https://msdn.microsoft.com/powershell/dsc/pullserver) que puede utilizarse para centralizar la administración de máquinas e informar sobre su estado.
Para las soluciones de nube, DSC se puede utilizar siempre que se pueda usar Windows.
También hay ofertas específicas de Azure basadas en la configuración de estado deseado, como [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), que centraliza la creación de informes de DSC.

## <a name="dsc-and-compatibility"></a>DSC y la compatibilidad

Aunque DSC se introdujo en Windows Server 2012 R2, está disponible para los sistemas operativos inferiores mediante el paquete Windows Management Framework (WMF).
Puede encontrar más información sobre WMF en la [página principal de PowerShell](https://msdn.microsoft.com/en-us/powershell/).

DSC también se puede usar para administrar Linux. Para más información, consulte [Introducción a la configuración de estado deseado (DSC) para Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).