---
title: Código de ejemplo de AccessDbProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 7f75a3a3d2ab89696bb34ec2fdf7ba7a5ce0f9b1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416225"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="75b6e-102">Ejemplo de código AccessDbProviderSample06</span><span class="sxs-lookup"><span data-stu-id="75b6e-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="75b6e-103">En el código siguiente se muestra la implementación del proveedor de contenido de Windows PowerShell que se describe en [crear un proveedor de contenido de Windows PowerShell](./creating-a-windows-powershell-content-provider.md).</span><span class="sxs-lookup"><span data-stu-id="75b6e-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="75b6e-104">Este proveedor permite al usuario manipular el contenido de los elementos de un almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="75b6e-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="75b6e-105">Puede descargar el C# archivo de código fuente (AccessDBSampleProvider06.CS) para este proveedor mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="75b6e-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="75b6e-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="75b6e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="75b6e-107">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="75b6e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="75b6e-108">Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="75b6e-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="75b6e-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="75b6e-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="75b6e-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="75b6e-110">See Also</span></span>

[<span data-ttu-id="75b6e-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="75b6e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="75b6e-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="75b6e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
