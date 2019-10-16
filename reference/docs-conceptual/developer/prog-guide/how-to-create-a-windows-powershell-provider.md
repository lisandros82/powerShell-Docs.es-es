---
title: Cómo crear un proveedor de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: ffbf8028ba2b52e77d8e22c061baa9b8b67f6da3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366654"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Cómo crear un proveedor de Windows PowerShell

En esta sección se describe cómo crear un proveedor de Windows PowerShell. Un proveedor de Windows PowerShell se puede considerar de dos maneras. Para el usuario, el proveedor representa un conjunto de datos almacenados. Por ejemplo, los datos almacenados pueden ser la metabase de Internet Information Services (IIS), el registro de Microsoft Windows, el sistema de archivos de Windows, Active Directory y la variable y los datos de alias almacenados por Windows PowerShell.

Para el desarrollador, el proveedor de Windows PowerShell es la interfaz entre el usuario y los datos a los que el usuario necesita acceder. Desde esta perspectiva, cada tipo de proveedor descrito en esta sección admite un conjunto de interfaces y clases base específicas que permiten al tiempo de ejecución de Windows PowerShell exponer determinados cmdlets al usuario de una manera común.

## <a name="providers-provided-by-windows-powershell"></a>Proveedores proporcionados por Windows PowerShell

Windows PowerShell proporciona varios proveedores (como el proveedor FileSystem, el proveedor del registro y el proveedor de alias) que se usan para tener acceso a los almacenes de datos conocidos. Para obtener más información acerca de los proveedores proporcionados por Windows PowerShell, use el siguiente comando para obtener acceso a la ayuda en línea:

**PS > Get-Help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Obtener acceso a los datos almacenados mediante rutas de Windows PowerShell

Los proveedores de Windows PowerShell son accesibles para el tiempo de ejecución de Windows PowerShell y para los comandos mediante programación a través del uso de rutas de acceso de Windows PowerShell. La mayoría de las veces, estas rutas de acceso se usan para acceder directamente a los datos a través del proveedor. Sin embargo, algunas rutas de acceso pueden resolverse en rutas internas del proveedor que permiten a un cmdlet usar interfaces de programación de aplicaciones (API) que no sean de Windows PowerShell para acceder a los datos. Para obtener más información sobre cómo funcionan los proveedores de Windows PowerShell en Windows PowerShell, consulte funcionamiento de [Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Exponer cmdlets de proveedor mediante unidades de Windows PowerShell

Un proveedor de Windows PowerShell expone sus cmdlets compatibles mediante unidades de Windows PowerShell virtuales. Windows PowerShell aplica las siguientes reglas para una unidad de Windows PowerShell:

- El nombre de una unidad puede ser cualquier secuencia alfanumérica.

- Una unidad se puede especificar en cualquier punto válido de una ruta de acceso, denominada "raíz".

- Una unidad se puede implementar para cualquier dato almacenado, no solo para el sistema de archivos.

- Cada unidad mantiene su propia ubicación de trabajo actual, lo que permite al usuario conservar el contexto al cambiar de unidad.

## <a name="in-this-section"></a>En esta sección

En la tabla siguiente se enumeran los temas que incluyen ejemplos de código que se basan entre sí. A partir del segundo tema, el tiempo de ejecución de Windows PowerShell puede inicializar y no inicializar el proveedor básico de Windows PowerShell. en el tema siguiente se agrega funcionalidad para tener acceso a los datos. en el tema siguiente se agrega funcionalidad para manipular los datos ( los elementos de los datos almacenados), etc.

|Tema|Definición|
|-----------|----------------|
|[Diseño del proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)|En este tema se tratan los aspectos que debe tener en cuenta antes de implementar un proveedor de Windows PowerShell. Resume las clases y las interfaces base del proveedor de Windows PowerShell que se usan.|
|[Crear un proveedor básico de Windows PowerShell](./creating-a-basic-windows-powershell-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permita al tiempo de ejecución de Windows PowerShell inicializar y anular la inicialización del proveedor.|
|[Crear un proveedor de unidades de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite al usuario obtener acceso a un almacén de datos a través de una unidad de Windows PowerShell.|
|[Crear un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permita al usuario manipular los elementos de un almacén de datos.|
|[Crear un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permita al usuario trabajar en almacenes de datos multinivel.|
|[Crear un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permite al usuario navegar por los elementos de un almacén de datos de forma jerárquica.|
|[Crear un proveedor de contenido de Windows PowerShell](./creating-a-windows-powershell-content-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permita al usuario manipular el contenido de los elementos de un almacén de datos.|
|[Crear un proveedor de propiedades de Windows PowerShell](./creating-a-windows-powershell-property-provider.md)|En este tema se muestra cómo crear un proveedor de Windows PowerShell que permita al usuario manipular las propiedades de los elementos de un almacén de datos.|

## <a name="see-also"></a>Véase también

[Cómo funciona Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)
