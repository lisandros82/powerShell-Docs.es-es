---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC para Linux nxSshAuthorizedKeys
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="335af-103">Recurso de DSC para Linux nxSshAuthorizedKeys</span><span class="sxs-lookup"><span data-stu-id="335af-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="335af-104">El recurso **nxAuthorizedKeys** de la configuración de estado de deseado (DSC) de PowerShell ofrece un mecanismo para administrar claves ssh autorizadas para un usuario especificado.</span><span class="sxs-lookup"><span data-stu-id="335af-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="335af-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="335af-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="335af-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="335af-106">Properties</span></span>

|  <span data-ttu-id="335af-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="335af-107">Property</span></span> |  <span data-ttu-id="335af-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="335af-108">Description</span></span> |
|---|---|
| <span data-ttu-id="335af-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="335af-109">KeyComment</span></span>| <span data-ttu-id="335af-110">Un comentario único para la clave.</span><span class="sxs-lookup"><span data-stu-id="335af-110">A unique comment for the key.</span></span> <span data-ttu-id="335af-111">Se utiliza para identificar las claves de forma única.</span><span class="sxs-lookup"><span data-stu-id="335af-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="335af-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="335af-112">Ensure</span></span>| <span data-ttu-id="335af-113">Especifica si la clave está definida.</span><span class="sxs-lookup"><span data-stu-id="335af-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="335af-114">Establezca esta propiedad en "Absent" para asegurarse de que la clave no exista en el archivo de claves autorizadas del usuario.</span><span class="sxs-lookup"><span data-stu-id="335af-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="335af-115">Establézcala en "Present" para asegurarse de que la clave esté definida en el archivo de claves autorizadas del usuario.</span><span class="sxs-lookup"><span data-stu-id="335af-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="335af-116">Nombre de usuario</span><span class="sxs-lookup"><span data-stu-id="335af-116">Username</span></span>| <span data-ttu-id="335af-117">El nombre de usuario para el que se administrarán las claves ssh autorizadas.</span><span class="sxs-lookup"><span data-stu-id="335af-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="335af-118">Si no se define, el usuario predeterminado es "root".</span><span class="sxs-lookup"><span data-stu-id="335af-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="335af-119">Clave</span><span class="sxs-lookup"><span data-stu-id="335af-119">Key</span></span>| <span data-ttu-id="335af-120">El contenido de la clave.</span><span class="sxs-lookup"><span data-stu-id="335af-120">The contents of the key.</span></span> <span data-ttu-id="335af-121">Esto es necesario si el valor de **Ensure** se establece en "Present".</span><span class="sxs-lookup"><span data-stu-id="335af-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="335af-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="335af-122">DependsOn</span></span> | <span data-ttu-id="335af-123">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="335af-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="335af-124">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="335af-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="335af-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="335af-125">Example</span></span>

<span data-ttu-id="335af-126">En el ejemplo siguiente se define una clave ssh autorizada pública para el usuario "monuser".</span><span class="sxs-lookup"><span data-stu-id="335af-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```