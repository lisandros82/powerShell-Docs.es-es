---
title: Descripción de la codificación de archivo en VSCode y PowerShell
description: Configuración de la codificación de archivo en VSCode y PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 73e766832d56a08bd5ef16df11899a0aab0badae
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795129"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="98f93-103">Descripción de la codificación de archivo en VSCode y PowerShell</span><span class="sxs-lookup"><span data-stu-id="98f93-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="98f93-104">Al usar VS Code para crear y editar scripts de PowerShell, es importante que los archivos se guarden con el formato de codificación de caracteres correcto.</span><span class="sxs-lookup"><span data-stu-id="98f93-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="98f93-105">¿Qué es la codificación de archivo y por qué es importante?</span><span class="sxs-lookup"><span data-stu-id="98f93-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="98f93-106">VSCode administra la interfaz entre una entrada manual de cadenas de caracteres en un búfer y la lectura/escritura de bloques de bytes en el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="98f93-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="98f93-107">Cuando VSCode guarda un archivo, usa una codificación de texto para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="98f93-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="98f93-108">De forma similar, cuando PowerShell ejecuta un script debe convertir los bytes de un archivo a caracteres para reconstruir el archivo en un programa de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98f93-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="98f93-109">Dado que VSCode escribe el archivo y PowerShell lee el archivo, deben usar el mismo sistema de codificación.</span><span class="sxs-lookup"><span data-stu-id="98f93-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="98f93-110">Este proceso de análisis de un script de PowerShell es: *bytes* -> *caracteres* -> *tokens* -> *árbol de sintaxis abstracta* -> *ejecución*.</span><span class="sxs-lookup"><span data-stu-id="98f93-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="98f93-111">VSCode y PowerShell se instalan con una configuración de codificación predeterminada sensible.</span><span class="sxs-lookup"><span data-stu-id="98f93-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="98f93-112">Sin embargo, la codificación predeterminada usada por PowerShell ha cambiado con la publicación de PowerShell Core (versión 6.x).</span><span class="sxs-lookup"><span data-stu-id="98f93-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="98f93-113">Para garantizar que no tiene problemas con el uso de PowerShell o la extensión de PowerShell en VSCode, debe configurar sus opciones de VSCode y PowerShell correctamente.</span><span class="sxs-lookup"><span data-stu-id="98f93-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="98f93-114">Causas comunes de problemas de codificación</span><span class="sxs-lookup"><span data-stu-id="98f93-114">Common causes of encoding issues</span></span>

<span data-ttu-id="98f93-115">Se producen problemas de codificación cuando la codificación de VSCode o el archivo de script no coincide con la codificación esperada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98f93-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="98f93-116">No hay ninguna forma de que PowerShell determine automáticamente la codificación del archivo.</span><span class="sxs-lookup"><span data-stu-id="98f93-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="98f93-117">Es más probable tener problemas de codificación cuando se usan caracteres que no están en el [juego de caracteres ASCII de 7 bits](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="98f93-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="98f93-118">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="98f93-118">For example:</span></span>

