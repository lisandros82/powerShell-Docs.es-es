---
title: Creación de espacios de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857911"
---
# <a name="creating-runspaces"></a>Creación de espacios de ejecución

Un espacio de ejecución es el entorno operativo para los comandos que se invocan mediante una aplicación host. Este entorno incluye los comandos y los datos que se encuentran actualmente y las restricciones de lenguaje que se aplican actualmente.

 Las aplicaciones host pueden utilizar el espacio de ejecución predeterminada proporcionada por Windows PowerShell, que incluye todos los comandos de núcleo disponible, o crear un espacio de ejecución personalizado que incluya solo un subconjunto de los comandos disponibles. Para crear un espacio de ejecución personalizado, cree un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) de objetos y asignarla a su espacio de ejecución.

## <a name="runspace-tasks"></a>Tareas del espacio de ejecución

1. [Creación de un InitialSessionState](./creating-an-initialsessionstate.md)

2. [Creación de un espacio de ejecución restringida](./creating-a-constrained-runspace.md)

3. [Crear varios espacios de ejecución](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Véase también
