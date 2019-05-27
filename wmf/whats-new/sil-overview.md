---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Registro de inventario de software (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855440"
---
# <a name="software-inventory-logging-sil"></a>Registro de inventario de software (SIL)

> [!IMPORTANT]
> Al instalar WMF 5.x en un servidor de Windows Server 2012 R2 que ya ejecuta SIL, es necesario ejecutar el cmdlet Start-SilLogging después de la instalación de WMF, ya que el proceso de instalación detendrá por error la característica Registro de inventario de software.

La característica Registro de inventario de software ayuda a reducir los costos operativos derivados de la obtención de información precisa sobre el software de Microsoft instalado de forma local en un servidor y, en especial, en numerosos servidores en un entorno de TI (suponiendo que esté instalado y se ejecute en dicho entorno). Siempre que haya uno configurado, puede reenviar estos datos a un servidor de agregación y recopilar los datos de registro en un mismo lugar mediante un proceso automático y uniforme.

Aunque también se pueden registrar datos de inventario de software con una consulta directa a cada equipo, la característica Registro de inventario de software puede, mediante una arquitectura de reenvío (a través de la red) que se inicia en cada servidor, superar los retos de detección de servidores típicos en muchos escenarios relativos al inventario y a la administración de activos de software. Registro de inventario de software usa SSL para proteger los datos que se reenvían a través de HTTPS a un servidor de agregación. Almacenar los datos en un mismo lugar facilita su análisis y manipulación, así como compartirlos cuando sea necesario.

Estos datos no se envían a Microsoft como parte de la funcionalidad de la característica. Solo el propietario con licencia del software del servidor y los administradores pueden hacer uso de los datos y de la funcionalidad del registro de inventario de software.

Para más información y documentación sobre los cmdlets de Registro de inventario de software, consulte [Administrar el Registro de inventario de software en Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
