---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 306241bc5ec854c0e2ed835009a79b21fc249f14
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="known-issues-and-limitations"></a>Problemas y limitaciones conocidos

<a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a>Los accesos directos de PowerShell se interrumpen cuando se usan por primera vez
------------------------------------------------------------

**Resolución:** realice una de las acciones siguientes.

1.  Haga clic con el botón derecho en el acceso directo de PowerShell. Seleccione "Windows PowerShell" para iniciar en modo sin privilegios elevados.
2.  Haga clic con el botón derecho en el acceso directo de PowerShell. Haga clic en "Windows PowerShell" y seleccione "Ejecutar como administrador" para iniciar en modo con privilegios elevados.

Después de llevar a cabo cualquiera de las acciones anteriores, los accesos directos de PowerShell funcionarán. Estas acciones deben realizarse una sola vez.


<a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a>Los módulos de PowerShell y los recursos de DSC notifican errores sobre ExecutionPolicy en Windows 7
-------------------------------------------------------------------------------------
En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.

**Resolución:** establezca ExecutionPolicy en RemoteSigned. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):

```powershell
Set-ExecutionPolicy RemoteSigned
```

<a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a>La conexión a un punto de conexión de Exchange remoto antiguo causa un bloqueo
------------------------------------------------------------

El punto de conexión de Exchange le redirige a un nuevo punto de conexión. Hay un error en la lógica de redirección que causa un bloqueo.

**Resolución:** realice la conexión directamente al nuevo punto de conexión.


<a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a>La característica Registro de inventario de software se detiene erróneamente después de la instalación de WMF 5.0 en Windows Server 2012 R2
-------------------------------------------------------------------------------------------------------------

Al instalar WMF 5.0 en un sistema Windows Server 2012 R2 que ya ejecuta SIL, la característica Registro de inventario de software de detiene por error después de la instalación.

**Resolución:** ejecute el cmdlet Start-SilLogging después de la instalación de WMF, ya que el proceso de instalación detendrá por error la característica Registro de inventario de software.

<a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a>Get-ChildItem no funciona si -LiteralPath y –Recurse se usan juntos.
--------------------------------------------------------------------------

Si un nombre de directorio contiene un carácter comodín no válido, Get-ChildItem no producirá los resultados esperados si -LiteralPath y -Recurse se usan juntos.

**Resolución:** no es lo ideal, pero la solución actual es implementar la recursividad en el script en lugar de depender del cmdlet.


<a name="sysprep-fails-after-wmf-50-installation"></a>Se produce un error de Sysprep después de la instalación de WMF 5.0
----------------------------------------

Hay dos soluciones alternativas para este problema según la versión de Windows Server que se ejecute.

**Resolución:**
- Para sistemas que ejecutan **Windows Server 2008 R2**
  1. Abra Powershell como administrador.
  2. Ejecute el siguiente comando.

  ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
  ```
  3. Ejecute el comando y omita el error, tal como se espera.

  ```powershell
    Publish-SilData
   ```
  4. Elimine los archivos del directorio \Windows\System32\Logfiles\SIL\.

  ```powershell
    Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5. Instale todas las actualizaciones disponibles de Windows importantes y comience a utilizar Sysyprep con normalidad.

- Para sistemas que ejecutan **Windows Server 2012**
  1.    Después de instalar WMF 5.0 en el servidor para la preparación del sistema con Sysprep, inicie sesión como administrador.
  2.    Copie Generize.xml desde el directorio \Windows\System32\Sysprep\ActionFiles\ a una ubicación fuera del directorio de Windows, como C:\.
  3.    Abra la copia de Generalize.xml con el Bloc de notas.
  4.    Busque y quite el texto siguiente; hay que eliminar una instancia de cada caso (se encuentran casi al final del documento).

    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```

  5.    Guarde la copia modificada de Generalize.xml y cierre el archivo.
  6.    Abra una ventana del símbolo del sistema como administrador.
  7.    Ejecute el siguiente comando para adquirir la titularidad del archivo Generalize.xml en la carpeta system32:

    ```
    Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```

  8.    Ejecute el siguiente comando para establecer los permisos adecuados en el archivo:

    ```
    Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
    ```
      * Responda de manera afirmativa cuando se le solicite confirmación.
      * Tenga en cuenta que `<AdministratorUserName>` se debe reemplazar por el nombre de usuario administrador en el equipo. Por ejemplo, "Administrador".

  9.    Copie el archivo modificado que ha guardado en el directorio Sysprep; para ello, use el comando siguiente:

    ```
    xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
    ```
      * Responda de manera afirmativa para sobrescribir (tenga en cuenta que si no aparece ningún mensaje para sobrescribir, debe comprobar la ruta de acceso especificada).
      * Se supone que la copia modificada de Generalize.xml se ha copiado en C:\.

  10.   Generalize.xml se ha actualizado con la solución alternativa. Ejecute Sysprep con la opción de generalizar habilitada.