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
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="74f39-102">Configuración de la autorización basada en roles</span><span class="sxs-lookup"><span data-stu-id="74f39-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="74f39-103">En este tema se muestra cómo configurar la Directiva de autorización basada en roles para la implementación de ejemplo de la interfaz [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) que se describe en implementación de la [autorización personalizada para la administración. Extensión de IIS de OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="74f39-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="74f39-104">En este ejemplo, configurará un archivo XML usado por la aplicación de ejemplo de administración de OData para definir la Directiva de autorización.</span><span class="sxs-lookup"><span data-stu-id="74f39-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="74f39-105">Creará dos roles y asociará distintos módulos de Windows PowerShell que contengan flujos de trabajo con esos roles.</span><span class="sxs-lookup"><span data-stu-id="74f39-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="74f39-106">El esquema que define el archivo XML se muestra en el [esquema de configuración de autorización basada en roles](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="74f39-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="74f39-107">Modificación del archivo RBacConfiguration. XML</span><span class="sxs-lookup"><span data-stu-id="74f39-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="74f39-108">Este archivo define la Directiva de autorización para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="74f39-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="74f39-109">Los roles se definen mediante el uso de nodos `Group`.</span><span class="sxs-lookup"><span data-stu-id="74f39-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="74f39-110">Un nodo `Group` define los comandos de Windows PowerShell que pueden ejecutar los usuarios asignados a ese grupo.</span><span class="sxs-lookup"><span data-stu-id="74f39-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="74f39-111">Los usuarios se asignan a los grupos mediante los nodos `User`.</span><span class="sxs-lookup"><span data-stu-id="74f39-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="74f39-112">En estos ejemplos, agregará un módulo al nodo @no__t de administrador-0 y agregará un usuario a cada grupo.</span><span class="sxs-lookup"><span data-stu-id="74f39-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="74f39-113">Agregar un módulo a un nodo de grupo</span><span class="sxs-lookup"><span data-stu-id="74f39-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="74f39-114">Cree un archivo denominado **RBacConfiguration. XML** en un editor de texto.</span><span class="sxs-lookup"><span data-stu-id="74f39-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="74f39-115">Este archivo debe guardarse en el directorio principal de la aplicación para el servicio Web.</span><span class="sxs-lookup"><span data-stu-id="74f39-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="74f39-116">Inserte el texto siguiente en el archivo.</span><span class="sxs-lookup"><span data-stu-id="74f39-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="74f39-117">El archivo contiene dos nodos `Group`.</span><span class="sxs-lookup"><span data-stu-id="74f39-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="74f39-118">Estos representan los dos roles utilizados en este ejemplo, los roles `NonAdminGroup` y `AdminGroup`.</span><span class="sxs-lookup"><span data-stu-id="74f39-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="74f39-119">Agregue el siguiente código XML directamente después del cierre de la etiqueta `Cmdlets` en el primer nodo `Group`:</span><span class="sxs-lookup"><span data-stu-id="74f39-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="74f39-120">Agregar un usuario a un nodo de grupo</span><span class="sxs-lookup"><span data-stu-id="74f39-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="74f39-121">Abra el archivo **RBacConfiguration. XML** en un editor de texto.</span><span class="sxs-lookup"><span data-stu-id="74f39-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="74f39-122">Este archivo se encuentra en la carpeta C: \\ \ inetpub\wwwroot\Modata si no cambió el nombre del punto de conexión antes de la instalación.</span><span class="sxs-lookup"><span data-stu-id="74f39-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="74f39-123">Directamente después de la etiqueta de cierre en el nodo `Users`, agregue el siguiente código XML:</span><span class="sxs-lookup"><span data-stu-id="74f39-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="74f39-124">Directamente después del XML agregado en el paso anterior, agregue el siguiente código XML:</span><span class="sxs-lookup"><span data-stu-id="74f39-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```