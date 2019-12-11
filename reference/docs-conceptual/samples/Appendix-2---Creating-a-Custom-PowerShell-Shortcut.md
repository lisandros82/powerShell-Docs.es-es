---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Apéndice 2 Crear un acceso directo de PowerShell personalizado
ms.openlocfilehash: 6f1a6a8187b1797103e3620b2cf9155978807ea5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030306"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Apéndice 2: Crear de un acceso directo de PowerShell personalizado

El siguiente procedimiento describe cómo crear un acceso directo a Windows PowerShell que tenga varias opciones prácticas personalizadas.

1. Crear un acceso directo que apunte a Powershell.exe.

2. Haga clic con el botón derecho en el acceso directo y, después, haga clic en **Propiedades**.

3. Haga clic en la pestaña **Opciones**.

4. En la sección **Editar opciones**, active la casilla **Edición rápida**.

    Esta configuración permite seleccionar texto en la ventana de la consola de Windows PowerShell arrastrando el botón izquierdo del ratón, así como copiar texto en el Portapapeles presionando ENTRAR o haciendo clic con el botón derecho.

5. En la sección **Editar opciones**, active la casilla **Modo de inserción**. Esta configuración permite hacer clic con el botón derecho en la ventana de la consola para pegar texto automáticamente desde el Portapapeles.

6. En la sección **Historial de comandos**, escriba o seleccione un número entre 1 y 999 en el cuadro **Tamaño del búfer**. Esta acción establece el número de comandos escritos que se mantendrán en el búfer de la consola.

7. En la sección **Historial de comandos**, active la casilla **Descartar duplicados antiguos** para eliminar los comandos repetidos del búfer de la consola.

8. Haga clic en la pestaña **Diseño**.

9. En la sección **Tamaño del búfer de pantalla** escriba un número entre 1 y 9999 en el cuadro **Alto**. El alto representa el número de líneas de salida que se almacenan en búfer. Este es el número máximo de líneas que se conservan para ver cuándo se desplaza por la ventana de la consola. Si este número es inferior al alto que se muestra en la sección **Tamaño de la ventana**, el alto del tamaño de la ventana se reducirá automáticamente al mismo valor.

10. En la sección **Tamaño de la ventana**, escriba un número entre 1 y 9999 para el ancho. Este representa el número de caracteres que se muestran en la ventana de la consola. El ancho predeterminado es 80 y el formato de salida de Windows PowerShell está diseñado para este ancho.

11. Si desea colocar la consola en un punto concreto del escritorio al abrirla, desactive la casilla **Dejar que el sistema ubique la ventana** en la sección **Posición de la ventana** y, luego, cambie los valores de los cuadros **Izquierda** y **Superior** de la sección **Posición de la ventana**.

12. Haga clic en **Aceptar**.
