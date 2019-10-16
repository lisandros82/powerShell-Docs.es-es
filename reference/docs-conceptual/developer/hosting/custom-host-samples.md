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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367514"
---
# <a name="custom-host-samples"></a>Ejemplos de host personalizado

En esta sección se incluye código de ejemplo para escribir un host personalizado. Puede usar Microsoft Visual Studio para crear una aplicación de consola y, a continuación, copiar el código de los temas de esta sección en la aplicación host.

## <a name="in-this-section"></a>En esta sección

 [Ejemplo de Host01](./host01-sample.md) Este ejemplo muestra cómo implementar una aplicación host que usa un host personalizado básico.

 [Ejemplo de Host02](./host02-sample.md) En este ejemplo se muestra cómo escribir una aplicación host que usa el tiempo de ejecución de Windows PowerShell junto con una implementación de host personalizado. La aplicación host establece la referencia cultural del host en alemán, ejecuta el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) y muestra los resultados tal y como se verán con pwrsh. exe y, a continuación, imprime los datos y la hora actuales en alemán.

 [Ejemplo de Host03](./host03-sample.md) En este ejemplo se muestra cómo crear una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola.

 [Ejemplo de Host04](./host04-sample.md) En este ejemplo se muestra cómo crear una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola. Esta aplicación host también permite mostrar avisos para que el usuario pueda especificar varias opciones.

 [Ejemplo de Host05](./host05-sample.md) En este ejemplo se muestra cómo crear una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola. Esta aplicación host también admite llamadas a equipos remotos mediante los cmdlets [Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) y [Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) .

 [Ejemplo de Host06](./host06-sample.md) En este ejemplo se muestra cómo crear una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola. Además, este ejemplo utiliza las API de Tokenizer para especificar el color del texto que el usuario ha escrito.

## <a name="see-also"></a>Véase también
