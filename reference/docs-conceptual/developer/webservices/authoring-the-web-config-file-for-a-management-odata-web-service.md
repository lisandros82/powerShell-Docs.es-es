---
title: Crear el archivo Web. config para un servicio Web de Management OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359794"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Creación del archivo Web.config para un servicio web de Management OData

Para poder implementar el servicio Web de administración de OData, debe configurar el archivo Web. config para que apunte a los archivos de esquema XML y a los archivos DLL que implementan [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) y [ Interfaces System. Management. Automation. Remoting. Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) .

## <a name="sample-config-file"></a>Archivo de configuración de ejemplo

A continuación se muestra un ejemplo del aspecto del archivo Web. config para el servicio Web.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a>Véase también

[Implementación de la autorización personalizada para un servicio Web OData de administración](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[Implementación de Configuracióndesesión para un servicio Web OData de administración](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Crear el archivo de esquema MOF para un servicio Web de Management OData](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Crear el archivo de esquema XML para un servicio Web de Management OData](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Creación de un servicio Web Management OData](./creating-a-management-odata-web-service.md)