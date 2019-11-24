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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359774"
---
# <a name="configuring-role-based-authorization"></a>Configuración de la autorización basada en roles

En este tema se muestra cómo configurar la Directiva de autorización basada en roles para la implementación de ejemplo de la interfaz [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) que se describe en [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).

En este ejemplo, configurará un archivo XML usado por la aplicación de ejemplo de administración de OData para definir la Directiva de autorización. Creará dos roles y asociará distintos módulos de Windows PowerShell que contengan flujos de trabajo con esos roles. El esquema que define el archivo XML se muestra en el [esquema de configuración de autorización basada en roles](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modificación del archivo RBacConfiguration. XML

Este archivo define la Directiva de autorización para la aplicación. Los roles se definen mediante el uso de `Group` nodos. Un nodo `Group` define los comandos de Windows PowerShell que pueden ejecutar los usuarios asignados a ese grupo. Los usuarios se asignan a los grupos mediante `User` nodos.

En estos ejemplos, agregará un módulo al nodo `Group` de administrador y agregará un usuario a cada grupo.

#### <a name="adding-a-module-to-a-group-node"></a>Agregar un módulo a un nodo de grupo

1. Cree un archivo denominado **RBacConfiguration. XML** en un editor de texto. Este archivo debe guardarse en el directorio principal de la aplicación para el servicio Web. Inserte el texto siguiente en el archivo.

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

2. El archivo contiene dos nodos `Group`. Estos representan los dos roles utilizados en este ejemplo, los roles `NonAdminGroup` y `AdminGroup`.

   Agregue el siguiente código XML directamente después de la etiqueta de cierre `Cmdlets` en el primer nodo `Group`:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Agregar un usuario a un nodo de grupo

1. Abra el archivo **RBacConfiguration. XML** en un editor de texto. Este archivo se encuentra en la carpeta C:\\\inetpub\wwwroot\Modata si no cambió el nombre del punto de conexión antes de la instalación.

2. Directamente después de la etiqueta de cierre del nodo `Users`, agregue el siguiente código XML:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Directamente después del XML agregado en el paso anterior, agregue el siguiente código XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```