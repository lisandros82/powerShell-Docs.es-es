---
title: Creación de un servicio Web Management OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359724"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="b99c7-102">Creación de un servicio web de Management OData</span><span class="sxs-lookup"><span data-stu-id="b99c7-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="b99c7-103">La extensión IIS Management ODATA es una infraestructura para crear un extremo de servicio Web ASP.NET que expone los datos de administración, a los que se accede a través de scripts y cmdlets de Windows PowerShell, como entidades de servicio Web de OData.</span><span class="sxs-lookup"><span data-stu-id="b99c7-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="b99c7-104">Para ello, procesa las solicitudes de OData y las convierte en una invocación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b99c7-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="b99c7-105">Los equipos de producto se pueden basar en esta infraestructura para crear puntos de conexión que exponen conjuntos específicos de datos de administración.</span><span class="sxs-lookup"><span data-stu-id="b99c7-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="b99c7-106">Descargue e instale el ejemplo [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) .</span><span class="sxs-lookup"><span data-stu-id="b99c7-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="b99c7-107">Siga las instrucciones para implementar el servicio Web.</span><span class="sxs-lookup"><span data-stu-id="b99c7-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="b99c7-108">Este servicio Web expone servicios y procesos a través de operaciones de creación, lectura, actualización y eliminación (CRUD).</span><span class="sxs-lookup"><span data-stu-id="b99c7-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="b99c7-109">Las solicitudes CRUD realizadas al servicio Web invocan comandos de Windows PowerShell que realizan las operaciones solicitadas.</span><span class="sxs-lookup"><span data-stu-id="b99c7-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="b99c7-110">Una asignación entre las operaciones CRUD y los comandos subyacentes de Windows PowerShell se implementa mediante dos archivos de esquema, Schema. mof y Schema. Xml.</span><span class="sxs-lookup"><span data-stu-id="b99c7-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="b99c7-111">El archivo Schema. mof usa el estándar de objetos administrados (MOF) del [equipo de administración distribuida](https://www.dmtf.org/) (DMTF).</span><span class="sxs-lookup"><span data-stu-id="b99c7-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="b99c7-112">El archivo Schema. xml utiliza un esquema XML que se describe en el [esquema de asignación de recursos](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="b99c7-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b99c7-113">Antes de habilitar la extensión de IIS Management ODATA en Windows Server 2008 R2 SP1, deben estar habilitadas las siguientes características.</span><span class="sxs-lookup"><span data-stu-id="b99c7-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="b99c7-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="b99c7-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="b99c7-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="b99c7-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="b99c7-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="b99c7-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="b99c7-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="b99c7-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="b99c7-118">Pasos para crear un servicio Web Management OData</span><span class="sxs-lookup"><span data-stu-id="b99c7-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="b99c7-119">En los temas siguientes se describe cómo crear e implementar un servicio Web de administración de OData.</span><span class="sxs-lookup"><span data-stu-id="b99c7-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="b99c7-120">Agregar recursos a un servicio Web de Management OData</span><span class="sxs-lookup"><span data-stu-id="b99c7-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="b99c7-121">Implementación de la autorización personalizada para un servicio Web OData de administración</span><span class="sxs-lookup"><span data-stu-id="b99c7-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="b99c7-122">Implementación de Configuracióndesesión para un servicio Web OData de administración</span><span class="sxs-lookup"><span data-stu-id="b99c7-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="b99c7-123">Crear el archivo de esquema MOF para un servicio Web de Management OData</span><span class="sxs-lookup"><span data-stu-id="b99c7-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="b99c7-124">Crear el archivo de esquema XML para un servicio Web de Management OData</span><span class="sxs-lookup"><span data-stu-id="b99c7-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="b99c7-125">Crear el archivo Web. config para un servicio Web de administración de OData</span><span class="sxs-lookup"><span data-stu-id="b99c7-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="b99c7-126">Implementación de un servicio Web OData de administración</span><span class="sxs-lookup"><span data-stu-id="b99c7-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="b99c7-127">Asociación de entidades de Management OData</span><span class="sxs-lookup"><span data-stu-id="b99c7-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="b99c7-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="b99c7-128">See Also</span></span>

[<span data-ttu-id="b99c7-129">Archivos de esquema de extensión IIS de Management ODATA</span><span class="sxs-lookup"><span data-stu-id="b99c7-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
