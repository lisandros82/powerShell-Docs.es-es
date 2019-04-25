---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Obtener información de ayuda detallada
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: e58814f512aa2c5914f92f942cf2a4a76956ee20
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086534"
---
# <a name="getting-detailed-help-information"></a>Obtener información de ayuda detallada

PowerShell incluye temas de ayuda detallados que explican conceptos de PowerShell y el lenguaje de PowerShell. También hay artículos de Ayuda para cada cmdlet y proveedor, así como para muchas funciones y scripts.

Puede ver estos artículos de Ayuda en el símbolo del sistema o ver las versiones actualizadas más recientemente de estos artículos en la documentación en línea de [PowerShell](/powershell/scripting/overview).

## <a name="getting-help-for-cmdlets"></a>Obtención de ayuda para cmdlets

Para obtener ayuda acerca de los cmdlets de PowerShell, use el cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help). Por ejemplo, para obtener ayuda para el cmdlet `Get-ChildItem`, escriba:

```powershell
Get-Help Get-ChildItem
```

o

```powershell
Get-ChildItem -?
```

También puede obtener ayuda sobre el cmdlet Get-Help. Por ejemplo:

```powershell
Get-Help Get-Help
```

Para obtener una lista de todos los artículos de Ayuda de cmdlets de la sesión, escriba:

```powershell
Get-Help -Category Cmdlet
```

Para mostrar una página de cada artículo de Ayuda cada vez, use la función `help` o su alias `man`.
Por ejemplo, para mostrar la Ayuda acerca del cmdlet `Get-ChildItem`, escriba

```powershell
man Get-ChildItem
```

o

```powershell
help Get-ChildItem
```

Para mostrar información detallada, use el parámetro **Detailed** del cmdlet `Get-Help`. Por ejemplo, para obtener información detallada acerca del cmdlet `Get-ChildItem`, escriba:

```powershell
Get-Help Get-ChildItem -Detailed
```

Para mostrar todo el contenido del artículo de Ayuda, use el parámetro **Full** del cmdlet `Get-Help`. Por ejemplo, para mostrar todo el contenido del artículo de Ayuda para el cmdlet `Get-ChildItem`, escriba:

```powershell
Get-Help Get-ChildItem -Full
```

Para obtener ayuda detallada acerca de los parámetros de un cmdlet, use el parámetro **Parameter** del cmdlet `Get-Help`. Por ejemplo, para obtener ayuda detallada acerca de todos los parámetros del cmdlet `Get-ChildItem`, escriba:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Para mostrar solo los ejemplos de un artículo de Ayuda, use el parámetro **Examples** de `Get-Help`.
Por ejemplo, para mostrar solo los ejemplos del artículo de Ayuda para el cmdlet `Get-ChildItem`, escriba:

```powershell
Get-Help Get-ChildItem -Examples
```

Para obtener información sobre cómo escribir artículos de Ayuda para los cmdlets que escribe, consulte [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets) (Cómo escribir ayuda para cmdlet).

## <a name="getting-conceptual-help"></a>Obtención de ayuda conceptual

El cmdlet `Get-Help` también muestra información acerca de artículos conceptuales en PowerShell, incluidos los artículos sobre el lenguaje de PowerShell. Los artículos de Ayuda conceptual comienzan por el prefijo "about_", como about_line_editing. (Los nombres de artículos conceptuales deben especificarse en inglés, incluso en versiones no inglesas de PowerShell).

Para mostrar una lista de artículos conceptuales, escriba:

```powershell
Get-Help about_*
```

Para mostrar un artículo de Ayuda determinado, escriba el nombre del artículo, por ejemplo:

```powershell
Get-Help about_command_syntax
```

Los parámetros de `Get-Help`, como **Detailed**, **Parameter** y **Examples**, no tienen ningún efecto en la presentación de artículos de Ayuda conceptuales.

## <a name="getting-help-about-providers"></a>Obtención de ayuda acerca de los proveedores

El cmdlet `Get-Help` muestra información sobre los proveedores de PowerShell. Para obtener ayuda sobre un proveedor, escriba `Get-Help` seguido del nombre del proveedor. Por ejemplo, para obtener ayuda sobre el proveedor del Registro, escriba:

```powershell
Get-Help registry
```

Para obtener una lista de todos los artículos de Ayuda de proveedor de la sesión, escriba

```powershell
Get-Help -Category provider
```

Los parámetros de `Get-Help`, como **Detailed**, **Parameter** y **Examples**, no tienen ningún efecto en la presentación de artículos de Ayuda de proveedor.

## <a name="getting-help-about-scripts-and-functions"></a>Obtención de ayuda acerca de scripts y funciones

Muchos scripts y funciones de PowerShell tienen artículos de Ayuda. Use el cmdlet `Get-Help` para mostrar los artículos de Ayuda de scripts y funciones.

Para mostrar la Ayuda de una función, escriba `Get-Help` seguido del nombre de función. Por ejemplo, para obtener ayuda para la función `Disable-PSRemoting`, escriba:

```powershell
Get-Help Disable-PSRemoting
```

Para mostrar la Ayuda de un script, escriba la ruta de acceso al archivo de script. Si el script no está en una ruta de acceso mencionada en la variable de entorno Path, debe utilizar la ruta de acceso completa.

Por ejemplo, si tiene un script denominado "TestScript.ps1" en el directorio C:\\PS-Test, para mostrar el artículo de Ayuda del script, escriba:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

Los parámetros que están diseñados para mostrar la ayuda del cmdlet también funcionan para la ayuda del script y de la función. Sin embargo, la ayuda para las funciones y los scripts no se muestra cuando se ejecuta `Get-Help *`.

Para obtener información sobre cómo escribir artículos de ayuda para sus funciones y scripts, consulte los siguientes artículos:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Obtención de ayuda en línea

La visualización de los artículos de la Ayuda en línea es una de las mejores maneras de obtener ayuda. Los artículos en línea son más fáciles de actualizar y proporcionan el contenido más actual.

Para obtener ayuda en línea, pruebe el parámetro **Online** del cmdlet `Get-Help`. Todos los artículos de Ayuda que vienen con PowerShell, como la Ayuda de proveedores y los artículos de Ayuda conceptual (Acerca de), están disponibles en línea en la documentación de [PowerShell](/powershell/scripting/powershell-scripting).

> [!NOTE]
> No se puede usar el parámetro **Online** con temas conceptuales (about_\*) ni artículos de Ayuda de proveedor.
> La ayuda en línea es opcional, por tanto no funciona para todos los cmdlets, funciones o scripts.

Por ejemplo, para obtener la versión en línea del tema de Ayuda sobre el cmdlet `Get-ChildItem`, escriba:

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell abre el artículo en el explorador predeterminado. Si se admite la Ayuda en línea para un artículo de Ayuda, también puede ver la dirección URL del artículo de Ayuda. La dirección URL aparece en la sección Vínculos relacionados de un artículo de Ayuda.

Por ejemplo, para ver la dirección URL de la versión en línea del cmdlet Add-Computer, escriba:

```powershell
Get-Help Add-Computer
```

A continuación, se muestra la primera línea de la sección Vínculos relacionados del artículo.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Para más información sobre cómo proporcionar soporte técnico en línea para los artículos de Ayuda, consulte [about_Comment_Based_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Vea también

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
