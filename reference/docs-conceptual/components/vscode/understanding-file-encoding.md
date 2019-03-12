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
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="aee1b-103">Descripción de la codificación de archivo en VSCode y PowerShell</span><span class="sxs-lookup"><span data-stu-id="aee1b-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="aee1b-104">Al usar VS Code para crear y editar scripts de PowerShell, es importante que los archivos se guardan con el formato de codificación de caracteres correcto.</span><span class="sxs-lookup"><span data-stu-id="aee1b-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="aee1b-105">¿Qué es la codificación de archivos y por qué es importante?</span><span class="sxs-lookup"><span data-stu-id="aee1b-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="aee1b-106">VSCode administra la interfaz entre humano al escribir cadenas de caracteres en un búfer y bloques de lectura/escritura de bytes en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="aee1b-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="aee1b-107">Cuando VSCode guarda un archivo, usa una codificación para hacer esto de texto.</span><span class="sxs-lookup"><span data-stu-id="aee1b-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="aee1b-108">De forma similar, cuando PowerShell ejecuta una secuencia de comandos debe convertir los bytes en un archivo a caracteres para reconstruir el archivo en un programa de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aee1b-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="aee1b-109">Dado que VSCode escribe el archivo y PowerShell lee el archivo, que necesitan usar el mismo sistema de codificación.</span><span class="sxs-lookup"><span data-stu-id="aee1b-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="aee1b-110">Este proceso de análisis de un script de PowerShell es: *bytes* -> *caracteres* -> *tokens*  ->   *árbol de sintaxis abstracta* -> *ejecución*.</span><span class="sxs-lookup"><span data-stu-id="aee1b-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="aee1b-111">VSCode y PowerShell se instalan con una configuración de codificación predeterminado razonable.</span><span class="sxs-lookup"><span data-stu-id="aee1b-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="aee1b-112">Sin embargo, la codificación predeterminada usando PowerShell ha cambiado con la versión de PowerShell Core (versión 6.x).</span><span class="sxs-lookup"><span data-stu-id="aee1b-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="aee1b-113">Para asegurarse de que no tiene problemas con PowerShell o la extensión de PowerShell en VSCode, deberá establecer la configuración de VSCode y PowerShell correctamente.</span><span class="sxs-lookup"><span data-stu-id="aee1b-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="aee1b-114">Causas comunes de problemas de codificación</span><span class="sxs-lookup"><span data-stu-id="aee1b-114">Common causes of encoding issues</span></span>

<span data-ttu-id="aee1b-115">Problemas de codificación se producen cuando la codificación de VSCode o el archivo de script no coincide con la codificación esperada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aee1b-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="aee1b-116">No hay ninguna manera de PowerShell determinar automáticamente la codificación del archivo.</span><span class="sxs-lookup"><span data-stu-id="aee1b-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="aee1b-117">Es más probable de problemas de codificación cuando se usa caracteres no está en el [juego de caracteres ASCII de 7 bits](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="aee1b-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="aee1b-118">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="aee1b-118">For example:</span></span>

