---
ms.date: 06/12/2018
keywords: wmf,powershell,setup
title: Windows Management Framework (WMF)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36943615"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) proporciona una interfaz de administración coherente para Windows. WMF proporciona una manera óptima de administrar varias versiones de cliente de Windows y de Windows Server. Los paquetes de instalador de WMF contienen actualizaciones para la funcionalidad de administración y están disponibles para versiones anteriores de Windows.

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

|Versión de sistema operativo  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2016       |Se envía en la caja|            |            |             |            |
|Windows 10                |Se envía en la caja|Se envía en la caja|            |             |            |
|Windows Server 2012 R2    |Sí         |Sí         |Se envía en la caja|             |            |
|Windows 8.1               |Sí         |Sí         |Se envía en la caja|             |            |
|Windows Server 2012       |Sí         |Sí         |Sí         |Se envía en la caja |            |
|Windows 8                 |            |            |            |Se envía en la caja |            |
|Windows Server 2008 R2 SP1|Sí         |Sí         |Sí         |Sí          |Se envía en la caja|
|Windows 7 SP1             |Sí         |Sí         |Sí         |Sí          |Se envía en la caja|
|Windows Server 2008 SP2   |            |            |            |Sí          |Sí         |
|Windows Vista             |            |            |            |             |Sí         |
|Windows Server 2003       |            |            |            |             |Sí         |
|Windows XP                |            |            |            |Sí          |            |

**Se envía en la caja**: las características de la versión especificada de WMF se han enviado en la versión indicada del cliente de Windows o Windows Server.

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
