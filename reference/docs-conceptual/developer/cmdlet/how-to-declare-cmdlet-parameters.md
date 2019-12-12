---
title: Cómo declarar parámetros de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365684"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Cómo declarar los parámetros del cmdlet

En estos ejemplos se muestra cómo declarar parámetros con nombre, posicionales, obligatorios, opcionales y modificadores. En estos ejemplos también se muestra cómo definir un alias de parámetro.

## <a name="how-to-declare-a-named-parameter"></a>Cómo declarar un parámetro con nombre

- Defina una propiedad pública como se muestra en el código siguiente. Al agregar el atributo Parameter, omita la palabra clave `Position` del atributo.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obtener más información sobre el atributo Parameter, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Cómo declarar un parámetro posicional

- Defina una propiedad pública como se muestra en el código siguiente. Al agregar el atributo Parameter, establezca la palabra clave `Position` en la posición del argumento. Un valor de 0 indica la primera posición.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obtener más información sobre el atributo Parameter, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Cómo declarar un parámetro obligatorio

- Defina una propiedad pública como se muestra en el código siguiente. Al agregar el atributo Parameter, establezca la palabra clave `Mandatory` en `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Para obtener más información sobre el atributo Parameter, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Cómo declarar un parámetro opcional

- Defina una propiedad pública como se muestra en el código siguiente. Al agregar el atributo Parameter, omita la palabra clave `Mandatory`.

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

- Defina una propiedad pública como Type [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter)y, a continuación, declare el atributo Parameter.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Para obtener más información sobre el atributo Parameter, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Cómo declarar un parámetro con alias

- Defina una propiedad pública como se muestra en el código siguiente. Agregue un atributo de alias que Enumere los alias del parámetro. En este ejemplo, se definen tres alias para el mismo parámetro. El primer alias proporciona un acceso directo. El segundo y el tercer alias proporcionan nombres que se pueden utilizar para distintos escenarios.

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

Para obtener más información sobre el atributo alias, vea [alias Attribute declaration](./alias-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[System. Management. Automation. Parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter)

[Declaración de atributo de parámetro](./parameter-attribute-declaration.md)

[Declaración de atributo de alias](./alias-attribute-declaration.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
