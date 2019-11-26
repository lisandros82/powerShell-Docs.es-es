---
title: Guía del programador&#39;de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: f8cbaf464345b8f2b693e72f3dbe781a47605b28
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417777"
---
# <a name="windows-powershell-programmer39s-guide"></a>Guía del programador&#39;de Windows PowerShell

Esta guía del programador está dirigida a los desarrolladores interesados en proporcionar un entorno de administración de línea de comandos para los administradores del sistema. Windows PowerShell proporciona una manera sencilla de crear comandos de administración que exponen objetos de .NET, a la vez que permite que Windows PowerShell realice la mayor parte del trabajo.

En el desarrollo de comandos tradicional, es necesario escribir un analizador de parámetros, un enlazador de parámetros, filtros y todas las demás funciones expuestas por cada comando. Windows PowerShell proporciona lo siguiente para facilitar la escritura de comandos:

- Un eficaz entorno de ejecución de Windows PowerShell (motor de ejecución) con su propio analizador y un mecanismo para enlazar automáticamente los parámetros de comando.

- Utilidades para dar formato y mostrar los resultados del comando mediante un intérprete de línea de comandos (CLI).

- Compatibilidad con altos niveles de funcionalidad (a través de proveedores de Windows PowerShell) que facilitan el acceso a los datos almacenados.

  Con un costo reducido, puede representar un objeto .NET mediante un comando enriquecido o un conjunto de comandos que le ofrecerán una experiencia de línea de comandos completa para el administrador.

  En la siguiente sección se tratan los conceptos y términos clave de Windows PowerShell. Familiarícese con estos conceptos y términos antes de empezar el desarrollo.

## <a name="about-windows-powershell"></a>Acerca de Windows PowerShell

Windows PowerShell define varios tipos de comandos que puede usar en el desarrollo. Estos comandos incluyen: funciones, filtros, scripts, alias y archivos ejecutables (aplicaciones). El tipo de comando principal descrito en esta guía es un sencillo comando pequeño denominado "cmdlet". Windows PowerShell proporciona un conjunto de cmdlets y admite totalmente la personalización de cmdlets para adaptarse a su entorno. El tiempo de ejecución de Windows PowerShell procesa todos los tipos de comandos de la misma forma que los cmdlets, mediante canalizaciones.

