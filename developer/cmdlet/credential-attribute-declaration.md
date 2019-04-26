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
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068325"
---
# <a name="credential-attribute-declaration"></a>Declaración de atributo de credenciales

La credencial es un atributo opcional que puede utilizarse con los parámetros de la credencial de tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) para que una cadena también se puede pasar como argumento al parámetro. Cuando se agrega este atributo a una declaración de parámetro, Windows PowerShell convierte la entrada de cadena en un [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto. Por ejemplo, el [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet utiliza este atributo para que Windows PowerShell genere la [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto devuelto por el cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[Credential]
```

## <a name="remarks"></a>Observaciones

- Normalmente, este atributo se usa por los parámetros de tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) para que una cadena también se puede pasar como argumento al parámetro. Cuando un [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto se pasa al parámetro, Windows PowerShell no hace nada.

- Al crear el [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) objeto, Windows PowerShell usa el Host actual para mostrar los mensajes adecuados al usuario. Por ejemplo, el valor predeterminado Host muestra un símbolo del sistema para un nombre de usuario y una contraseña cuando se utiliza este atributo. Sin embargo, si se utiliza un host personalizado que define un símbolo del sistema diferente, a continuación, se mostrará ese mensaje.

- Este atributo se utiliza con el atributo de parámetro. Para obtener más información acerca de ese atributo, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).

- El atributo de credencial se define mediante el [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) clase.

## <a name="see-also"></a>Véase también

[Alias de parámetro](./parameter-aliases.md)

[Declaración de atributo de parámetro](./parameter-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
