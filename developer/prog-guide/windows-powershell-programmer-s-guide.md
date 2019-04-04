---
title: Programador de Windows PowerShell&#39;guía | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 75425fbd38141fc82dd834835912c357ecfa6d2b
ms.sourcegitcommit: 0ca836d1044e46d3a7dcbc69fa93d84f74848559
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920397"
---
# <a name="windows-powershell-programmer39s-guide"></a>Programador de Windows PowerShell&#39;guía

Esta guía del programador está dirigida a desarrolladores interesados en proporcionar un entorno de línea de comandos de administración para los administradores del sistema. Windows PowerShell proporciona una manera sencilla para crear comandos de administración que exponen los objetos. NET, permitiendo que Windows PowerShell realizar la mayoría del trabajo por usted.

En el desarrollo de comandos tradicionales, deberá escribir un analizador de parámetro, un enlazador de parámetros, filtros y todas la demás funcionalidades expuestas por cada comando. Windows PowerShell ofrece lo siguiente para que sea fácil de escribir los comandos:

- Una eficaz Windows PowerShell en tiempo de ejecución (motor de ejecución) con su propio analizador y un mecanismo para enlazar automáticamente parámetros de comando.

- Utilidades para dar formato y mostrar los resultados del comando con un intérprete de línea de comandos (CLI).

- Compatibilidad con altos niveles de funcionalidad (a través de proveedores de Windows PowerShell) que facilitan el acceso a los datos almacenados.

  Con un costo reducido, puede representar un objeto .NET mediante un comando enriquecido o un conjunto de comandos que ofrecerá una experiencia de línea de comandos completa para el administrador.

  La siguiente sección trata los conceptos clave de Windows PowerShell y los términos. Familiarícese con estos conceptos y términos antes de comenzar a desarrollar.

## <a name="about-windows-powershell"></a>Acerca de Windows PowerShell

Windows PowerShell define varios tipos de comandos que puede usar en el desarrollo. Estos comandos incluyen: funciones, filtros, las secuencias de comandos, alias y los archivos ejecutables (aplicaciones). El tipo de comando principal descrito en esta guía es un comando simple y pequeño denominado un "cmdlet". Windows PowerShell ofrece un conjunto de cmdlets y es totalmente compatible con la personalización de cmdlet para adaptarlo a su entorno. El tiempo de ejecución de Windows PowerShell procesa todos los tipos de comando, al igual que los cmdlets, uso de canalizaciones.

