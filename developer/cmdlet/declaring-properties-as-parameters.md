---
title: Declarar propiedades como parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068273"
---
# <a name="declaring-properties-as-parameters"></a>Declaración de propiedades como parámetros

En este tema se proporciona información básica que debe comprender antes de declarar los parámetros de un cmdlet.

Para declarar los parámetros de un cmdlet dentro de la clase de cmdlet, definir las propiedades públicas que representan cada parámetro y, a continuación, agregue uno o varios atributos de parámetro para cada propiedad. El tiempo de ejecución de Windows PowerShell usa los atributos de parámetro para identificar la propiedad como un parámetro de cmdlet. La sintaxis básica para declarar el atributo de parámetro es `[Parameter()]`.

Este es un ejemplo de una propiedad definida como un parámetro necesario.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Estas son algunas cosas que recordar acerca de los parámetros.

- Un parámetro debe marcarse explícitamente como público. Parámetros que no están marcados como público predeterminado para interno y no se encontrará el tiempo de ejecución de Windows PowerShell.

- Los parámetros deben definirse como tipos de Microsoft .NET Framework para proporcionar una mejor validación de parámetros. Por ejemplo, los parámetros que están restringidos a un valor fuera de un conjunto de valores deben definirse como un tipo de enumeración. Parámetros que toman un valor de identificador uniforme de recursos (URI) deben ser del tipo [System.Uri](/dotnet/api/System.Uri).

- Evite los parámetros de cadena básicas de las propiedades de todos excepto texto sin formato.

- Puede agregar un parámetro a cualquier número de conjuntos de parámetros. Para obtener más información acerca de conjuntos de parámetros, vea [conjuntos de parámetros de Cmdlet](./cmdlet-parameter-sets.md).

Windows PowerShell también proporciona un conjunto de parámetros comunes que están disponibles para todos los cmdlets. Para obtener más información sobre estos parámetros y sus alias, vea [parámetros comunes de Cmdlet](./common-parameter-names.md).

## <a name="see-also"></a>Véase también

[Parámetros comunes de cmdlet](./common-parameter-names.md)

[Tipos de parámetro de Cmdlet](./types-of-cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
