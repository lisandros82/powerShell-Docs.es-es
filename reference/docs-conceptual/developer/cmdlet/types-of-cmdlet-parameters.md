---
title: Tipos de parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369314"
---
# <a name="types-of-cmdlet-parameters"></a>Tipos de parámetros del cmdlet

En este tema se describen los diferentes tipos de parámetros que se pueden declarar en los cmdlets de. Los parámetros de cmdlet pueden ser posicionales, con nombre, obligatorios, opcionales o modificadores.

## <a name="positional-and-named-parameters"></a>Parámetros posicionales y con nombre

Todos los parámetros de cmdlet son parámetros con nombre o posicionales. Un parámetro con nombre requiere que escriba el nombre y el argumento del parámetro al llamar al cmdlet. Un parámetro posicional solo requiere que se escriban los argumentos en orden relativo. A continuación, el sistema asigna el primer argumento sin nombre al primer parámetro posicional. El sistema asigna el segundo argumento sin nombre al segundo parámetro sin nombre, y así sucesivamente. De forma predeterminada, todos los parámetros de cmdlet son parámetros con nombre.

Para definir un parámetro con nombre, omita la palabra clave `Position` en la declaración de atributo de **parámetro** , tal y como se muestra en la siguiente declaración de parámetro.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Para definir un parámetro posicional, agregue la palabra clave `Position` en la declaración de atributo de parámetro y, a continuación, especifique una posición. En el ejemplo siguiente, el parámetro `UserName` se declara como un parámetro posicional con la posición 0. Esto significa que el primer argumento de la llamada se enlazará automáticamente a este parámetro.

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
> Un buen diseño de cmdlet recomienda que los parámetros más usados se declaren como parámetros posicionales para que el usuario no tenga que escribir el nombre del parámetro cuando se ejecute el cmdlet.

Los parámetros con nombre y posicionales aceptan argumentos únicos o varios argumentos separados por comas. Solo se permiten varios argumentos si el parámetro acepta una colección como una matriz de cadenas. Puede mezclar parámetros posicionales y con nombre en el mismo cmdlet. En este caso, el sistema recupera primero los argumentos con nombre y, a continuación, intenta asignar los argumentos sin nombre restantes a los parámetros posicionales.

Los siguientes comandos muestran las distintas formas en las que puede especificar argumentos únicos y varios para los parámetros del cmdlet `Get-Command`. Observe que en los dos últimos ejemplos, no es necesario especificar **-Name** porque el parámetro `Name` se define como un parámetro posicional.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Parámetros obligatorios y opcionales

También puede definir parámetros de cmdlet como parámetros obligatorios u opcionales. (Debe especificarse un parámetro obligatorio antes de que el tiempo de ejecución de Windows PowerShell invoque el cmdlet).  De forma predeterminada, los parámetros se definen como opcionales.

Para definir un parámetro obligatorio, agregue la palabra clave `Mandatory` en la declaración de atributo de parámetro y establézcala en `true`, como se muestra en la siguiente declaración de parámetro.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Para definir un parámetro opcional, omita la palabra clave `Mandatory` en la declaración de atributo de **parámetro** , tal y como se muestra en la siguiente declaración de parámetro.

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

Windows PowerShell proporciona un tipo [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter) que permite definir un parámetro cuyo valor se establece automáticamente en `false` si no se especifica el parámetro cuando se llama al cmdlet. Siempre que sea posible, use parámetros de modificador en lugar de parámetros booleanos.

Considere el ejemplo siguiente. De forma predeterminada, varios cmdlets de Windows PowerShell no pasan un objeto de salida a la canalización. Sin embargo, estos cmdlets tienen un parámetro de modificador `PassThru` que invalida el comportamiento predeterminado. Si se especifica el parámetro `PassThru` cuando se llama a estos cmdlets, el cmdlet devuelve un objeto de salida a la canalización.

Si necesita que el parámetro tenga un valor predeterminado de `true` cuando no se especifica el parámetro en la llamada, considere la posibilidad de invertir el sentido del parámetro. Por ejemplo, en lugar de establecer el atributo Parameter en un valor booleano de `true`, declare la propiedad como el tipo [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter) y, a continuación, establezca el valor predeterminado del parámetro en `false`.

Para definir un parámetro de modificador, declare la propiedad como el tipo [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter) , como se muestra en el ejemplo siguiente.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Para hacer que el cmdlet actúe sobre el parámetro cuando se especifica, utilice la siguiente estructura dentro de uno de los métodos de procesamiento de entrada.

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
