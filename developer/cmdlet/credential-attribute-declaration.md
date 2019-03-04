---
title: Declaración de atributo de credenciales | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: abdd6e915b768b8ac688b6fc8c3194723961765e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863401"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="dca9c-102">Declaración de atributo de credenciales</span><span class="sxs-lookup"><span data-stu-id="dca9c-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="dca9c-103">La credencial es un atributo opcional que puede utilizarse con los parámetros de la credencial de tipo [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que una cadena también se puede pasar como argumento al parámetro.</span><span class="sxs-lookup"><span data-stu-id="dca9c-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="dca9c-104">Cuando se agrega este atributo a una declaración de parámetro, Windows PowerShell convierte la entrada de cadena en un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="dca9c-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="dca9c-105">Por ejemplo, el [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet utiliza este atributo para que Windows PowerShell genere la [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto devuelto por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dca9c-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>
<span data-ttu-id="dca9c-106">La credencial es un atributo opcional que puede utilizarse con los parámetros de la credencial de tipo [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que una cadena también se puede pasar como argumento al parámetro.</span><span class="sxs-lookup"><span data-stu-id="dca9c-106">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="dca9c-107">Cuando se agrega este atributo a una declaración de parámetro, Windows PowerShell convierte la entrada de cadena en un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.</span><span class="sxs-lookup"><span data-stu-id="dca9c-107">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="dca9c-108">Por ejemplo, el [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet utiliza este atributo para que Windows PowerShell genere la [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto devuelto por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dca9c-108">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="dca9c-109">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dca9c-109">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="dca9c-110">Observaciones</span><span class="sxs-lookup"><span data-stu-id="dca9c-110">Remarks</span></span>

- <span data-ttu-id="dca9c-111">Normalmente, este atributo se usa por los parámetros de tipo [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que una cadena también se puede pasar como argumento al parámetro.</span><span class="sxs-lookup"><span data-stu-id="dca9c-111">Typically this attribute is used by parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="dca9c-112">Cuando un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto se pasa al parámetro, Windows PowerShell no hace nada.</span><span class="sxs-lookup"><span data-stu-id="dca9c-112">When a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="dca9c-113">Al crear el [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto, Windows PowerShell usa el Host actual para mostrar los mensajes adecuados al usuario.</span><span class="sxs-lookup"><span data-stu-id="dca9c-113">When creating the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="dca9c-114">Por ejemplo, el valor predeterminado Host muestra un símbolo del sistema para un nombre de usuario y una contraseña cuando se utiliza este atributo.</span><span class="sxs-lookup"><span data-stu-id="dca9c-114">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="dca9c-115">Sin embargo, si se utiliza un host personalizado que define un símbolo del sistema diferente, a continuación, se mostrará ese mensaje.</span><span class="sxs-lookup"><span data-stu-id="dca9c-115">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="dca9c-116">Este atributo se utiliza con el atributo de parámetro.</span><span class="sxs-lookup"><span data-stu-id="dca9c-116">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="dca9c-117">Para obtener más información acerca de ese atributo, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="dca9c-117">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="dca9c-118">El atributo de credencial se define mediante el [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) clase.</span><span class="sxs-lookup"><span data-stu-id="dca9c-118">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="dca9c-119">Véase también</span><span class="sxs-lookup"><span data-stu-id="dca9c-119">See Also</span></span>

[<span data-ttu-id="dca9c-120">Alias de parámetro</span><span class="sxs-lookup"><span data-stu-id="dca9c-120">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="dca9c-121">Declaración de atributo de parámetro</span><span class="sxs-lookup"><span data-stu-id="dca9c-121">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="dca9c-122">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dca9c-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
