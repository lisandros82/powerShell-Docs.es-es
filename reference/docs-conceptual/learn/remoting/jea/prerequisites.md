---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Requisitos previos de JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017816"
---
# <a name="prerequisites"></a>Requisitos previos

Just Enough Administration es una característica incluida en PowerShell 5.0 y versiones posteriores. En este artículo se describen los requisitos previos que se deben cumplir para empezar a usar JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Comprobar qué versión de PowerShell está instalada

Para comprobar qué versión de PowerShell está instalada en el sistema, compruebe la variable `$PSVersionTable` en un símbolo del sistema de Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA está disponible con PowerShell 5.0 y versiones posteriores. Para obtener la funcionalidad completa, se recomienda instalar la versión más reciente de PowerShell disponible para el sistema. En la tabla siguiente, se describe la disponibilidad de JEA en Windows Server:

| Sistema operativo de servidor |                Disponibilidad de JEA                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016+    | Preinstalado                                   |
| Windows Server 2012 R2  | Funcionalidad completa con WMF 5.1                |
| Windows Server 2012     | Funcionalidad completa con WMF 5.1                |
| Windows Server 2008 R2  | Funcionalidad reducida<sup>1</sup> con WMF 5.1 |

También puede usar JEA en el equipo de casa o del trabajo:

| Sistema operativo de cliente |                   Disponibilidad de JEA                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Preinstalado                                         |
| Windows 10 1603, 1511   | Preinstalado, con funcionalidad reducida<sup>2</sup> |
| Windows 10 1507         | No disponible                                        |
| Windows 8, 8.1          | Funcionalidad completa con WMF 5.1                      |
| Windows 7               | Funcionalidad reducida<sup>1</sup> con WMF 5.1       |

- <sup>1</sup> JEA no se puede configurar para usar cuentas de servicio administradas de grupo en Windows Server 2008 R2 o Windows 7. Las cuentas virtuales y otras características de JEA *sí* se admiten.

- <sup>2</sup> Las características de JEA siguientes no se admiten en las versiones 1511 y 1603 de Windows 10:

  - Ejecución como una cuenta de servicio administrada de grupo
  - Reglas de acceso condicional en configuraciones de sesión
  - Unidad de usuario
  - Concesión de acceso a cuentas de usuario locales

  Para obtener compatibilidad con estas características, actualice Windows a la versión 1607 (actualización de aniversario) o a una versión superior.

### <a name="install-windows-management-framework"></a>Instalar Windows Management Framework

Si ejecuta una versión anterior de PowerShell, es posible que tenga que actualizar el sistema con la actualización más reciente de Windows Management Framework (WMF). Para obtener más información, vea la documentación de [WMF](/powershell/wmf/overview).

Se recomienda probar la compatibilidad de la carga de trabajo con WMF antes de actualizar todos los servidores.

Los usuarios de Windows 10 deben instalar las actualizaciones más recientes de las características para obtener la versión actual de Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Habilitar Comunicación remota con PowerShell

La comunicación remota de PowerShell proporciona la base sobre la que se compila JEA. Es necesario garantizar que la comunicación remota de PowerShell está habilitada y protegida de forma adecuada antes de poder usar JEA. Para obtener más información, vea [Seguridad de WinRM](/powershell/scripting/learn/remoting/winrmsecurity).

La comunicación remota de PowerShell está habilitada de manera predeterminada en Windows Server 2012, 2012 R2 y 2016. Puede habilitar la comunicación remota de PowerShell si ejecuta el siguiente comando en una ventana de PowerShell con privilegios elevados.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Habilitar el registro de bloques de script y módulos de PowerShell (opcional)

En los siguientes pasos se habilita el registro para todas las acciones de PowerShell del sistema. El registro de módulos de PowerShell no es necesario para JEA, pero se recomienda activarlo para asegurarse de que los comandos que ejecutan los usuarios se registran en una ubicación central.

Puede configurar la directiva de registro de módulos de PowerShell mediante la directiva de grupo.

1. Abra el Editor de directivas de grupo local en una estación de trabajo o un objeto de directiva de grupo en la consola de administración de directivas de grupo en un controlador de dominio de Active Directory.
2. Vaya a **Configuración del equipo\\Plantillas administrativas\\Componentes de Windows\\Windows PowerShell**.
3. Haga doble clic en **Activar registro de módulos**.
4. Haga clic en **Habilitado**.
5. En la sección Opciones, haga clic en **Mostrar** junto a Nombres de módulos.
6. Escriba `*` en la ventana emergente para registrar comandos de todos los módulos.
7. Haga clic en **Aceptar** para establecer la directiva.
8. Haga doble clic en **Activar el registro de bloque de script de PowerShell**.
9. Haga clic en **Habilitado**.
10. Haga clic en **Aceptar** para establecer la directiva.
11. (Solo en equipos unidos a un dominio) Ejecute `gpupdate` o espere a que la directiva de grupo procese la directiva actualizada y aplique la configuración.

También puede habilitar la transcripción de PowerShell de todo el sistema a través de la directiva de grupo.

## <a name="next-steps"></a>Pasos siguientes

[Crear un archivo de funcionalidad de rol](role-capabilities.md)

[Crear un archivo de configuración de sesión](session-configurations.md)

## <a name="see-also"></a>Vea también

[Seguridad de WinRM](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ the Blue Team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
