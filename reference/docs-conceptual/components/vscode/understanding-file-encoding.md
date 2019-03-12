---
title: Descripción de la codificación de archivo en VSCode y PowerShell
description: Configurar la codificación del archivo en VSCode y PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 9cf445ebd0c2bb2dbdf4438f02dafe3df3a5d1e2
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429812"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Descripción de la codificación de archivo en VSCode y PowerShell

Al usar VS Code para crear y editar scripts de PowerShell, es importante que los archivos se guardan con el formato de codificación de caracteres correcto.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>¿Qué es la codificación de archivos y por qué es importante?

VSCode administra la interfaz entre humano al escribir cadenas de caracteres en un búfer y bloques de lectura/escritura de bytes en el sistema de archivos. Cuando VSCode guarda un archivo, usa una codificación para hacer esto de texto.

De forma similar, cuando PowerShell ejecuta una secuencia de comandos debe convertir los bytes en un archivo a caracteres para reconstruir el archivo en un programa de PowerShell. Dado que VSCode escribe el archivo y PowerShell lee el archivo, que necesitan usar el mismo sistema de codificación. Este proceso de análisis de un script de PowerShell es: *bytes* -> *caracteres* -> *tokens*  ->   *árbol de sintaxis abstracta* -> *ejecución*.

VSCode y PowerShell se instalan con una configuración de codificación predeterminado razonable. Sin embargo, la codificación predeterminada usando PowerShell ha cambiado con la versión de PowerShell Core (versión 6.x). Para asegurarse de que no tiene problemas con PowerShell o la extensión de PowerShell en VSCode, deberá establecer la configuración de VSCode y PowerShell correctamente.

## <a name="common-causes-of-encoding-issues"></a>Causas comunes de problemas de codificación

Problemas de codificación se producen cuando la codificación de VSCode o el archivo de script no coincide con la codificación esperada de PowerShell. No hay ninguna manera de PowerShell determinar automáticamente la codificación del archivo.

