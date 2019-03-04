---
title: Referencia de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: dfda6cb68b089a30a156760345420ee80d1d3ae9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862111"
---
# <a name="windows-powershell-reference"></a>Referencia de Windows PowerShell

Windows PowerShell es un entorno de conectadas a .NET Framework de Microsoft diseñado para la automatización administrativa. Windows PowerShell proporciona un nuevo enfoque para generar los comandos, componer soluciones y creación gráfica de usuario de las herramientas de administración basado en la interfaz.

Windows PowerShell permite a un administrador del sistema automatizar la administración de recursos del sistema mediante la ejecución de comandos directamente o a través de scripts.

## <a name="developer-audience"></a>Audiencia de desarrolladores

El Kit de desarrollo de Software (SDK) de Windows PowerShell se ha diseñado para los desarrolladores de comando que requieren información de referencia sobre las API proporcionadas por Windows PowerShell. Los desarrolladores de comandos use Windows PowerShell para crear comandos y proveedores que extienden las tareas que pueden realizarse mediante Windows PowerShell.

## <a name="windows-powershell-resources"></a>Recursos de Windows PowerShell

Además del SDK de Windows PowerShell, los siguientes recursos proporcionan más información.

[Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) proporciona una introducción a Windows PowerShell: el idioma, los cmdlets, los proveedores y el uso de objetos.

[Escribir un módulo de Windows PowerShell](./module/writing-a-windows-powershell-module.md) proporciona información y ejemplos para los administradores, desarrolladores de secuencia de comandos y los desarrolladores de cmdlets que necesitan para empaquetar y distribuir sus soluciones de Windows PowerShell mediante los módulos de Windows PowerShell.

[Escribir un Cmdlet de Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) proporciona información y ejemplos de código para los administradores de programas que diseñan los cmdlets y para los desarrolladores que están implementando el código del cmdlet.

[Blog del equipo de Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) el mejor recurso para aprender y colaborar con otros usuarios de Windows PowerShell. Lea el blog del equipo de Windows PowerShell y, a continuación, unir el foro de usuarios de Windows PowerShell (microsoft.public.windows.powershell). Use Windows Live Search para buscar otros blogs de Windows PowerShell y recursos. A continuación, al desarrollar sus conocimientos, libremente aportar sus propias ideas.

[Explorador de módulos de PowerShell](/powershell/module/) proporciona las últimas versiones de los temas de Ayuda de línea de comandos.

## <a name="class-libraries"></a>Bibliotecas de clases

[System.Management.Automation](/dotnet/api/System.Management.Automation) este espacio de nombres es el espacio de nombres raíz de Windows PowerShell. Contiene las clases, enumeraciones e interfaces necesarias para implementar cmdlets personalizados. En concreto, el [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase es la clase base de todos los cmdlet se deben derivar las clases. Para obtener más información acerca de los cmdlets, vea.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) este espacio de nombres contiene las clases, enumeraciones e interfaces necesarias para implementar un proveedor de Windows PowerShell. En concreto, el [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase es la clase base desde qué todas PowerShell de Windows se deben derivar clases de proveedor.

[Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) este espacio de nombres contiene las clases para los cmdlets y proveedores implementados por Windows PowerShell. Del mismo modo, se recomienda que cree un *YourName*. Espacio de nombres de comandos para los cmdlets que implementan.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) este espacio de nombres contiene las clases, enumeraciones e interfaces que el cmdlet se usa para definir la interacción entre el usuario y Windows PowerShell.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) este espacio de nombres contiene las clases bases utilizadas por otras clases del espacio de nombres. Por ejemplo, el [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) clase es la clase base para el [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) clase.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) este espacio de nombres contiene las clases, enumeraciones e interfaces utilizadas para crear un espacio de ejecución de Windows PowerShell. En este contexto, el proceso de Windows PowerShell es el contexto en el que una o varias canalizaciones de Windows PowerShell invocan cmdlets. Es decir, los cmdlets funcionan dentro del contexto de un espacio de ejecución de Windows PowerShell. Para obtener más información aboutWindows espacios de ejecución de PowerShell, consulte [espacios de ejecución de Windows PowerShell](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
