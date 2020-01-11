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
ms.openlocfilehash: c00590df4d07e0f5ed9e93fd84a2780329753e39
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870870"
---
# <a name="windows-powershell-reference"></a>Referencia de Windows PowerShell

Windows PowerShell es un entorno conectado a un marco de Microsoft .NET diseñado para la automatización administrativa. Windows PowerShell proporciona un enfoque nuevo para compilar comandos, componer soluciones y crear herramientas de administración basadas en la interfaz gráfica de usuario.

Windows PowerShell permite que un administrador del sistema automatice la administración de recursos del sistema mediante la ejecución de comandos, ya sea directamente o a través de scripts.

## <a name="developer-audience"></a>Audiencia de los desarrolladores

El kit de desarrollo de software (SDK) de Windows PowerShell está escrito para los desarrolladores de comandos que necesitan información de referencia sobre las API proporcionadas por Windows PowerShell. Los desarrolladores de comandos usan Windows PowerShell para crear comandos y proveedores que extienden las tareas que puede realizar Windows PowerShell.

## <a name="windows-powershell-resources"></a>Recursos de Windows PowerShell

Además del SDK de Windows PowerShell, los siguientes recursos proporcionan más información.

[Introducción con Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Proporciona una introducción a Windows PowerShell: el lenguaje, los cmdlets, los proveedores y el uso de objetos.

[Escribir un módulo de Windows PowerShell](./module/writing-a-windows-powershell-module.md) Proporciona información y ejemplos para administradores, desarrolladores de scripts y desarrolladores de cmdlets que necesitan empaquetar y distribuir sus soluciones de Windows PowerShell con los módulos de Windows PowerShell.

[Escribir un cmdlet de Windows PowerShell](./cmdlet/writing-a-windows-powershell-cmdlet.md) Proporciona información y ejemplos de código para los administradores de programas que diseñan cmdlets y para desarrolladores que implementan código de cmdlet.

[Blog del equipo de Windows PowerShell](https://blogs.msdn.microsoft.com/PowerShell/) El mejor recurso para aprender y colaborar con otros usuarios de Windows PowerShell. Lea el blog del Equipo de Windows PowerShell y únase al Foro de usuarios de Windows PowerShell (microsoft.public.windows.powershell).
Use Windows Live Search para buscar en otros blogs y recursos de Windows PowerShell. Después, a medida que desarrolle sus conocimientos, puede colaborar libremente con sus ideas.

[Explorador de módulos de PowerShell](/powershell/module/) Proporciona las versiones más recientes de los temas de ayuda de la línea de comandos.

## <a name="class-libraries"></a>Bibliotecas de clases

[System. Management. Automation](/dotnet/api/System.Management.Automation) este espacio de nombres es el espacio de nombres raíz para Windows PowerShell. Contiene las clases, enumeraciones e interfaces necesarias para implementar cmdlets personalizados. En concreto, la clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) es la clase base de la que se deben derivar todas las clases de cmdlet. Para obtener más información acerca de los cmdlets, vea.

[System. Management. Automation. Provider](/dotnet/api/System.Management.Automation.Provider) : este espacio de nombres contiene las clases, enumeraciones e interfaces necesarias para implementar un proveedor de Windows PowerShell. En concreto, la clase [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) es la clase base de la que se deben derivar todas las clases de proveedor de Windows PowerShell.

[Microsoft. PowerShell. Commands](/dotnet/api/Microsoft.PowerShell.Commands) este espacio de nombres contiene las clases para los cmdlets y proveedores implementados por Windows PowerShell. Del mismo modo, se recomienda que cree un *sunombre*. Espacio de nombres de los comandos para los cmdlets que se implementan.

[System. Management. Automation. host:](/dotnet/api/System.Management.Automation.Host) este espacio de nombres contiene las clases, enumeraciones e interfaces que el cmdlet usa para definir la interacción entre el usuario y Windows PowerShell.

[System. Management. Automation. Internal](/dotnet/api/System.Management.Automation.Internal) este espacio de nombres contiene las clases base utilizadas por otras clases de espacio de nombres. Por ejemplo, la clase [System. Management. Automation. Internal. Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) es la clase base de la clase [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .

[System. Management. Automation.](/dotnet/api/System.Management.Automation.Runspaces) runspace este espacio de nombres contiene las clases, enumeraciones e interfaces que se usan para crear un espacio de ejecución de Windows PowerShell. En este contexto, el espacio de ejecución de Windows PowerShell es el contexto en el que una o más canalizaciones de Windows PowerShell invocan cmdlets. Es decir, los cmdlets funcionan en el contexto de un espacio de ejecución de Windows PowerShell. Para obtener más información sobre los espacios de aboutWindows de PowerShell, consulte [espacios de Windows PowerShell](hosting/creating-runspaces.md).