Es más probable de problemas de codificación cuando se usa caracteres no está en el [juego de caracteres ASCII de 7 bits](https://ascii.cl/). Por ejemplo:

- Acentuadas caracteres latinos (`É`, `ü`)
- Caracteres no latinos, como cirílico (`Д`, `Ц`)
- Han chino (`脚`, `本`)

Causas comunes de problemas de codificación son:

- Las codificaciones de VSCode y PowerShell no han cambiado de sus valores predeterminados. Para PowerShell 5.1 y, a continuación, el valor predeterminado de codificación es diferente de VSCode.
- Otro editor tiene abierto y sobrescribe el archivo en una nueva codificación. Esto suele ocurrir con el ISE.
- El archivo está desprotegido en el control de código fuente en una codificación que es diferente de qué VSCode o PowerShell espera. Esto puede ocurrir cuando colaboradores usan editores con distintas configuraciones de codificación.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Cómo saber si tiene problemas de codificación

Errores de codificación a menudo se presenten como analizar errores en los scripts. Si encuentra las secuencias de caracteres extraños en la secuencia de comandos, éste puede ser el problema. En el ejemplo siguiente, un guión corto (`–`) aparece como los caracteres `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Este problema se produce porque VSCode codifica el carácter `–` en UTF-8, como los bytes `0xE2 0x80 0x93`.
Cuando estos bytes se descodificación como Windows-1252, se interpretan como caracteres `â€“`.

Algunas secuencias de caracteres extraños que ve podría incluyen:

- `â€“` en lugar de `–`
- `â€”` en lugar de `—`
- `Ã„2` en lugar de `Ä`
- `Â` en lugar de ` ` (un espacio de no separación)
- `Ã©` en lugar de `é`

Este práctico [referencia](https://www.i18nqa.com/debug/utf8-debug.html) se enumeran los patrones comunes que indican un problema de codificación UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Cómo interactúa la extensión de PowerShell en VSCode con codificaciones

La extensión de PowerShell interactúa con las secuencias de comandos de varias maneras:

1. Cuando se editan scripts en VSCode, el contenido se envía con VSCode para la extensión. El [Protocolo de servidor de lenguaje][] obliga a que este contenido se transfiere en UTF-8. Por lo tanto, no es posible que la extensión obtener una codificación incorrecta.
2. Cuando las secuencias de comandos se ejecutan directamente en la consola integrada, se leen desde el archivo de PowerShell directamente. Si la codificación de PowerShell difiere de VSCode, algo puede salir mal aquí.
3. Cuando una secuencia de comandos que se abre en VSCode hace referencia a otra secuencia de comandos que no está abierto en VSCode, la extensión se vuelve a cargar el contenido del script desde el sistema de archivos. La extensión de PowerShell tiene como valor predeterminado para la codificación UTF-8, pero usa [marca de orden de bytes][], o l. MAT, la detección para seleccionar la codificación correcta.

El problema se produce cuando suponiendo que la codificación de formatos sin una marca BOM (como [UTF-8][] sin BOM y [Windows-1252][]).
La extensión de PowerShell tiene como valor predeterminado UTF-8. La extensión no puede cambiar la configuración de codificación de VSCode.
Para obtener más información, consulte [emitir 824 #](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Elegir la codificación correcta

Las aplicaciones y diferentes sistemas pueden utilizar codificaciones diferentes:

- En .NET Standard en la web y en el mundo de Linux, UTF-8 es ahora la codificación dominante.
- Muchas aplicaciones de .NET Framework usan [UTF-16][]. Por motivos históricos, esto se denomina "Unicode", un término que ahora hace referencia a una amplia [estándar](https://en.wikipedia.org/wiki/Unicode) que incluye tanto UTF-8 y UTF-16.
- En Windows, muchas aplicaciones nativas entendible Unicode seguirán usando Windows-1252 de forma predeterminada.

Codificaciones Unicode también tienen el concepto de un orden de bytes (BOM) de marcar. L. MAT producen al principio del texto para indicar que un descodificador la codificación que se está usando el texto. Para las codificaciones multibyte, también indica la marca BOM [endian](https://en.wikipedia.org/wiki/Endianness) de la codificación. L. MAT están diseñadas para ser bytes que rara vez se producen en texto no Unicode, lo que permite una estimación razonable de que el texto es Unicode cuando hay una marca BOM.

L. MAT son opcionales y su adopción no es tan popular del mundo de Linux porque se utiliza una convención confiable de UTF-8 en todas partes. La mayoría de las aplicaciones de Linux, por supuesto que la entrada de texto está codificado en UTF-8. Si bien muchas aplicaciones Linux reconocerá y tratar correctamente una marca BOM, un número no lo hace, dando lugar a artefactos en el texto que se manipula con esas aplicaciones.

**Por lo tanto,**:

- Si trabaja principalmente con las aplicaciones de Windows y Windows PowerShell, es preferible una codificación como UTF-8 con BOM o UTF-16.
- Si trabaja en las plataformas, es preferible UTF-8 con BOM.
- Si trabaja principalmente en contextos asociados de Linux, es preferible UTF-8 sin marca BOM.
- Windows-1252 y Latín-1 son básicamente las codificaciones heredadas que debe evitar si es posible.
  Sin embargo, algunas aplicaciones anteriores de Windows que dependen de ellos.
- También merece la pena mencionar que firma de scripts es [dependiente codificación](https://github.com/PowerShell/PowerShell/issues/3466), lo que significa que un cambio de codificación en una secuencia de comandos con signo será necesario volver a firmar.

## <a name="configuring-vscode"></a>Configuración de VSCode

De VSCode codificación predeterminada es UTF-8 sin marca BOM.

Para establecer [Codificación de VSCode][], vaya a la configuración de VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) y establezca el `"files.encoding"` configuración:

```json
"files.encoding": "utf8bom"
```

Algunos de los valores posibles son:

- `utf8`: [UTF-8] sin marca BOM
- `utf8bom`: [UTF-8] con BOM
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

Debe obtener una lista desplegable para esto en la vista de la interfaz gráfica de usuario o ver las finalizaciones para él en JSON.

También puede agregar lo siguiente para detectar automáticamente codificación cuando sea posible:

```json
"files.autoGuessEncoding": true
```

Si no desea que esta configuración afecta a todos los tipos de archivos, VSCode también permite que las configuraciones por idioma. Crear una configuración específica del lenguaje colocando la configuración un `[<language-name>]` campo. Por ejemplo:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Configuración de PowerShell

De PowerShell codificación predeterminada varía en función de la versión:

- En PowerShell 6 +, la codificación predeterminada es UTF-8 sin marca BOM en todas las plataformas.
- En Windows PowerShell, la codificación predeterminada es normalmente una extensión de Windows 1252 [latin-1][], también conocido como ISO 8859-1.

En PowerShell 5 + puede encontrar la codificación predeterminada con esto:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

La siguiente [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) puede usarse para determinar qué codificación de la sesión de PowerShell se infiere para una secuencia de comandos sin una marca BOM.

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

Es posible configurar PowerShell para usar una codificación determinada, generalmente más mediante la configuración del perfil. Vea los artículos siguientes:

- [@mklement0]del [respuesta sobre la codificación de PowerShell en StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]del [entrada de blog sobre cómo tratar la entrada sin una marca BOM UTF-8 en PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

No es posible forzar PowerShell para usar una codificación de entrada específica. PowerShell 5.1 y, a continuación de forma predeterminada en Windows-1252 codificación cuando no hay ninguna marca BOM. Por motivos de interoperabilidad, es mejor guardar scripts en un formato Unicode con una marca BOM.

> [!IMPORTANT]
> Cualquier otra herramienta tiene ese toque PowerShell scripts pueden verse afectados por las opciones de codificación o volver a codifican sus scripts para otra codificación.

### <a name="existing-scripts"></a>Scripts existentes

Las secuencias de comandos ya se encuentren en el sistema de archivos que necesite volver a codificarse a la nueva codificación elegida. En la barra inferior de VSCode, verá la etiqueta UTF-8. Haga clic en él para abrir la barra de acciones y seleccione **guardar con codificación**. Ahora puede elegir una codificación de nueva para ese archivo. Consulte [Codificación de VSCode][] para obtener instrucciones completas.

Si necesita volver a codificar varios archivos, puede usar el siguiente script:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>El entorno de scripting integrado (ISE) de PowerShell

Si también editar scripts con el ISE de PowerShell, deberá sincronizar la configuración de codificación no existe.

El ISE debe respetar una marca BOM, pero también es posible usar la reflexión para [establecer la codificación](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Tenga en cuenta que esto no se conserven entre las nuevas empresas.

### <a name="source-control-software"></a>Software de control de código fuente

Algunas herramientas de control de código fuente como git, pasar por alto las codificaciones; GIT simplemente realiza un seguimiento de los bytes.
Como TFS o Mercurial, puede que otros no. Incluso algunas herramientas basados en git se basan en texto de descodificación.

Cuando esto sucede, asegúrese de:

- Configurar la codificación en el control de código fuente para que coincida con la configuración de VSCode de texto.
- Asegúrese de que todos los archivos se protegen en el control de código fuente en la codificación correspondiente.
- Tenga cuidado de los cambios realizados en la codificación que se reciben a través del control de código fuente. Un signo de esta clave es una diferencia que indica los cambios pero donde nada parece haber cambiado (porque tienen bytes pero no lo ha hecho caracteres).

### <a name="collaborators-environments"></a>Entornos de colaboradores

Encima de la configuración de control de código fuente, asegúrese de que los colaboradores en cualquier archivo que comparte no tienen opciones que reemplacen la codificación al volver a codificar los archivos de PowerShell.

### <a name="other-programs"></a>Otros programas

Cualquier otro programa que lee o escribe un script de PowerShell puede volver a codificarlo.

Ejemplos:

- Uso del Portapapeles para copiar y pegar un script. Esto es habitual en escenarios como:
  - Copiar una secuencia de comandos en una máquina virtual
  - Copiar una secuencia de comandos de un correo electrónico o una página Web
  - Copiar una secuencia de comandos dentro o fuera de un documento de Microsoft Word o PowerPoint
- Otros editores de texto, como:
  - Notepad
  - vim
  - Cualquier otro editor de secuencia de comandos de PowerShell
- Texto de edición de utilidades, como:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operadores de redirección de PowerShell como `>` y `>>`
  - `sed`/`awk`
- Programas de transferencia, el archivo como:
  - Un explorador web, al descargar las secuencias de comandos
  - Un recurso compartido de archivos

Algunas de estas herramientas tratan de bytes en lugar de texto, pero otros ofrecen las configuraciones de codificación. En esos casos donde deberá configurar una codificación, deberá hacer lo mismo como su editor de codificación para evitar problemas.

## <a name="other-resources-on-encoding-in-powershell"></a>Otros recursos en la codificación en PowerShell

Hay algunas otras publicaciones interesantes sobre la codificación y la configuración de codificación en PowerShell que vale la pena una lectura:

- [@mklement0]del [resumen de codificación de PowerShell en StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Problemas anteriores se abre en vscode-PowerShell para la codificación de problemas:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [El clásico *Joel sobre el Software* escribir acerca de Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Codificación en .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca de orden de bytes]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de servidor de lenguaje]: https://microsoft.github.io/language-server-protocol/
[Codificación de VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
