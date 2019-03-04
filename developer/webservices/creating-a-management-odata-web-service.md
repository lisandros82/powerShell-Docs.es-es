---
title: Creación de un servicio de administración Web de OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856631"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="6c28e-102">Creación de un servicio web de Management OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="6c28e-103">Extensión IIS Management ODATA es una infraestructura para crear un punto de conexión de servicio de web ASP.NET que expone los datos de administración, tiene acceso mediante los cmdlets de Windows PowerShell y las secuencias de comandos, como entidades de servicio Web de OData.</span><span class="sxs-lookup"><span data-stu-id="6c28e-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="6c28e-104">Lo consigue procesar las solicitudes de OData y convertirlos en una invocación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6c28e-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="6c28e-105">Los equipos de productos pueden compilar encima de esta infraestructura para crear puntos de conexión que exponen conjuntos específicos de datos de administración.</span><span class="sxs-lookup"><span data-stu-id="6c28e-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="6c28e-106">Descargue e instale el [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) ejemplo.</span><span class="sxs-lookup"><span data-stu-id="6c28e-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="6c28e-107">Siga las instrucciones para implementar el servicio web.</span><span class="sxs-lookup"><span data-stu-id="6c28e-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="6c28e-108">Este servicio web expone los servicios y procesos a través de operaciones de creación, lectura, actualización y eliminación (CRUD).</span><span class="sxs-lookup"><span data-stu-id="6c28e-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="6c28e-109">Las solicitudes CRUD realizadas al servicio web de invocan comandos de Windows PowerShell que realizan las operaciones solicitadas.</span><span class="sxs-lookup"><span data-stu-id="6c28e-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="6c28e-110">Una asignación entre las operaciones CRUD y los comandos de Windows PowerShell subyacentes se implementa mediante schema.xml, schema.mof y los archivos de dos esquemas.</span><span class="sxs-lookup"><span data-stu-id="6c28e-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="6c28e-111">El archivo schema.mof utiliza el [Distributed Management Task Force](https://www.dmtf.org/) estándar (DMTF) MOF (Managed Object).</span><span class="sxs-lookup"><span data-stu-id="6c28e-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="6c28e-112">El archivo schema.xml usa un esquema XML que se describe en [esquema de asignación de recursos](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="6c28e-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c28e-113">Antes de habilitar la extensión de IIS Management ODATA en Windows Server 2008 R2 SP1, deben habilitarse las siguientes características.</span><span class="sxs-lookup"><span data-stu-id="6c28e-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="6c28e-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="6c28e-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="6c28e-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="6c28e-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="6c28e-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="6c28e-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="6c28e-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="6c28e-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="6c28e-118">Pasos para crear un servicio web de IIS Management OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="6c28e-119">Los temas siguientes describen cómo crear e implementar un servicio web de IIS Management OData.</span><span class="sxs-lookup"><span data-stu-id="6c28e-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="6c28e-120">Agregar recursos a un servicio de administración Web de OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="6c28e-121">Implementación de la autorización personalizada para un servicio web de IIS Management OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="6c28e-122">Implementación de Configuracióndesesión para un servicio web de IIS Management OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="6c28e-123">Crea el archivo de esquema MOF para un servicio web de IIS Management OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="6c28e-124">Crea el archivo de esquema XML para un servicio web de IIS Management OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="6c28e-125">Crea el archivo Web.config para un servicio web de IIS Management OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="6c28e-126">Implementar un servicio web de IIS Management OData</span><span class="sxs-lookup"><span data-stu-id="6c28e-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="6c28e-127">Asociar las entidades de OData de administración</span><span class="sxs-lookup"><span data-stu-id="6c28e-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="6c28e-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="6c28e-128">See Also</span></span>

[<span data-ttu-id="6c28e-129">Archivos de esquema de extensión Management ODATA de IIS</span><span class="sxs-lookup"><span data-stu-id="6c28e-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
