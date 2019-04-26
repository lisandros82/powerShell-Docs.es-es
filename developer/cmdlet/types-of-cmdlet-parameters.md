---
title: Tipos de parámetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067202"
---
# <a name="types-of-cmdlet-parameters"></a>Tipos de parámetros del cmdlet

En este tema se describe los distintos tipos de parámetros que se pueden declarar en los cmdlets. Los parámetros de cmdlet pueden ser posicionales, con nombre, requerido, opcional o parámetros de modificador.

## <a name="positional-and-named-parameters"></a>Parámetros posicionales y con nombre

Todos los parámetros de cmdlet son parámetros con nombre o posicionales. Un parámetro con nombre se solicita que escriba el nombre del parámetro y el argumento al llamar al cmdlet. Un parámetro posicional sólo requiere que escriba los argumentos en orden relativo. El sistema, a continuación, asigna el primer argumento sin nombre para el primer parámetro posicional. El sistema asigna el segundo argumento sin nombre para el segundo parámetro sin nombre y así sucesivamente. De forma predeterminada, todos los parámetros de cmdlet son parámetros con nombre.

Para definir un parámetro con nombre, omita el `Position` palabra clave en el **parámetro** atributo de declaración, como se muestra en la siguiente declaración de parámetro.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Para definir un parámetro posicional, agregue el `Position` palabra clave en el parámetro de declaración de atributos y, a continuación, especifique una posición. En el ejemplo siguiente, la `UserName` parámetro se declara como un parámetro de posición por la posición 0. Esto significa que el primer argumento de la llamada se enlaza automáticamente a este parámetro.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Cmdlet de buen diseño, se recomienda que los parámetros más usados pueden declarar como parámetros de posición para que el usuario no tiene que escriba el nombre del parámetro cuando se ejecuta el cmdlet.

Parámetros posicionales y con nombre acepten argumentos únicos o varios argumentos separados por comas. Se permiten múltiples argumentos sólo si el parámetro acepta una colección como una matriz de cadenas. Puede mezclar parámetros posicionales y con nombre en el mismo cmdlet. En este caso, el sistema recupera los argumentos con nombre en primer lugar y, a continuación, intenta asignar el resto sin nombre argumentos para los parámetros posicionales.

Los comandos siguientes muestran las distintas formas en que puede especificar solo y varios argumentos para los parámetros de la `Get-Command` cmdlet. Tenga en cuenta que en las dos últimas muestras, **-nombre** no deben especificarse porque el `Name` parámetro se define como un parámetro posicional.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Parámetros obligatorios y opcionales

También puede definir parámetros de cmdlet como parámetros obligatorios u opcionales. (Se debe especificar un parámetro obligatorio antes de que el tiempo de ejecución de Windows PowerShell invoque el cmdlet.)  De forma predeterminada, los parámetros se definen como opcionales.

Para definir un parámetro obligatorio, agregue el `Mandatory` palabra clave en el parámetro de declaración de atributos y establézcalo en `true`, como se muestra en la siguiente declaración de parámetro.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Para definir un parámetro opcional, omita el `Mandatory` palabra clave en el **parámetro** atributo de declaración, como se muestra en la siguiente declaración de parámetro.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Parámetros de modificador

Windows PowerShell ofrece un [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) tipo que le permite definir un parámetro cuyo valor se establece automáticamente en `false` si no se especifica el parámetro cuando el cmdlet se llama. Siempre que sea posible, use los parámetros de modificador en lugar de los parámetros Boolean.

Considere el ejemplo siguiente. De forma predeterminada, varios cmdlets de Windows PowerShell no pase un objeto de salida por la canalización. Sin embargo, estos cmdlets tienen un `PassThru` modificador de parámetro que reemplaza el comportamiento predeterminado. Si el `PassThru` parámetro se especifica cuando se llama a estos cmdlets, el cmdlet devuelve un objeto de salida a la canalización.

Si necesita el parámetro tenga un valor predeterminado de `true` cuando el parámetro no se especifica en la llamada, considere la posibilidad de invertir el sentido del parámetro. Para obtener el ejemplo, en lugar de establecer el atributo de parámetro en un valor booleano de `true`, declare la propiedad como el [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) escriba y, a continuación, establezca el valor predeterminado del parámetro para `false`.

Para definir un parámetro de modificador, declare la propiedad como el [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) type, tal como se muestra en el ejemplo siguiente.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Para que el cmdlet actuar en el parámetro cuando se especifica, use la siguiente estructura dentro de uno de los métodos de procesamiento de entrada.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
