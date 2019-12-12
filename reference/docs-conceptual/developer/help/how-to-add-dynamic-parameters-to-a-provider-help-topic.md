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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361264"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="391bf-102">Cómo agregar parámetros dinámicos a un tema de Ayuda de proveedor</span><span class="sxs-lookup"><span data-stu-id="391bf-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="391bf-103">En esta sección se explica cómo rellenar la sección de **parámetros dinámicos** de un tema de ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="391bf-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="391bf-104">*Los parámetros dinámicos* son parámetros de un cmdlet o una función que solo están disponibles en las condiciones especificadas.</span><span class="sxs-lookup"><span data-stu-id="391bf-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="391bf-105">Los parámetros dinámicos que se documentan en un tema de ayuda del proveedor son los parámetros dinámicos que el proveedor agrega al cmdlet o la función cuando el cmdlet o la función se usa en la unidad del proveedor.</span><span class="sxs-lookup"><span data-stu-id="391bf-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="391bf-106">Los parámetros dinámicos también se pueden documentar en la ayuda de cmdlet personalizada para un proveedor.</span><span class="sxs-lookup"><span data-stu-id="391bf-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="391bf-107">Al escribir la ayuda de proveedor y la ayuda de cmdlet personalizada para un proveedor, incluya la documentación de parámetros dinámicos en ambos documentos.</span><span class="sxs-lookup"><span data-stu-id="391bf-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="391bf-108">Si un proveedor no implementa ningún parámetro dinámico, el tema de ayuda del proveedor contiene un elemento de `DynamicParameters` vacío.</span><span class="sxs-lookup"><span data-stu-id="391bf-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="391bf-109">Para agregar parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="391bf-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="391bf-110">En el archivo *AssemblyName*. dll-help. XML, dentro del elemento `providerHelp`, agregue un elemento `DynamicParameters`.</span><span class="sxs-lookup"><span data-stu-id="391bf-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="391bf-111">El elemento `DynamicParameters` debe aparecer después del elemento `Tasks` y antes del elemento `RelatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="391bf-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="391bf-112">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="391bf-112">For example:</span></span>

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

   <span data-ttu-id="391bf-113">Si el proveedor no implementa ningún parámetro dinámico, el elemento `DynamicParameters` puede estar vacío.</span><span class="sxs-lookup"><span data-stu-id="391bf-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="391bf-114">En el elemento `DynamicParameters`, para cada parámetro dinámico, agregue un elemento `DynamicParameter`.</span><span class="sxs-lookup"><span data-stu-id="391bf-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="391bf-115">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="391bf-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="391bf-116">En cada `DynamicParameter` elemento, agregue un elemento `Name` y `CmdletSupported`.</span><span class="sxs-lookup"><span data-stu-id="391bf-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="391bf-117">Nombre del elemento</span><span class="sxs-lookup"><span data-stu-id="391bf-117">Element Name</span></span>|<span data-ttu-id="391bf-118">Descripción</span><span class="sxs-lookup"><span data-stu-id="391bf-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="391bf-119">Name</span><span class="sxs-lookup"><span data-stu-id="391bf-119">Name</span></span>|<span data-ttu-id="391bf-120">Especifica el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="391bf-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="391bf-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="391bf-121">CmdletSupported</span></span>|<span data-ttu-id="391bf-122">Especifica los cmdlets en los que el parámetro es válido.</span><span class="sxs-lookup"><span data-stu-id="391bf-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="391bf-123">Escriba una lista separada por comas de nombres de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="391bf-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="391bf-124">Por ejemplo, el siguiente documento XML documenta el `Encoding` parámetro dinámico que el proveedor FileSystem de Windows PowerShell agrega a los cmdlets `Add-Content`, `Get-Content``Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="391bf-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="391bf-125">En cada `DynamicParameter` elemento, agregue un elemento `Type`.</span><span class="sxs-lookup"><span data-stu-id="391bf-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="391bf-126">El elemento `Type` es un contenedor para el elemento `Name` que contiene el tipo .NET del valor del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="391bf-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="391bf-127">Por ejemplo, el siguiente XML muestra que el tipo .NET del parámetro dinámico `Encoding` es la enumeración [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="391bf-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="391bf-128">Agregue el elemento `Description`, que contiene una breve descripción del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="391bf-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="391bf-129">Al redactar la descripción, siga las directrices prescritas para todos los parámetros de cmdlet en [Cómo agregar información de parámetros](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="391bf-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="391bf-130">Por ejemplo, el código XML siguiente incluye la descripción de la `Encoding` parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="391bf-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="391bf-131">Agregue el elemento `PossibleValues` y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="391bf-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="391bf-132">Juntos, estos elementos describen los valores del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="391bf-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="391bf-133">Este elemento está diseñado para los valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="391bf-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="391bf-134">Si el parámetro dinámico no toma un valor, como es el caso de un parámetro de modificador o los valores no se pueden enumerar, agregue un elemento `PossibleValues` vacío.</span><span class="sxs-lookup"><span data-stu-id="391bf-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="391bf-135">En la tabla siguiente se enumeran y describen el elemento `PossibleValues` y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="391bf-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="391bf-136">Nombre del elemento</span><span class="sxs-lookup"><span data-stu-id="391bf-136">Element Name</span></span>|<span data-ttu-id="391bf-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="391bf-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="391bf-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="391bf-138">PossibleValues</span></span>|<span data-ttu-id="391bf-139">Este elemento es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="391bf-139">This element is a container.</span></span> <span data-ttu-id="391bf-140">A continuación se describen sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="391bf-140">Its child elements are described below.</span></span> <span data-ttu-id="391bf-141">Agregue un elemento `PossibleValues` a cada tema de ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="391bf-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="391bf-142">El elemento puede estar vacío.</span><span class="sxs-lookup"><span data-stu-id="391bf-142">The element can be empty.</span></span>|
   |<span data-ttu-id="391bf-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="391bf-143">PossibleValue</span></span>|<span data-ttu-id="391bf-144">Este elemento es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="391bf-144">This element is a container.</span></span> <span data-ttu-id="391bf-145">A continuación se describen sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="391bf-145">Its child elements are described below.</span></span> <span data-ttu-id="391bf-146">Agregue un elemento `PossibleValue` para cada valor del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="391bf-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="391bf-147">Value</span><span class="sxs-lookup"><span data-stu-id="391bf-147">Value</span></span>|<span data-ttu-id="391bf-148">Especifica el nombre del valor.</span><span class="sxs-lookup"><span data-stu-id="391bf-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="391bf-149">Descripción</span><span class="sxs-lookup"><span data-stu-id="391bf-149">Description</span></span>|<span data-ttu-id="391bf-150">Este elemento contiene un elemento `Para`.</span><span class="sxs-lookup"><span data-stu-id="391bf-150">This element contains a `Para` element.</span></span> <span data-ttu-id="391bf-151">El texto del elemento `Para` describe el valor que se denomina en el elemento `Value`.</span><span class="sxs-lookup"><span data-stu-id="391bf-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="391bf-152">Por ejemplo, el siguiente código XML muestra un elemento `PossibleValue` del parámetro dinámico `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="391bf-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="391bf-153">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="391bf-153">Example</span></span>

<span data-ttu-id="391bf-154">En el ejemplo siguiente se muestra el elemento `DynamicParameters` del parámetro dinámico `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="391bf-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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