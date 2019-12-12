---
title: Ejemplos de hosts personalizados | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367514"
---
# <a name="custom-host-samples"></a><span data-ttu-id="a69a6-102">Ejemplos de host personalizado</span><span class="sxs-lookup"><span data-stu-id="a69a6-102">Custom Host Samples</span></span>

<span data-ttu-id="a69a6-103">En esta sección se incluye código de ejemplo para escribir un host personalizado.</span><span class="sxs-lookup"><span data-stu-id="a69a6-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="a69a6-104">Puede usar Microsoft Visual Studio para crear una aplicación de consola y, a continuación, copiar el código de los temas de esta sección en la aplicación host.</span><span class="sxs-lookup"><span data-stu-id="a69a6-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a69a6-105">En esta sección</span><span class="sxs-lookup"><span data-stu-id="a69a6-105">In This Section</span></span>

 <span data-ttu-id="a69a6-106">[Ejemplo de Host01](./host01-sample.md) Este ejemplo muestra cómo implementar una aplicación host que usa un host personalizado básico.</span><span class="sxs-lookup"><span data-stu-id="a69a6-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="a69a6-107">[Ejemplo de Host02](./host02-sample.md) En este ejemplo se muestra cómo escribir una aplicación host que usa el tiempo de ejecución de Windows PowerShell junto con una implementación de host personalizado.</span><span class="sxs-lookup"><span data-stu-id="a69a6-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="a69a6-108">La aplicación host establece la referencia cultural del host en alemán, ejecuta el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) y muestra los resultados tal y como se verán con pwrsh. exe y, a continuación, imprime los datos y la hora actuales en alemán.</span><span class="sxs-lookup"><span data-stu-id="a69a6-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="a69a6-109">[Ejemplo de Host03](./host03-sample.md) En este ejemplo se muestra cómo crear una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola.</span><span class="sxs-lookup"><span data-stu-id="a69a6-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="a69a6-110">[Ejemplo de Host04](./host04-sample.md) En este ejemplo se muestra cómo crear una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola.</span><span class="sxs-lookup"><span data-stu-id="a69a6-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="a69a6-111">Esta aplicación host también permite mostrar avisos para que el usuario pueda especificar varias opciones.</span><span class="sxs-lookup"><span data-stu-id="a69a6-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="a69a6-112">[Ejemplo de Host05](./host05-sample.md) En este ejemplo se muestra cómo crear una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola.</span><span class="sxs-lookup"><span data-stu-id="a69a6-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="a69a6-113">Esta aplicación host también admite llamadas a equipos remotos mediante los cmdlets [Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) y [Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) .</span><span class="sxs-lookup"><span data-stu-id="a69a6-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="a69a6-114">[Ejemplo de Host06](./host06-sample.md) En este ejemplo se muestra cómo crear una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola.</span><span class="sxs-lookup"><span data-stu-id="a69a6-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="a69a6-115">Además, este ejemplo utiliza las API de Tokenizer para especificar el color del texto que el usuario ha escrito.</span><span class="sxs-lookup"><span data-stu-id="a69a6-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="a69a6-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="a69a6-116">See Also</span></span>
