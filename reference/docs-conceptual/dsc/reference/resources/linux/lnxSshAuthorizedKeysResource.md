---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC para Linux nxSshAuthorizedKeys
ms.openlocfilehash: 6e008efcbff2e679650d0bc3d5b8b573f6ef83e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953262"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a>Recurso de DSC para Linux nxSshAuthorizedKeys

El recurso **nxAuthorizedKeys** de la configuración de estado de deseado (DSC) de PowerShell ofrece un mecanismo para administrar claves ssh autorizadas para un usuario especificado.

## <a name="syntax"></a>Sintaxis

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|KeyComment |Un comentario único para la clave. Se utiliza para identificar las claves de forma única. |
|Nombre de usuario |El nombre de usuario para el que se administrarán las claves ssh autorizadas. Si no se define, el usuario predeterminado es **root**. |
|Clave |El contenido de la clave. Esto es necesario si el valor de **Ensure** se establece en **Present**.|

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Especifica si la clave está definida. Establezca esta propiedad en **Absent** para asegurarse de que la clave no exista en el archivo de claves autorizadas del usuario. Establézcala en **Present** para asegurarse de que la clave esté definida en el archivo de claves autorizadas del usuario. |

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se define una clave ssh autorizada pública para el usuario "monuser".

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```