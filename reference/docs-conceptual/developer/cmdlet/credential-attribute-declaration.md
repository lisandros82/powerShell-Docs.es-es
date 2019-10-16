---
title: Declaración de atributo de credencial | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369894"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="b9c3c-102">Declaración de atributo de credenciales</span><span class="sxs-lookup"><span data-stu-id="b9c3c-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="b9c3c-103">El atributo Credential es un atributo opcional que se puede usar con parámetros de credenciales de tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , de modo que también se pueda pasar una cadena como argumento al parámetro.</span><span class="sxs-lookup"><span data-stu-id="b9c3c-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="b9c3c-104">Cuando se agrega este atributo a una declaración de parámetro, Windows PowerShell convierte la entrada de cadena en un objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .</span><span class="sxs-lookup"><span data-stu-id="b9c3c-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="b9c3c-105">Por ejemplo, el cmdlet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) usa este atributo para que Windows PowerShell genere el objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) devuelto por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b9c3c-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9c3c-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b9c3c-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="b9c3c-107">Observaciones</span><span class="sxs-lookup"><span data-stu-id="b9c3c-107">Remarks</span></span>

- <span data-ttu-id="b9c3c-108">Normalmente, este atributo lo usan los parámetros de tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , de modo que también se puede pasar una cadena como argumento al parámetro.</span><span class="sxs-lookup"><span data-stu-id="b9c3c-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="b9c3c-109">Cuando se pasa un objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) al parámetro, Windows PowerShell no hace nada.</span><span class="sxs-lookup"><span data-stu-id="b9c3c-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="b9c3c-110">Al crear el objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , Windows PowerShell usa el host actual para mostrar las solicitudes correspondientes al usuario.</span><span class="sxs-lookup"><span data-stu-id="b9c3c-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="b9c3c-111">Por ejemplo, el host predeterminado muestra un mensaje para un nombre de usuario y una contraseña cuando se utiliza este atributo.</span><span class="sxs-lookup"><span data-stu-id="b9c3c-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="b9c3c-112">Sin embargo, si se usa un host personalizado que define un mensaje diferente, se mostrará dicho mensaje.</span><span class="sxs-lookup"><span data-stu-id="b9c3c-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="b9c3c-113">Este atributo se usa con el atributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="b9c3c-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="b9c3c-114">Para obtener más información sobre ese atributo, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="b9c3c-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="b9c3c-115">El atributo Credential se define mediante la clase [System. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .</span><span class="sxs-lookup"><span data-stu-id="b9c3c-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9c3c-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="b9c3c-116">See Also</span></span>

[<span data-ttu-id="b9c3c-117">Alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="b9c3c-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="b9c3c-118">Declaración de atributo de parámetro</span><span class="sxs-lookup"><span data-stu-id="b9c3c-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="b9c3c-119">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9c3c-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
