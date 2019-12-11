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
# <a name="working-with-printers"></a><span data-ttu-id="f3d8f-103">Trabajar con impresoras</span><span class="sxs-lookup"><span data-stu-id="f3d8f-103">Working with Printers</span></span>

<span data-ttu-id="f3d8f-104">Puede usar Windows PowerShell para administrar impresoras mediante WMI y el objeto COM WScript.Network de WSH.</span><span class="sxs-lookup"><span data-stu-id="f3d8f-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="f3d8f-105">Usaremos una combinación de ambas herramientas para demostrar tareas específicas.</span><span class="sxs-lookup"><span data-stu-id="f3d8f-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="f3d8f-106">Enumerar las conexiones de impresora</span><span class="sxs-lookup"><span data-stu-id="f3d8f-106">Listing Printer Connections</span></span>

<span data-ttu-id="f3d8f-107">La manera más sencilla de enumerar las impresoras instaladas en un equipo es usar la clase WMI **Win32_Printer**:</span><span class="sxs-lookup"><span data-stu-id="f3d8f-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer
```

<span data-ttu-id="f3d8f-108">También puede enumerar las impresoras mediante el objeto COM **WScript.Network** que suele usarse en los scripts de WSH:</span><span class="sxs-lookup"><span data-stu-id="f3d8f-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="f3d8f-109">Dado que este comando devuelve una colección de cadenas simple de nombres de puerto y nombres de dispositivo de impresión sin ninguna etiqueta distintiva, no es fácil de interpretar.</span><span class="sxs-lookup"><span data-stu-id="f3d8f-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="f3d8f-110">Agregar una impresora de red</span><span class="sxs-lookup"><span data-stu-id="f3d8f-110">Adding a Network Printer</span></span>

<span data-ttu-id="f3d8f-111">Para agregar una nueva impresora de red, use **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="f3d8f-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="f3d8f-112">Establecer una impresora predeterminada</span><span class="sxs-lookup"><span data-stu-id="f3d8f-112">Setting a Default Printer</span></span>

<span data-ttu-id="f3d8f-113">Para usar WMI para establecer la impresora predeterminada, busque la impresora en la colección **Win32_Printer** y luego invoque el método **SetDefaultPrinter**:</span><span class="sxs-lookup"><span data-stu-id="f3d8f-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="f3d8f-114">**WScript.Network** es un poco más fácil de usar, porque tiene un método **SetDefaultPrinter** que toma el nombre de la impresora como argumento:</span><span class="sxs-lookup"><span data-stu-id="f3d8f-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="f3d8f-115">Quitar una conexión de impresora</span><span class="sxs-lookup"><span data-stu-id="f3d8f-115">Removing a Printer Connection</span></span>

<span data-ttu-id="f3d8f-116">Para quitar una conexión de impresora, use el método **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="f3d8f-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
