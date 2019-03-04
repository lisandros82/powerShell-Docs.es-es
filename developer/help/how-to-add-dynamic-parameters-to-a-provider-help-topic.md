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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="b7f47-102">Cómo agregar parámetros dinámicos a un tema de Ayuda de proveedor</span><span class="sxs-lookup"><span data-stu-id="b7f47-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="b7f47-103">Esta sección explica cómo rellenar el **parámetros dinámicos** sección de un tema de Ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="b7f47-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="b7f47-104">*Los parámetros dinámicos* son parámetros de un cmdlet o función que están disponibles solo en las condiciones especificadas.</span><span class="sxs-lookup"><span data-stu-id="b7f47-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="b7f47-105">Los parámetros dinámicos que se documentan en un tema de Ayuda del proveedor son los parámetros dinámicos que el proveedor se agrega a la función o cmdlet cuando se usa el cmdlet o función en la unidad del proveedor.</span><span class="sxs-lookup"><span data-stu-id="b7f47-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="b7f47-106">También se pueden documentar los parámetros dinámicos en la Ayuda de cmdlet personalizado para un proveedor.</span><span class="sxs-lookup"><span data-stu-id="b7f47-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="b7f47-107">Al escribir la Ayuda del proveedor y ayuda de cmdlet personalizado para un proveedor, incluir la documentación del parámetro dinámico en ambos documentos.</span><span class="sxs-lookup"><span data-stu-id="b7f47-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="b7f47-108">Para obtener más información acerca de la Ayuda de cmdlet personalizado, consulte [escritura Windows PowerShell Cmdlet ayuda personalizada para los proveedores](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="b7f47-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="b7f47-109">Si un proveedor no implementa ningún parámetro dinámico, el tema de Ayuda de proveedor contiene un valor vacío `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="b7f47-110">Para agregar los parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="b7f47-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="b7f47-111">En el *AssemblyName*archivo .dll help.xml dentro la `providerHelp` elemento, agregue un `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="b7f47-112">El `DynamicParameters` elemento debe aparecer después de la `Tasks` elemento y antes de la `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="b7f47-113">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="b7f47-113">For example:</span></span>

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

   <span data-ttu-id="b7f47-114">Si el proveedor no implementa ningún parámetro dinámico, el `DynamicParameters` elemento puede estar vacío.</span><span class="sxs-lookup"><span data-stu-id="b7f47-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="b7f47-115">Dentro de la `DynamicParameters` elemento para cada parámetro dinámico, agregue un `DynamicParameter` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="b7f47-116">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="b7f47-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="b7f47-117">En cada `DynamicParameter` elemento, agregue un `Name` y `CmdletSupported` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="b7f47-118">Nombre del elemento</span><span class="sxs-lookup"><span data-stu-id="b7f47-118">Element Name</span></span>|<span data-ttu-id="b7f47-119">Descripción</span><span class="sxs-lookup"><span data-stu-id="b7f47-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="b7f47-120">Nombre</span><span class="sxs-lookup"><span data-stu-id="b7f47-120">Name</span></span>|<span data-ttu-id="b7f47-121">Especifica el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="b7f47-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="b7f47-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="b7f47-122">CmdletSupported</span></span>|<span data-ttu-id="b7f47-123">Especifica los cmdlets en el que el parámetro es válido.</span><span class="sxs-lookup"><span data-stu-id="b7f47-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="b7f47-124">Escriba una lista separada por comas de nombres de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b7f47-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="b7f47-125">Por ejemplo, los siguientes documentos XML la `Encoding` parámetro dinámico que el proveedor FileSystem de Windows PowerShell agrega a la `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b7f47-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="b7f47-126">En cada `DynamicParameter` elemento, agregue un `Type` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="b7f47-127">El `Type` elemento es un contenedor para el `Name` elemento que contiene el tipo .NET del valor del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="b7f47-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="b7f47-128">Por ejemplo, el siguiente XML muestra que el tipo de .NET de la `Encoding` parámetro dinámico es el [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeración.</span><span class="sxs-lookup"><span data-stu-id="b7f47-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="b7f47-129">Agregar el `Description` elemento, que contiene una breve descripción del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="b7f47-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="b7f47-130">Al crear la descripción, use las directrices prescritas para todos los parámetros de cmdlet en [cómo agregar información de parámetro](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="b7f47-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="b7f47-131">Por ejemplo, el siguiente código XML incluye la descripción de la `Encoding` parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="b7f47-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="b7f47-132">Agregar el `PossibleValues` elemento y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="b7f47-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="b7f47-133">Juntos, estos elementos describen los valores del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="b7f47-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="b7f47-134">Este elemento está diseñado para los valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="b7f47-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="b7f47-135">Si el parámetro dinámico no tiene un valor, como es el caso de un parámetro de modificador, o no se pueden enumerar los valores, agregue un valor vacío `PossibleValues` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="b7f47-136">En la tabla siguiente enumera y describe el `PossibleValues` elemento y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="b7f47-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="b7f47-137">Nombre del elemento</span><span class="sxs-lookup"><span data-stu-id="b7f47-137">Element Name</span></span>|<span data-ttu-id="b7f47-138">Descripción</span><span class="sxs-lookup"><span data-stu-id="b7f47-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="b7f47-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="b7f47-139">PossibleValues</span></span>|<span data-ttu-id="b7f47-140">Este elemento es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="b7f47-140">This element is a container.</span></span> <span data-ttu-id="b7f47-141">Sus elementos secundarios se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="b7f47-141">Its child elements are described below.</span></span> <span data-ttu-id="b7f47-142">Agregue uno `PossibleValues` elemento para cada tema de Ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="b7f47-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="b7f47-143">El elemento puede estar vacío.</span><span class="sxs-lookup"><span data-stu-id="b7f47-143">The element can be empty.</span></span>|
   |<span data-ttu-id="b7f47-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="b7f47-144">PossibleValue</span></span>|<span data-ttu-id="b7f47-145">Este elemento es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="b7f47-145">This element is a container.</span></span> <span data-ttu-id="b7f47-146">Sus elementos secundarios se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="b7f47-146">Its child elements are described below.</span></span> <span data-ttu-id="b7f47-147">Agregue uno `PossibleValue` (elemento) para cada valor del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="b7f47-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="b7f47-148">Value</span><span class="sxs-lookup"><span data-stu-id="b7f47-148">Value</span></span>|<span data-ttu-id="b7f47-149">Especifica el nombre del valor.</span><span class="sxs-lookup"><span data-stu-id="b7f47-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="b7f47-150">Descripción</span><span class="sxs-lookup"><span data-stu-id="b7f47-150">Description</span></span>|<span data-ttu-id="b7f47-151">Este elemento contiene un `Para` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-151">This element contains a `Para` element.</span></span> <span data-ttu-id="b7f47-152">El texto en el `Para` elemento describe el valor que se menciona en la `Value` elemento.</span><span class="sxs-lookup"><span data-stu-id="b7f47-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="b7f47-153">Por ejemplo, el siguiente XML muestra una `PossibleValue` elemento de la `Encoding` parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="b7f47-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="b7f47-154">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="b7f47-154">Example</span></span>

<span data-ttu-id="b7f47-155">El ejemplo siguiente se muestra el `DynamicParameters` elemento de la `Encoding` parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="b7f47-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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