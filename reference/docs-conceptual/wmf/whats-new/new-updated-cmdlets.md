---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Cmdlets nuevos y actualizados
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147595"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="a52ef-103">Cmdlets nuevos y actualizados</span><span class="sxs-lookup"><span data-stu-id="a52ef-103">New and updated cmdlets</span></span>

<span data-ttu-id="a52ef-104">Se agregaron cmdlets nuevos y se actualizaron los cmdlets existentes según los comentarios de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="a52ef-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="a52ef-105">Cmdlets Archive</span><span class="sxs-lookup"><span data-stu-id="a52ef-105">Archive cmdlets</span></span>

<span data-ttu-id="a52ef-106">Dos cmdlets nuevos, `Compress-Archive` y `Expand-Archive`, permiten comprimir y expandir archivos ZIP.</span><span class="sxs-lookup"><span data-stu-id="a52ef-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="a52ef-107">Para más información, consulte la documentación del módulo [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/).</span><span class="sxs-lookup"><span data-stu-id="a52ef-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="a52ef-108">Cmdlets del catálogo</span><span class="sxs-lookup"><span data-stu-id="a52ef-108">Catalog Cmdlets</span></span>

<span data-ttu-id="a52ef-109">Se agregaron dos cmdlets nuevos en el módulo Microsoft.PowerShell.Security.</span><span class="sxs-lookup"><span data-stu-id="a52ef-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="a52ef-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a52ef-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="a52ef-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="a52ef-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="a52ef-112">Estos generan y validan los archivos de catálogo de Windows.</span><span class="sxs-lookup"><span data-stu-id="a52ef-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="a52ef-113">Cmdlets Clipboard</span><span class="sxs-lookup"><span data-stu-id="a52ef-113">Clipboard cmdlets</span></span>

<span data-ttu-id="a52ef-114">`Get-Clipboard` y `Set-Clipboard` facilitan la transferencia de contenido desde y hasta una sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a52ef-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="a52ef-115">Los cmdlets Clipboard admiten imágenes, archivos de audio, listas de archivos y texto.</span><span class="sxs-lookup"><span data-stu-id="a52ef-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="a52ef-116">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="a52ef-116">For more information, see:</span></span>

