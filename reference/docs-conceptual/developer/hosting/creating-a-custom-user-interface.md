---
title: Crear una interfaz de usuario personalizada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367634"
---
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="27eb1-102">Creación de una interfaz de usuario personalizada</span><span class="sxs-lookup"><span data-stu-id="27eb1-102">Creating a custom user interface</span></span>

<span data-ttu-id="27eb1-103">Windows PowerShell proporciona clases e interfaces abstractas que permiten crear una interfaz de usuario interactiva personalizada que hospeda el motor de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27eb1-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="27eb1-104">Para crear una interfaz de usuario personalizada, debe implementar la clase [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) .</span><span class="sxs-lookup"><span data-stu-id="27eb1-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="27eb1-105">Opcionalmente, también puede implementar las clases [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)y [System. Management. Automation. host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) , y las interfaces [System. Management. Automation. host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) y [System. Management. Automation. host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) .</span><span class="sxs-lookup"><span data-stu-id="27eb1-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
