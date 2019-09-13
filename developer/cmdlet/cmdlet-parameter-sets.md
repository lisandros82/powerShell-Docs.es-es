---
title: Conjuntos de parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936196"
---
# <a name="cmdlet-parameter-sets"></a>Conjuntos de parámetros de cmdlet

PowerShell usa conjuntos de parámetros para que pueda escribir un único cmdlet que puede realizar diferentes acciones en diferentes escenarios. Los conjuntos de parámetros permiten exponer diferentes parámetros al usuario. Y, para devolver información diferente en función de los parámetros especificados por el usuario.

## <a name="examples-of-parameter-sets"></a>Ejemplos de conjuntos de parámetros

Por ejemplo, el cmdlet `Get-EventLog` de PowerShell devuelve información diferente en función de si el usuario especifica el parámetro **List** o **logname** . Si se especifica el parámetro **List** , el cmdlet devuelve información sobre los propios archivos de registro, pero no la información de evento que contienen. Si se especifica el parámetro **logname** , el cmdlet devuelve información sobre los eventos de un registro de eventos específico. Los parámetros **List** y **logname** identifican dos conjuntos de parámetros independientes.

## <a name="unique-parameter"></a>Parámetro único

Cada conjunto de parámetros debe tener un parámetro único que el motor en tiempo de ejecución de PowerShell use para exponer el conjunto de parámetros adecuado. Si es posible, el parámetro único debe ser un parámetro obligatorio. Cuando un parámetro es obligatorio, el usuario debe especificar el parámetro y el tiempo de ejecución de PowerShell usa ese parámetro para identificar el conjunto de parámetros. El parámetro Unique no puede ser obligatorio si el cmdlet está diseñado para ejecutarse sin especificar ningún parámetro.

## <a name="multiple-parameter-sets"></a>Varios conjuntos de parámetros

En la ilustración siguiente, la columna izquierda muestra tres conjuntos de parámetros válidos. El **parámetro** a es único para el primer conjunto de parámetros, el **parámetro B** es único para el segundo conjunto de parámetros y el **parámetro C** es único para el tercer conjunto de parámetros. En la columna derecha, los conjuntos de parámetros no tienen un parámetro único.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Requisitos del conjunto de parámetros

Los siguientes requisitos se aplican a todos los conjuntos de parámetros.

- Cada conjunto de parámetros debe tener al menos un parámetro único. Si es posible, convierta este parámetro en un parámetro obligatorio.

- Un conjunto de parámetros que contiene varios parámetros posicionales debe definir posiciones únicas para cada parámetro. Dos parámetros posicionales no pueden especificar la misma posición.

- Solo un parámetro de un conjunto puede declarar la `ValueFromPipeline` palabra clave con un valor `true`de.
  Varios parámetros pueden definir la `ValueFromPipelineByPropertyName` palabra clave con un valor `true`de.

- Si no se especifica ningún conjunto de parámetros para un parámetro, el parámetro pertenece a todos los conjuntos de parámetros.

> [!NOTE]
> Para un cmdlet o una función, hay un límite de 32 conjuntos de parámetros.

## <a name="default-parameter-sets"></a>Conjuntos de parámetros predeterminados

Cuando se definen varios conjuntos de parámetros, puede usar la `DefaultParameterSetName` palabra clave del atributo **cmdlet** para especificar el conjunto de parámetros predeterminado. PowerShell usa el conjunto de parámetros predeterminado si no puede determinar el conjunto de parámetros que se va a usar según la información proporcionada por el comando. Para obtener más información sobre el atributo **cmdlet** , consulte [declaración de atributos de cmdlet](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Declarar conjuntos de parámetros

Para crear un conjunto de parámetros, debe especificar la `ParameterSetName` palabra clave al declarar el atributo de **parámetro** para cada parámetro del conjunto de parámetros. Para los parámetros que pertenecen a varios conjuntos de parámetros, agregue un atributo de **parámetro** para cada conjunto de parámetros. Este atributo permite definir el parámetro de forma diferente para cada conjunto de parámetros. Por ejemplo, puede definir un parámetro como obligatorio en un conjunto y opcional en otro. Sin embargo, cada conjunto de parámetros debe contener un parámetro único. Para obtener más información, vea [declaración de atributos de parámetros](parameter-attribute-declaration.md).

En el ejemplo siguiente, el parámetro de **nombre de usuario** es el parámetro `Test01` único del conjunto de parámetros y el parámetro **ComputerName** `Test02` es el parámetro único del conjunto de parámetros. El parámetro **SharedParam** pertenece a ambos conjuntos y es obligatorio para el `Test01` conjunto de parámetros, pero es `Test02` opcional para el conjunto de parámetros.

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
private string sharedParam;
```