- <span data-ttu-id="98f93-119">Caracteres latinos acentuados (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="98f93-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="98f93-120">Caracteres no latinos; por ejemplo, cirílico (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="98f93-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="98f93-121">Chino Han (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="98f93-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="98f93-122">Algunas causas comunes de problemas de codificación son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="98f93-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="98f93-123">Las codificaciones de VSCode y PowerShell no han cambiado respecto a sus valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="98f93-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="98f93-124">Para PowerShell 5.1 y versiones posteriores, el valor predeterminado de codificación es diferente del de VSCode.</span><span class="sxs-lookup"><span data-stu-id="98f93-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="98f93-125">Otro editor ha abierto y sobrescrito el archivo en una nueva codificación.</span><span class="sxs-lookup"><span data-stu-id="98f93-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="98f93-126">Esto suele ocurrir con el ISE.</span><span class="sxs-lookup"><span data-stu-id="98f93-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="98f93-127">El archivo se incorpora al control de código fuente en una codificación distinta a la que VSCode o PowerShell esperaba.</span><span class="sxs-lookup"><span data-stu-id="98f93-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="98f93-128">Esto puede ocurrir cuando los colaboradores usan editores con distintas configuraciones de codificación.</span><span class="sxs-lookup"><span data-stu-id="98f93-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="98f93-129">Procedimiento para saber si tiene problemas de codificación</span><span class="sxs-lookup"><span data-stu-id="98f93-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="98f93-130">Los errores de codificación, a menudo, se presentan como errores de análisis en los scripts.</span><span class="sxs-lookup"><span data-stu-id="98f93-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="98f93-131">Si encuentra secuencias de caracteres extraños en su script, éste puede ser el problema.</span><span class="sxs-lookup"><span data-stu-id="98f93-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="98f93-132">En el ejemplo siguiente, un guión corto (`–`) aparece como los caracteres `â€“`:</span><span class="sxs-lookup"><span data-stu-id="98f93-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="98f93-133">Este problema se produce porque VSCode codifica el carácter `–` en UTF-8 como los bytes `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="98f93-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="98f93-134">Cuando estos bytes se descodifican como Windows-1252, se interpretan como los caracteres `â€“`.</span><span class="sxs-lookup"><span data-stu-id="98f93-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="98f93-135">Entre algunas secuencias de caracteres extraños que podría ver se incluyen:</span><span class="sxs-lookup"><span data-stu-id="98f93-135">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="98f93-136">`â€“` en lugar de `–`</span><span class="sxs-lookup"><span data-stu-id="98f93-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="98f93-137">`â€”` en lugar de `—`</span><span class="sxs-lookup"><span data-stu-id="98f93-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="98f93-138">`Ã„2` en lugar de `Ä`</span><span class="sxs-lookup"><span data-stu-id="98f93-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="98f93-139">`Â` en lugar de ` ` (un espacio de no separación)</span><span class="sxs-lookup"><span data-stu-id="98f93-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="98f93-140">`Ã©` en lugar de `é`
<!-- markdownlint-enable MD038 --></span><span class="sxs-lookup"><span data-stu-id="98f93-140">`Ã©` instead of `é`
<!-- markdownlint-enable MD038 --></span></span>

<span data-ttu-id="98f93-141">Esta [referencia](https://www.i18nqa.com/debug/utf8-debug.html) práctica detalla los patrones comunes que indican un problema de codificación UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="98f93-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="98f93-142">De qué forma la extensión de PowerShell en VSCode interactúa con las codificaciones</span><span class="sxs-lookup"><span data-stu-id="98f93-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="98f93-143">La extensión de PowerShell interactúa con los scripts de varias maneras:</span><span class="sxs-lookup"><span data-stu-id="98f93-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="98f93-144">Cuando los scripts se editan en VSCode, el contenido lo envía VSCode a la extensión.</span><span class="sxs-lookup"><span data-stu-id="98f93-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="98f93-145">El [protocolo de servidor de lenguaje][] obliga a que este contenido se transfiera en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="98f93-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="98f93-146">Por lo tanto, no es posible que la extensión obtenga la codificación incorrecta.</span><span class="sxs-lookup"><span data-stu-id="98f93-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="98f93-147">Cuando los scripts se ejecutan directamente en la consola integrada, se leen desde el archivo de PowerShell directamente.</span><span class="sxs-lookup"><span data-stu-id="98f93-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="98f93-148">Si la codificación de PowerShell difiere de la de VSCode, es posible que algo no funcione bien.</span><span class="sxs-lookup"><span data-stu-id="98f93-148">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="98f93-149">Cuando un script que está abierto en VSCode hace referencia a otro script que no está abierto en VSCode, la extensión pasa de nuevo a cargar el contenido del script desde el sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="98f93-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="98f93-150">La extensión de PowerShell tiene como valor predeterminado la codificación UTF-8, pero usa la detección de [marca BOM][] para seleccionar la codificación correcta.</span><span class="sxs-lookup"><span data-stu-id="98f93-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="98f93-151">El problema se produce cuando se asume la codificación de formatos sin BOM (como [UTF-8][] sin BOM y [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="98f93-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="98f93-152">La extensión de PowerShell tiene como valor predeterminado UTF-8.</span><span class="sxs-lookup"><span data-stu-id="98f93-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="98f93-153">La extensión no puede cambiar la configuración de codificación de VSCode.</span><span class="sxs-lookup"><span data-stu-id="98f93-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="98f93-154">Para obtener más información, vea el [problema #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="98f93-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="98f93-155">Elección de la codificación correcta</span><span class="sxs-lookup"><span data-stu-id="98f93-155">Choosing the right encoding</span></span>

<span data-ttu-id="98f93-156">Las aplicaciones y los sistemas distintos pueden utilizar codificaciones diferentes:</span><span class="sxs-lookup"><span data-stu-id="98f93-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="98f93-157">En .NET Standard, en la web y en el entorno Linux, UTF-8 es ahora la codificación dominante.</span><span class="sxs-lookup"><span data-stu-id="98f93-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="98f93-158">Muchas aplicaciones de .NET Framework usan [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="98f93-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="98f93-159">Por motivos históricos, a veces recibe la denominación de "Unicode", un término que ahora hace referencia a un amplio [estándar](https://en.wikipedia.org/wiki/Unicode) que incluye tanto UTF-8 como UTF-16.</span><span class="sxs-lookup"><span data-stu-id="98f93-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="98f93-160">En Windows, muchas aplicaciones nativas anteriores a Unicode siguen usando Windows-1252 de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="98f93-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="98f93-161">Las codificaciones Unicode también tienen el concepto de una marca BOM.</span><span class="sxs-lookup"><span data-stu-id="98f93-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="98f93-162">Las BOM se producen al principio del texto para indicar a un descodificador la codificación que está usando el texto.</span><span class="sxs-lookup"><span data-stu-id="98f93-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="98f93-163">Para las codificaciones multibyte, la BOM también indica la marca [endianness](https://en.wikipedia.org/wiki/Endianness) de la codificación.</span><span class="sxs-lookup"><span data-stu-id="98f93-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="98f93-164">Las BOM están diseñadas para ser bytes que rara vez se producen en texto no Unicode, permitiendo una estimación razonable de que el texto es Unicode cuando hay una BOM.</span><span class="sxs-lookup"><span data-stu-id="98f93-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="98f93-165">Las BOM son opcionales y su adopción no es tan popular en los entornos Linux, porque se utiliza de forma generalizada una convención dependiente de UTF-8.</span><span class="sxs-lookup"><span data-stu-id="98f93-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="98f93-166">La mayoría de las aplicaciones Linux dan por supuesto que la entrada de texto está codificada en UTF-8.</span><span class="sxs-lookup"><span data-stu-id="98f93-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="98f93-167">Si bien muchas aplicaciones Linux reconocen y tratan correctamente una BOM, algunas no lo hacen y esto provoca anomalías en el texto manipulado con esas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="98f93-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="98f93-168">**Por lo tanto**:</span><span class="sxs-lookup"><span data-stu-id="98f93-168">**Therefore**:</span></span>

- <span data-ttu-id="98f93-169">Si trabaja principalmente con aplicaciones Windows y Windows PowerShell, es preferible una codificación como UTF-8 con BOM o UTF-16.</span><span class="sxs-lookup"><span data-stu-id="98f93-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="98f93-170">Si trabaja en varias plataformas, es preferible UTF-8 con BOM.</span><span class="sxs-lookup"><span data-stu-id="98f93-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="98f93-171">Si trabaja principalmente en contextos asociados a Linux, es preferible UTF-8 sin BOM.</span><span class="sxs-lookup"><span data-stu-id="98f93-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="98f93-172">Windows-1252 y Latín-1 son básicamente codificaciones heredadas que deben evitarse en la medida de lo posible.</span><span class="sxs-lookup"><span data-stu-id="98f93-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="98f93-173">Sin embargo, algunas aplicaciones más antiguas de Windows pueden dependen de ellas.</span><span class="sxs-lookup"><span data-stu-id="98f93-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="98f93-174">También merece la pena mencionar que la firma de scripts [depende de la codificación](https://github.com/PowerShell/PowerShell/issues/3466), lo cual significa que un tras cambio de codificación en un script firmado será necesario volver a firmar.</span><span class="sxs-lookup"><span data-stu-id="98f93-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="98f93-175">Configuración de VSCode</span><span class="sxs-lookup"><span data-stu-id="98f93-175">Configuring VSCode</span></span>

<span data-ttu-id="98f93-176">La codificación predeterminada de VSCode es UTF-8 sin BOM.</span><span class="sxs-lookup"><span data-stu-id="98f93-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="98f93-177">Para establecer la [Codificación de VSCode][], vaya a la configuración de VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) y establezca el ajuste `"files.encoding"`:</span><span class="sxs-lookup"><span data-stu-id="98f93-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="98f93-178">Algunos valores posibles son:</span><span class="sxs-lookup"><span data-stu-id="98f93-178">Some possible values are:</span></span>

- <span data-ttu-id="98f93-179">`utf8`: [UTF-8] sin BOM</span><span class="sxs-lookup"><span data-stu-id="98f93-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="98f93-180">`utf8bom`: [UTF-8] con BOM</span><span class="sxs-lookup"><span data-stu-id="98f93-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="98f93-181">`utf16le`: [UTF-16] little endian</span><span class="sxs-lookup"><span data-stu-id="98f93-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="98f93-182">`utf16be`: [UTF-16] big endian</span><span class="sxs-lookup"><span data-stu-id="98f93-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="98f93-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="98f93-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="98f93-184">Debe obtener una lista desplegable para esto en la vista de la interfaz gráfica de usuario, o los resultados de ello en la vista de JSON.</span><span class="sxs-lookup"><span data-stu-id="98f93-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="98f93-185">También puede agregar lo siguiente para detectar automáticamente la codificación, cuando sea posible:</span><span class="sxs-lookup"><span data-stu-id="98f93-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="98f93-186">Si no desea que estos ajustes afecten a todos los tipos de archivos, VSCode también permite configuraciones por idioma.</span><span class="sxs-lookup"><span data-stu-id="98f93-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="98f93-187">Cree un ajuste específico del lenguaje colocando los ajustes en un campo `[<language-name>]`.</span><span class="sxs-lookup"><span data-stu-id="98f93-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="98f93-188">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="98f93-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="98f93-189">Configuración de PowerShell</span><span class="sxs-lookup"><span data-stu-id="98f93-189">Configuring PowerShell</span></span>

<span data-ttu-id="98f93-190">La codificación predeterminada de PowerShell varía en función de la versión:</span><span class="sxs-lookup"><span data-stu-id="98f93-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="98f93-191">En PowerShell 6 +, la codificación predeterminada es UTF-8 sin BOM en todas las plataformas.</span><span class="sxs-lookup"><span data-stu-id="98f93-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="98f93-192">En Windows PowerShell, la codificación predeterminada es normalmente Windows 1252, una extensión de [Latín-1][], también conocida como ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="98f93-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="98f93-193">En PowerShell 5+ puede encontrar la codificación predeterminada con esto:</span><span class="sxs-lookup"><span data-stu-id="98f93-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="98f93-194">El siguiente [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) puede usarse para determinar la codificación que la sesión de PowerShell infiere para un script sin una BOM.</span><span class="sxs-lookup"><span data-stu-id="98f93-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="98f93-195">Es posible configurar PowerShell para que use una codificación determinada, de forma más general mediante la configuración del perfil.</span><span class="sxs-lookup"><span data-stu-id="98f93-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="98f93-196">Vea los artículos siguientes:</span><span class="sxs-lookup"><span data-stu-id="98f93-196">See the following articles:</span></span>

- <span data-ttu-id="98f93-197">[Respuesta sobre la codificación de PowerShell en StackOverflow](https://stackoverflow.com/a/40098904), de [@mklement0].</span><span class="sxs-lookup"><span data-stu-id="98f93-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="98f93-198">[Entrada de blog sobre cómo tratar la entrada UTF-8 sin BOM en PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/), de [@rkeithhill].</span><span class="sxs-lookup"><span data-stu-id="98f93-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="98f93-199">No es posible obligar a PowerShell a usar una codificación de entrada específica.</span><span class="sxs-lookup"><span data-stu-id="98f93-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="98f93-200">PowerShell 5.1 y versiones posteriores, de forma predeterminada, aplican la codificación Windows-1252 cuando no hay ninguna BOM.</span><span class="sxs-lookup"><span data-stu-id="98f93-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="98f93-201">Por motivos de interoperabilidad, es mejor guardar los scripts en un formato Unicode con una BOM.</span><span class="sxs-lookup"><span data-stu-id="98f93-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98f93-202">Cualquier otra herramienta que tenga y entre en contacto con scripts de PowerShell puede verse afectada por sus opciones de codificación o puede volver a codificar los scripts a otra codificación.</span><span class="sxs-lookup"><span data-stu-id="98f93-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="98f93-203">Scripts existentes</span><span class="sxs-lookup"><span data-stu-id="98f93-203">Existing scripts</span></span>

<span data-ttu-id="98f93-204">Es posible que los scripts que ya se encuentran en el sistema de archivos deban volver a codificarse a la nueva codificación elegida.</span><span class="sxs-lookup"><span data-stu-id="98f93-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="98f93-205">En la barra inferior de VSCode, verá la etiqueta UTF-8.</span><span class="sxs-lookup"><span data-stu-id="98f93-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="98f93-206">Haga clic en ella para abrir la barra de acciones y seleccione **Guardar con codificación**.</span><span class="sxs-lookup"><span data-stu-id="98f93-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="98f93-207">Ahora puede elegir una codificación de nueva para ese archivo.</span><span class="sxs-lookup"><span data-stu-id="98f93-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="98f93-208">Vea la información acerca de la [codificación de VSCode][] para obtener instrucciones completas.</span><span class="sxs-lookup"><span data-stu-id="98f93-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="98f93-209">Si necesita volver a codificar varios archivos, puede usar el siguiente script:</span><span class="sxs-lookup"><span data-stu-id="98f93-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="98f93-210">El entorno de scripting integrado (ISE) de PowerShell</span><span class="sxs-lookup"><span data-stu-id="98f93-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="98f93-211">Si también edita scripts con PowerShell ISE, deberá sincronizar la configuración de codificación allí.</span><span class="sxs-lookup"><span data-stu-id="98f93-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="98f93-212">El ISE debe respetar una BOM, pero también es posible usar el reflejo para [establecer la codificación](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="98f93-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="98f93-213">Tenga en cuenta que esto no se mantiene entre los inicios.</span><span class="sxs-lookup"><span data-stu-id="98f93-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="98f93-214">Software de control de código fuente</span><span class="sxs-lookup"><span data-stu-id="98f93-214">Source control software</span></span>

<span data-ttu-id="98f93-215">Algunas herramientas de control de código fuente, como GIT, ignoran las codificaciones; GIT simplemente realiza un seguimiento de los bytes.</span><span class="sxs-lookup"><span data-stu-id="98f93-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="98f93-216">Otras, como TFS o Mercurial, puede que no.</span><span class="sxs-lookup"><span data-stu-id="98f93-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="98f93-217">Existen también algunas herramientas basadas en GIT que se basan en la descodificación de texto.</span><span class="sxs-lookup"><span data-stu-id="98f93-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="98f93-218">Cuando esto sucede, asegúrese de llevar a cabo lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="98f93-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="98f93-219">Configure la codificación de texto en el control de código fuente para que coincida con la configuración de VSCode.</span><span class="sxs-lookup"><span data-stu-id="98f93-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="98f93-220">Asegúrese de que todos los archivos se incorporen al control de código fuente en la codificación adecuada.</span><span class="sxs-lookup"><span data-stu-id="98f93-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="98f93-221">Sea precavido con los cambios en la codificación que se reciben a través del control de código fuente.</span><span class="sxs-lookup"><span data-stu-id="98f93-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="98f93-222">Una señal clave de esto son unas diferencias que indican la presencia de cambios pero donde nada parece haber cambiado (porque los bytes han cambiado, pero los caracteres no).</span><span class="sxs-lookup"><span data-stu-id="98f93-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="98f93-223">Entornos de colaboradores</span><span class="sxs-lookup"><span data-stu-id="98f93-223">Collaborators' environments</span></span>

<span data-ttu-id="98f93-224">Como paso previo a la configuración del control de código fuente, asegúrese de que los colaboradores en cualquier archivo que comparta no tengan ninguna opción que reemplace la codificación volviendo a codificar los archivos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98f93-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="98f93-225">Otros programas</span><span class="sxs-lookup"><span data-stu-id="98f93-225">Other programs</span></span>

<span data-ttu-id="98f93-226">Cualquier otro programa que lea o escriba un script de PowerShell puede volver a codificarlo.</span><span class="sxs-lookup"><span data-stu-id="98f93-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="98f93-227">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="98f93-227">Some examples are:</span></span>

- <span data-ttu-id="98f93-228">Uso del Portapapeles para copiar y pegar un script.</span><span class="sxs-lookup"><span data-stu-id="98f93-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="98f93-229">Esto es habitual en escenarios como:</span><span class="sxs-lookup"><span data-stu-id="98f93-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="98f93-230">Copiar un script en una máquina virtual</span><span class="sxs-lookup"><span data-stu-id="98f93-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="98f93-231">Copiar un script fuera de un correo electrónico o una página web</span><span class="sxs-lookup"><span data-stu-id="98f93-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="98f93-232">Copiar un script dentro o fuera de un documento de Microsoft Word o PowerPoint</span><span class="sxs-lookup"><span data-stu-id="98f93-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="98f93-233">Otros editores de texto, como:</span><span class="sxs-lookup"><span data-stu-id="98f93-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="98f93-234">Notepad</span><span class="sxs-lookup"><span data-stu-id="98f93-234">Notepad</span></span>
  - <span data-ttu-id="98f93-235">vim</span><span class="sxs-lookup"><span data-stu-id="98f93-235">vim</span></span>
  - <span data-ttu-id="98f93-236">Cualquier otro editor de scripts de PowerShell</span><span class="sxs-lookup"><span data-stu-id="98f93-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="98f93-237">Utilidades de edición de texto, como:</span><span class="sxs-lookup"><span data-stu-id="98f93-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="98f93-238">Operadores de redirección de PowerShell, como `>` y `>>`</span><span class="sxs-lookup"><span data-stu-id="98f93-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="98f93-239">Programas de transferencia de archivos, como:</span><span class="sxs-lookup"><span data-stu-id="98f93-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="98f93-240">Un explorador web, al descargar scripts</span><span class="sxs-lookup"><span data-stu-id="98f93-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="98f93-241">Un recurso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="98f93-241">A file share</span></span>

<span data-ttu-id="98f93-242">Algunas de estas herramientas manejan bytes en lugar de texto, pero otros ofrecen configuraciones de codificación.</span><span class="sxs-lookup"><span data-stu-id="98f93-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="98f93-243">En los casos en que deba configurar una codificación, tendrá que hacer la misma codificación que su editor, para evitar problemas.</span><span class="sxs-lookup"><span data-stu-id="98f93-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="98f93-244">Otros recursos sobre la codificación en PowerShell</span><span class="sxs-lookup"><span data-stu-id="98f93-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="98f93-245">Hay algunas otras publicaciones interesantes sobre la codificación y la configuración de la codificación en PowerShell, que vale la pena leer:</span><span class="sxs-lookup"><span data-stu-id="98f93-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="98f93-246">[Resumen sobre la codificación de PowerShell en StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8), de [@mklement0]</span><span class="sxs-lookup"><span data-stu-id="98f93-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="98f93-247">Problemas anteriores abiertos en vscode-PowerShell para los problemas de codificación:</span><span class="sxs-lookup"><span data-stu-id="98f93-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="98f93-248">#1308</span><span class="sxs-lookup"><span data-stu-id="98f93-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="98f93-249">#1628</span><span class="sxs-lookup"><span data-stu-id="98f93-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="98f93-250">#1680</span><span class="sxs-lookup"><span data-stu-id="98f93-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="98f93-251">#1744</span><span class="sxs-lookup"><span data-stu-id="98f93-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="98f93-252">#1751</span><span class="sxs-lookup"><span data-stu-id="98f93-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="98f93-253">El clásico informe de *Joel on Software* acerca de Unicode</span><span class="sxs-lookup"><span data-stu-id="98f93-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="98f93-254">Codificación en .NET Standard</span><span class="sxs-lookup"><span data-stu-id="98f93-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[Latín-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[marca BOM]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Protocolo de servidor de lenguaje]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Codificación de VSCode]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
