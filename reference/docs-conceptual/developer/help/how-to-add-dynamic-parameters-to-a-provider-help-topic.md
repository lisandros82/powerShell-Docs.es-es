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
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361264"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Cómo agregar parámetros dinámicos a un tema de Ayuda de proveedor

En esta sección se explica cómo rellenar la sección de **parámetros dinámicos** de un tema de ayuda del proveedor.

*Los parámetros dinámicos* son parámetros de un cmdlet o una función que solo están disponibles en las condiciones especificadas.

Los parámetros dinámicos que se documentan en un tema de ayuda del proveedor son los parámetros dinámicos que el proveedor agrega al cmdlet o la función cuando el cmdlet o la función se usa en la unidad del proveedor.

Los parámetros dinámicos también se pueden documentar en la ayuda de cmdlet personalizada para un proveedor. Al escribir la ayuda de proveedor y la ayuda de cmdlet personalizada para un proveedor, incluya la documentación de parámetros dinámicos en ambos documentos.

Si un proveedor no implementa ningún parámetro dinámico, el tema de ayuda del proveedor contiene un elemento `DynamicParameters` vacío.

### <a name="to-add-dynamic-parameters"></a>Para agregar parámetros dinámicos

1. En el archivo *AssemblyName*. dll-help. XML, dentro del elemento `providerHelp`, agregue un elemento `DynamicParameters`. El elemento `DynamicParameters` debe aparecer después del elemento `Tasks` y antes del elemento `RelatedLinks`.

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

   Si el proveedor no implementa ningún parámetro dinámico, el elemento `DynamicParameters` puede estar vacío.

2. En el elemento `DynamicParameters`, para cada parámetro dinámico, agregue un elemento `DynamicParameter`.

   Por ejemplo:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. En cada elemento `DynamicParameter`, agregue un elemento `Name` y `CmdletSupported`.

   |Nombre del elemento|Descripción|
   |------------------|-----------------|
   |Name|Especifica el nombre del parámetro.|
   |CmdletSupported|Especifica los cmdlets en los que el parámetro es válido. Escriba una lista separada por comas de nombres de cmdlet.|

   Por ejemplo, el siguiente documento XML documenta el parámetro dinámico `Encoding` que el proveedor FileSystem de Windows PowerShell agrega a los cmdlets `Add-Content`, `Get-Content` y `Set-Content`.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. En cada elemento `DynamicParameter`, agregue un elemento `Type`. El elemento `Type` es un contenedor para el elemento `Name` que contiene el tipo .NET del valor del parámetro dinámico.

   Por ejemplo, el siguiente XML muestra que el tipo .NET del parámetro dinámico `Encoding` es la enumeración [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

5. Agregue el elemento `Description`, que contiene una breve descripción del parámetro dinámico. Al redactar la descripción, siga las directrices prescritas para todos los parámetros de cmdlet en [Cómo agregar información de parámetros](./how-to-add-parameter-information.md).

   Por ejemplo, el siguiente código XML incluye la descripción del parámetro dinámico `Encoding`.

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

6. Agregue el elemento `PossibleValues` y sus elementos secundarios. Juntos, estos elementos describen los valores del parámetro dinámico. Este elemento está diseñado para los valores enumerados. Si el parámetro dinámico no toma un valor, como es el caso de un parámetro de modificador o los valores no se pueden enumerar, agregue un elemento `PossibleValues` vacío.

   En la tabla siguiente se enumeran y describen el elemento `PossibleValues` y sus elementos secundarios.

   |Nombre del elemento|Descripción|
   |------------------|-----------------|
   |PossibleValues|Este elemento es un contenedor. A continuación se describen sus elementos secundarios. Agregue un elemento `PossibleValues` a cada tema de ayuda del proveedor. El elemento puede estar vacío.|
   |PossibleValue|Este elemento es un contenedor. A continuación se describen sus elementos secundarios. Agregue un elemento `PossibleValue` para cada valor del parámetro dinámico.|
   |Value|Especifica el nombre del valor.|
   |Descripción|Este elemento contiene un elemento `Para`. El texto del elemento `Para` describe el valor que se denomina en el elemento `Value`.|

   Por ejemplo, el siguiente código XML muestra un elemento `PossibleValue` del parámetro dinámico `Encoding`.

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

En el ejemplo siguiente se muestra el elemento `DynamicParameters` del parámetro dinámico `Encoding`.

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