---
title: Cómo crear un proveedor de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 06910f32752668f13400f9be0767a2179133df04
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081757"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Cómo crear un proveedor de Windows PowerShell

En esta sección se describe cómo crear un proveedor de Windows PowerShell. Un proveedor de Windows PowerShell puede considerarse de dos maneras. Para el usuario, el proveedor representa un conjunto de datos almacenados. Por ejemplo, los datos almacenados pueden ser la Metabase de Internet Information Services (IIS), el registro de Windows de Microsoft, el sistema de archivos de Windows, Active Directory y los datos de variable y alias almacenados mediante Windows PowerShell.

Para el desarrollador, el proveedor de Windows PowerShell es la interfaz entre el usuario y los datos que el usuario debe tener acceso. Desde esta perspectiva, cada tipo de proveedor que se describe en esta sección es compatible con un conjunto de clases específicas de bases e interfaces que permiten el tiempo de ejecución de Windows PowerShell exponer determinados cmdlets para el usuario de una manera común.

## <a name="providers-provided-by-windows-powershell"></a>Proveedores de Windows PowerShell

Windows PowerShell proporciona varios proveedores (por ejemplo, el proveedor FileSystem, el proveedor del registro y el proveedor de Alias) que se usan para tener acceso a almacenes de datos conocidos. Para obtener más información acerca de los proveedores proporcionados por Windows PowerShell, use el comando siguiente para acceder a la Ayuda en línea:

**PS > get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Obtener acceso a los datos almacenados mediante rutas de acceso de Windows PowerShell

Proveedores de Windows PowerShell son accesibles para el tiempo de ejecución de Windows PowerShell y comandos mediante programación mediante el uso de rutas de acceso de Windows PowerShell. La mayoría de los casos, estas rutas de acceso se utilizan para tener acceso directamente a los datos a través del proveedor. Sin embargo, algunas rutas de acceso se pueden resolver en rutas de acceso interna del proveedor que permiten un cmdlet para usar interfaces de programación de aplicaciones (API) de que no sean de Windows PowerShell para acceder a los datos. Para obtener más información sobre el funcionan de los proveedores de Windows PowerShell en Windows PowerShell, consulte [cómo Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Las unidades de exposición de los Cmdlets de proveedor mediante Windows PowerShell

Un proveedor de Windows PowerShell expone sus cmdlets compatibles con unidades de disco virtuales de Windows PowerShell. Windows PowerShell se aplica a las siguientes reglas para una unidad de Windows PowerShell:

- El nombre de una unidad puede ser cualquier secuencia alfanumérico.

- En cualquier momento válido en una ruta de acceso, denominado "raíz", se puede especificar una unidad.

- Puede implementarse una unidad de datos almacenados, no solo el sistema de archivos.

- Cada unidad mantiene su propia ubicación de trabajo actual, que permite al usuario conservar el contexto al cambiar entre las unidades.

## <a name="in-this-section"></a>En esta sección

En la tabla siguiente se enumera los temas que incluyen ejemplos de código que se compilan entre sí. Empezando por el segundo tema, el proveedor básico de Windows PowerShell se puede inicializar y sin inicializar el tiempo de ejecución de Windows PowerShell, el tema siguiente agrega funcionalidad para tener acceso a los datos, el siguiente tema agrega funcionalidad para manipular los datos ( los elementos de los datos almacenados), y así sucesivamente.

|Tema|Definición|
|-----------|----------------|
|[Diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)|Este tema describen los factores que debe considerar antes de implementar un proveedor de Windows PowerShell. Resume las clases base del proveedor de Windows PowerShell e interfaces que se usan.|
|[Creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite que el tiempo de ejecución de Windows PowerShell inicializar y anular la inicialización del proveedor.|
|[Creación de un proveedor de la unidad de PowerShell de Windows](./creating-a-windows-powershell-drive-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite al usuario acceder a un almacén de datos a través de una unidad de Windows PowerShell.|
|[Creación de un proveedor de elementos de PowerShell de Windows](./creating-a-windows-powershell-item-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite al usuario manipular los elementos en un almacén de datos.|
|[Creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite al usuario para que funcione en almacenes de datos de varias capas.|
|[Creación de un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite al usuario navegar por los elementos de un almacén de datos de forma jerárquica.|
|[Creación de un proveedor de contenido de PowerShell de Windows](./creating-a-windows-powershell-content-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite al usuario manipular el contenido de elementos en un almacén de datos.|
|[Creación de un proveedor de propiedades de PowerShell de Windows](./creating-a-windows-powershell-property-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite al usuario manipular las propiedades de elementos en un almacén de datos.|

## <a name="see-also"></a>Véase también

[Cómo funciona Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)
