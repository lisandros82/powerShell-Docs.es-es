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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417994"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="dfa49-102">Ejemplo de código AccessDbProviderSample01</span><span class="sxs-lookup"><span data-stu-id="dfa49-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="dfa49-103">En el código siguiente se muestra la implementación del proveedor de Windows PowerShell que se describe en [crear un proveedor básico de Windows PowerShell](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="dfa49-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="dfa49-104">Esta implementación proporciona métodos para iniciar y detener el proveedor y, aunque no proporciona un medio para tener acceso a un almacén de datos o para obtener o establecer los datos en el almacén de datos, proporciona la funcionalidad básica requerida por todos los proveedores.</span><span class="sxs-lookup"><span data-stu-id="dfa49-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="dfa49-105">Puede descargar el C# archivo de código fuente (AccessDBSampleProvider01.CS) para este proveedor mediante el kit de desarrollo de software de Windows para los componentes de tiempo de ejecución de Windows Vista y Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="dfa49-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="dfa49-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="dfa49-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="dfa49-107">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="dfa49-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="dfa49-108">Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="dfa49-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="dfa49-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="dfa49-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="dfa49-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="dfa49-110">See Also</span></span>

[<span data-ttu-id="dfa49-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dfa49-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="dfa49-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="dfa49-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
