---
title: Declaración de clase de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363524"
---
# <a name="cmdlet-class-declaration"></a>Declaración de clase del cmdlet

Una clase de marco de Microsoft .NET se declara como un cmdlet especificando el atributo del **cmdlet** como metadatos para la clase. (El atributo **cmdlet** es el único atributo necesario para todos los cmdlets). Al especificar el atributo del **cmdlet** , debe especificar el par verbo-y-sustantivo que identifica el cmdlet para el usuario. Además, debe describir la funcionalidad de Windows PowerShell que admite el cmdlet. Para obtener más información sobre la sintaxis de declaración que se usa para especificar el atributo de **cmdlet** , vea [declaración de atributo de cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> El atributo **cmdlet** se define mediante la clase [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Las propiedades de esta clase corresponden a los parámetros de declaración que se utilizan al declarar el atributo.

## <a name="nouns"></a>Nombres

El nombre del cmdlet especifica los recursos en los que actúa el cmdlet. El nombre diferencia los cmdlets de otros cmdlets.

Los nombres de los nombres de cmdlet deben ser específicos y, en el caso de nombres genéricos, como *Server*, es mejor agregar un prefijo corto que diferencie el recurso de otros recursos similares. Por ejemplo, un nombre de cmdlet que incluye un sustantivo con un prefijo es `Get-SQLServer`. La combinación de un sustantivo específico con un verbo más general permite al usuario localizar rápidamente el cmdlet por su acción y, a continuación, identificar el cmdlet por su recurso y evitar la duplicación de nombres de cmdlets innecesarios.

Para obtener una lista de los caracteres especiales que no se pueden usar en los nombres de cmdlet, consulte las [directrices de desarrollo necesarias](./required-development-guidelines.md).

## <a name="verbs"></a>Verbos

Cuando se especifica un verbo, las instrucciones de desarrollo requieren el uso de uno de los verbos predefinidos proporcionados por Windows PowerShell. Al usar uno de estos verbos predefinidos, se garantiza la coherencia entre los cmdlets que se escriben y los cmdlets escritos por Microsoft y por otros usuarios. Por ejemplo, el verbo "Get" se usa para los cmdlets que recuperan datos.

Para obtener más información sobre las directrices para los verbos, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md). Para obtener una lista de los caracteres especiales que no se pueden usar en los nombres de cmdlet, consulte las [directrices de desarrollo necesarias](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Compatibilidad con la funcionalidad de Windows PowerShell

El atributo **cmdlet** también le permite especificar que el cmdlet admite parte de la funcionalidad común proporcionada por Windows PowerShell. Esto incluye compatibilidad con la funcionalidad común, como la confirmación de comentarios de usuario (denominada compatibilidad con la característica ShouldProcess) y la compatibilidad con transacciones. (La compatibilidad con transacciones se presentó en Windows PowerShell 2,0).

Para obtener más información sobre la sintaxis de declaración que se usa para especificar el atributo de **cmdlet** , vea [declaración de atributo de cmdlet](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definición de clase de cmdlet

El código siguiente es la definición de una clase de cmdlet de GetProc. Observe que se usa la grafía Pascal y que el nombre de la clase incluye el verbo y el nombre del cmdlet.

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Mayúsculas y minúsculas Pascal

Cuando asigne nombre a los cmdlets, utilice la grafía Pascal. Por ejemplo, los cmdlets `Get-Item` y `Get-ItemProperty` muestran la manera correcta de usar las mayúsculas y minúsculas al asignar nombres a los cmdlets.

## <a name="see-also"></a>Véase también

[System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Declaración de CmdletAttribute](./cmdlet-attribute-declaration.md)

[Nombres de verbo de cmdlet](./approved-verbs-for-windows-powershell-commands.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
