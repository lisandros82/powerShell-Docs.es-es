---
title: Cómo declarar los parámetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067930"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Cómo declarar los parámetros del cmdlet

Estos ejemplos muestran cómo se declara con nombre, posición, requerido, opcional y parámetros de modificador. Estos ejemplos también muestra cómo definir un alias de parámetro.

## <a name="how-to-declare-a-named-parameter"></a>Cómo declarar un parámetro con nombre

- Definir una propiedad pública como se muestra en el código siguiente. Al agregar el atributo Parameter, omita el `Position` palabra clave del atributo.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obtener más información sobre el atributo de parámetro, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Cómo declarar un parámetro posicional

- Definir una propiedad pública como se muestra en el código siguiente. Cuando agregue el atributo Parameter, establezca el `Position` palabra clave a la posición del argumento. Un valor de 0 indica que la primera posición.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obtener más información sobre el atributo de parámetro, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Cómo declarar un parámetro obligatorio

- Definir una propiedad pública como se muestra en el código siguiente. Cuando agregue el atributo Parameter, establezca el `Mandatory` palabra clave para `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obtener más información sobre el atributo de parámetro, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Cómo declarar un parámetro opcional

- Definir una propiedad pública como se muestra en el código siguiente. Al agregar el atributo Parameter, omita el `Mandatory` palabra clave.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Cómo declarar un parámetro de modificador

- Defina una propiedad pública como tipo [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)y, a continuación, declare el atributo de parámetro.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Para obtener más información sobre el atributo de parámetro, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Cómo declarar un parámetro con alias

- Definir una propiedad pública como se muestra en el código siguiente. Agregue un Alias (atributo) que se enumera los alias para el parámetro. En este ejemplo, se definen tres alias para el mismo parámetro. El primer alias proporciona un acceso directo. Los alias de la segundo y terceros proporcionan nombres que se puede usar para diferentes escenarios.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obtener más información sobre el atributo de Alias, vea [la declaración de atributo Alias](./alias-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Declaración de atributo de parámetro](./parameter-attribute-declaration.md)

[Declaración de atributo de alias](./alias-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
