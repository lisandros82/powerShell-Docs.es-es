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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="8c254-102">Cómo agregar parámetros dinámicos a un tema de Ayuda de proveedor</span><span class="sxs-lookup"><span data-stu-id="8c254-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="8c254-103">En esta sección se explica cómo rellenar la sección de **parámetros dinámicos** de un tema de ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="8c254-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="8c254-104">*Los parámetros dinámicos* son parámetros de un cmdlet o una función que solo están disponibles en las condiciones especificadas.</span><span class="sxs-lookup"><span data-stu-id="8c254-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="8c254-105">Los parámetros dinámicos que se documentan en un tema de ayuda del proveedor son los parámetros dinámicos que el proveedor agrega al cmdlet o la función cuando el cmdlet o la función se usa en la unidad del proveedor.</span><span class="sxs-lookup"><span data-stu-id="8c254-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="8c254-106">Los parámetros dinámicos también se pueden documentar en la ayuda de cmdlet personalizada para un proveedor.</span><span class="sxs-lookup"><span data-stu-id="8c254-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="8c254-107">Al escribir la ayuda de proveedor y la ayuda de cmdlet personalizada para un proveedor, incluya la documentación de parámetros dinámicos en ambos documentos.</span><span class="sxs-lookup"><span data-stu-id="8c254-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="8c254-108">Para obtener más información sobre la ayuda de cmdlet personalizada, consulte [Writing Windows PowerShell Custom cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="8c254-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="8c254-109">Si un proveedor no implementa ningún parámetro dinámico, el tema de ayuda del proveedor contiene un `DynamicParameters` elemento vacío.</span><span class="sxs-lookup"><span data-stu-id="8c254-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="8c254-110">Para agregar parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="8c254-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="8c254-111">En el archivo *AssemblyName*. dll-help. XML, dentro del `providerHelp` elemento, agregue un `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="8c254-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="8c254-112">El `DynamicParameters` elemento debe aparecer después del `Tasks` elemento y antes del `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="8c254-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="8c254-113">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8c254-113">For example:</span></span>

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

   <span data-ttu-id="8c254-114">Si el proveedor no implementa ningún parámetro dinámico, el `DynamicParameters` elemento puede estar vacío.</span><span class="sxs-lookup"><span data-stu-id="8c254-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="8c254-115">En el `DynamicParameters` elemento, agregue un `DynamicParameter` elemento para cada parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="8c254-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="8c254-116">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8c254-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="8c254-117">En cada `DynamicParameter` elemento, agregue un `Name` elemento `CmdletSupported` y.</span><span class="sxs-lookup"><span data-stu-id="8c254-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="8c254-118">Nombre del elemento</span><span class="sxs-lookup"><span data-stu-id="8c254-118">Element Name</span></span>|<span data-ttu-id="8c254-119">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="8c254-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="8c254-120">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="8c254-120">Name</span></span>|<span data-ttu-id="8c254-121">Especifica el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="8c254-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="8c254-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="8c254-122">CmdletSupported</span></span>|<span data-ttu-id="8c254-123">Especifica los cmdlets en los que el parámetro es válido.</span><span class="sxs-lookup"><span data-stu-id="8c254-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="8c254-124">Escriba una lista separada por comas de nombres de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c254-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="8c254-125">Por ejemplo, el siguiente XML documenta el `Encoding` parámetro dinámico que el proveedor filesystem de Windows PowerShell agrega a `Add-Content`los `Get-Content`cmdlets,, `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="8c254-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="8c254-126">En cada `DynamicParameter` elemento, agregue un `Type` elemento.</span><span class="sxs-lookup"><span data-stu-id="8c254-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="8c254-127">El `Type` elemento es un contenedor para el `Name` elemento que contiene el tipo .net del valor del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="8c254-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="8c254-128">Por ejemplo, el código XML siguiente muestra que el tipo .net del `Encoding` parámetro dinámico es la enumeración [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="8c254-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="8c254-129">Agregue el `Description` elemento, que contiene una breve descripción del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="8c254-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="8c254-130">Al redactar la descripción, siga las directrices prescritas para todos los parámetros de cmdlet en [Cómo agregar información de parámetros](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="8c254-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="8c254-131">Por ejemplo, el código XML siguiente incluye la descripción del `Encoding` parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="8c254-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="8c254-132">Agregue el `PossibleValues` elemento y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="8c254-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="8c254-133">Juntos, estos elementos describen los valores del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="8c254-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="8c254-134">Este elemento está diseñado para los valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="8c254-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="8c254-135">Si el parámetro dinámico no toma un valor, como es el caso de un parámetro de modificador o los valores no se pueden enumerar, agregue un elemento `PossibleValues` vacío.</span><span class="sxs-lookup"><span data-stu-id="8c254-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="8c254-136">En la tabla siguiente se enumeran `PossibleValues` y describen el elemento y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="8c254-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="8c254-137">Nombre del elemento</span><span class="sxs-lookup"><span data-stu-id="8c254-137">Element Name</span></span>|<span data-ttu-id="8c254-138">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="8c254-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="8c254-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="8c254-139">PossibleValues</span></span>|<span data-ttu-id="8c254-140">Este elemento es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="8c254-140">This element is a container.</span></span> <span data-ttu-id="8c254-141">A continuación se describen sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="8c254-141">Its child elements are described below.</span></span> <span data-ttu-id="8c254-142">Agregue un `PossibleValues` elemento a cada tema de ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="8c254-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="8c254-143">El elemento puede estar vacío.</span><span class="sxs-lookup"><span data-stu-id="8c254-143">The element can be empty.</span></span>|
   |<span data-ttu-id="8c254-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="8c254-144">PossibleValue</span></span>|<span data-ttu-id="8c254-145">Este elemento es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="8c254-145">This element is a container.</span></span> <span data-ttu-id="8c254-146">A continuación se describen sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="8c254-146">Its child elements are described below.</span></span> <span data-ttu-id="8c254-147">Agregue un `PossibleValue` elemento para cada valor del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="8c254-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="8c254-148">Valor</span><span class="sxs-lookup"><span data-stu-id="8c254-148">Value</span></span>|<span data-ttu-id="8c254-149">Especifica el nombre del valor.</span><span class="sxs-lookup"><span data-stu-id="8c254-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="8c254-150">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="8c254-150">Description</span></span>|<span data-ttu-id="8c254-151">Este elemento contiene un `Para` elemento.</span><span class="sxs-lookup"><span data-stu-id="8c254-151">This element contains a `Para` element.</span></span> <span data-ttu-id="8c254-152">El texto `Para` del elemento describe el valor que se denomina en el `Value` elemento.</span><span class="sxs-lookup"><span data-stu-id="8c254-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="8c254-153">Por ejemplo, el siguiente código XML muestra `PossibleValue` un elemento `Encoding` del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="8c254-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="8c254-154">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="8c254-154">Example</span></span>

<span data-ttu-id="8c254-155">En el ejemplo siguiente se `DynamicParameters` muestra el elemento `Encoding` del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="8c254-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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