- [<span data-ttu-id="a52ef-117">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="a52ef-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="a52ef-118">Set-Clipboard</span><span class="sxs-lookup"><span data-stu-id="a52ef-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="a52ef-119">Cmdlets de sintaxis de mensajes de cifrado (CMS)</span><span class="sxs-lookup"><span data-stu-id="a52ef-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="a52ef-120">Los cmdlets de sintaxis de mensajes de cifrado admiten el cifrado y descifrado de contenido mediante el formato estándar IETF para proteger los mensajes de forma criptográfica según se documenta en [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="a52ef-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="a52ef-121">El estándar de cifrado de CMS implementa la criptografía de clave pública, donde la clave usada para cifrar contenido (la *clave pública*) y la clave usada para descifrar contenido (la *clave privada*) son independientes.</span><span class="sxs-lookup"><span data-stu-id="a52ef-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="a52ef-122">La clave pública se puede compartir y no se considera información confidencial.</span><span class="sxs-lookup"><span data-stu-id="a52ef-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="a52ef-123">Todo el contenido cifrado con la clave pública solo se puede descifrar con la clave privada.</span><span class="sxs-lookup"><span data-stu-id="a52ef-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="a52ef-124">Para obtener más información, consulte [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography) (Criptografía mediante claves públicas).</span><span class="sxs-lookup"><span data-stu-id="a52ef-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="a52ef-125">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="a52ef-125">For more information see:</span></span>

- [<span data-ttu-id="a52ef-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="a52ef-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="a52ef-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="a52ef-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="a52ef-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="a52ef-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="a52ef-129">Los certificados requieren un identificador de uso de claves (EKU) único, como "Firma de código" o "Correo cifrado", para identificarlos como certificados de cifrado de datos en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a52ef-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="a52ef-130">Para ver certificados de cifrado de documentos en el proveedor de certificados, puede usar el parámetro dinámico **DocumentEncryptionCert** de `Get-ChildItem`:</span><span class="sxs-lookup"><span data-stu-id="a52ef-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="a52ef-131">Extraer y analizar objetos estructurados del contenido de la cadena</span><span class="sxs-lookup"><span data-stu-id="a52ef-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="a52ef-132">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="a52ef-132">ConvertFrom-String</span></span>

<span data-ttu-id="a52ef-133">El cmdlet `ConvertFrom-String` nuevo admite dos modos:</span><span class="sxs-lookup"><span data-stu-id="a52ef-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="a52ef-134">Análisis delimitado básico</span><span class="sxs-lookup"><span data-stu-id="a52ef-134">Basic delimited parsing</span></span>
- <span data-ttu-id="a52ef-135">Análisis controlado por ejemplos generados automáticamente</span><span class="sxs-lookup"><span data-stu-id="a52ef-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="a52ef-136">De forma predeterminada, el análisis delimitado divide la entrada en el espacio en blanco y asigna los nombres de propiedad a los grupos resultantes.</span><span class="sxs-lookup"><span data-stu-id="a52ef-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="a52ef-137">El parámetro **UpdateTemplate** guarda los resultados del algoritmo de aprendizaje en un comentario en el archivo de plantilla.</span><span class="sxs-lookup"><span data-stu-id="a52ef-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="a52ef-138">Esto convierte el proceso de aprendizaje (la fase más lenta) en un costo puntual.</span><span class="sxs-lookup"><span data-stu-id="a52ef-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="a52ef-139">La ejecución de `ConvertFrom-String` con una plantilla que contenga el algoritmo de aprendizaje codificado es ahora casi instantánea.</span><span class="sxs-lookup"><span data-stu-id="a52ef-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="a52ef-140">Para más información, consulte [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="a52ef-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="a52ef-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="a52ef-141">Convert-String</span></span>

<span data-ttu-id="a52ef-142">`Convert-String` permite proporcionar ejemplos de antes y después sobre cómo quiere que se vea el texto.</span><span class="sxs-lookup"><span data-stu-id="a52ef-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="a52ef-143">El cmdlet da formato al texto de manera automática.</span><span class="sxs-lookup"><span data-stu-id="a52ef-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="a52ef-144">Para más información, consulte [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="a52ef-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="a52ef-145">Actualizaciones del objeto FileInfo</span><span class="sxs-lookup"><span data-stu-id="a52ef-145">Updates to FileInfo object</span></span>

<span data-ttu-id="a52ef-146">La información de la versión de archivo puede ser errónea, especialmente en casos en el archivo se revisó.</span><span class="sxs-lookup"><span data-stu-id="a52ef-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="a52ef-147">WMF 5.0 agrega las nuevas propiedades de script **FileVersionRaw** y **ProductVersionRaw** a los objetos **FileInfo**.</span><span class="sxs-lookup"><span data-stu-id="a52ef-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="a52ef-148">Estas son las propiedades tal como se muestran para powershell.exe (teniendo en cuenta que $pid es el identificador del proceso de PowerShell):</span><span class="sxs-lookup"><span data-stu-id="a52ef-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="a52ef-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="a52ef-149">Format-Hex</span></span>

<span data-ttu-id="a52ef-150">`Format-Hex` permite ver datos de texto o binarios en formato hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="a52ef-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="a52ef-151">Para más información, consulte [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="a52ef-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="a52ef-152">Get-ChildItem tiene el parámetro -Depth</span><span class="sxs-lookup"><span data-stu-id="a52ef-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="a52ef-153">`Get-ChildItem` tiene ahora un parámetro **Depth** que se usa con **Recurse** para limitar la recursión:</span><span class="sxs-lookup"><span data-stu-id="a52ef-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="a52ef-154">Compatibilidad de los módulos para la declaración de intervalos de versiones (1.\*, etc.)</span><span class="sxs-lookup"><span data-stu-id="a52ef-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="a52ef-155">Ahora puede combinar **MinimumVersion** y **MaximumVersion** para importar un módulo dentro de un intervalo específico.</span><span class="sxs-lookup"><span data-stu-id="a52ef-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="a52ef-156">Los parámetros también admiten caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="a52ef-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="a52ef-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="a52ef-157">New-Guid</span></span>

<span data-ttu-id="a52ef-158">Hay muchos escenarios donde será necesario un identificador único.</span><span class="sxs-lookup"><span data-stu-id="a52ef-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="a52ef-159">El cmdlet `New-GUID` proporciona una manera sencilla de crear un GUID.</span><span class="sxs-lookup"><span data-stu-id="a52ef-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="a52ef-160">Parámetro NoNewLine</span><span class="sxs-lookup"><span data-stu-id="a52ef-160">NoNewLine parameter</span></span>

<span data-ttu-id="a52ef-161">`Out-File`, `Add-Content` y `Set-Content` ahora tienen un modificador **NoNewline** que omite una línea nueva después de la salida.</span><span class="sxs-lookup"><span data-stu-id="a52ef-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="a52ef-162">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a52ef-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="a52ef-163">Sin **NoNewline** especificado, cada fragmento estaría en una línea diferente:</span><span class="sxs-lookup"><span data-stu-id="a52ef-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="a52ef-164">Interactuar con los vínculos simbólicos mediante cmdlets Item mejorados</span><span class="sxs-lookup"><span data-stu-id="a52ef-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="a52ef-165">El cmdlet Item y algunos cmdlets relacionados se extendieron para admitir vínculos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="a52ef-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="a52ef-166">Archivos de vínculos simbólicos</span><span class="sxs-lookup"><span data-stu-id="a52ef-166">Symbolic link files</span></span>

<span data-ttu-id="a52ef-167">En este ejemplo, creamos un nuevo archivo de vínculo simbólico llamado MySymLinkFile.txt en C:\Temp que vincula a $pshome\profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="a52ef-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="a52ef-168">Los tres ejemplos generan el mismo resultado.</span><span class="sxs-lookup"><span data-stu-id="a52ef-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="a52ef-169">Directorios de vínculos simbólicos</span><span class="sxs-lookup"><span data-stu-id="a52ef-169">Symbolic link directories</span></span>

<span data-ttu-id="a52ef-170">En este ejemplo, creamos un directorio de vínculo simbólico llamado MySymLinkDir en C:\Temp que vincula a la carpeta $pshome.</span><span class="sxs-lookup"><span data-stu-id="a52ef-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="a52ef-171">Los tres ejemplos generan el mismo resultado.</span><span class="sxs-lookup"><span data-stu-id="a52ef-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="a52ef-172">Vínculos físicos</span><span class="sxs-lookup"><span data-stu-id="a52ef-172">Hard links</span></span>

<span data-ttu-id="a52ef-173">Las mismas combinaciones de **Path** y **Name** permitidas como se describió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a52ef-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="a52ef-174">Uniones de directorio</span><span class="sxs-lookup"><span data-stu-id="a52ef-174">Directory junctions</span></span>

<span data-ttu-id="a52ef-175">Las mismas combinaciones de **Path** y **Name** permitidas como se describió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a52ef-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="a52ef-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="a52ef-176">Get-ChildItem</span></span>

<span data-ttu-id="a52ef-177">`Get-ChildItem` ahora muestra una "l" en la propiedad **Mode** para indicar un directorio o archivo de vínculo simbólico.</span><span class="sxs-lookup"><span data-stu-id="a52ef-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="a52ef-178">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="a52ef-178">Remove-Item</span></span>

<span data-ttu-id="a52ef-179">Quitar los vínculos simbólicos funciona tal como quitar cualquier otro tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="a52ef-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="a52ef-180">Use el parámetro **Force** para quitar los archivos en el directorio de destino y el vínculo simbólico.</span><span class="sxs-lookup"><span data-stu-id="a52ef-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="a52ef-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="a52ef-181">New-TemporaryFile</span></span>

<span data-ttu-id="a52ef-182">A veces es necesario crear un archivo temporal en los scripts.</span><span class="sxs-lookup"><span data-stu-id="a52ef-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="a52ef-183">Ahora puede hacerlo con el cmdlet `New-TemporaryFile`:</span><span class="sxs-lookup"><span data-stu-id="a52ef-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="a52ef-184">Administración de conmutadores de red con PowerShell</span><span class="sxs-lookup"><span data-stu-id="a52ef-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="a52ef-185">Los cmdlet NetworkSwitch, introducidos en WMF 5.0, permiten aplicar la configuración de modificador, LAN virtual (VLAN) y básica del puerto del modificador de red de capa 2 a los modificadores de red certificados con el logotipo de Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="a52ef-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="a52ef-186">Con estos cmdlets puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a52ef-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="a52ef-187">Configuración global del modificador, como:</span><span class="sxs-lookup"><span data-stu-id="a52ef-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="a52ef-188">Establecer el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="a52ef-188">Set host name</span></span>
  - <span data-ttu-id="a52ef-189">Establecer el banner del modificador.</span><span class="sxs-lookup"><span data-stu-id="a52ef-189">Set switch banner</span></span>
  - <span data-ttu-id="a52ef-190">Mantener la configuración.</span><span class="sxs-lookup"><span data-stu-id="a52ef-190">Persist configuration</span></span>
  - <span data-ttu-id="a52ef-191">Habilitar o deshabilitar una característica.</span><span class="sxs-lookup"><span data-stu-id="a52ef-191">Enable or disable feature</span></span>

- <span data-ttu-id="a52ef-192">Configuración de VLAN:</span><span class="sxs-lookup"><span data-stu-id="a52ef-192">VLAN configuration:</span></span>
  - <span data-ttu-id="a52ef-193">Crear o quitar la VLAN.</span><span class="sxs-lookup"><span data-stu-id="a52ef-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="a52ef-194">Habilitar o deshabilitar la VLAN.</span><span class="sxs-lookup"><span data-stu-id="a52ef-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="a52ef-195">Enumerar la VLAN.</span><span class="sxs-lookup"><span data-stu-id="a52ef-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="a52ef-196">Establecer el nombre descriptivo de una VLAN.</span><span class="sxs-lookup"><span data-stu-id="a52ef-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="a52ef-197">Configuración de puerto de la capa 2:</span><span class="sxs-lookup"><span data-stu-id="a52ef-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="a52ef-198">Enumerar los puertos.</span><span class="sxs-lookup"><span data-stu-id="a52ef-198">Enumerate ports</span></span>
  - <span data-ttu-id="a52ef-199">Habilitar o deshabilitar los puertos.</span><span class="sxs-lookup"><span data-stu-id="a52ef-199">Enable or disable ports</span></span>
  - <span data-ttu-id="a52ef-200">Establecer los modos de puerto y sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="a52ef-200">Set port modes and properties</span></span>
  - <span data-ttu-id="a52ef-201">Agregar o asociar la VLAN al modo de tronco o acceso en el puerto.</span><span class="sxs-lookup"><span data-stu-id="a52ef-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="a52ef-202">Para más información, consulte la documentación de [NetworkSwitchManager](/powershell/module/networkswitchmanager/).</span><span class="sxs-lookup"><span data-stu-id="a52ef-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="a52ef-203">Generar cmdlets de PowerShell basados en un punto de conexión de OData con ODataUtils</span><span class="sxs-lookup"><span data-stu-id="a52ef-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="a52ef-204">El módulo ODataUtils permite la generación de cmdlets de PowerShell desde los puntos de conexión de REST que admiten OData.</span><span class="sxs-lookup"><span data-stu-id="a52ef-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="a52ef-205">El módulo Microsoft.PowerShell.ODataUtils incluye estas características:</span><span class="sxs-lookup"><span data-stu-id="a52ef-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="a52ef-206">Canalización de información adicional del punto de conexión del lado servidor al lado cliente.</span><span class="sxs-lookup"><span data-stu-id="a52ef-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="a52ef-207">Compatibilidad con la paginación del lado cliente.</span><span class="sxs-lookup"><span data-stu-id="a52ef-207">Client-side paging support</span></span>
- <span data-ttu-id="a52ef-208">Filtrado del lado servidor mediante el parámetro -Select.</span><span class="sxs-lookup"><span data-stu-id="a52ef-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="a52ef-209">Compatibilidad con los encabezados de solicitud web.</span><span class="sxs-lookup"><span data-stu-id="a52ef-209">Support for web request headers</span></span>

<span data-ttu-id="a52ef-210">Los cmdlets de proxy que genera el cmdlet `Export-ODataEndPointProxy` proporcionan información adicional del punto de conexión de OData del lado servidor en el flujo de **información**.</span><span class="sxs-lookup"><span data-stu-id="a52ef-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="a52ef-211">En el ejemplo siguiente, recuperamos el producto principal y capturamos la salida en la variable `$infoStream`.</span><span class="sxs-lookup"><span data-stu-id="a52ef-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="a52ef-212">Al especificar el parámetro **IncludeTotalResponseCount**, se obtiene el recuento total de todos los registros **Product** disponibles en el servidor.</span><span class="sxs-lookup"><span data-stu-id="a52ef-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="a52ef-213">Puede obtener los registros del servidor en lotes mediante la compatibilidad con la paginación del lado cliente.</span><span class="sxs-lookup"><span data-stu-id="a52ef-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="a52ef-214">Resulta útil cuando se necesita obtener una gran cantidad de datos del servidor a través de la red.</span><span class="sxs-lookup"><span data-stu-id="a52ef-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="a52ef-215">Los cmdlets de proxy generados admiten el parámetro **Select** que se usa como filtro para recibir solamente las propiedades de registro que el cliente necesita.</span><span class="sxs-lookup"><span data-stu-id="a52ef-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="a52ef-216">Este filtrado se produce en el servidor, lo que disminuye la cantidad de datos que se transfieren a través de la red.</span><span class="sxs-lookup"><span data-stu-id="a52ef-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="a52ef-217">El cmdlet `Export-ODataEndpointProxy`, y los cmdlets de proxy que genera, ahora admiten el parámetro **Headers**.</span><span class="sxs-lookup"><span data-stu-id="a52ef-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="a52ef-218">El encabezado se puede usar para canalizar la información adicional que espera el punto de conexión de OData.</span><span class="sxs-lookup"><span data-stu-id="a52ef-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="a52ef-219">En el ejemplo siguiente, una tabla hash que contiene una clave de suscripción se proporciona al parámetro **Headers**.</span><span class="sxs-lookup"><span data-stu-id="a52ef-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="a52ef-220">Este es un ejemplo típico de los servicios que están esperando una clave de suscripción para autenticación.</span><span class="sxs-lookup"><span data-stu-id="a52ef-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
