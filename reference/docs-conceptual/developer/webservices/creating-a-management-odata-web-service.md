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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359724"
---
# <a name="creating-a-management-odata-web-service"></a>Creación de un servicio web de Management OData

La extensión IIS Management ODATA es una infraestructura para crear un extremo de servicio Web ASP.NET que expone los datos de administración, a los que se accede a través de scripts y cmdlets de Windows PowerShell, como entidades de servicio Web de OData. Para ello, procesa las solicitudes de OData y las convierte en una invocación de Windows PowerShell. Los equipos de producto se pueden basar en esta infraestructura para crear puntos de conexión que exponen conjuntos específicos de datos de administración.

Descargue e instale el ejemplo [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) . Siga las instrucciones para implementar el servicio Web. Este servicio Web expone servicios y procesos a través de operaciones de creación, lectura, actualización y eliminación (CRUD). Las solicitudes CRUD realizadas al servicio Web invocan comandos de Windows PowerShell que realizan las operaciones solicitadas. Una asignación entre las operaciones CRUD y los comandos subyacentes de Windows PowerShell se implementa mediante dos archivos de esquema, Schema. mof y Schema. Xml. El archivo Schema. mof usa el estándar de objetos administrados (MOF) del [equipo de administración distribuida](https://www.dmtf.org/) (DMTF). El archivo Schema. xml utiliza un esquema XML que se describe en el [esquema de asignación de recursos](./resource-mapping-schema.md).

> [!IMPORTANT]
> Antes de habilitar la extensión de IIS Management ODATA en Windows Server 2008 R2 SP1, deben estar habilitadas las siguientes características.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Pasos para crear un servicio Web Management OData

En los temas siguientes se describe cómo crear e implementar un servicio Web de administración de OData.

- [Agregar recursos a un servicio Web de Management OData](./adding-resources-to-a-management-odata-web-service.md)

- [Implementación de la autorización personalizada para un servicio Web OData de administración](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementación de Configuracióndesesión para un servicio Web OData de administración](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Crear el archivo de esquema MOF para un servicio Web de Management OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Crear el archivo de esquema XML para un servicio Web de Management OData](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Crear el archivo Web. config para un servicio Web de administración de OData](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Implementación de un servicio Web OData de administración](./deploying-a-management-odata-web-service.md)

- [Asociación de entidades de Management OData](./associating-management-odata-entities.md)

## <a name="see-also"></a>Véase también

[Archivos de esquema de extensión IIS de Management ODATA](./management-odata-iis-extension-schema-files.md)