- <span data-ttu-id="aee1b-119">Acentuadas caracteres latinos (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="aee1b-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="aee1b-120">Caracteres no latinos, como cirílico (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="aee1b-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="aee1b-121">Han chino (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="aee1b-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="aee1b-122">Causas comunes de problemas de codificación son:</span><span class="sxs-lookup"><span data-stu-id="aee1b-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="aee1b-123">Las codificaciones de VSCode y PowerShell no han cambiado de sus valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="aee1b-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="aee1b-124">Para PowerShell 5.1 y, a continuación, el valor predeterminado de codificación es diferente de VSCode.</span><span class="sxs-lookup"><span data-stu-id="aee1b-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="aee1b-125">Otro editor tiene abierto y sobrescribe el archivo en una nueva codificación.</span><span class="sxs-lookup"><span data-stu-id="aee1b-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="aee1b-126">Esto suele ocurrir con el ISE.</span><span class="sxs-lookup"><span data-stu-id="aee1b-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="aee1b-127">El archivo está desprotegido en el control de código fuente en una codificación que es diferente de qué VSCode o PowerShell espera.</span><span class="sxs-lookup"><span data-stu-id="aee1b-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="aee1b-128">Esto puede ocurrir cuando colaboradores usan editores con distintas configuraciones de codificación.</span><span class="sxs-lookup"><span data-stu-id="aee1b-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="aee1b-129">Cómo saber si tiene problemas de codificación</span><span class="sxs-lookup"><span data-stu-id="aee1b-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="aee1b-130">Errores de codificación a menudo se presenten como analizar errores en los scripts.</span><span class="sxs-lookup"><span data-stu-id="aee1b-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="aee1b-131">Si encuentra las secuencias de caracteres extraños en la secuencia de comandos, éste puede ser el problema.</span><span class="sxs-lookup"><span data-stu-id="aee1b-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="aee1b-132">En el ejemplo siguiente, un guión corto (`–`) aparece como los caracteres `â€“`:</span><span class="sxs-lookup"><span data-stu-id="aee1b-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="aee1b-133">Este problema se produce porque VSCode codifica el carácter `–` en UTF-8, como los bytes `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="aee1b-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="aee1b-134">Cuando estos bytes se descodificación como Windows-1252, se interpretan como caracteres `â€“`.</span><span class="sxs-lookup"><span data-stu-id="aee1b-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="aee1b-135">Algunas secuencias de caracteres extraños que ve podría incluyen:</span><span class="sxs-lookup"><span data-stu-id="aee1b-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="aee1b-136">`â€“` en lugar de `–`</span><span class="sxs-lookup"><span data-stu-id="aee1b-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="aee1b-137">`â€”` en lugar de `—`</span><span class="sxs-lookup"><span data-stu-id="aee1b-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="aee1b-138">`Ã„2` en lugar de `Ä`</span><span class="sxs-lookup"><span data-stu-id="aee1b-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="aee1b-139">`Â` en lugar de ` ` (un espacio de no separación)</span><span class="sxs-lookup"><span data-stu-id="aee1b-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="aee1b-140">`Ã©` en lugar de `é`</span><span class="sxs-lookup"><span data-stu-id="aee1b-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="aee1b-141">Este práctico [referencia](https://www.i18nqa.com/debug/utf8-debug.html) se enumeran los patrones comunes que indican un problema de codificación UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="aee1b-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="aee1b-142">Cómo interactúa la extensión de PowerShell en VSCode con codificaciones</span><span class="sxs-lookup"><span data-stu-id="aee1b-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="aee1b-143">La extensión de PowerShell interactúa con las secuencias de comandos de varias maneras:</span><span class="sxs-lookup"><span data-stu-id="aee1b-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="aee1b-144">Cuando se editan scripts en VSCode, el contenido se envía con VSCode para la extensión.</span><span class="sxs-lookup"><span data-stu-id="aee1b-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="aee1b-145">El [Protocolo de servidor de lenguaje][] obliga a que este contenido se transfiere en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="aee1b-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="aee1b-146">Por lo tanto, no es posible que la extensión obtener una codificación incorrecta.</span><span class="sxs-lookup"><span data-stu-id="aee1b-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="aee1b-147">Cuando las secuencias de comandos se ejecutan directamente en la consola integrada, se leen desde el archivo de PowerShell directamente.</span><span class="sxs-lookup"><span data-stu-id="aee1b-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="aee1b-148">Si la codificación de PowerShell difiere de VSCode, algo puede salir mal aquí.</span><span class="sxs-lookup"><span data-stu-id="aee1b-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="aee1b-149">Cuando una secuencia de comandos que se abre en VSCode hace referencia a otra secuencia de comandos que no está abierto en VSCode, la extensión se vuelve a cargar el contenido del script desde el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="aee1b-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="aee1b-150">La extensión de PowerShell tiene como valor predeterminado para la codificación UTF-8, pero usa [marca de orden de bytes][], o l. MAT, la detección para seleccionar la codificación correcta.</span><span class="sxs-lookup"><span data-stu-id="aee1b-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="aee1b-151">El problema se produce cuando suponiendo que la codificación de formatos sin una marca BOM (como [UTF-8][] sin BOM y [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="aee1b-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="aee1b-152">La extensión de PowerShell tiene como valor predeterminado UTF-8.</span><span class="sxs-lookup"><span data-stu-id="aee1b-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="aee1b-153">La extensión no puede cambiar la configuración de codificación de VSCode.</span><span class="sxs-lookup"><span data-stu-id="aee1b-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="aee1b-154">Para obtener más información, consulte [emitir 824 #](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="aee1b-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="aee1b-155">Elegir la codificación correcta</span><span class="sxs-lookup"><span data-stu-id="aee1b-155">Choosing the right encoding</span></span>

<span data-ttu-id="aee1b-156">Las aplicaciones y diferentes sistemas pueden utilizar codificaciones diferentes:</span><span class="sxs-lookup"><span data-stu-id="aee1b-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="aee1b-157">En .NET Standard en la web y en el mundo de Linux, UTF-8 es ahora la codificación dominante.</span><span class="sxs-lookup"><span data-stu-id="aee1b-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="aee1b-158">Muchas aplicaciones de .NET Framework usan [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="aee1b-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="aee1b-159">Por motivos históricos, esto se denomina "Unicode", un término que ahora hace referencia a una amplia [estándar](https://en.wikipedia.org/wiki/Unicode) que incluye tanto UTF-8 y UTF-16.</span><span class="sxs-lookup"><span data-stu-id="aee1b-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="aee1b-160">En Windows, muchas aplicaciones nativas entendible Unicode seguirán usando Windows-1252 de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="aee1b-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="aee1b-161">Codificaciones Unicode también tienen el concepto de un orden de bytes (BOM) de marcar.</span><span class="sxs-lookup"><span data-stu-id="aee1b-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="aee1b-162">L. MAT producen al principio del texto para indicar que un descodificador la codificación que se está usando el texto.</span><span class="sxs-lookup"><span data-stu-id="aee1b-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="aee1b-163">Para las codificaciones multibyte, también indica la marca BOM [endian](https://en.wikipedia.org/wiki/Endianness) de la codificación.</span><span class="sxs-lookup"><span data-stu-id="aee1b-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="aee1b-164">L. MAT están diseñadas para ser bytes que rara vez se producen en texto no Unicode, lo que permite una estimación razonable de que el texto es Unicode cuando hay una marca BOM.</span><span class="sxs-lookup"><span data-stu-id="aee1b-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="aee1b-165">L. MAT son opcionales y su adopción no es tan popular del mundo de Linux porque se utiliza una convención confiable de UTF-8 en todas partes.</span><span class="sxs-lookup"><span data-stu-id="aee1b-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="aee1b-166">La mayoría de las aplicaciones de Linux, por supuesto que la entrada de texto está codificado en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="aee1b-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="aee1b-167">Si bien muchas aplicaciones Linux reconocerá y tratar correctamente una marca BOM, un número no lo hace, dando lugar a artefactos en el texto que se manipula con esas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="aee1b-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="aee1b-168">**Por lo tanto,**:</span><span class="sxs-lookup"><span data-stu-id="aee1b-168">**Therefore**:</span></span>

- <span data-ttu-id="aee1b-169">Si trabaja principalmente con las aplicaciones de Windows y Windows PowerShell, es preferible una codificación como UTF-8 con BOM o UTF-16.</span><span class="sxs-lookup"><span data-stu-id="aee1b-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="aee1b-170">Si trabaja en las plataformas, es preferible UTF-8 con BOM.</span><span class="sxs-lookup"><span data-stu-id="aee1b-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="aee1b-171">Si trabaja principalmente en contextos asociados de Linux, es preferible UTF-8 sin marca BOM.</span><span class="sxs-lookup"><span data-stu-id="aee1b-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="aee1b-172">Windows-1252 y Latín-1 son básicamente las codificaciones heredadas que debe evitar si es posible.</span><span class="sxs-lookup"><span data-stu-id="aee1b-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="aee1b-173">Sin embargo, algunas aplicaciones anteriores de Windows que dependen de ellos.</span><span class="sxs-lookup"><span data-stu-id="aee1b-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="aee1b-174">También merece la pena mencionar que firma de scripts es [dependiente codificación](https://github.com/PowerShell/PowerShell/issues/3466), lo que significa que un cambio de codificación en una secuencia de comandos con signo será necesario volver a firmar.</span><span class="sxs-lookup"><span data-stu-id="aee1b-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="aee1b-175">Configuración de VSCode</span><span class="sxs-lookup"><span data-stu-id="aee1b-175">Configuring VSCode</span></span>

<span data-ttu-id="aee1b-176">De VSCode codificación predeterminada es UTF-8 sin marca BOM.</span><span class="sxs-lookup"><span data-stu-id="aee1b-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="aee1b-177">Para establecer [Codificación de VSCode][], vaya a la configuración de VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) y establezca el `"files.encoding"` configuración:</span><span class="sxs-lookup"><span data-stu-id="aee1b-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="aee1b-178">Algunos de los valores posibles son:</span><span class="sxs-lookup"><span data-stu-id="aee1b-178">Some possible values are:</span></span>

- <span data-ttu-id="aee1b-179">`utf8`: [UTF-8] sin marca BOM</span><span class="sxs-lookup"><span data-stu-id="aee1b-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="aee1b-180">`utf8bom`: [UTF-8] con BOM</span><span class="sxs-lookup"><span data-stu-id="aee1b-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="aee1b-181">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="aee1b-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="aee1b-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="aee1b-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="aee1b-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="aee1b-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="aee1b-184">Debe obtener una lista desplegable para esto en la vista de la interfaz gráfica de usuario o ver las finalizaciones para él en JSON.</span><span class="sxs-lookup"><span data-stu-id="aee1b-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="aee1b-185">También puede agregar lo siguiente para detectar automáticamente codificación cuando sea posible:</span><span class="sxs-lookup"><span data-stu-id="aee1b-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="aee1b-186">Si no desea que esta configuración afecta a todos los tipos de archivos, VSCode también permite que las configuraciones por idioma.</span><span class="sxs-lookup"><span data-stu-id="aee1b-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="aee1b-187">Crear una configuración específica del lenguaje colocando la configuración un `[<language-name>]` campo.</span><span class="sxs-lookup"><span data-stu-id="aee1b-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="aee1b-188">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="aee1b-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="aee1b-189">Configuración de PowerShell</span><span class="sxs-lookup"><span data-stu-id="aee1b-189">Configuring PowerShell</span></span>

<span data-ttu-id="aee1b-190">De PowerShell codificación predeterminada varía en función de la versión:</span><span class="sxs-lookup"><span data-stu-id="aee1b-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="aee1b-191">En PowerShell 6 +, la codificación predeterminada es UTF-8 sin marca BOM en todas las plataformas.</span><span class="sxs-lookup"><span data-stu-id="aee1b-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="aee1b-192">En Windows PowerShell, la codificación predeterminada es normalmente una extensión de Windows 1252 [latin-1][], también conocido como ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="aee1b-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="aee1b-193">En PowerShell 5 + puede encontrar la codificación predeterminada con esto:</span><span class="sxs-lookup"><span data-stu-id="aee1b-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="aee1b-194">La siguiente [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) puede usarse para determinar qué codificación de la sesión de PowerShell se infiere para una secuencia de comandos sin una marca BOM.</span><span class="sxs-lookup"><span data-stu-id="aee1b-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="aee1b-195">Es posible configurar PowerShell para usar una codificación determinada, generalmente más mediante la configuración del perfil.</span><span class="sxs-lookup"><span data-stu-id="aee1b-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="aee1b-196">Vea los artículos siguientes:</span><span class="sxs-lookup"><span data-stu-id="aee1b-196">See the following articles:</span></span>

- <span data-ttu-id="aee1b-197">[@mklement0]del [respuesta sobre la codificación de PowerShell en StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="aee1b-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="aee1b-198">[@rkeithhill]del [entrada de blog sobre cómo tratar la entrada sin una marca BOM UTF-8 en PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="aee1b-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="aee1b-199">No es posible forzar PowerShell para usar una codificación de entrada específica.</span><span class="sxs-lookup"><span data-stu-id="aee1b-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="aee1b-200">PowerShell 5.1 y, a continuación de forma predeterminada en Windows-1252 codificación cuando no hay ninguna marca BOM.</span><span class="sxs-lookup"><span data-stu-id="aee1b-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="aee1b-201">Por motivos de interoperabilidad, es mejor guardar scripts en un formato Unicode con una marca BOM.</span><span class="sxs-lookup"><span data-stu-id="aee1b-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aee1b-202">Cualquier otra herramienta tiene ese toque PowerShell scripts pueden verse afectados por las opciones de codificación o volver a codifican sus scripts para otra codificación.</span><span class="sxs-lookup"><span data-stu-id="aee1b-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="aee1b-203">Scripts existentes</span><span class="sxs-lookup"><span data-stu-id="aee1b-203">Existing scripts</span></span>

<span data-ttu-id="aee1b-204">Las secuencias de comandos ya se encuentren en el sistema de archivos que necesite volver a codificarse a la nueva codificación elegida.</span><span class="sxs-lookup"><span data-stu-id="aee1b-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="aee1b-205">En la barra inferior de VSCode, verá la etiqueta UTF-8.</span><span class="sxs-lookup"><span data-stu-id="aee1b-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="aee1b-206">Haga clic en él para abrir la barra de acciones y seleccione **guardar con codificación**.</span><span class="sxs-lookup"><span data-stu-id="aee1b-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="aee1b-207">Ahora puede elegir una codificación de nueva para ese archivo.</span><span class="sxs-lookup"><span data-stu-id="aee1b-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="aee1b-208">Consulte [Codificación de VSCode][] para obtener instrucciones completas.</span><span class="sxs-lookup"><span data-stu-id="aee1b-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="aee1b-209">Si necesita volver a codificar varios archivos, puede usar el siguiente script:</span><span class="sxs-lookup"><span data-stu-id="aee1b-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="aee1b-210">El entorno de scripting integrado (ISE) de PowerShell</span><span class="sxs-lookup"><span data-stu-id="aee1b-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="aee1b-211">Si también editar scripts con el ISE de PowerShell, deberá sincronizar la configuración de codificación no existe.</span><span class="sxs-lookup"><span data-stu-id="aee1b-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="aee1b-212">El ISE debe respetar una marca BOM, pero también es posible usar la reflexión para [establecer la codificación](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="aee1b-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="aee1b-213">Tenga en cuenta que esto no se conserven entre las nuevas empresas.</span><span class="sxs-lookup"><span data-stu-id="aee1b-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="aee1b-214">Software de control de código fuente</span><span class="sxs-lookup"><span data-stu-id="aee1b-214">Source control software</span></span>

<span data-ttu-id="aee1b-215">Algunas herramientas de control de código fuente como git, pasar por alto las codificaciones; GIT simplemente realiza un seguimiento de los bytes.</span><span class="sxs-lookup"><span data-stu-id="aee1b-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="aee1b-216">Como TFS o Mercurial, puede que otros no.</span><span class="sxs-lookup"><span data-stu-id="aee1b-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="aee1b-217">Incluso algunas herramientas basados en git se basan en texto de descodificación.</span><span class="sxs-lookup"><span data-stu-id="aee1b-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="aee1b-218">Cuando esto sucede, asegúrese de:</span><span class="sxs-lookup"><span data-stu-id="aee1b-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="aee1b-219">Configurar la codificación en el control de código fuente para que coincida con la configuración de VSCode de texto.</span><span class="sxs-lookup"><span data-stu-id="aee1b-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="aee1b-220">Asegúrese de que todos los archivos se protegen en el control de código fuente en la codificación correspondiente.</span><span class="sxs-lookup"><span data-stu-id="aee1b-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="aee1b-221">Tenga cuidado de los cambios realizados en la codificación que se reciben a través del control de código fuente.</span><span class="sxs-lookup"><span data-stu-id="aee1b-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="aee1b-222">Un signo de esta clave es una diferencia que indica los cambios pero donde nada parece haber cambiado (porque tienen bytes pero no lo ha hecho caracteres).</span><span class="sxs-lookup"><span data-stu-id="aee1b-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="aee1b-223">Entornos de colaboradores</span><span class="sxs-lookup"><span data-stu-id="aee1b-223">Collaborators' environments</span></span>

<span data-ttu-id="aee1b-224">Encima de la configuración de control de código fuente, asegúrese de que los colaboradores en cualquier archivo que comparte no tienen opciones que reemplacen la codificación al volver a codificar los archivos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aee1b-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="aee1b-225">Otros programas</span><span class="sxs-lookup"><span data-stu-id="aee1b-225">Other programs</span></span>

<span data-ttu-id="aee1b-226">Cualquier otro programa que lee o escribe un script de PowerShell puede volver a codificarlo.</span><span class="sxs-lookup"><span data-stu-id="aee1b-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="aee1b-227">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="aee1b-227">Some examples are:</span></span>

- <span data-ttu-id="aee1b-228">Uso del Portapapeles para copiar y pegar un script.</span><span class="sxs-lookup"><span data-stu-id="aee1b-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="aee1b-229">Esto es habitual en escenarios como:</span><span class="sxs-lookup"><span data-stu-id="aee1b-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="aee1b-230">Copiar una secuencia de comandos en una máquina virtual</span><span class="sxs-lookup"><span data-stu-id="aee1b-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="aee1b-231">Copiar una secuencia de comandos de un correo electrónico o una página Web</span><span class="sxs-lookup"><span data-stu-id="aee1b-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="aee1b-232">Copiar una secuencia de comandos dentro o fuera de un documento de Microsoft Word o PowerPoint</span><span class="sxs-lookup"><span data-stu-id="aee1b-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="aee1b-233">Otros editores de texto, como:</span><span class="sxs-lookup"><span data-stu-id="aee1b-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="aee1b-234">Notepad</span><span class="sxs-lookup"><span data-stu-id="aee1b-234">Notepad</span></span>
  - <span data-ttu-id="aee1b-235">vim</span><span class="sxs-lookup"><span data-stu-id="aee1b-235">vim</span></span>
  - <span data-ttu-id="aee1b-236">Cualquier otro editor de secuencia de comandos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="aee1b-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="aee1b-237">Texto de edición de utilidades, como:</span><span class="sxs-lookup"><span data-stu-id="aee1b-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="aee1b-238">Operadores de redirección de PowerShell como `>` y `>>`</span><span class="sxs-lookup"><span data-stu-id="aee1b-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="aee1b-239">Programas de transferencia, el archivo como:</span><span class="sxs-lookup"><span data-stu-id="aee1b-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="aee1b-240">Un explorador web, al descargar las secuencias de comandos</span><span class="sxs-lookup"><span data-stu-id="aee1b-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="aee1b-241">Un recurso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="aee1b-241">A file share</span></span>

<span data-ttu-id="aee1b-242">Algunas de estas herramientas tratan de bytes en lugar de texto, pero otros ofrecen las configuraciones de codificación.</span><span class="sxs-lookup"><span data-stu-id="aee1b-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="aee1b-243">En esos casos donde deberá configurar una codificación, deberá hacer lo mismo como su editor de codificación para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="aee1b-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="aee1b-244">Otros recursos en la codificación en PowerShell</span><span class="sxs-lookup"><span data-stu-id="aee1b-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="aee1b-245">Hay algunas otras publicaciones interesantes sobre la codificación y la configuración de codificación en PowerShell que vale la pena una lectura:</span><span class="sxs-lookup"><span data-stu-id="aee1b-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="aee1b-246">[@mklement0]del [resumen de codificación de PowerShell en StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="aee1b-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="aee1b-247">Problemas anteriores se abre en vscode-PowerShell para la codificación de problemas:</span><span class="sxs-lookup"><span data-stu-id="aee1b-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="aee1b-248">#1308</span><span class="sxs-lookup"><span data-stu-id="aee1b-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="aee1b-249">#1628</span><span class="sxs-lookup"><span data-stu-id="aee1b-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="aee1b-250">#1680</span><span class="sxs-lookup"><span data-stu-id="aee1b-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="aee1b-251">#1744</span><span class="sxs-lookup"><span data-stu-id="aee1b-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="aee1b-252">#1751</span><span class="sxs-lookup"><span data-stu-id="aee1b-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="aee1b-253">El clásico *Joel sobre el Software* escribir acerca de Unicode</span><span class="sxs-lookup"><span data-stu-id="aee1b-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="aee1b-254">Codificación en .NET Standard</span><span class="sxs-lookup"><span data-stu-id="aee1b-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca de orden de bytes]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de servidor de lenguaje]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Codificación de VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
