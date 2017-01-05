---
title: Windows Management Framework (WMF)
ms.date: 2016-12-07
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: b652613561655c4cbd63342b0fcc495195f83a80
ms.sourcegitcommit: b88151841dd44c8ee9296d0855d8b322cbf16076
translationtype: HT
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) es el mecanismo de entrega que proporciona una interfaz de administración coherente entre las distintas versiones de Windows y Windows Server.
Con la instalación de WMF, los clientes consiguen una manera de poder operar en diferentes sistemas operativos del entorno sin problemas.
WMF hace que las actualizaciones de la funcionalidad de administración, de una versión determinada de Windows y Windows Server, estén disponibles para su instalación en las versiones inferiores (normalmente, en 2 versiones inferiores) de Windows y Windows Server.

La instalación de WMF permite agregar o actualizar las características siguientes:

- Windows PowerShell
- Configuración de estado deseado (DSC) de Windows PowerShell
- Windows PowerShell Integrated Script Environment (ISE)
- Administración remota de Windows (WinRM)
- Windows Management Instrumentation (WMI)
- Windows PowerShell Web Services (Extensión IIS Management OData)
- Registro de inventario de software (SIL)
- Proveedor de CIM del administrador del servidor

## <a name="wmf-release-notes"></a>Notas de la versión WMF

Para más información acerca de las diversas mejoras en PowerShell y en otros componentes de un determinado WMF, consulte los vínculos siguientes para revisar las notas de la versión:

- [WMF 5.1 (versión preliminar)](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)

## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilidad WMF entre sistemas operativos Windows

| Versión de sistema operativo | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Se envía en la caja |  |  |  |  |
| Windows 10 | Se envía en la caja | Se envía en la caja  | | | |  
| Windows Server 2012 R2| Sí | Sí | Se envía en la caja |  |  |
| Windows 8.1 | Sí | Sí |  Se envía en la caja |  |  |
| Windows Server 2012 | Sí | Sí | Sí |  Se envía en la caja | |
| Windows 8 |  |  |  | Se envía en la caja | |
| Windows Server 2008 R2 SP1 | Sí | Sí | Sí |  Sí| Se envía en la caja |
| Windows 7 SP1  | Sí | Sí | Sí | Sí | Se envía en la caja |
| Windows Server 2008 SP2 | | | | Sí | Sí |
| Windows Vista | | | | | Sí |
| Windows Server 2003| | | |  | Sí |
| Windows XP | | | |  | Sí |

**"Se envía en la caja"**: las características de `specified WMF` se han enviado en la versión indicada de Windows y Windows Server.
Por tanto, no hay que instalar `specified WMF` en las versiones indicadas de los sistemas operativos.
