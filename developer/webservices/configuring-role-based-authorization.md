---
title: Configuración de la autorización basada en roles | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859601"
---
# <a name="configuring-role-based-authorization"></a>Configuración de la autorización basada en roles

En este tema se muestra cómo configurar la directiva de autorización basada en roles para la implementación de ejemplo de la [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interfaz se describe en [implementación personalizada Autorización para la extensión IIS Management OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).

En este ejemplo, configurará un archivo XML que se usa la aplicación de IIS Management OData de ejemplo para definir la directiva de autorización. Creará dos roles y asociar diferentes módulos de Windows PowerShell que contienen flujos de trabajo con esos roles. El esquema que define el archivo XML está disponible en [esquema de configuración de autorización basada en roles](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modificación del archivo RBacConfiguration.xml

Este archivo define la directiva de autorización para la aplicación. Los roles se definen mediante `Group` nodos. Un `Group` nodo define los comandos de Windows PowerShell que se pueden ejecutar los usuarios asignados a ese grupo. Los usuarios se asignan a grupos mediante el uso de `User` nodos.

En estos ejemplos, agregará un módulo al administrador `Group` nodo, y agregar un usuario a cada grupo.

#### <a name="adding-a-module-to-a-group-node"></a>Agregar un módulo a un nodo de grupo

1. Cree un archivo denominado **RBacConfiguration.xml** en un editor de texto. Este archivo debe guardarse en el directorio principal de la aplicación para el servicio web. Inserte el siguiente texto en el archivo.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. El archivo contiene dos `Group` nodos. Estos representan los dos roles utilizados en este ejemplo, el `NonAdminGroup` y `AdminGroup` roles.

   Directamente después del cierre `Cmdlets` en la primera etiqueta `Group` nodo, agregue el siguiente XML:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Agregar un usuario a un nodo de grupo

1. Abra el **RBacConfiguration.xml** archivo en un editor de texto. Este archivo se encuentra en la carpeta C:\\\inetpub\wwwroot\Modata si no ha cambiado el nombre de punto de conexión antes de la instalación.

2. Directamente después de la etiqueta de cierre en el `Users` nodo, agregue el siguiente XML:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Directamente después de agrega el código XML en el paso anterior, agregue el siguiente código XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```