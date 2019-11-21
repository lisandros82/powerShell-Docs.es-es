---
title: Descripción de la codificación de archivo en VSCode y PowerShell
description: Configuración de la codificación de archivo en VSCode y PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 3283e1262c8eb26906429ecf195cfa0b122b330f
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117408"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Descripción de la codificación de archivo en VSCode y PowerShell

Al usar VS Code para crear y editar scripts de PowerShell, es importante que los archivos se guarden con el formato de codificación de caracteres correcto.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>¿Qué es la codificación de archivo y por qué es importante?

VSCode administra la interfaz entre una entrada manual de cadenas de caracteres en un búfer y la lectura/escritura de bloques de bytes en el sistema de archivos. Cuando VSCode guarda un archivo, usa una codificación de texto para decidir en qué bytes se convierte cada carácter.

De forma similar, cuando PowerShell ejecuta un script debe convertir los bytes de un archivo a caracteres para reconstruir el archivo en un programa de PowerShell. Dado que VSCode escribe el archivo y PowerShell lee el archivo, deben usar el mismo sistema de codificación. Este proceso de análisis de un script de PowerShell es: *bytes* -> *caracteres* -> *tokens* -> *árbol de sintaxis abstracta* -> *ejecución*.

VSCode y PowerShell se instalan con una configuración de codificación predeterminada sensible. Sin embargo, la codificación predeterminada usada por PowerShell ha cambiado con la publicación de PowerShell Core (versión 6.x). Para garantizar que no tiene problemas con el uso de PowerShell o la extensión de PowerShell en VSCode, debe configurar sus opciones de VSCode y PowerShell correctamente.

## <a name="common-causes-of-encoding-issues"></a>Causas comunes de problemas de codificación

Se producen problemas de codificación cuando la codificación de VSCode o el archivo de script no coincide con la codificación esperada de PowerShell. No hay ninguna forma de que PowerShell determine automáticamente la codificación del archivo.

