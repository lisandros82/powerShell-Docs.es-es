---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabajar con impresoras
ms.openlocfilehash: 816388325cc3155f1dbd1bc15fc1736155216092
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030679"
---
# <a name="working-with-printers"></a>Trabajar con impresoras

Puede usar Windows PowerShell para administrar impresoras mediante WMI y el objeto COM WScript.Network de WSH. Usaremos una combinación de ambas herramientas para demostrar tareas específicas.

## <a name="listing-printer-connections"></a>Enumerar las conexiones de impresora

La manera más sencilla de enumerar las impresoras instaladas en un equipo es usar la clase WMI **Win32_Printer**:

```powershell
Get-WmiObject -Class Win32_Printer
```

También puede enumerar las impresoras mediante el objeto COM **WScript.Network** que suele usarse en los scripts de WSH:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Dado que este comando devuelve una colección de cadenas simple de nombres de puerto y nombres de dispositivo de impresión sin ninguna etiqueta distintiva, no es fácil de interpretar.

## <a name="adding-a-network-printer"></a>Agregar una impresora de red

Para agregar una nueva impresora de red, use **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Establecer una impresora predeterminada

Para usar WMI para establecer la impresora predeterminada, busque la impresora en la colección **Win32_Printer** y luego invoque el método **SetDefaultPrinter**:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** es un poco más fácil de usar, porque tiene un método **SetDefaultPrinter** que toma el nombre de la impresora como argumento:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Quitar una conexión de impresora

Para quitar una conexión de impresora, use el método **WScript.Network RemovePrinterConnection**:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
