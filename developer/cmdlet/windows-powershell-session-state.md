---
title: Estado de sesión de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066981"
---
# <a name="windows-powershell-session-state"></a>Estado de sesión de Windows PowerShell

Estado de sesión se refiere a la configuración actual de una sesión de Windows PowerShell o el módulo. Una sesión de Windows PowerShell es el entorno operativo que se usa de forma interactiva por el usuario de la línea de comandos o mediante programación una aplicación host. El estado de una sesión se conoce como el estado de sesión global.

Desde la perspectiva del desarrollador, una sesión de Windows PowerShell se refiere al tiempo de entre una aplicación host cuando abre un espacio de ejecución de Windows PowerShell y cuando cierra el espacio de ejecución. Visto de otra forma, la sesión sea la duración de una instancia del motor de Windows PowerShell que se invoca mientras existe el espacio de ejecución.

## <a name="module-session-state"></a>Estado de sesión del módulo

Estados de sesión del módulo se crean cada vez que se importa el módulo o uno de sus módulos anidados en la sesión. Cuando un módulo exporta un elemento como un cmdlet, función o script, se agrega una referencia a ese elemento en el estado de sesión global de la sesión. Sin embargo, cuando se ejecuta el elemento, se ejecuta en el estado de sesión del módulo.

## <a name="session-state-data"></a>Datos de estado de sesión

Datos de estado de sesión pueden ser público o privado. Datos públicos están disponibles para las llamadas desde fuera del estado de sesión mientras los datos privados solo están disponibles para llamadas desde el estado de sesión. Por ejemplo, un módulo puede tener una función privada que se puede llamar solo por el módulo o sólo internamente por un elemento público que se ha exportado. Esto es similar a los miembros públicos y privados de un tipo de .NET Framework.

Datos de estado de sesión se almacenan por la instancia actual del motor de ejecución dentro del contexto de la sesión actual de Windows PowerShell. Datos de estado de sesión constan de los siguientes elementos:

- Información de ruta de acceso

- Información de la unidad

- Información del proveedor de Windows PowerShell

- Información sobre los módulos importados y referencias a los elementos de módulo (como cmdlets, funciones y scripts) que se exportan el módulo. Esta información y estas referencias son de solo el estado de sesión global.

- Información de variable de estado de sesión

## <a name="accessing-session-state-data-within-cmdlets"></a>Acceso a los datos de estado de sesión dentro de los Cmdlets

Cmdlets puede tener acceso a datos de estado de sesión o indirectamente a través del [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) propiedad de la clase del cmdlet o directamente a través del [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) clase. El [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) clase proporciona propiedades que pueden utilizarse para investigar los distintos tipos de datos de estado de sesión.

## <a name="see-also"></a>Véase también

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Cmdlets de Windows PowerShell](./cmdlet-overview.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Shell de SDK de Windows PowerShell](../windows-powershell-reference.md)
