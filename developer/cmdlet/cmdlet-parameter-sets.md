---
title: Establece el parámetro de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068519"
---
# <a name="cmdlet-parameter-sets"></a>Conjuntos de parámetros del cmdlet

Windows PowerShell usa conjuntos de parámetros para que pueda escribir un solo cmdlet que puede realizar acciones diferentes para distintos escenarios. Conjuntos de parámetros le permiten exponer diferentes parámetros para el usuario y para devolver información diferente en función de los parámetros especificados por el usuario.

## <a name="examples-of-parameter-sets"></a>Ejemplos de conjuntos de parámetros

Por ejemplo, el `Get-EventLog` cmdlet (proporcionado por Windows PowerShell) devuelve información diferente dependiendo de si el usuario especifica la `List` o `LogName` parámetro. Si el `List` parámetro se especifica, el cmdlet devuelve información acerca de los archivos de registro a sí mismos, pero no la información de evento que contienen. Si el `LogName` parámetro se especifica, el cmdlet devuelve información acerca de los eventos en un registro de eventos específico. El `List` y `LogName` parámetros identifican dos conjuntos de parámetros independiente.

## <a name="unique-parameter"></a>Parámetro único

Cada conjunto de parámetros debe tener un parámetro único que puede utilizar el tiempo de ejecución de Windows PowerShell para exponer el conjunto de parámetros apropiado. Si es posible, el único parámetro debe ser un parámetro obligatorio. Cuando un parámetro es obligatorio, se obliga al usuario especificar el parámetro y el tiempo de ejecución de Windows PowerShell puede usar ese parámetro para identificar el parámetro configurado para usar. El parámetro unique no puede ser obligatorio si el cmdlet está diseñado para ejecutarse sin especificar ningún parámetro.

## <a name="multiple-parameter-sets"></a>Varios conjuntos de parámetros

En la siguiente ilustración, la columna izquierda muestra tres conjuntos de parámetros válidos. Un parámetro es único para el primer conjunto de parámetros, parámetro B es único para el segundo conjunto de parámetros y parámetro C es único para el tercer conjunto de parámetros. Sin embargo, en la columna derecha, los conjuntos de parámetros no tienen un parámetro único.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Requisitos del conjunto de parámetros

Los siguientes requisitos se aplican a todos los conjuntos de parámetros.

- Cada conjunto de parámetros debe tener al menos un parámetro único. Asegúrese de este parámetro si es posible, un parámetro obligatorio.

- Un conjunto de parámetros que contiene varios parámetros posicionales debe definir posiciones únicas para cada parámetro. No hay dos parámetros posicionales pueden especificar la misma posición.

- Solo un parámetro en un conjunto se puede declarar el `ValueFromPipeline` palabra clave con un valor de `true`. Pueden definir varios parámetros la `ValueFromPipelineByPropertyName` palabra clave con un valor de `true`.

- Si no se especifica ningún conjunto de parámetros para un parámetro, el parámetro pertenece a todos los conjuntos de parámetros.

## <a name="default-parameter-sets"></a>Conjuntos de parámetros predeterminados

Cuando se definen varios conjuntos de parámetros, puede usar el `DefaultParameterSetName` palabra clave del atributo de Cmdlet para especificar el conjunto de parámetros de forma predeterminada. Windows PowerShell usa el parámetro predeterminado configurado si no se puede determinar el parámetro establecido en utilizar según la información proporcionada por el comando. Para obtener más información sobre el atributo de Cmdlet, consulte [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Declarar los conjuntos de parámetros

Para crear un conjunto de parámetros, debe especificar el `ParameterSetName` palabra clave cuando se declara el atributo de parámetro para cada parámetro en el conjunto de parámetros. Para los parámetros que pertenecen a varios conjuntos de parámetros, agregue un atributo de parámetro para cada conjunto de parámetros. Esto le permite definir el parámetro de forma diferente para cada conjunto de parámetros. Por ejemplo, puede definir un parámetro como obligatorio en un conjunto y opcional en otro. Sin embargo, cada conjunto de parámetros debe contener un parámetro único.

En el ejemplo siguiente, la `UserName` parámetro es el único parámetro del conjunto de parámetro Test01 y el `ComputerName` parámetro es el único parámetro del conjunto de parámetro Prueba02. El `SharedParam` parámetro pertenece a ambos conjuntos y es obligatorio para el parámetro Test01 establecer pero opcional para el conjunto de parámetros Prueba02.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```