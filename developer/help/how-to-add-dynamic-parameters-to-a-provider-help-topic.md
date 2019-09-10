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
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848117"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="f1769-102">Cómo agregar parámetros dinámicos a un tema de Ayuda de proveedor</span><span class="sxs-lookup"><span data-stu-id="f1769-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="f1769-103">En esta sección se explica cómo rellenar la sección de **parámetros dinámicos** de un tema de ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="f1769-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="f1769-104">*Los parámetros dinámicos* son parámetros de un cmdlet o una función que solo están disponibles en las condiciones especificadas.</span><span class="sxs-lookup"><span data-stu-id="f1769-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="f1769-105">Los parámetros dinámicos que se documentan en un tema de ayuda del proveedor son los parámetros dinámicos que el proveedor agrega al cmdlet o la función cuando el cmdlet o la función se usa en la unidad del proveedor.</span><span class="sxs-lookup"><span data-stu-id="f1769-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="f1769-106">Los parámetros dinámicos también se pueden documentar en la ayuda de cmdlet personalizada para un proveedor.</span><span class="sxs-lookup"><span data-stu-id="f1769-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="f1769-107">Al escribir la ayuda de proveedor y la ayuda de cmdlet personalizada para un proveedor, incluya la documentación de parámetros dinámicos en ambos documentos.</span><span class="sxs-lookup"><span data-stu-id="f1769-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="f1769-108">Si un proveedor no implementa ningún parámetro dinámico, el tema de ayuda del proveedor contiene un `DynamicParameters` elemento vacío.</span><span class="sxs-lookup"><span data-stu-id="f1769-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="f1769-109">Para agregar parámetros dinámicos</span><span class="sxs-lookup"><span data-stu-id="f1769-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="f1769-110">En el archivo *AssemblyName*. dll-help. XML, dentro del `providerHelp` elemento, agregue un `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="f1769-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="f1769-111">El `DynamicParameters` elemento debe aparecer después del `Tasks` elemento y antes del `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="f1769-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="f1769-112">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f1769-112">For example:</span></span>

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

   <span data-ttu-id="f1769-113">Si el proveedor no implementa ningún parámetro dinámico, el `DynamicParameters` elemento puede estar vacío.</span><span class="sxs-lookup"><span data-stu-id="f1769-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="f1769-114">En el `DynamicParameters` elemento, agregue un `DynamicParameter` elemento para cada parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="f1769-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="f1769-115">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f1769-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="f1769-116">En cada `DynamicParameter` elemento, agregue un `Name` elemento `CmdletSupported` y.</span><span class="sxs-lookup"><span data-stu-id="f1769-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="f1769-117">Nombre del elemento</span><span class="sxs-lookup"><span data-stu-id="f1769-117">Element Name</span></span>|<span data-ttu-id="f1769-118">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="f1769-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="f1769-119">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="f1769-119">Name</span></span>|<span data-ttu-id="f1769-120">Especifica el nombre del parámetro.</span><span class="sxs-lookup"><span data-stu-id="f1769-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="f1769-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="f1769-121">CmdletSupported</span></span>|<span data-ttu-id="f1769-122">Especifica los cmdlets en los que el parámetro es válido.</span><span class="sxs-lookup"><span data-stu-id="f1769-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="f1769-123">Escriba una lista separada por comas de nombres de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f1769-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="f1769-124">Por ejemplo, el siguiente XML documenta el `Encoding` parámetro dinámico que el proveedor filesystem de Windows PowerShell agrega a `Add-Content`los `Get-Content`cmdlets,, `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="f1769-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="f1769-125">En cada `DynamicParameter` elemento, agregue un `Type` elemento.</span><span class="sxs-lookup"><span data-stu-id="f1769-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="f1769-126">El `Type` elemento es un contenedor para el `Name` elemento que contiene el tipo .net del valor del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="f1769-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="f1769-127">Por ejemplo, el código XML siguiente muestra que el tipo .net del `Encoding` parámetro dinámico es la enumeración [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="f1769-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="f1769-128">Agregue el `Description` elemento, que contiene una breve descripción del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="f1769-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="f1769-129">Al redactar la descripción, siga las directrices prescritas para todos los parámetros de cmdlet en [Cómo agregar información de parámetros](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="f1769-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="f1769-130">Por ejemplo, el código XML siguiente incluye la descripción del `Encoding` parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="f1769-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="f1769-131">Agregue el `PossibleValues` elemento y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="f1769-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="f1769-132">Juntos, estos elementos describen los valores del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="f1769-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="f1769-133">Este elemento está diseñado para los valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="f1769-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="f1769-134">Si el parámetro dinámico no toma un valor, como es el caso de un parámetro de modificador o los valores no se pueden enumerar, agregue un elemento `PossibleValues` vacío.</span><span class="sxs-lookup"><span data-stu-id="f1769-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="f1769-135">En la tabla siguiente se enumeran `PossibleValues` y describen el elemento y sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="f1769-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="f1769-136">Nombre del elemento</span><span class="sxs-lookup"><span data-stu-id="f1769-136">Element Name</span></span>|<span data-ttu-id="f1769-137">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="f1769-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="f1769-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="f1769-138">PossibleValues</span></span>|<span data-ttu-id="f1769-139">Este elemento es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="f1769-139">This element is a container.</span></span> <span data-ttu-id="f1769-140">A continuación se describen sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="f1769-140">Its child elements are described below.</span></span> <span data-ttu-id="f1769-141">Agregue un `PossibleValues` elemento a cada tema de ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="f1769-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="f1769-142">El elemento puede estar vacío.</span><span class="sxs-lookup"><span data-stu-id="f1769-142">The element can be empty.</span></span>|
   |<span data-ttu-id="f1769-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="f1769-143">PossibleValue</span></span>|<span data-ttu-id="f1769-144">Este elemento es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="f1769-144">This element is a container.</span></span> <span data-ttu-id="f1769-145">A continuación se describen sus elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="f1769-145">Its child elements are described below.</span></span> <span data-ttu-id="f1769-146">Agregue un `PossibleValue` elemento para cada valor del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="f1769-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="f1769-147">Value</span><span class="sxs-lookup"><span data-stu-id="f1769-147">Value</span></span>|<span data-ttu-id="f1769-148">Especifica el nombre del valor.</span><span class="sxs-lookup"><span data-stu-id="f1769-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="f1769-149">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="f1769-149">Description</span></span>|<span data-ttu-id="f1769-150">Este elemento contiene un `Para` elemento.</span><span class="sxs-lookup"><span data-stu-id="f1769-150">This element contains a `Para` element.</span></span> <span data-ttu-id="f1769-151">El texto `Para` del elemento describe el valor que se denomina en el `Value` elemento.</span><span class="sxs-lookup"><span data-stu-id="f1769-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="f1769-152">Por ejemplo, el siguiente código XML muestra `PossibleValue` un elemento `Encoding` del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="f1769-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="f1769-153">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f1769-153">Example</span></span>

<span data-ttu-id="f1769-154">En el ejemplo siguiente se `DynamicParameters` muestra el elemento `Encoding` del parámetro dinámico.</span><span class="sxs-lookup"><span data-stu-id="f1769-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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