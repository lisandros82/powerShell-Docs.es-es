---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Finalidad del modelo de objetos de scripting de Windows PowerShell ISE
ms.technology: powershell
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 079b23ca1338fdb888e13cc187e9498a141916aa
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Finalidad del modelo de objetos de scripting de Windows PowerShell ISE
  Los objetos están asociados con la forma y la función de Windows PowerShell Integrated Scripting Environment (ISE). La referencia del modelo de objeto proporciona detalles sobre los métodos y las propiedades de los miembros que estos objetos exponen. Se proporcionan ejemplos que muestran cómo puede utilizar scripts para acceder directamente a estos métodos y propiedades. El modelo de objetos de scripting facilita el siguiente intervalo de tareas.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Personalización de la apariencia de Windows PowerShell ISE
 Puede utilizar el modelo de objetos para modificar las opciones y la configuración de la aplicación. Por ejemplo, puede modificarlas como sigue:

-   Puede cambiar el color de los errores, las advertencias, los resultados detallados y los resultados de depuración.

-   Puede obtener o establecer los colores de fondo del panel de comandos, del panel de resultados y del panel de scripts.

-   Puede definir el color de primer plano del panel de resultados.

-   Puede establecer el nombre y el tamaño de la fuente para Windows PowerShell ISE.

-   Puede configurar las advertencias. Esta configuración incluye advertencias que se emiten cuando se abre un archivo en varias pestañas de PowerShell o cuando se ejecuta un script en el archivo antes de que se haya guardado el archivo.

-   Puede cambiar entre una vista en la que el panel de scripts y el panel de resultados se encuentran en paralelo y una vista en la que el panel de scripts está en la parte superior del panel de resultados. Puede acoplar el panel de comandos en la parte inferior o superior del panel de resultados.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Mejora de la funcionalidad de Windows PowerShell ISE
 Puede utilizar el modelo de objetos para mejorar la funcionalidad de Windows PowerShell ISE. Por ejemplo, puede:

-   Agregar y modificar la instancia del mismo Windows PowerShell ISE. Por ejemplo, para cambiar los menús, puede agregar nuevos elementos de menú y asignarlos a scripts.

-   Crear scripts que llevan a cabo algunas de las tareas que puede realizar mediante el uso de los botones y comandos de menú en Windows PowerShell ISE. Por ejemplo, puede agregar, quitar o seleccionar una pestaña de PowerShell.

-   Complementar tareas que se pueden realizar con el uso de botones y comandos de menú. Por ejemplo, puede cambiar el nombre de una pestaña de PowerShell.

-   Manipular los búferes de texto para el panel de comandos, el panel de resultados y el panel de scripts que están asociados a un archivo. Por ejemplo, puede:

    -   Obtener o establecer todo el texto.

    -   Obtener o establecer una selección de texto.

    -   Ejecutar un script o una parte seleccionada de un script.

    -   Desplazar una línea en la vista.

    -   Insertar texto en una posición de intercalación.

    -   Seleccionar un bloque de texto.

    -   Obtener el último número de línea.

-   Realizar operaciones de archivo. Por ejemplo, puede:

    -   Abrir un archivo, guardar un archivo o guardar un archivo con un nombre diferente.

    -   Determinar si un archivo ha cambiado desde que se guardó por última vez.

    -   Obtener el nombre de archivo.

    -   Seleccionar un archivo.

## <a name="automating-tasks"></a>Automatización de tareas
 Puede utilizar el modelo de objetos de scripting para crear métodos abreviados de teclado para operaciones frecuentes.

## <a name="see-also"></a>Véase también
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md) 
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
