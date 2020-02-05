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
ms.openlocfilehash: b830571418fe75bbfc68df02f20a6012efefd99a
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996067"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="70e97-102">Creación del archivo de esquema XML para un servicio web de Management OData</span><span class="sxs-lookup"><span data-stu-id="70e97-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="70e97-103">Después de definir los recursos que el servicio Web expondrá (consulte [creación del archivo de esquema MOF para un servicio Web de Management OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), debe asignar esos recursos a los cmdlets de Windows PowerShell subyacentes que implementan las operaciones admitidas para cada recurso mediante la creación de un archivo XML que se ajusta al [esquema de asignación de recursos](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="70e97-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="70e97-104">El archivo XML también especifica las direcciones URL que usa el cliente para tener acceso a los recursos.</span><span class="sxs-lookup"><span data-stu-id="70e97-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="70e97-105">Mappng recursos a direcciones URL</span><span class="sxs-lookup"><span data-stu-id="70e97-105">Mappng resources to URLs</span></span>

<span data-ttu-id="70e97-106">La primera parte del archivo XML asigna los recursos definidos en el archivo de esquema MOF a las direcciones URL que se usan para obtener acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="70e97-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="70e97-107">En el ejemplo siguiente se muestra la asignación.</span><span class="sxs-lookup"><span data-stu-id="70e97-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="https://schemas.microsoft.com/powershell-web-services/2010/09">
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

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="70e97-108">Asignación de cmdlets a operaciones CRUD</span><span class="sxs-lookup"><span data-stu-id="70e97-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="70e97-109">A continuación, especifique los cmdlets que corresponden a las operaciones CRUD (crear, leer, actualizar y eliminar) que admiten los recursos.</span><span class="sxs-lookup"><span data-stu-id="70e97-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="70e97-110">En el esquema de [asignación de recursos](./resource-mapping-schema.md)OData de administración, las operaciones CRUD se asignan de la siguiente manera.</span><span class="sxs-lookup"><span data-stu-id="70e97-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="70e97-111">CRUD (comando)</span><span class="sxs-lookup"><span data-stu-id="70e97-111">CRUD command</span></span>|<span data-ttu-id="70e97-112">Elemento XML</span><span class="sxs-lookup"><span data-stu-id="70e97-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="70e97-113">Crear</span><span class="sxs-lookup"><span data-stu-id="70e97-113">Create</span></span>|<span data-ttu-id="70e97-114">Crear</span><span class="sxs-lookup"><span data-stu-id="70e97-114">Create</span></span>|
|<span data-ttu-id="70e97-115">Leer</span><span class="sxs-lookup"><span data-stu-id="70e97-115">Read</span></span>|<span data-ttu-id="70e97-116">Consulta</span><span class="sxs-lookup"><span data-stu-id="70e97-116">Query</span></span>|
|<span data-ttu-id="70e97-117">Actualizar</span><span class="sxs-lookup"><span data-stu-id="70e97-117">Update</span></span>|<span data-ttu-id="70e97-118">Actualizar</span><span class="sxs-lookup"><span data-stu-id="70e97-118">Update</span></span>|
|<span data-ttu-id="70e97-119">Eliminar</span><span class="sxs-lookup"><span data-stu-id="70e97-119">Delete</span></span>|<span data-ttu-id="70e97-120">Eliminar</span><span class="sxs-lookup"><span data-stu-id="70e97-120">Delete</span></span>|

<span data-ttu-id="70e97-121">En el ejemplo siguiente se muestran las asignaciones de las operaciones de creación, lectura y actualización en el recurso `Service`.</span><span class="sxs-lookup"><span data-stu-id="70e97-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="70e97-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="70e97-122">See Also</span></span>

[<span data-ttu-id="70e97-123">Crear el archivo de esquema MOF para un servicio Web de Management OData</span><span class="sxs-lookup"><span data-stu-id="70e97-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="70e97-124">Esquema de asignación de recursos</span><span class="sxs-lookup"><span data-stu-id="70e97-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="70e97-125">Creación de un servicio Web Management OData</span><span class="sxs-lookup"><span data-stu-id="70e97-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)