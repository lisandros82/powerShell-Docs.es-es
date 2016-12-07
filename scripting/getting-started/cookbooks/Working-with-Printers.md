---
title: Trabajar con impresoras
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 2142d7ef1d1cc9b20ecc1ab35b9685817c838347
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="working-with-printers"></a>Trabajar con impresoras
Puede usar Windows PowerShell para administrar impresoras mediante WMI y el objeto COM WScript.Network de WSH. Usaremos una combinación de ambas herramientas para demostrar tareas específicas.

### <a name="listing-printer-connections"></a>Enumerar las conexiones de impresora
La manera más sencilla de enumerar las impresoras instaladas en un equipo es usar la clase WMI **Win32_Printer**:

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

También puede enumerar las impresoras mediante el objeto COM **WScript.Network** que suele usarse en los scripts de WSH:

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Dado que este comando devuelve una colección de cadenas simple de nombres de puerto y nombres de dispositivo de impresión sin ninguna etiqueta distintiva, no es fácil de interpretar.

### <a name="adding-a-network-printer"></a>Agregar una impresora de red
Para agregar una nueva impresora de red, use **WScript.Network**:

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Establecer una impresora predeterminada
Para usar WMI para establecer la impresora predeterminada, busque la impresora en la colección **Win32_Printer** y luego invoque el método **SetDefaultPrinter**:

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** es un poco más fácil de usar, porque tiene un método **SetDefaultPrinter** que toma el nombre de la impresora como argumento:

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Quitar una conexión de impresora
Para quitar una conexión de impresora, use el método **WScript.Network RemovePrinterConnection**:

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

