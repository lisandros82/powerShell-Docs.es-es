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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367634"
---
# <a name="creating-a-custom-user-interface"></a>Creación de una interfaz de usuario personalizada

Windows PowerShell proporciona clases e interfaces abstractas que permiten crear una interfaz de usuario interactiva personalizada que hospeda el motor de Windows PowerShell. Para crear una interfaz de usuario personalizada, debe implementar la clase [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) . Opcionalmente, también puede implementar las clases [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)y [System. Management. Automation. host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) , y el [ Interfaces System. Management. Automation](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) . host. Ihostsupportsinteractivesession y [System. Management. Automation. host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) .
