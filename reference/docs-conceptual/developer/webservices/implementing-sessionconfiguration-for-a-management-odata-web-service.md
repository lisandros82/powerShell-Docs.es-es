---
title: Implementación de Configuracióndesesión para un servicio Web OData de administración | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b2a7ce2-3c33-469c-a4a4-b8fe3bd05324
caps.latest.revision: 5
ms.openlocfilehash: 93780ee8af80d78a5b97a32098384a148070b54a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366144"
---
# <a name="implementing-sessionconfiguration-for-a-management-odata-web-service"></a><span data-ttu-id="25a01-102">Implementación de SessionConfiguration para un servicio web de Management OData</span><span class="sxs-lookup"><span data-stu-id="25a01-102">Implementing SessionConfiguration for a Management OData web service</span></span>

<span data-ttu-id="25a01-103">El uso del servicio Web de Windows PowerShell requiere un tercero para implementar la interfaz [System. Management. Automation. Remoting. Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) para exponer cmdlets de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25a01-103">Using the Windows PowerShell Web Service requires a third party to implement the [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interface to expose Windows PowerShell cmdlets.</span></span> <span data-ttu-id="25a01-104">Esta interfaz proporciona acceso a información sobre la sesión remota que el servicio Web utiliza para ejecutar los cmdlets en el servidor.</span><span class="sxs-lookup"><span data-stu-id="25a01-104">This interface provides access to information about the remote session that the web service uses to run the cmdlets on the server.</span></span> <span data-ttu-id="25a01-105">Después de escribir el código para implementar la interfaz, debe compilarlo en un archivo DLL que se usará en la aplicación Web.</span><span class="sxs-lookup"><span data-stu-id="25a01-105">After writing the code to implement the interface, you must compile it into a DLL to be used in the web application.</span></span>

## <a name="implementation-of-pssessionconfiguration-interface"></a><span data-ttu-id="25a01-106">Implementación de la interfaz PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="25a01-106">Implementation of PSSessionConfiguration interface</span></span>

<span data-ttu-id="25a01-107">El código siguiente implementa la interfaz [System. Management. Automation. Remoting. Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) .</span><span class="sxs-lookup"><span data-stu-id="25a01-107">The following code implements the [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interface.</span></span>

```csharp
//-----------------------------------------------------------------------
// <copyright file="SessionConfiguration.cs" company="Microsoft Corporation">
//     Copyright (C) 2011 Microsoft Corporation
// </copyright>
//-----------------------------------------------------------------------

namespace Microsoft.Samples.Management.OData.RoleBasedPlugins
{
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Management.Automation;
    using System.Management.Automation.Remoting;
    using System.Management.Automation.Runspaces;

    /// <summary>
    /// Custom Session configuration implementation
    /// </summary>
    public class SessionConfiguration : PSSessionConfiguration
    {
        /// <summary>
        /// Gets application private data
        /// </summary>
        /// <param name="senderInfo">Sender information</param>
        /// <returns>Always returns null</returns>
        public override PSPrimitiveDictionary GetApplicationPrivateData(PSSenderInfo senderInfo)
        {
            return null;
        }

        /// <summary>
        /// Gets custom initial session state
        /// It relies on the RBAC system to give list of commands allowed for a user
        /// and creates Initial Session state from that
        /// </summary>
        /// <param name="senderInfo">Sender information</param>
        /// <returns>Custom initial Session state</returns>
        public override InitialSessionState GetInitialSessionState(PSSenderInfo senderInfo)
        {
            if (senderInfo == null)
            {
                throw new ArgumentNullException("senderInfo");
            }

            if (senderInfo.UserInfo == null)
            {
                throw new ArgumentException("senderInfo.UserInfo is null");
            }

            InitialSessionState initialSessionState = InitialSessionState.CreateDefault();
            foreach (SessionStateCommandEntry command in initialSessionState.Commands)
            {
                command.Visibility = SessionStateEntryVisibility.Private;
            }

            List<string> scripts = RbacSystem.Current.GetScripts(senderInfo.UserInfo);
            foreach (string script in scripts)
            {
                initialSessionState.Commands.Add(new SessionStateScriptEntry(script));
            }

            List<string> modules = RbacSystem.Current.GetModules(senderInfo.UserInfo);
            if (modules.Count > 0)
            {
                initialSessionState.ImportPSModule(modules.ToArray());
            }

            // enable execution of scripts in this process
            System.Environment.SetEnvironmentVariable("PSExecutionPolicyPreference", "unrestricted");

            List<string> cmdletsFromRbac = RbacSystem.Current.GetCmdlets(senderInfo.UserInfo);

            // Add all commands from Rbac system to Initial Session State commands
            foreach (string cmdlet in cmdletsFromRbac)
            {
                SessionStateCommandEntry cmdletFromRbac = initialSessionState.Commands.FirstOrDefault(item => string.Equals(item.Name, cmdlet, StringComparison.OrdinalIgnoreCase));
                if (cmdletFromRbac == null)
                {
                    throw new ArgumentException("Command not found in InitialSessionState " + cmdlet);
                }

                cmdletFromRbac.Visibility = SessionStateEntryVisibility.Public;
            }

            return initialSessionState;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="25a01-108">Véase también</span><span class="sxs-lookup"><span data-stu-id="25a01-108">See Also</span></span>

[<span data-ttu-id="25a01-109">Implementación de la autorización personalizada para un servicio Web OData de administración</span><span class="sxs-lookup"><span data-stu-id="25a01-109">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)