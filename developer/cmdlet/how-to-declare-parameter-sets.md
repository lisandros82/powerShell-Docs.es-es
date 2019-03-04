---
title: Cómo declarar los conjuntos de parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859701"
---
# <a name="how-to-declare-parameter-sets"></a>Cómo declarar los conjuntos de parámetros

En este ejemplo se muestra cómo se definen dos conjuntos de parámetros al declarar los parámetros para un cmdlet. Cada conjunto de parámetros tiene un parámetro único y un parámetro compartido que está usando ambos conjuntos de parámetros. Para obtener más información acerca de los conjuntos de parámetros, incluida la forma de especificar el conjunto de parámetros predeterminados, consulte [conjuntos de parámetros de Cmdlet](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Siempre que sea posible, defina el parámetro unique de un parámetro establecido como un parámetro necesario. Sin embargo, si desea que el cmdlet se ejecuten sin especificar ningún parámetro, el único parámetro puede ser un parámetro opcional. Por ejemplo, el parámetro unique de la `Get-Command` cmdlet es opcional.

## <a name="how-to-define-two-parameter-sets"></a>Cómo se definen dos conjuntos de parámetros

1. Agregar el `ParameterSet` palabra clave para el atributo de parámetro para el parámetro único del primer conjunto de parámetros.

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

2. Agregar el `ParameterSet` palabra clave para el atributo de parámetro para el parámetro único del segundo conjunto de parámetros.

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

3. Para el parámetro al que pertenece a ambos conjuntos de parámetros, agregue un atributo de parámetro para cada conjunto de parámetros y, a continuación, agregue el `ParameterSet` palabra clave para cada conjunto. En cada atributo de parámetro, puede especificar cómo se define ese parámetro. Puede ser un parámetro opcional en un conjunto y obligatoria en otro.

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
