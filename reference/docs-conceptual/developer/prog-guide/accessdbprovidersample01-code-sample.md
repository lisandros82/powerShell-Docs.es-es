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
ms.openlocfilehash: 429339a86b44bfa53302329fe1e21f6f91c52b42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360554"
---
# <a name="accessdbprovidersample01-code-sample"></a>Ejemplo de código AccessDbProviderSample01

En el código siguiente se muestra la implementación del proveedor de Windows PowerShell que se describe en [crear un proveedor básico de Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). Esta implementación proporciona métodos para iniciar y detener el proveedor y, aunque no proporciona un medio para tener acceso a un almacén de datos o para obtener o establecer los datos en el almacén de datos, proporciona la funcionalidad básica requerida por todos los proveedores.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (AccessDBSampleProvider01.CS) para este proveedor mediante el kit de desarrollo de software de Windows para los componentes de tiempo de ejecución de Windows Vista y Microsoft .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .
>
> Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
