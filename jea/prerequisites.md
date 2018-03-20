---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,security
title: Requisitos previos de JEA
ms.openlocfilehash: e6ee16e34eb9f1f0b2f3601c1aa9e90ab4f785f1
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="prerequisites"></a>Requisitos previos

> Se aplica a: Windows PowerShell 5.0

Just Enough Administration es una característica incluida con Windows PowerShell 5.0 y versiones posteriores.
En este tema, se describen los requisitos previos que se deben cumplir para empezar a usar JEA.

## <a name="install-jea"></a>Instalar JEA

JEA está disponible con Windows PowerShell 5.0 y versiones posteriores, pero se recomienda que instale la versión más reciente de PowerShell disponible para su sistema para obtener la funcionalidad completa.
En la tabla siguiente, se describe la disponibilidad de JEA en Windows Server:

Sistema operativo de servidor   | Disponibilidad de JEA
--------------------------|--------------------------------
Windows Server 2016       | Preinstalado
Windows Server 2012 R2    | Funcionalidad completa con WMF 5.1
Windows Server 2012       | Funcionalidad completa con WMF 5.1
Windows Server 2008 R2    | Funcionalidad reducida<sup>1</sup> con WMF 5.1

También puede usar JEA en el equipo de casa o del trabajo:

Sistema operativo de cliente   | Disponibilidad de JEA
--------------------------|-----------------------------------------------------
Windows 10 1607+          | Preinstalado
Windows 10 1603, 1511     | Preinstalado, con funcionalidad reducida<sup>2</sup>
Windows 10 1507           | No disponible
Windows 8, 8.1            | Funcionalidad completa con WMF 5.1
Windows 7                 | Funcionalidad reducida<sup>1</sup> con WMF 5.1

<sup>1</sup> JEA no se puede configurar para usar cuentas de servicio administradas de grupo en Windows Server 2008 R2 o Windows 7.
Las cuentas virtuales y otras características de JEA *sí* se admiten.

<sup>2</sup> Las versiones 1511 y 1603 de Windows 10 no admiten las siguientes características de JEA: ejecución como una cuenta de servicio administrada de grupo, reglas de acceso condicional en configuraciones de sesión, la unidad de usuario y concesión de acceso a cuentas de usuario locales.
Para obtener compatibilidad con estas características, actualice Windows a la versión 1607 (actualización de aniversario) o a una versión superior.

### <a name="check-which-version-of-powershell-is-installed"></a>Comprobar qué versión de PowerShell está instalada

Para comprobar qué versión de PowerShell está instalada en el sistema, compruebe la variable `$PSVersionTable` en un símbolo del sistema de Windows PowerShell.

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

Está listo para usar JEA si la versión *principal* es igual o superior a **5**.
Para obtener la mejor experiencia y tener acceso a todas las características más recientes, se recomienda que actualice a la versión de PowerShell **5.1** cuando sea posible.

### <a name="install-windows-management-framework"></a>Instalar Windows Management Framework

Si ejecuta una versión anterior de PowerShell, deberá actualizar el sistema con la última actualización de Windows Management Framework (WMF).
Los paquetes de actualización y un vínculo a las notas de la versión de WMF más recientes están disponibles en el [Centro de descarga](https://aka.ms/WMF5).

Se recomienda encarecidamente que pruebe la compatibilidad de la carga de trabajo con WMF antes de actualizar todos los servidores.

Los usuarios de Windows 10 deben instalar las actualizaciones más recientes de las características para obtener la versión actual de Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Habilitar Comunicación remota con PowerShell

La comunicación remota de PowerShell proporciona la base sobre la que se compila JEA.
Por tanto, es necesario garantizar que la comunicación remota de PowerShell está habilitada y [adecuadamente protegida](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) en su sistema antes de poder usar JEA.

La comunicación remota de PowerShell está habilitada de manera predeterminada en Windows Server 2012, 2012 R2 y 2016.
Puede habilitar la comunicación remota de PowerShell si ejecuta el siguiente comando en una ventana de PowerShell con privilegios elevados.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Habilitar el registro de bloques de script y módulos de PowerShell (opcional)

En los siguientes pasos se habilita el registro para todas las acciones de PowerShell del sistema.
El registro de módulos de PowerShell no es necesario para JEA, pero se recomienda encarecidamente que lo active para asegurarse de que los comandos que ejecutan los usuarios se registran en una ubicación central.

Puede configurar la directiva de registro de módulos de PowerShell mediante la directiva de grupo.

1. Abra el Editor de directivas de grupo local en una estación de trabajo o un objeto de directiva de grupo en la consola de administración de directivas de grupo en un controlador de dominio de Active Directory.
2. Vaya a **Configuración del equipo\\Plantillas administrativas\\Componentes de Windows\\Windows PowerShell**.
3. Haga doble clic en **Activar registro de módulos**.
4. Haga clic en **Habilitado**.
5. En la sección Opciones, haga clic en **Mostrar** junto a Nombres de módulos.
6. Escriba "**\***" en la ventana emergente. Esto indica a PowerShell que registre los comandos de todos los módulos.
7. Haga clic en **Aceptar** para establecer la directiva.
8. Haga doble clic en **Activar el registro de bloque de script de PowerShell**.
9. Haga clic en **Habilitado**.
10. Haga clic en **Aceptar** para establecer la directiva.
11. (Solo en equipos unidos a un dominio) Ejecute **gpupdate** o espere a que la directiva de grupo procese la directiva actualizada y aplique la configuración.

También puede habilitar la transcripción de PowerShell de todo el sistema a través de la directiva de grupo.

## <a name="next-steps"></a>Pasos siguientes

- [Crear un archivo de funcionalidad de rol](role-capabilities.md)
- [Crear un archivo de configuración de sesión](session-configurations.md)

## <a name="see-also"></a>Vea también

- [Información adicional sobre la seguridad de WinRM y comunicación remota de PowerShell](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [Entrada de blog sobre seguridad de *PowerShell ♥ the Blue Team*](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

