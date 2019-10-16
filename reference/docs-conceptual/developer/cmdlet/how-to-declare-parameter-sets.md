---
title: Cómo declarar conjuntos de parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365614"
---
# <a name="how-to-declare-parameter-sets"></a>Cómo declarar los conjuntos de parámetros

En este ejemplo se muestra cómo definir dos conjuntos de parámetros al declarar los parámetros de un cmdlet. Cada conjunto de parámetros tiene un parámetro único y un parámetro compartido que usan ambos conjuntos de parámetros. Para obtener más información sobre los conjuntos de parámetros, incluido el modo de especificar el conjunto de parámetros predeterminado, consulte conjuntos de parámetros de [cmdlet](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Siempre que sea posible, defina el parámetro único de un conjunto de parámetros como parámetro necesario. Sin embargo, si desea que el cmdlet se ejecute sin especificar ningún parámetro, el parámetro único puede ser un parámetro opcional. Por ejemplo, el parámetro Unique del cmdlet `Get-Command` es opcional.

## <a name="how-to-define-two-parameter-sets"></a>Cómo definir dos conjuntos de parámetros

1. Agregue la palabra clave `ParameterSet` al atributo Parameter del parámetro Unique del primer conjunto de parámetros.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Agregue la palabra clave `ParameterSet` al atributo Parameter del parámetro Unique del segundo conjunto de parámetros.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Para el parámetro que pertenece a ambos conjuntos de parámetros, agregue un atributo de parámetro para cada conjunto de parámetros y, a continuación, agregue la palabra clave `ParameterSet` a cada conjunto. En cada atributo de parámetro, puede especificar cómo se define ese parámetro. Un parámetro puede ser opcional en un conjunto y obligatorio en otro.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Véase también

[Conjuntos de parámetros de cmdlet](./cmdlet-parameter-sets.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
