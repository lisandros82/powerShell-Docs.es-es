---
title: Ejemplo de código AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859671"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="15199-102">Ejemplo de código AccessDbProviderSample01</span><span class="sxs-lookup"><span data-stu-id="15199-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="15199-103">El código siguiente muestra la implementación del proveedor de Windows PowerShell descrito en [creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="15199-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="15199-104">Esta implementación proporciona métodos para iniciar y detener el proveedor y, aunque no proporciona un medio para tener acceso a un almacén de datos o para obtener o establecer los datos en el almacén de datos, proporcionan la funcionalidad básica requerida por todos los proveedores.</span><span class="sxs-lookup"><span data-stu-id="15199-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="15199-105">Puede descargar el C# (AccessDBSampleProvider01.cs) de archivo de código fuente para este proveedor mediante el Kit del desarrollo de Software de Windows para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="15199-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="15199-106">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="15199-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="15199-107">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="15199-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="15199-108">Para obtener más información acerca de otras implementaciones del proveedor de Windows PowerShell, consulte [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="15199-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="15199-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="15199-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="15199-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="15199-110">See Also</span></span>

[<span data-ttu-id="15199-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15199-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="15199-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="15199-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)