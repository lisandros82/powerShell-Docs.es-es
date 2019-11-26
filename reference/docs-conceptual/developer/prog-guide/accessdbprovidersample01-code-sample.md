---
title: Código de ejemplo de AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 22cfbc63bd369ebcb2fd8a0d0e8d1995941bbb0f
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417994"
---
# <a name="accessdbprovidersample01-code-sample"></a>Ejemplo de código AccessDbProviderSample01

En el código siguiente se muestra la implementación del proveedor de Windows PowerShell que se describe en [crear un proveedor básico de Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). Esta implementación proporciona métodos para iniciar y detener el proveedor y, aunque no proporciona un medio para tener acceso a un almacén de datos o para obtener o establecer los datos en el almacén de datos, proporciona la funcionalidad básica requerida por todos los proveedores.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (AccessDBSampleProvider01.CS) para este proveedor mediante el kit de desarrollo de software de Windows para los componentes de tiempo de ejecución de Windows Vista y Microsoft .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .
>
> Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Vea también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