Es más probable tener problemas de codificación cuando se usan caracteres que no están en el [juego de caracteres ASCII de 7 bits](https://ascii.cl/). Por ejemplo:

- Caracteres que no son letras extendidos, como guion largo (`—`), espacio de no separación (` `) o comilla doble izquierda (`“`)
- Caracteres latinos acentuados (`É`, `ü`)
- Caracteres no latinos; por ejemplo, cirílico (`Д`, `Ц`)
- Caracteres de CJK (`本`, `화`, `が`)

Algunas causas comunes de problemas de codificación son las siguientes:

- Las codificaciones de VSCode y PowerShell no han cambiado respecto a sus valores predeterminados. Para PowerShell 5.1 y versiones posteriores, el valor predeterminado de codificación es diferente del de VSCode.
- Otro editor ha abierto y sobrescrito el archivo en una nueva codificación. Esto suele ocurrir con el ISE.
- El archivo se incorpora al control de código fuente en una codificación distinta a la que VSCode o PowerShell esperaba. Esto puede ocurrir cuando los colaboradores usan editores con distintas configuraciones de codificación.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Procedimiento para saber si tiene problemas de codificación

Los errores de codificación, a menudo, se presentan como errores de análisis en los scripts. Si encuentra secuencias de caracteres extraños en su script, éste puede ser el problema. En el ejemplo siguiente, un guión corto (`–`) aparece como los caracteres `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Este problema se produce porque VSCode codifica el carácter `–` en UTF-8 como los bytes `0xE2 0x80 0x93`.
Cuando estos bytes se descodifican como Windows-1252, se interpretan como los caracteres `â€“`.

Entre algunas secuencias de caracteres extraños que podría ver se incluyen:

<!-- markdownlint-disable MD038 -->
- `â€“` en lugar de `–`
- `â€”` en lugar de `—`
- `Ã„2` en lugar de `Ä`
- `Â` en lugar de ` ` (un espacio de no separación)
- `Ã©` en lugar de `é`
<!-- markdownlint-enable MD038 -->

Esta [referencia](https://www.i18nqa.com/debug/utf8-debug.html) práctica detalla los patrones comunes que indican un problema de codificación UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>De qué forma la extensión de PowerShell en VSCode interactúa con las codificaciones

La extensión de PowerShell interactúa con los scripts de varias maneras:

1. Cuando los scripts se editan en VSCode, el contenido lo envía VSCode a la extensión. El [protocolo de servidor de lenguaje][] obliga a que este contenido se transfiera en UTF-8. Por lo tanto, no es posible que la extensión obtenga la codificación incorrecta.
2. Cuando los scripts se ejecutan directamente en la consola integrada, se leen desde el archivo de PowerShell directamente. Si la codificación de PowerShell difiere de la de VSCode, es posible que algo no funcione bien.
3. Cuando un script que está abierto en VSCode hace referencia a otro script que no está abierto en VSCode, la extensión pasa de nuevo a cargar el contenido del script desde el sistema de archivos. La extensión de PowerShell tiene como valor predeterminado la codificación UTF-8, pero usa la detección de [marca BOM][] para seleccionar la codificación correcta.

El problema se produce cuando se asume la codificación de formatos sin BOM (como [UTF-8][] sin BOM y [Windows-1252][]).
La extensión de PowerShell tiene como valor predeterminado UTF-8. La extensión no puede cambiar la configuración de codificación de VSCode.
Para obtener más información, vea el [problema #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Elección de la codificación correcta

Las aplicaciones y los sistemas distintos pueden utilizar codificaciones diferentes:

- En .NET Standard, en la web y en el entorno Linux, UTF-8 es ahora la codificación dominante.
- Muchas aplicaciones de .NET Framework usan [UTF-16][]. Por motivos históricos, a veces recibe la denominación de "Unicode", un término que ahora hace referencia a un amplio [estándar](https://en.wikipedia.org/wiki/Unicode) que incluye tanto UTF-8 como UTF-16.
- En Windows, muchas aplicaciones nativas anteriores a Unicode siguen usando Windows-1252 de forma predeterminada.

Las codificaciones Unicode también tienen el concepto de una marca BOM. Las BOM se producen al principio del texto para indicar a un descodificador la codificación que está usando el texto. Para las codificaciones multibyte, la BOM también indica la marca [endianness](https://en.wikipedia.org/wiki/Endianness) de la codificación. Las BOM están diseñadas para ser bytes que rara vez se producen en texto no Unicode, permitiendo una estimación razonable de que el texto es Unicode cuando hay una BOM.

Las BOM son opcionales y su adopción no es tan popular en los entornos Linux, porque se utiliza de forma generalizada una convención dependiente de UTF-8. La mayoría de las aplicaciones Linux dan por supuesto que la entrada de texto está codificada en UTF-8. Si bien muchas aplicaciones Linux reconocen y tratan correctamente una BOM, algunas no lo hacen y esto provoca anomalías en el texto manipulado con esas aplicaciones.

**Por lo tanto**:

- Si trabaja principalmente con aplicaciones Windows y Windows PowerShell, es preferible una codificación como UTF-8 con BOM o UTF-16.
- Si trabaja en varias plataformas, es preferible UTF-8 con BOM.
- Si trabaja principalmente en contextos asociados a Linux, es preferible UTF-8 sin BOM.
- Windows-1252 y Latín-1 son básicamente codificaciones heredadas que deben evitarse en la medida de lo posible.
  Sin embargo, algunas aplicaciones más antiguas de Windows pueden dependen de ellas.
- También merece la pena mencionar que la firma de scripts [depende de la codificación](https://github.com/PowerShell/PowerShell/issues/3466), lo cual significa que un tras cambio de codificación en un script firmado será necesario volver a firmar.

## <a name="configuring-vscode"></a>Configuración de VSCode

La codificación predeterminada de VSCode es UTF-8 sin BOM.

Para establecer la [codificación de VSCode][], vaya a la configuración de VSCode (<kbd>Ctrl</kbd>+<kbd>,</kbd>) y establezca el ajuste `"files.encoding"`:

```json
"files.encoding": "utf8bom"
```

Algunos valores posibles son:

- `utf8`: [UTF-8] sin BOM
- `utf8bom`: [UTF-8] con BOM
- `utf16le`: [UTF-16] little endian
- `utf16be`: [UTF-16] big endian
- `windows1252`: [Windows-1252]

Debe obtener una lista desplegable para esto en la vista de la interfaz gráfica de usuario, o los resultados de ello en la vista de JSON.

También puede agregar lo siguiente para detectar automáticamente la codificación, cuando sea posible:

```json
"files.autoGuessEncoding": true
```

Si no desea que estos ajustes afecten a todos los tipos de archivos, VSCode también permite configuraciones por idioma. Cree un ajuste específico del lenguaje colocando los ajustes en un campo `[<language-name>]`. Por ejemplo:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configuración de PowerShell

La codificación predeterminada de PowerShell varía en función de la versión:

- En PowerShell 6 +, la codificación predeterminada es UTF-8 sin BOM en todas las plataformas.
- En Windows PowerShell, la codificación predeterminada es normalmente Windows 1252, una extensión de [latin-1][], también conocida como ISO 8859-1.

En PowerShell 5+ puede encontrar la codificación predeterminada con esto:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

El siguiente [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) puede usarse para determinar la codificación que la sesión de PowerShell infiere para un script sin una BOM.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

Es posible configurar PowerShell para que use una codificación determinada, de forma más general mediante la configuración del perfil. Vea los artículos siguientes:

- [Respuesta sobre la codificación de PowerShell en StackOverflow](https://stackoverflow.com/a/40098904), de [@mklement0].
- [Entrada de blog sobre cómo tratar la entrada UTF-8 sin BOM en PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/), de [@rkeithhill].

No es posible obligar a PowerShell a usar una codificación de entrada específica. PowerShell 5.1 y versiones posteriores, de forma predeterminada, aplican la codificación Windows-1252 cuando no hay ninguna BOM. Por motivos de interoperabilidad, es mejor guardar los scripts en un formato Unicode con una BOM.

> [!IMPORTANT]
> Cualquier otra herramienta que tenga y entre en contacto con scripts de PowerShell puede verse afectada por sus opciones de codificación o puede volver a codificar los scripts a otra codificación.

### <a name="existing-scripts"></a>Scripts existentes

Es posible que los scripts que ya se encuentran en el sistema de archivos deban volver a codificarse a la nueva codificación elegida. En la barra inferior de VSCode, verá la etiqueta UTF-8. Haga clic en ella para abrir la barra de acciones y seleccione **Guardar con codificación**. Ahora puede elegir una codificación de nueva para ese archivo. Vea la información acerca de la [codificación de VSCode][] para obtener instrucciones completas.

Si necesita volver a codificar varios archivos, puede usar el siguiente script:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>El entorno de scripting integrado (ISE) de PowerShell

Si también edita scripts con PowerShell ISE, deberá sincronizar la configuración de codificación allí.

El ISE debe respetar una BOM, pero también es posible usar el reflejo para [establecer la codificación](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Tenga en cuenta que esto no se mantiene entre los inicios.

### <a name="source-control-software"></a>Software de control de código fuente

Algunas herramientas de control de código fuente, como GIT, ignoran las codificaciones; GIT simplemente realiza un seguimiento de los bytes.
Otras, como Azure DevOps o Mercurial, puede que no. Existen también algunas herramientas basadas en GIT que se basan en la descodificación de texto.

Cuando esto sucede, asegúrese de llevar a cabo lo siguiente:

- Configure la codificación de texto en el control de código fuente para que coincida con la configuración de VSCode.
- Asegúrese de que todos los archivos se incorporen al control de código fuente en la codificación adecuada.
- Sea precavido con los cambios en la codificación que se reciben a través del control de código fuente. Una señal clave de esto son unas diferencias que indican la presencia de cambios pero donde nada parece haber cambiado (porque los bytes han cambiado, pero los caracteres no).

### <a name="collaborators-environments"></a>Entornos de colaboradores

Como paso previo a la configuración del control de código fuente, asegúrese de que los colaboradores en cualquier archivo que comparta no tengan ninguna opción que reemplace la codificación volviendo a codificar los archivos de PowerShell.

### <a name="other-programs"></a>Otros programas

Cualquier otro programa que lea o escriba un script de PowerShell puede volver a codificarlo.

Ejemplos:

- Uso del Portapapeles para copiar y pegar un script. Esto es habitual en escenarios como:
  - Copiar un script en una máquina virtual
  - Copiar un script fuera de un correo electrónico o una página web
  - Copiar un script dentro o fuera de un documento de Microsoft Word o PowerPoint
- Otros editores de texto, como:
  - Notepad
  - vim
  - Cualquier otro editor de scripts de PowerShell
- Utilidades de edición de texto, como:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operadores de redirección de PowerShell, como `>` y `>>`
  - `sed`/`awk`
- Programas de transferencia de archivos, como:
  - Un explorador web, al descargar scripts
  - Un recurso compartido de archivos

Algunas de estas herramientas manejan bytes en lugar de texto, pero otros ofrecen configuraciones de codificación. En los casos en que deba configurar una codificación, tendrá que hacer la misma codificación que su editor, para evitar problemas.

## <a name="other-resources-on-encoding-in-powershell"></a>Otros recursos sobre la codificación en PowerShell

Hay algunas otras publicaciones interesantes sobre la codificación y la configuración de la codificación en PowerShell, que vale la pena leer:

- [Resumen sobre la codificación de PowerShell en StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8), de [@mklement0]
- Problemas anteriores abiertos en vscode-PowerShell para los problemas de codificación:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [El clásico informe de *Joel on Software* acerca de Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Codificación en .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca BOM]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de servidor de lenguaje]: https://microsoft.github.io/language-server-protocol/
[codificación de VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
