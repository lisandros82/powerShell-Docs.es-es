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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369104"
---
# <a name="windows-powershell-session-state"></a>Estado de sesión de Windows PowerShell

El estado de sesión hace referencia a la configuración actual de un módulo o sesión de Windows PowerShell. Una sesión de Windows PowerShell es el entorno operativo que usa el usuario de línea de comandos de forma interactiva o mediante programación para una aplicación host. El estado de sesión de una sesión se conoce como estado de sesión global.

Desde la perspectiva del desarrollador, una sesión de Windows PowerShell se refiere al tiempo entre el momento en que una aplicación host abre un espacio de ejecución de Windows PowerShell y cuando cierra el espacio de ejecución. En otra forma, la sesión es la duración de una instancia del motor de Windows PowerShell que se invoca mientras existe el espacio de ejecución.

## <a name="module-session-state"></a>Estado de sesión del módulo

Los Estados de la sesión del módulo se crean cada vez que el módulo o uno de sus módulos anidados se importa en la sesión. Cuando un módulo exporta un elemento, como un cmdlet, una función o un script, se agrega una referencia a ese elemento al estado de sesión global de la sesión. Sin embargo, cuando se ejecuta el elemento, se ejecuta en el estado de sesión del módulo.

## <a name="session-state-data"></a>Datos de estado de sesión

Los datos de estado de sesión pueden ser públicos o privados. Los datos públicos están disponibles para las llamadas desde fuera del estado de sesión mientras que los datos privados solo están disponibles para las llamadas desde el estado de sesión. Por ejemplo, un módulo puede tener una función privada a la que solo puede llamar el módulo o que solo un elemento público que se ha exportado internamente. Esto es similar a los miembros públicos y privados de un tipo de .NET Framework.

Los datos de estado de sesión se almacenan en la instancia actual del motor de ejecución en el contexto de la sesión actual de Windows PowerShell. Los datos de estado de sesión se componen de los siguientes elementos:

- Información de ruta de acceso

- Información de la unidad

- Información del proveedor de Windows PowerShell

- Información sobre los módulos importados y las referencias a los elementos de módulo (como cmdlets, funciones y scripts) que exporta el módulo. Esta información y estas referencias solo son para el estado de sesión global.

- Información de variable de estado de sesión

## <a name="accessing-session-state-data-within-cmdlets"></a>Obtener acceso a los datos de estado de sesión en cmdlets

Los cmdlets pueden tener acceso indirectamente a los datos de estado de sesión a través de la propiedad [System. Management. Automation. PSCmdlet. SessionState *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) de la clase de cmdlet o directamente a través de la clase [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) . La clase [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) proporciona propiedades que se pueden utilizar para investigar distintos tipos de datos de estado de sesión.

## <a name="see-also"></a>Véase también

[System. Management. Automation. PSCmdlet. SessionState](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System. Management. Automation. SessionState? Displayproperty = FullName](/dotnet/api/System.Management.Automation.SessionState)

[Cmdlets de Windows PowerShell](./cmdlet-overview.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[SDK de Windows PowerShell Shell](../windows-powershell-reference.md)