Además de los comandos, Windows PowerShell es compatible con distintos proveedores de Windows PowerShell personalizables que realizan disponibles conjuntos específicos de los cmdlets. El shell funciona dentro de la aplicación de host proporcionados por Windows PowerShell (PowerShell.exe Windows), pero es igualmente accesible desde una aplicación de host personalizado que puede desarrollar para satisfacer necesidades específicas. Para obtener más información, consulte [cómo Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-cmdlets"></a>Cmdlets de Windows PowerShell

Un cmdlet es un comando ligero que se usa en el entorno de Windows PowerShell. El tiempo de ejecución de Windows PowerShell invoca estos cmdlets en el contexto de scripts de automatización que se proporcionan en la línea de comandos, y el tiempo de ejecución de Windows PowerShell también invoca mediante programación por medio de Windows PowerShell APIs.

Para obtener más información acerca de los cmdlets, consulte [escribir un Cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Proveedores de Windows PowerShell

Para realizar tareas administrativas, puede que el usuario deberá examinar los datos almacenados en un almacén de datos (por ejemplo, el sistema de archivos, el registro de Windows o un almacén de certificados). Para facilitar estas operaciones, Windows PowerShell define un módulo llama a un proveedor de Windows PowerShell que puede utilizarse para tener acceso a un almacén de datos específico, como el registro de Windows. Cada proveedor admite un conjunto de cmdlets relacionados para proporcionar al usuario una vista simétrica de los datos en el almacén.

Windows PowerShell proporciona distintos proveedores de Windows PowerShell. Por ejemplo, el proveedor del registro es compatible con la navegación y manipulación del registro de Windows. Las claves del registro se representan como elementos y valores del registro se tratan como propiedades.

Si expone un almacén de datos que el usuario deberá acceder, es posible que deberá escribir su propio proveedor de Windows PowerShell, como se describe en [crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Para obtener más información aboutWindows proveedores de PowerShell, consulte [cómo Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="host-application"></a>Aplicación host

Windows PowerShell incluye el valor predeterminado host aplicación powershell.exe, que es una aplicación de consola que interactúa con el usuario y hospeda el tiempo de ejecución de Windows PowerShell con una ventana de consola.

Solo en raras ocasiones deberá escribir su propia aplicación de host de Windows PowerShell, aunque se admite la personalización. Un caso en que es posible que necesite su propia aplicación es cuando tiene un requisito para una interfaz gráfica de usuario que sea más rico que la interfaz proporcionada por la aplicación de host predeterminado. También puede una aplicación personalizada cuando base la interfaz gráfica de usuario en la línea de comandos. Para obtener más información, consulte [cómo crear una aplicación de Host de Windows PowerShell](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).

### <a name="windows-powershell-runtime"></a>Tiempo de ejecución de Windows PowerShell

El tiempo de ejecución de Windows PowerShell es el motor de ejecución que implementa el procesamiento de comandos. Incluye las clases que proporcionan la interfaz entre la aplicación host y los comandos de Windows PowerShell y los proveedores. El tiempo de ejecución de Windows PowerShell se implementa como un objeto de espacio de ejecución de la sesión actual de Windows PowerShell, que es el entorno operativo en el que se ejecutan comandos y el shell. Para obtener detalles operativos, consulte [cómo Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-language"></a>Lenguaje de Windows PowerShell

El lenguaje de Windows PowerShell proporciona mecanismos para invocar comandos y funciones de scripting. Para obtener información completa de secuencias de comandos, consulte que la referencia del lenguaje de Windows PowerShell incluidos con Windows PowerShell.

### <a name="extended-type-system-ets"></a>Sistema de tipo extendido (ETS)

Windows PowerShell proporciona acceso a una variedad de diferentes objetos, como .NET y objetos XML. Como consecuencia, para presentar una abstracción común para todos los tipos de objeto del shell utiliza su sistema de tipos extendido (ETS). Mayoría de las funciones ETS es transparente para el usuario, pero el script o el desarrollador de .NET se usa para los siguientes fines:

- Visualización de un subconjunto de los miembros de determinados objetos. Windows PowerShell proporciona una vista "adaptada" de los distintos tipos de objeto específico.

- Agregar miembros a los objetos existentes.

- Acceso a los objetos serializados.

- Escribir objetos personalizados.

  Con ETS, puede crear nuevos flexibles "tipos" que son compatibles con el lenguaje de Windows PowerShell. Si es desarrollador de. NET, es posible trabajar con objetos con la misma semántica que el lenguaje de Windows PowerShell se aplica a secuencias de comandos, por ejemplo, para determinar si un objeto se evalúa como `true`.

  Para obtener más información acerca de ETS y cómo Windows PowerShell usa los objetos, consulte [conceptos de objetos de Windows PowerShell](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).

## <a name="programming-for-windows-powershell"></a>Programación para Windows PowerShell

Windows PowerShell define su código para los comandos, proveedores y otros módulos de programa con .NET Framework. No se limitan el uso de Microsoft Visual Studio en la creación de módulos personalizados para Windows PowerShell, aunque los ejemplos proporcionados en esta guía son conocidos para ejecutar esta herramienta. Puede usar cualquier lenguaje .NET que admite la herencia de clases y el uso de atributos. En algunos casos, Windows PowerShell APIs requieren el lenguaje de programación para tener acceso a los tipos genéricos.

## <a name="programmers-reference"></a>Referencia del programador

Referencia al desarrollar para Windows PowerShell, vea el [SDK de Windows PowerShell](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Introducción al uso de Windows PowerShell

Para obtener más información acerca de cómo empezar a usar el shell de Windows PowerShell, consulte el [Introducción a Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) incluidos con Windows PowerShell. Un documento de referencia rápida tríptico también se proporciona instrucciones detalladas para su uso del cmdlet.

## <a name="contents-of-this-guide"></a>Contenido de esta guía

|Tema|Definición|
|-----------|----------------|
|[Cómo crear un proveedor de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)|En esta sección se describe cómo crear un proveedor de Windows PowerShell para Windows PowerShell.|
|[Cómo crear una aplicación de Host de PowerShell de Windows](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|En esta sección se describe cómo escribir una aplicación host que manipula un espacio de ejecución y cómo escribir una aplicación host que implementa su propio host personalizado.|
|[Cómo crear un complemento de Windows PowerShell](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|En esta sección se describe cómo crear un complemento que se usa para registrar todos los cmdlets y proveedores en un ensamblado y cómo crear un complemento personalizado.|
|[Cómo crear un shell de la consola](./how-to-create-a-console-shell.md)|En esta sección se describe cómo crear un shell de consola que no es extensible.|
|[Conceptos de Windows PowerShell](./windows-powershell-concepts.md)|Esta sección contiene información conceptual que le ayudará a entender Windows PowerShell desde el punto de vista de un desarrollador.|

## <a name="see-also"></a>Véase también

[SDK de Windows PowerShell](../windows-powershell-reference.md)
