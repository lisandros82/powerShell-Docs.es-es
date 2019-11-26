---
title: Código de ejemplo de AccessDbProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 33cdebd7f2f5ae21ec7aff559382362025d12e47
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416252"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="d272e-102">Ejemplo de código AccessDbProviderSample02</span><span class="sxs-lookup"><span data-stu-id="d272e-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="d272e-103">En el código siguiente se muestra la implementación del proveedor de Windows PowerShell que se describe en [crear un proveedor de unidades de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d272e-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="d272e-104">Esta implementación crea una ruta de acceso, establece una conexión con una base de datos de Access y, a continuación, quita la unidad.</span><span class="sxs-lookup"><span data-stu-id="d272e-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="d272e-105">Puede descargar el C# archivo de código fuente (AccessDBSampleProvider02.CS) para este proveedor mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="d272e-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d272e-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="d272e-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="d272e-107">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="d272e-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="d272e-108">Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d272e-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="d272e-109">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="d272e-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="d272e-110">Vea también</span><span class="sxs-lookup"><span data-stu-id="d272e-110">See Also</span></span>

[<span data-ttu-id="d272e-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d272e-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d272e-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d272e-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
