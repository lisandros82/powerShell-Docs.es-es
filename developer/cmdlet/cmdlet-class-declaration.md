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
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055094"
---
# <a name="cmdlet-class-declaration"></a>Declaración de clase del cmdlet

Una clase de Microsoft .NET Framework se declara como un cmdlet especificando el **Cmdlet** atributo como metadatos de la clase. (El **Cmdlet** atributo es el único atributo obligatorio para todos los cmdlets). Al especificar el **Cmdlet** atributo, debe especificar el par de verbo y sustantivo que identifica el cmdlet para el usuario. Y debe describir la funcionalidad de Windows PowerShell que es compatible con el cmdlet. Para obtener más información sobre la sintaxis de declaración que se usa para especificar el **Cmdlet** atributo, vea [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> El **Cmdlet** atributo está definido por el [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) clase. Las propiedades de esta clase se corresponden a los parámetros de declaración que se usan cuando se declara el atributo.

## <a name="nouns"></a>Sustantivos

El nombre del cmdlet especifica los recursos en el que actúa el cmdlet. El término marca la diferencia de los cmdlets de otros cmdlets.

Deben ser sustantivos en los nombres de cmdlet específico y en el caso de los nombres genéricos, como *server*, es aconsejable agregar un prefijo corto que diferencia a los recursos de otros recursos similares. Por ejemplo, es un nombre de cmdlet que incluye un nombre con un prefijo `Get-SQLServer`. La combinación de un sustantivo específico con un verbo más general permite al usuario localizar rápidamente el cmdlet por su acción y, a continuación, identifique el cmdlet por sus recursos al evitar la duplicación de nombre de cmdlet innecesarios.

Para obtener una lista de caracteres especiales que no se puede usar en los nombres de cmdlet, consulte [las instrucciones de desarrollo necesario](./required-development-guidelines.md).

## <a name="verbs"></a>Verbos

Cuando se especifica un verbo, las directrices de desarrollo requieren que se use uno de los verbos predefinidos proporcionados por Windows PowerShell. Al usar uno de estos verbos predefinidos, garantizará la coherencia entre los cmdlets que escribe y los cmdlets que se escriben por Microsoft y otros usuarios. Por ejemplo, el verbo "Get" se usa para los cmdlets que recuperar datos.

Para obtener más información acerca de las instrucciones para los verbos, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md). Para obtener una lista de caracteres especiales que no se puede usar en los nombres de cmdlet, consulte [las instrucciones de desarrollo necesario](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Compatibilidad con la funcionalidad de Windows PowerShell

El **Cmdlet** atributo también permite especificar que el cmdlet admite parte de la funcionalidad común proporcionada por Windows PowerShell. Esto incluye compatibilidad para funciones comunes como la confirmación de comentarios del usuario (denominado compatibilidad con la característica ShouldProcess) y compatibilidad con transacciones. (La compatibilidad con las transacciones se introdujo en Windows PowerShell 2.0).

Para obtener más información sobre la sintaxis de declaración que se usa para especificar el **Cmdlet** atributo, vea [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definición de clase de cmdlet

El código siguiente es la definición para una clase de cmdlet GetProc. Tenga en cuenta que se utilizan mayúsculas y minúsculas de Pascal y que el nombre de la clase incluye el verbo y sustantivo del cmdlet.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Mayúsculas y minúsculas de Pascal

Cuando asigne nombre a los cmdlets, use casillas Pascal mayúsculas y minúsculas. Por ejemplo, el `Get-Item` y `Get-ItemProperty` cmdlets muestran la manera correcta de utilizar las mayúsculas y minúsculas al asignar nombres a los cmdlets.

## <a name="see-also"></a>Véase también

[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Declaración CmdletAttribute](./cmdlet-attribute-declaration.md)

[Nombres de verbo del cmdlet](./approved-verbs-for-windows-powershell-commands.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
