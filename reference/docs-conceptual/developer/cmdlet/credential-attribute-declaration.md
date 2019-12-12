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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369894"
---
# <a name="credential-attribute-declaration"></a>Declaración de atributo de credenciales

El atributo Credential es un atributo opcional que se puede usar con parámetros de credenciales de tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , de modo que también se pueda pasar una cadena como argumento al parámetro. Cuando se agrega este atributo a una declaración de parámetro, Windows PowerShell convierte la entrada de cadena en un objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) . Por ejemplo, el cmdlet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) usa este atributo para que Windows PowerShell genere el objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) devuelto por el cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[Credential]
```

## <a name="remarks"></a>Observaciones

- Normalmente, este atributo lo usan los parámetros de tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , de modo que también se puede pasar una cadena como argumento al parámetro. Cuando se pasa un objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) al parámetro, Windows PowerShell no hace nada.

- Al crear el objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , Windows PowerShell usa el host actual para mostrar las solicitudes correspondientes al usuario. Por ejemplo, el host predeterminado muestra un mensaje para un nombre de usuario y una contraseña cuando se utiliza este atributo. Sin embargo, si se usa un host personalizado que define un mensaje diferente, se mostrará dicho mensaje.

- Este atributo se usa con el atributo Parameter. Para obtener más información sobre ese atributo, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).

- El atributo Credential se define mediante la clase [System. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .

## <a name="see-also"></a>Véase también

[Alias de parámetro](./parameter-aliases.md)

[Declaración de atributo de parámetro](./parameter-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
