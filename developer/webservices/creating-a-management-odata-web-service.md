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
# <a name="creating-a-management-odata-web-service"></a>Creación de un servicio web de Management OData

Extensión IIS Management ODATA es una infraestructura para crear un punto de conexión de servicio de web ASP.NET que expone los datos de administración, tiene acceso mediante los cmdlets de Windows PowerShell y las secuencias de comandos, como entidades de servicio Web de OData. Lo consigue procesar las solicitudes de OData y convertirlos en una invocación de Windows PowerShell. Los equipos de productos pueden compilar encima de esta infraestructura para crear puntos de conexión que exponen conjuntos específicos de datos de administración.

Descargue e instale el [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) ejemplo. Siga las instrucciones para implementar el servicio web. Este servicio web expone los servicios y procesos a través de operaciones de creación, lectura, actualización y eliminación (CRUD). Las solicitudes CRUD realizadas al servicio web de invocan comandos de Windows PowerShell que realizan las operaciones solicitadas. Una asignación entre las operaciones CRUD y los comandos de Windows PowerShell subyacentes se implementa mediante schema.xml, schema.mof y los archivos de dos esquemas. El archivo schema.mof utiliza el [Distributed Management Task Force](https://www.dmtf.org/) estándar (DMTF) MOF (Managed Object). El archivo schema.xml usa un esquema XML que se describe en [esquema de asignación de recursos](./resource-mapping-schema.md).

> [!IMPORTANT]
> Antes de habilitar la extensión de IIS Management ODATA en Windows Server 2008 R2 SP1, deben habilitarse las siguientes características.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Pasos para crear un servicio web de IIS Management OData

Los temas siguientes describen cómo crear e implementar un servicio web de IIS Management OData.

- [Agregar recursos a un servicio de administración Web de OData](./adding-resources-to-a-management-odata-web-service.md)

- [Implementación de la autorización personalizada para un servicio web de IIS Management OData](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementación de Configuracióndesesión para un servicio web de IIS Management OData](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Crea el archivo de esquema MOF para un servicio web de IIS Management OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Crea el archivo de esquema XML para un servicio web de IIS Management OData](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Crea el archivo Web.config para un servicio web de IIS Management OData](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Implementar un servicio web de IIS Management OData](./deploying-a-management-odata-web-service.md)

- [Asociar las entidades de OData de administración](./associating-management-odata-entities.md)

## <a name="see-also"></a>Véase también

[Archivos de esquema de extensión Management ODATA de IIS](./management-odata-iis-extension-schema-files.md)
