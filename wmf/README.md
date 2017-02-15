---
title: Windows Management Framework (WMF)
ms.date: 2017-02-14
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 749dd8b19592cb5f40a5aed32d28edeb5cb2dfc9
ms.sourcegitcommit: bb2c52577a519c0599a0b3c961f749fe0df70a45
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

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

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
