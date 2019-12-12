---
title: Crear el archivo de esquema XML para un servicio Web Management OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359804"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="5df57-102">Creación del archivo de esquema XML para un servicio web de Management OData</span><span class="sxs-lookup"><span data-stu-id="5df57-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="5df57-103">Después de definir los recursos que el servicio Web expondrá (consulte [creación del archivo de esquema MOF para un servicio Web de Management OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), debe asignar esos recursos a los cmdlets de Windows PowerShell subyacentes que implementan las operaciones admitidas para cada recurso mediante la creación de un archivo XML que se ajusta al [esquema de asignación de recursos](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="5df57-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="5df57-104">El archivo XML también especifica las direcciones URL que usa el cliente para tener acceso a los recursos.</span><span class="sxs-lookup"><span data-stu-id="5df57-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="5df57-105">Mappng recursos a direcciones URL</span><span class="sxs-lookup"><span data-stu-id="5df57-105">Mappng resources to URLs</span></span>

<span data-ttu-id="5df57-106">La primera parte del archivo XML asigna los recursos definidos en el archivo de esquema MOF a las direcciones URL que se usan para obtener acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="5df57-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="5df57-107">En el ejemplo siguiente se muestra la asignación.</span><span class="sxs-lookup"><span data-stu-id="5df57-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="5df57-108">Asignación de cmdlets a operaciones CRUD</span><span class="sxs-lookup"><span data-stu-id="5df57-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="5df57-109">A continuación, especifique los cmdlets que corresponden a las operaciones CRUD (crear, leer, actualizar y eliminar) que admiten los recursos.</span><span class="sxs-lookup"><span data-stu-id="5df57-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="5df57-110">En el esquema de [asignación de recursos](./resource-mapping-schema.md)OData de administración, las operaciones CRUD se asignan de la siguiente manera.</span><span class="sxs-lookup"><span data-stu-id="5df57-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="5df57-111">CRUD (comando)</span><span class="sxs-lookup"><span data-stu-id="5df57-111">CRUD command</span></span>|<span data-ttu-id="5df57-112">Elemento XML</span><span class="sxs-lookup"><span data-stu-id="5df57-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="5df57-113">Crear</span><span class="sxs-lookup"><span data-stu-id="5df57-113">Create</span></span>|<span data-ttu-id="5df57-114">Crear</span><span class="sxs-lookup"><span data-stu-id="5df57-114">Create</span></span>|
|<span data-ttu-id="5df57-115">Leer</span><span class="sxs-lookup"><span data-stu-id="5df57-115">Read</span></span>|<span data-ttu-id="5df57-116">Consulta</span><span class="sxs-lookup"><span data-stu-id="5df57-116">Query</span></span>|
|<span data-ttu-id="5df57-117">Actualizar</span><span class="sxs-lookup"><span data-stu-id="5df57-117">Update</span></span>|<span data-ttu-id="5df57-118">Actualizar</span><span class="sxs-lookup"><span data-stu-id="5df57-118">Update</span></span>|
|<span data-ttu-id="5df57-119">Eliminar</span><span class="sxs-lookup"><span data-stu-id="5df57-119">Delete</span></span>|<span data-ttu-id="5df57-120">Eliminar</span><span class="sxs-lookup"><span data-stu-id="5df57-120">Delete</span></span>|

<span data-ttu-id="5df57-121">En el ejemplo siguiente se muestran las asignaciones de las operaciones de creación, lectura y actualización en el recurso `Service`.</span><span class="sxs-lookup"><span data-stu-id="5df57-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="5df57-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="5df57-122">See Also</span></span>

[<span data-ttu-id="5df57-123">Crear el archivo de esquema MOF para un servicio Web de Management OData</span><span class="sxs-lookup"><span data-stu-id="5df57-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="5df57-124">Esquema de asignación de recursos</span><span class="sxs-lookup"><span data-stu-id="5df57-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="5df57-125">Creación de un servicio Web Management OData</span><span class="sxs-lookup"><span data-stu-id="5df57-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)