---
title: Crear espacios de espacios | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367584"
---
# <a name="creating-runspaces"></a>Creación de espacios de ejecución

Un espacio de ejecución es el entorno operativo para los comandos invocados por una aplicación host. Este entorno incluye los comandos y datos actualmente presentes y cualquier restricción de lenguaje que se aplique actualmente.

 Las aplicaciones host pueden usar el espacio de ejecución predeterminado proporcionado por Windows PowerShell, que incluye todos los comandos principales disponibles, o crear un espacio de ejecución personalizado que incluye solo un subconjunto de los comandos disponibles. Para crear un espacio de ejecución personalizado, cree un objeto [System. Management. Automation. runspace. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) y asígnelo al espacio de ejecución.

## <a name="runspace-tasks"></a>Tareas del espacio de ejecución

1. [Creación de un InitialSessionState](./creating-an-initialsessionstate.md)

2. [Crear un espacio de ejecución restringido](./creating-a-constrained-runspace.md)

3. [Crear varios espacios de espacios](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Véase también
