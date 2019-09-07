---
title: Cómo agregar parámetros dinámicos a un tema de ayuda del proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737600"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Cómo agregar parámetros dinámicos a un tema de Ayuda de proveedor

En esta sección se explica cómo rellenar la sección de **parámetros dinámicos** de un tema de ayuda del proveedor.

*Los parámetros dinámicos* son parámetros de un cmdlet o una función que solo están disponibles en las condiciones especificadas.

Los parámetros dinámicos que se documentan en un tema de ayuda del proveedor son los parámetros dinámicos que el proveedor agrega al cmdlet o la función cuando el cmdlet o la función se usa en la unidad del proveedor.

Los parámetros dinámicos también se pueden documentar en la ayuda de cmdlet personalizada para un proveedor. Al escribir la ayuda de proveedor y la ayuda de cmdlet personalizada para un proveedor, incluya la documentación de parámetros dinámicos en ambos documentos. Para obtener más información sobre la ayuda de cmdlet personalizada, consulte [Writing Windows PowerShell Custom cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Si un proveedor no implementa ningún parámetro dinámico, el tema de ayuda del proveedor contiene un `DynamicParameters` elemento vacío.

### <a name="to-add-dynamic-parameters"></a>Para agregar parámetros dinámicos

1. En el archivo *AssemblyName*. dll-help. XML, dentro del `providerHelp` elemento, agregue un `DynamicParameters` elemento. El `DynamicParameters` elemento debe aparecer después del `Tasks` elemento y antes del `RelatedLinks` elemento.

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

2. En el `DynamicParameters` elemento, agregue un `DynamicParameter` elemento para cada parámetro dinámico.

   Por ejemplo:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. En cada `DynamicParameter` elemento, agregue un `Name` elemento `CmdletSupported` y.

   |Nombre del elemento|DESCRIPCIÓN|
   |------------------|-----------------|
   |NOMBRE|Especifica el nombre del parámetro.|
   |CmdletSupported|Especifica los cmdlets en los que el parámetro es válido. Escriba una lista separada por comas de nombres de cmdlet.|

   Por ejemplo, el siguiente XML documenta el `Encoding` parámetro dinámico que el proveedor filesystem de Windows PowerShell agrega a `Add-Content`los `Get-Content`cmdlets,, `Set-Content` .

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. En cada `DynamicParameter` elemento, agregue un `Type` elemento. El `Type` elemento es un contenedor para el `Name` elemento que contiene el tipo .net del valor del parámetro dinámico.

   Por ejemplo, el código XML siguiente muestra que el tipo .net del `Encoding` parámetro dinámico es la enumeración [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

5. Agregue el `Description` elemento, que contiene una breve descripción del parámetro dinámico. Al redactar la descripción, siga las directrices prescritas para todos los parámetros de cmdlet en [Cómo agregar información de parámetros](./how-to-add-parameter-information.md).

   Por ejemplo, el código XML siguiente incluye la descripción del `Encoding` parámetro dinámico.

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

6. Agregue el `PossibleValues` elemento y sus elementos secundarios. Juntos, estos elementos describen los valores del parámetro dinámico. Este elemento está diseñado para los valores enumerados. Si el parámetro dinámico no toma un valor, como es el caso de un parámetro de modificador o los valores no se pueden enumerar, agregue un elemento `PossibleValues` vacío.

   En la tabla siguiente se enumeran `PossibleValues` y describen el elemento y sus elementos secundarios.

   |Nombre del elemento|DESCRIPCIÓN|
   |------------------|-----------------|
   |PossibleValues|Este elemento es un contenedor. A continuación se describen sus elementos secundarios. Agregue un `PossibleValues` elemento a cada tema de ayuda del proveedor. El elemento puede estar vacío.|
   |PossibleValue|Este elemento es un contenedor. A continuación se describen sus elementos secundarios. Agregue un `PossibleValue` elemento para cada valor del parámetro dinámico.|
   |Valor|Especifica el nombre del valor.|
   |DESCRIPCIÓN|Este elemento contiene un `Para` elemento. El texto `Para` del elemento describe el valor que se denomina en el `Value` elemento.|

   Por ejemplo, el siguiente código XML muestra `PossibleValue` un elemento `Encoding` del parámetro dinámico.

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

En el ejemplo siguiente se `DynamicParameters` muestra el elemento `Encoding` del parámetro dinámico.

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