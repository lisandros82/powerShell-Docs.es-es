---
title: Crear un flujo de trabajo con actividades de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359634"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Creación de un flujo de trabajo con actividades de Windows PowerShell

Puede crear un flujo de trabajo de Windows PowerShell seleccionando actividades en el cuadro de herramientas de Visual Studio y arrastrándolos a la ventana Diseñador de flujo de trabajo. Para obtener información sobre cómo agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio, vea [Agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

En los procedimientos siguientes se describe cómo crear un flujo de trabajo que comprueba el estado de dominio de un grupo de equipos especificados por el usuario, los une a un dominio si aún no están Unidos y, a continuación, vuelve a comprobar el estado.

### <a name="setting-up-the-project"></a>Configurar el proyecto

1. Siga el procedimiento descrito en [Agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) para crear un proyecto de flujo de trabajo y agregar las actividades de los ensamblados [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) y [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) al cuadro de herramientas.

2. Agregue System. Management. Automation, Microsoft. PowerShell. Activities, System. Management, Microsoft. PowerShell. Management. Activities y Microsoft. PowerShell. Commands. Management al proyecto como ensamblados de referencia.

### <a name="adding-activities-to-the-workflow"></a>Agregar actividades al flujo de trabajo

1. Agregue una actividad **Sequence** al flujo de trabajo.

2. Cree un argumento denominado `ComputerName` con un tipo de argumento de `String[]`. Este argumento representa los nombres de los equipos que se van a comprobar y a los que se va a combinar.

3. Cree un argumento denominado `DomainCred` del tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Este argumento representa las credenciales de dominio de una cuenta de dominio que está autorizada para unir un equipo al dominio.

4. Cree un argumento denominado `MachineCred` del tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential). Este argumento representa las credenciales de un administrador en los equipos para comprobar y unirse.

5. Agregue una actividad **ParallelForEach** dentro de la actividad **Sequence** . Escriba `comp` y `ComputerName` en los cuadros de texto para que el bucle recorra en iteración los elementos de la matriz de `ComputerName`.

6. Agregue una actividad **Sequence** al cuerpo de la actividad **ParallelForEach** . Establezca la propiedad **displayName** de la secuencia en `JoinDomain`.

7. Agregue una actividad **GetWmiObject** a la secuencia **JoinDomain** .

8. Edite las propiedades de la actividad **GetWmiObject** como se indica a continuación.

   |Property|Valor|
   |--------------|-----------|
   |**Las**|"Win32_ComputerSystem"|
   |**PSComputerName**|COMP|
   |**PSCredential**|MachineCred|

9. Agregue una actividad **AddComputer** a la secuencia **JoinDomain** después de la actividad **GetWmiObject** .

10. Edite las propiedades de la actividad **AddComputer** como se indica a continuación.

    |Property|Valor|
    |--------------|-----------|
    |**NombreDeEquipo**|COMP|
    |**DomainCredential**|DomainCred|

11. Agregue una actividad **RestartComputer** a la secuencia **JoinDomain** después de la actividad **AddComputer** .

12. Edite las propiedades de la actividad **RestartComputer** como se indica a continuación.

    |Property|Valor|
    |--------------|-----------|
    |**NombreDeEquipo**|COMP|
    |**Caja**|MachineCred|
    |**Para**|Microsoft. PowerShell. Commands. WaitForServiceTypes. PowerShell|
    |**Aplica**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. Agregue una actividad **GetWmiObject** a la secuencia **JoinDomain** después de la actividad **RestartComputer** . Edite sus propiedades para que coincidan con la actividad **GetWmiObject** anterior.

    Cuando haya terminado los procedimientos, la ventana de diseño de flujo de trabajo debería tener este aspecto.

    ![el XAML de JoinDomain en el diseñador de flujo de trabajo](../media/joindomainworkflow.png)
    ![JOINDOMAIN XAML en el diseñador de flujo de trabajo](../media/joindomainworkflow.png "JoinDomainWorkflow")