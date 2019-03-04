---
title: Cómo agregar parámetros dinámicos a un tema de Ayuda de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859881"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Cómo agregar parámetros dinámicos a un tema de Ayuda de proveedor

Esta sección explica cómo rellenar el **parámetros dinámicos** sección de un tema de Ayuda del proveedor.

*Los parámetros dinámicos* son parámetros de un cmdlet o función que están disponibles solo en las condiciones especificadas.

Los parámetros dinámicos que se documentan en un tema de Ayuda del proveedor son los parámetros dinámicos que el proveedor se agrega a la función o cmdlet cuando se usa el cmdlet o función en la unidad del proveedor.

También se pueden documentar los parámetros dinámicos en la Ayuda de cmdlet personalizado para un proveedor. Al escribir la Ayuda del proveedor y ayuda de cmdlet personalizado para un proveedor, incluir la documentación del parámetro dinámico en ambos documentos. Para obtener más información acerca de la Ayuda de cmdlet personalizado, consulte [escritura Windows PowerShell Cmdlet ayuda personalizada para los proveedores](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Si un proveedor no implementa ningún parámetro dinámico, el tema de Ayuda de proveedor contiene un valor vacío `DynamicParameters` elemento.

### <a name="to-add-dynamic-parameters"></a>Para agregar los parámetros dinámicos

1. En el *AssemblyName*archivo .dll help.xml dentro la `providerHelp` elemento, agregue un `DynamicParameters` elemento. El `DynamicParameters` elemento debe aparecer después de la `Tasks` elemento y antes de la `RelatedLinks` elemento.

   Por ejemplo:

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   Si el proveedor no implementa ningún parámetro dinámico, el `DynamicParameters` elemento puede estar vacío.

2. Dentro de la `DynamicParameters` elemento para cada parámetro dinámico, agregue un `DynamicParameter` elemento.

   Por ejemplo:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. En cada `DynamicParameter` elemento, agregue un `Name` y `CmdletSupported` elemento.

   |Nombre del elemento|Descripción|
   |------------------|-----------------|
   |Nombre|Especifica el nombre del parámetro.|
   |CmdletSupported|Especifica los cmdlets en el que el parámetro es válido. Escriba una lista separada por comas de nombres de cmdlet.|

   Por ejemplo, los siguientes documentos XML la `Encoding` parámetro dinámico que el proveedor FileSystem de Windows PowerShell agrega a la `Add-Content`, `Get-Content`, `Set-Content` cmdlets.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. En cada `DynamicParameter` elemento, agregue un `Type` elemento. El `Type` elemento es un contenedor para el `Name` elemento que contiene el tipo .NET del valor del parámetro dinámico.

   Por ejemplo, el siguiente XML muestra que el tipo de .NET de la `Encoding` parámetro dinámico es el [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeración.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. Agregar el `Description` elemento, que contiene una breve descripción del parámetro dinámico. Al crear la descripción, use las directrices prescritas para todos los parámetros de cmdlet en [cómo agregar información de parámetro](./how-to-add-parameter-information.md).

   Por ejemplo, el siguiente código XML incluye la descripción de la `Encoding` parámetro dinámico.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. Agregar el `PossibleValues` elemento y sus elementos secundarios. Juntos, estos elementos describen los valores del parámetro dinámico. Este elemento está diseñado para los valores enumerados. Si el parámetro dinámico no tiene un valor, como es el caso de un parámetro de modificador, o no se pueden enumerar los valores, agregue un valor vacío `PossibleValues` elemento.

   En la tabla siguiente enumera y describe el `PossibleValues` elemento y sus elementos secundarios.

   |Nombre del elemento|Descripción|
   |------------------|-----------------|
   |PossibleValues|Este elemento es un contenedor. Sus elementos secundarios se describen a continuación. Agregue uno `PossibleValues` elemento para cada tema de Ayuda del proveedor. El elemento puede estar vacío.|
   |PossibleValue|Este elemento es un contenedor. Sus elementos secundarios se describen a continuación. Agregue uno `PossibleValue` (elemento) para cada valor del parámetro dinámico.|
   |Value|Especifica el nombre del valor.|
   |Descripción|Este elemento contiene un `Para` elemento. El texto en el `Para` elemento describe el valor que se menciona en la `Value` elemento.|

   Por ejemplo, el siguiente XML muestra una `PossibleValue` elemento de la `Encoding` parámetro dinámico.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra el `DynamicParameters` elemento de la `Encoding` parámetro dinámico.

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```