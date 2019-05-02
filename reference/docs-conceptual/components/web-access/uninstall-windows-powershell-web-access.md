---
ms.date: 08/23/2017
keywords: powershell, cmdlet
title: desinstalación de Windows PowerShell Web Access
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058146"
---
# <a name="uninstall-windows-powershell-web-access"></a>Desinstalar Windows PowerShell Web Access

Actualizado: 24 de junio de 2013

Se aplica a: Windows Server 2012 R2, Windows Server 2012

Los pasos descritos en este tema quitan el sitio web de Windows PowerShell Web Access y la aplicación correspondiente del servidor de puerta de enlace en el que están instalados.

## <a name="notify-users"></a>Notificar a los usuarios

Antes de comenzar, notifique a los usuarios de la consola basada en web de que quitará el sitio web.

Al desinstalar Windows PowerShell Web Access, no se desinstalan IIS ni las demás características que se instalaron automáticamente porque eran necesarias para la ejecución de Windows PowerShell Web Access.
El proceso de desinstalación deja instaladas las características de las cuales dependía Windows PowerShell Web Access. Si necesita desinstalarlas, puede hacerlo de manera individual.

## <a name="recommended-quick-uninstallation"></a>Desinstalación (rápida) recomendada

Los procedimientos de esta sección le ayudarán a desinstalar:

- la aplicación web de Windows PowerShell Web Access; y
- la característica de Windows PowerShell Web Access

usando cmdlets de Windows PowerShell.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Paso 1: Eliminar la aplicación web usando cmdlets

1. Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell.

    -   En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas.

    -   En la pantalla **Inicio** de Windows, haga clic en **Windows PowerShell**.

2. Escriba `Uninstall-PswaWebApplication` y, luego, presione **ENTRAR**.
   1. Si ha especificado su propio nombre de sitio web personalizado, agregue el parámetro `-WebsiteName` a su comando y especifique el nombre del sitio web.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Si ha usado una aplicación web personalizada (no la aplicación predeterminada, **pswa**), agregue el parámetro `-WebApplicationName` a su comando y especifique el nombre de la aplicación web.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Si usa un certificado de prueba, agregue el parámetro `DeleteTestCertificate` al cmdlet, como se muestra en el siguiente ejemplo.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Paso 2: Desinstalar Windows PowerShell Web Access usando cmdlets

1. Realice una de las siguientes acciones para abrir una sesión de Windows PowerShell con derechos de usuario elevados. Si ya se ha abierto una sesión, vaya al siguiente paso.

    -   En el escritorio de Windows, haga clic con el botón derecho en **Windows PowerShell** en la barra de tareas y luego haga clic en **Ejecutar como administrador**.

    -   En la pantalla **Inicio** de Windows, haga clic con el botón derecho en **Windows PowerShell** y, luego, en **Ejecutar como administrador**.

1. Escriba lo siguiente y luego presione **Entrar**, donde *computer_name* representa un servidor remoto del que desea quitar Windows PowerShell Web Access. El parámetro `-Restart` reinicia automáticamente los servidores de destino, si es necesario para la eliminación.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Para quitar roles y características de un VHD sin conexión, debe agregar los parámetros `-ComputerName` y `-VHD` . El parámetro `-ComputerName` contiene el nombre del servidor en el que se montará el VHD y el parámetro `-VHD` contiene la ruta de acceso al archivo VHD en el servidor especificado.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Para comprobar la eliminación de Windows PowerShell Web Access una vez finalizada, abra la página **Todos los servidores** del Administrador del servidor, seleccione un servidor del cual se haya quitado la característica y visualice el icono **Roles y características** en la página del servidor seleccionado.

    También puede ejecutar el cmdlet `Get-WindowsFeature` destinado al servidor seleccionado (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) para ver una lista de los roles y características instalados en el servidor.

## <a name="custom-uninstallation"></a>Desinstalación personalizada

Los procedimientos de esta sección le ayudarán a desinstalar tanto la aplicación web como la característica de Windows PowerShell Web Access mediante el Asistente para quitar roles y características del Administrador del servidor y la consola de Administrador de IIS.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Paso 1: Eliminar la aplicación web mediante el Administrador de IIS


1. Abra la consola del Administrador de IIS mediante uno de los siguientes procedimientos. Si ya se ha abierto, vaya al siguiente paso.

    -   En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor. En el menú **Herramientas** del Administrador del servidor, haga clic en **Administrador de Internet Information Services (IIS)**.

    -   En la pantalla **Inicio** de Windows, escriba cualquier parte del nombre **Administrador de Internet Information Services (IIS)**. Haga clic en el acceso directo cuando se muestre en los resultados de **Aplicaciones**.

1. En el panel del árbol del Administrador de IIS, seleccione el sitio web que ejecuta la aplicación web de Windows PowerShell Web Access.

1. En el panel **Acciones**, en **Administrar sitio web**, haga clic en **Detener**.

1. En el panel del árbol, haga clic con el botón derecho en la aplicación web del sitio web que ejecuta la aplicación web de Windows PowerShell Web Access y, luego, haga clic en **Quitar**.

1. En el panel del árbol, seleccione **Grupos de aplicaciones**, seleccione la carpeta del grupo de aplicaciones de Windows PowerShell Web Access, haga clic en **Detener** en el panel **Acciones** y luego haga clic en **Quitar** en el panel de contenido.

1. Cierre el Administrador de IIS.

> ![Nota de advertencia](images/SecurityNote.jpeg)**Nota**:
>
> El certificado no se elimina durante la desinstalación.
>
> Si creó un certificado autofirmado o usó un certificado de prueba y desea quitarlo, hágalo en el Administrador de IIS.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Paso 2: Desinstalar Windows PowerShell Web Access mediante el Asistente para quitar roles y características

1. Si ya se ha abierto el Administrador del servidor, vaya al siguiente paso. Si todavía no se ha abierto el Administrador del servidor, ábralo mediante una de las siguientes acciones.

    -   En el escritorio de Windows, haga clic en **Administrador del servidor** en la barra de tareas de Windows para iniciar el Administrador del servidor.

    -   En la pantalla **Inicio** de Windows, haga clic en **Administrador del servidor**.

1. En el menú **Administrar**, haga clic en **Quitar roles y funciones**.

1. En la página **Seleccionar servidor de destino**, seleccione el servidor o VHD sin conexión del cual desea quitar la característica. Para seleccionar un VHD sin conexión, primero seleccione el servidor en el que montará el VHD y después seleccione el archivo VHD. Una vez seleccionado el servidor de destino, haga clic en **Siguiente**.

1. Vuelva a hacer clic en **Siguiente** para ir directamente a la página **Quitar características**.

1. Desactive la casilla **Windows PowerShell Web Access** y luego haga clic en **Siguiente**.

1. En la página **Confirmar selecciones de eliminación**, haga clic en **Quitar**.

## <a name="see-also"></a>Véase también

- [Instalación y uso de Windows PowerShell Web Access](install-and-use-windows-powershell-web-access.md)
- [Ayuda del Administrador de IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)