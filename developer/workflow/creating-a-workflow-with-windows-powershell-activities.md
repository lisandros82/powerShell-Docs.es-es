---
title: Creación de un flujo de trabajo con actividades de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853471"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Creación de un flujo de trabajo con actividades de Windows PowerShell

Puede crear un flujo de trabajo de Windows PowerShell seleccionando las actividades desde el cuadro de herramientas de Visual Studio y arrastrarlos a la ventana del Diseñador de flujo de trabajo. Para obtener información acerca de cómo agregar actividades de Windows PowerShell en el cuadro de herramientas de Visual Studio, consulte [agregar actividades de Windows PowerShell para Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

Los procedimientos siguientes describen cómo crear un flujo de trabajo que comprueba el estado de dominio de un grupo de equipos especificado por el usuario, se une a un dominio si ya no están combinadas y, a continuación, comprueba el estado de nuevo.

### <a name="setting-up-the-project"></a>Configurar el proyecto

1. Siga el procedimiento de [agregar actividades de Windows PowerShell para Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para crear un proyecto de flujo de trabajo y agregar las actividades desde el [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) y [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) ensamblados en el cuadro de herramientas.

2. Agregar System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities y Microsoft.PowerShell.Commands.Management como para el proyecto como ensamblados de referencia.

### <a name="adding-activities-to-the-workflow"></a>Agregar actividades al flujo de trabajo

1. Agregar un **secuencia** actividad al flujo de trabajo.

2. Creación de un argumento con nombre `ComputerName` con un tipo de argumento `String[]`. Este argumento representa los nombres de los equipos para comprobar y join.

3. Creación de un argumento con nombre `DomainCred` typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential). Este argumento representa las credenciales de dominio de una cuenta de dominio que está autorizado para unir un equipo al dominio.

4. Creación de un argumento con nombre `MachineCred` typu [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential). Este argumento representa las credenciales de administrador en los equipos para comprobar y join.

5. Agregar un **ParallelForEach** actividad dentro de la **secuencia** actividad. Escriba `comp` y `ComputerName` en los cuadros de texto para que el bucle recorre en iteración los elementos de la `ComputerName` matriz.

6. Agregar un **secuencia** actividad en el cuerpo de la **ParallelForEach** actividad. Establecer el **DisplayName** propiedad de la secuencia de `JoinDomain`.

7. Agregar un **GetWmiObject** actividad a la **JoinDomain** secuencia.

8. Editar las propiedades de la **GetWmiObject** actividad como se indica a continuación.

   |Propiedad|Value|
   |--------------|-----------|
   |**Clase**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. Agregar un **AddComputer** actividad a la **JoinDomain** secuencia después de la **GetWmiObject** actividad.

10. Editar las propiedades de la **AddComputer** actividad como se indica a continuación.

    |Propiedad|Value|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. Agregar un **RestartComputer** actividad a la **JoinDomain** secuencia después de la **AddComputer** actividad.

12. Editar las propiedades de la **RestartComputer** actividad como se indica a continuación.

    |Propiedad|Value|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**Credencial**|MachineCred|
    |**para**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. Agregar un **GetWmiObject** actividad a la **JoinDomain** secuencia después de la **RestartComputer** actividad. Editar sus propiedades para que sea el mismo que el anterior **GetWmiObject** actividad.

    Cuando haya terminado los procedimientos, la ventana de diseño de flujo de trabajo debe tener este aspecto.

    ![JoinDomain XAML en el Diseñador de flujo de trabajo](../media/joindomainworkflow.png)
    ![JoinDomain XAML en el Diseñador de flujo de trabajo](../media/joindomainworkflow.png "JoinDomainWorkflow")