---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: Finalidad del modelo de objetos de scripting de Windows PowerShell ISE
ms.openlocfilehash: 1f48df112bd19297baa311116e79d3d7603d7c81
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736239"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Finalidad del modelo de objetos de scripting de Windows PowerShell ISE

Los objetos están asociados con la forma y la función de Windows PowerShell Integrated Scripting Environment (ISE). La referencia del modelo de objeto proporciona detalles sobre los métodos y las propiedades de los miembros que estos objetos exponen. Se proporcionan ejemplos que muestran cómo puede utilizar scripts para acceder directamente a estos métodos y propiedades. El modelo de objetos de scripting facilita el siguiente intervalo de tareas.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Personalización de la apariencia de Windows PowerShell ISE

Puede utilizar el modelo de objetos para modificar las opciones y la configuración de la aplicación. Por ejemplo, puede modificarlas como sigue:

- Cambie el color de los errores, las advertencias, los resultados detallados y los resultados de depuración.
- Obtenga o establezca los colores de fondo del panel de comandos, del panel de resultados y del panel de scripts.
- Establezca el color de primer plano del panel de resultados.
- Establezca el nombre y el tamaño de la fuente para Windows PowerShell ISE.
- Configure advertencias. Esta configuración incluye advertencias que se emiten cuando se abre un archivo en varias pestañas de PowerShell o cuando se ejecuta un script en el archivo antes de que se haya guardado el archivo.
- Cambie entre una vista en la que el panel de scripts y el panel de resultados se encuentran en paralelo y una vista en la que el panel de scripts está en la parte superior del panel de resultados.
- Acople el panel de comandos en la parte inferior o superior del panel de resultados.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Mejora de la funcionalidad de Windows PowerShell ISE

Puede utilizar el modelo de objetos para mejorar la funcionalidad de Windows PowerShell ISE. Por ejemplo, puede:

- Agregar y modificar la instancia del mismo Windows PowerShell ISE. Por ejemplo, para cambiar los menús, puede agregar nuevos elementos de menú y asignarlos a scripts.
- Crear scripts que llevan a cabo algunas de las tareas que puede realizar mediante el uso de los botones y comandos de menú en Windows PowerShell ISE. Por ejemplo, puede agregar, quitar o seleccionar una pestaña de PowerShell.
- Complementar tareas que se pueden realizar con el uso de botones y comandos de menú. Por ejemplo, puede cambiar el nombre de una pestaña de PowerShell.
- Manipular los búferes de texto para el panel de comandos, el panel de resultados y el panel de scripts que están asociados a un archivo. Por ejemplo, puede:
  - Obtener o establecer todo el texto.
  - Obtener o establecer una selección de texto.
  - Ejecutar un script o una parte seleccionada de un script.
  - Desplazar una línea en la vista.
  - Insertar texto en una posición de intercalación.
  - Seleccionar un bloque de texto.
  - Obtener el último número de línea.
- Realizar operaciones de archivo. Por ejemplo, puede:
  - Abrir un archivo, guardar un archivo o guardar un archivo con un nombre diferente.
  - Determinar si un archivo ha cambiado desde que se guardó por última vez.
  - Obtener el nombre de archivo.
  - Seleccionar un archivo.

## <a name="automating-tasks"></a>Automatización de tareas

Puede utilizar el modelo de objetos de scripting para crear métodos abreviados de teclado para operaciones frecuentes.

## <a name="see-also"></a>Consulte también

- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
