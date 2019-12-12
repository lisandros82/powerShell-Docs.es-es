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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359794"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a><span data-ttu-id="453ca-102">Creación del archivo Web.config para un servicio web de Management OData</span><span class="sxs-lookup"><span data-stu-id="453ca-102">Authoring the Web.config file for a Management OData web service</span></span>

<span data-ttu-id="453ca-103">Para poder implementar el servicio Web de Management OData, debe configurar el archivo Web. config para que apunte a los archivos de esquema XML y a los archivos DLL que implementan las interfaces [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) y [System. Management. Automation. Remoting. Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) .</span><span class="sxs-lookup"><span data-stu-id="453ca-103">Before you can deploy your Management OData web service, you must configure the web.config file to point to the XML schema files and the DLLs that implement the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) and  [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.</span></span>

## <a name="sample-config-file"></a><span data-ttu-id="453ca-104">Archivo de configuración de ejemplo</span><span class="sxs-lookup"><span data-stu-id="453ca-104">Sample config file</span></span>

<span data-ttu-id="453ca-105">A continuación se muestra un ejemplo del aspecto del archivo Web. config para el servicio Web.</span><span class="sxs-lookup"><span data-stu-id="453ca-105">The following is an example of what the web.config file for your web service looks like.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="453ca-106">Véase también</span><span class="sxs-lookup"><span data-stu-id="453ca-106">See Also</span></span>

[<span data-ttu-id="453ca-107">Implementación de la autorización personalizada para un servicio Web OData de administración</span><span class="sxs-lookup"><span data-stu-id="453ca-107">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[<span data-ttu-id="453ca-108">Implementación de Configuracióndesesión para un servicio Web OData de administración</span><span class="sxs-lookup"><span data-stu-id="453ca-108">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[<span data-ttu-id="453ca-109">Crear el archivo de esquema MOF para un servicio Web de Management OData</span><span class="sxs-lookup"><span data-stu-id="453ca-109">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="453ca-110">Crear el archivo de esquema XML para un servicio Web de Management OData</span><span class="sxs-lookup"><span data-stu-id="453ca-110">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="453ca-111">Creación de un servicio Web Management OData</span><span class="sxs-lookup"><span data-stu-id="453ca-111">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)