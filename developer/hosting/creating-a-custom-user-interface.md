---
title: Creación de una interfaz de usuario personalizada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863721"
---
# <a name="creating-a-custom-user-interface"></a>Creación de una interfaz de usuario personalizada

Windows PowerShell proporciona las clases abstractas e interfaces que permiten crear una interfaz de usuario interactiva personalizado que hospeda el motor de Windows PowerShell. Para crear una interfaz de usuario personalizada, debe implementar la [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) clase. Si lo desea, también puede implementar la [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)y [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) clases y el [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) y [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.
