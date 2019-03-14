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
ms.openlocfilehash: 1513d340cdadc5cb7622e791cc3c163ff39dfe1d
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795409"
---
# <a name="credential-attribute-declaration"></a>Declaración de atributo de credenciales

La credencial es un atributo opcional que puede utilizarse con los parámetros de la credencial de tipo [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que una cadena también se puede pasar como argumento al parámetro. Cuando se agrega este atributo a una declaración de parámetro, Windows PowerShell convierte la entrada de cadena en un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto. Por ejemplo, el [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet utiliza este atributo para que Windows PowerShell genere la [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto devuelto por el cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[Credential]
```

## <a name="remarks"></a>Observaciones

- Normalmente, este atributo se usa por los parámetros de tipo [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) para que una cadena también se puede pasar como argumento al parámetro. Cuando un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto se pasa al parámetro, Windows PowerShell no hace nada.

- Al crear el [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto, Windows PowerShell usa el Host actual para mostrar los mensajes adecuados al usuario. Por ejemplo, el valor predeterminado Host muestra un símbolo del sistema para un nombre de usuario y una contraseña cuando se utiliza este atributo. Sin embargo, si se utiliza un host personalizado que define un símbolo del sistema diferente, a continuación, se mostrará ese mensaje.

- Este atributo se utiliza con el atributo de parámetro. Para obtener más información acerca de ese atributo, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).

- El atributo de credencial se define mediante el [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) clase.

## <a name="see-also"></a>Véase también

[Alias de parámetro](./parameter-aliases.md)

[Declaración de atributo de parámetro](./parameter-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