Además de los comandos, Windows PowerShell admite varios proveedores de Windows PowerShell personalizables que hacen que haya conjuntos específicos de cmdlets disponibles. El shell funciona dentro de la aplicación host proporcionada por Windows PowerShell (Windows PowerShell. exe), pero es igualmente accesible desde una aplicación host personalizada que se puede desarrollar para cumplir requisitos específicos. Para obtener más información, consulte [funcionamiento de Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-cmdlets"></a>Cmdlets de Windows PowerShell

Un cmdlet es un comando ligero que se usa en el entorno de Windows PowerShell. El tiempo de ejecución de Windows PowerShell invoca estos cmdlets en el contexto de los scripts de automatización que se proporcionan en la línea de comandos, y el tiempo de ejecución de Windows PowerShell también los invoca mediante programación a través de las API de Windows PowerShell.

Para obtener más información sobre los cmdlets, consulte [escribir un cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Proveedores de Windows PowerShell

En la realización de tareas administrativas, es posible que el usuario tenga que examinar los datos almacenados en un almacén de datos (por ejemplo, el sistema de archivos, el registro de Windows o un almacén de certificados). Para facilitar estas operaciones, Windows PowerShell define un módulo denominado proveedor de Windows PowerShell que se puede usar para tener acceso a un almacén de datos específico, como el registro de Windows. Cada proveedor admite un conjunto de cmdlets relacionados para proporcionar al usuario una vista simétrica de los datos del almacén.

Windows PowerShell proporciona varios proveedores predeterminados de Windows PowerShell. Por ejemplo, el proveedor del registro admite la navegación y la manipulación del registro de Windows. Las claves del registro se representan como elementos y los valores del registro se tratan como propiedades.

Si expone un almacén de datos al que el usuario necesitará acceder, es posible que tenga que escribir su propio proveedor de Windows PowerShell, tal como se describe en [creación de proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md). Para más información aboutWindows los proveedores de PowerShell, consulte [Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="host-application"></a>Aplicación host

Windows PowerShell incluye la aplicación host predeterminada PowerShell. exe, que es una aplicación de consola que interactúa con el usuario y hospeda el tiempo de ejecución de Windows PowerShell mediante una ventana de consola.

En raras ocasiones, tendrá que escribir su propia aplicación host para Windows PowerShell, aunque se admite la personalización. Un caso en el que podría necesitar su propia aplicación es cuando tiene un requisito para una interfaz de GUI que es más enriquecida que la interfaz proporcionada por la aplicación host predeterminada. También puede que desee una aplicación personalizada cuando esté basando su GUI en la línea de comandos. Para obtener más información, vea [Cómo crear una aplicación host de Windows PowerShell](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application).

### <a name="windows-powershell-runtime"></a>Tiempo de ejecución de Windows PowerShell

El tiempo de ejecución de Windows PowerShell es el motor de ejecución que implementa el procesamiento de comandos. Incluye las clases que proporcionan la interfaz entre la aplicación host y los comandos y proveedores de Windows PowerShell. El tiempo de ejecución de Windows PowerShell se implementa como un objeto de espacio de ejecución para la sesión actual de Windows PowerShell, que es el entorno operativo en el que se ejecutan el Shell y los comandos. Para obtener detalles operativos, consulte funcionamiento de [Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-language"></a>Lenguaje de Windows PowerShell

El lenguaje de Windows PowerShell proporciona funciones de scripting y mecanismos para invocar comandos. Para obtener información de scripting completa, vea la referencia del lenguaje de Windows PowerShell que se incluye con Windows PowerShell.

### <a name="extended-type-system-ets"></a>Sistema de tipos extendido (ETS)

Windows PowerShell proporciona acceso a una variedad de objetos diferentes, como objetos .NET y XML. Como consecuencia, para presentar una abstracción común para todos los tipos de objeto, el shell utiliza su sistema de tipos extendido (ETS). La mayoría de la funcionalidad de ETS es transparente para el usuario, pero el script o el desarrollador de .NET la usa para los siguientes fines:

- Ver un subconjunto de los miembros de objetos específicos. Windows PowerShell proporciona una vista "adaptada" de varios tipos de objetos específicos.

- Agregar miembros a objetos existentes.

- Acceso a objetos serializados.

- Escribir objetos personalizados.

  Con ETS, puede crear nuevos "tipos" flexibles que son compatibles con el lenguaje de Windows PowerShell. Si es un desarrollador de .NET, puede trabajar con objetos con la misma semántica que el lenguaje de Windows PowerShell que se aplica a los scripts, por ejemplo, para determinar si un objeto se evalúa como `true`.

  Para obtener más información sobre ETS y cómo Windows PowerShell usa los objetos, vea [conceptos de objetos de Windows PowerShell](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6).

## <a name="programming-for-windows-powershell"></a>Programación para Windows PowerShell

Windows PowerShell define su código para los comandos, proveedores y otros módulos de programa mediante el .NET Framework. No está limitado al uso de Microsoft Visual Studio en la creación de módulos personalizados para Windows PowerShell, aunque se sabe que los ejemplos proporcionados en esta guía se ejecutan en esta herramienta. Puede usar cualquier lenguaje .NET que admita la herencia de clases y el uso de atributos. En algunos casos, las API de Windows PowerShell requieren que el lenguaje de programación pueda acceder a los tipos genéricos.

## <a name="programmers-reference"></a>Referencia del programador

Como referencia al desarrollar para Windows PowerShell, vea el [SDK de Windows PowerShell](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Introducción con Windows PowerShell

Para obtener más información sobre cómo empezar a usar el shell de Windows PowerShell, consulte la [Introducción con](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Windows PowerShell incluido con Windows PowerShell. También se proporciona un documento de triple doblado de referencia rápida como un manual para el uso de cmdlets.

## <a name="contents-of-this-guide"></a>Contenido de esta guía

|Tema|Definición|
|-----------|----------------|
|[Cómo crear un proveedor de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)|En esta sección se describe cómo crear un proveedor de Windows PowerShell para Windows PowerShell.|
|[Cómo crear una aplicación host de Windows PowerShell](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application)|En esta sección se describe cómo escribir una aplicación host que manipula un espacio de ejecución y cómo escribir una aplicación host que implementa su propio host personalizado.|
|[Cómo crear un complemento de Windows PowerShell](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|En esta sección se describe cómo crear un complemento que se usa para registrar todos los cmdlets y proveedores en un ensamblado y cómo crear un complemento personalizado.|
|[Cómo crear un shell de consola](./how-to-create-a-console-shell.md)|En esta sección se describe cómo crear un shell de consola que no es extensible.|
|[Conceptos de Windows PowerShell](./windows-powershell-concepts.md)|Esta sección contiene información conceptual que le ayudará a entender Windows PowerShell desde el punto de vista de un desarrollador.|

## <a name="see-also"></a>Vea también

[Windows PowerShell SDK](../windows-powershell-reference.md)
