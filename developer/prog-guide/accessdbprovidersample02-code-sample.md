---
title: Ejemplo de código AccessDbProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795494"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="0f180-102">Ejemplo de código AccessDbProviderSample02</span><span class="sxs-lookup"><span data-stu-id="0f180-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="0f180-103">El código siguiente muestra la implementación del proveedor de Windows PowerShell descrito en [creación de un proveedor de la unidad de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="0f180-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="0f180-104">Esta implementación crea una ruta de acceso, realiza una conexión a una base de datos de Access y, a continuación, quita la unidad.</span><span class="sxs-lookup"><span data-stu-id="0f180-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="0f180-105">Puede descargar el C# (AccessDBSampleProvider02.cs) de archivo de código fuente para este proveedor mediante el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="0f180-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0f180-106">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="0f180-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0f180-107">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="0f180-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="0f180-108">Para obtener más información acerca de otras implementaciones del proveedor de Windows PowerShell, consulte [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="0f180-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="0f180-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="0f180-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="0f180-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="0f180-110">See Also</span></span>

[<span data-ttu-id="0f180-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f180-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0f180-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0f180-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)