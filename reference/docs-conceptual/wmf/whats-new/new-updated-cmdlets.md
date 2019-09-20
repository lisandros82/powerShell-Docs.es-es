---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Cmdlets nuevos y actualizados
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147595"
---
# <a name="new-and-updated-cmdlets"></a>Cmdlets nuevos y actualizados

Se agregaron cmdlets nuevos y se actualizaron los cmdlets existentes según los comentarios de la comunidad.

## <a name="archive-cmdlets"></a>Cmdlets Archive

Dos cmdlets nuevos, `Compress-Archive` y `Expand-Archive`, permiten comprimir y expandir archivos ZIP.

Para más información, consulte la documentación del módulo [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/).

## <a name="catalog-cmdlets"></a>Cmdlets del catálogo

Se agregaron dos cmdlets nuevos en el módulo Microsoft.PowerShell.Security.

- [New-FileCatalog](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [Test-FileCatalog](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

Estos generan y validan los archivos de catálogo de Windows.

## <a name="clipboard-cmdlets"></a>Cmdlets Clipboard

`Get-Clipboard` y `Set-Clipboard` facilitan la transferencia de contenido desde y hasta una sesión de Windows PowerShell. Los cmdlets Clipboard admiten imágenes, archivos de audio, listas de archivos y texto.

Para obtener más información, consulte:

- [Get-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [Set-Clipboard](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cmdlets de sintaxis de mensajes de cifrado (CMS)

Los cmdlets de sintaxis de mensajes de cifrado admiten el cifrado y descifrado de contenido mediante el formato estándar IETF para proteger los mensajes de forma criptográfica según se documenta en [RFC5652](https://tools.ietf.org/html/rfc5652.html).

El estándar de cifrado de CMS implementa la criptografía de clave pública, donde la clave usada para cifrar contenido (la *clave pública*) y la clave usada para descifrar contenido (la *clave privada*) son independientes.

La clave pública se puede compartir y no se considera información confidencial. Todo el contenido cifrado con la clave pública solo se puede descifrar con la clave privada. Para obtener más información, consulte [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography) (Criptografía mediante claves públicas).

Para obtener más información, vea:

- [Get-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [Unprotect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

Los certificados requieren un identificador de uso de claves (EKU) único, como "Firma de código" o "Correo cifrado", para identificarlos como certificados de cifrado de datos en PowerShell. Para ver certificados de cifrado de documentos en el proveedor de certificados, puede usar el parámetro dinámico **DocumentEncryptionCert** de `Get-ChildItem`:

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a>Extraer y analizar objetos estructurados del contenido de la cadena

### <a name="convertfrom-string"></a>ConvertFrom-String

El cmdlet `ConvertFrom-String` nuevo admite dos modos:

- Análisis delimitado básico
- Análisis controlado por ejemplos generados automáticamente

De forma predeterminada, el análisis delimitado divide la entrada en el espacio en blanco y asigna los nombres de propiedad a los grupos resultantes.

El parámetro **UpdateTemplate** guarda los resultados del algoritmo de aprendizaje en un comentario en el archivo de plantilla. Esto convierte el proceso de aprendizaje (la fase más lenta) en un costo puntual. La ejecución de `ConvertFrom-String` con una plantilla que contenga el algoritmo de aprendizaje codificado es ahora casi instantánea.

Para más información, consulte [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).

### <a name="convert-string"></a>Convert-String

`Convert-String` permite proporcionar ejemplos de antes y después sobre cómo quiere que se vea el texto. El cmdlet da formato al texto de manera automática.

Para más información, consulte [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).

## <a name="updates-to-fileinfo-object"></a>Actualizaciones del objeto FileInfo

La información de la versión de archivo puede ser errónea, especialmente en casos en el archivo se revisó. WMF 5.0 agrega las nuevas propiedades de script **FileVersionRaw** y **ProductVersionRaw** a los objetos **FileInfo**.
Estas son las propiedades tal como se muestran para powershell.exe (teniendo en cuenta que $pid es el identificador del proceso de PowerShell):

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a>Format-Hex

`Format-Hex` permite ver datos de texto o binarios en formato hexadecimal.

Para más información, consulte [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).

## <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem tiene el parámetro -Depth

`Get-ChildItem` tiene ahora un parámetro **Depth** que se usa con **Recurse** para limitar la recursión:

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a>Compatibilidad de los módulos para la declaración de intervalos de versiones (1.*, etc.)

Ahora puede combinar **MinimumVersion** y **MaximumVersion** para importar un módulo dentro de un intervalo específico. Los parámetros también admiten caracteres comodín.

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

## <a name="new-guid"></a>New-Guid

Hay muchos escenarios donde será necesario un identificador único. El cmdlet `New-GUID` proporciona una manera sencilla de crear un GUID.

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a>Parámetro NoNewLine

`Out-File`, `Add-Content` y `Set-Content` ahora tienen un modificador **NoNewline** que omite una línea nueva después de la salida. Por ejemplo:

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

Sin **NoNewline** especificado, cada fragmento estaría en una línea diferente:

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

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a>Interactuar con los vínculos simbólicos mediante cmdlets Item mejorados

El cmdlet Item y algunos cmdlets relacionados se extendieron para admitir vínculos simbólicos.

### <a name="symbolic-link-files"></a>Archivos de vínculos simbólicos

En este ejemplo, creamos un nuevo archivo de vínculo simbólico llamado MySymLinkFile.txt en C:\Temp que vincula a $pshome\profile.ps1. Los tres ejemplos generan el mismo resultado.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a>Directorios de vínculos simbólicos

En este ejemplo, creamos un directorio de vínculo simbólico llamado MySymLinkDir en C:\Temp que vincula a la carpeta $pshome. Los tres ejemplos generan el mismo resultado.

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a>Vínculos físicos

Las mismas combinaciones de **Path** y **Name** permitidas como se describió anteriormente.

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a>Uniones de directorio

Las mismas combinaciones de **Path** y **Name** permitidas como se describió anteriormente.

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a>Get-ChildItem

`Get-ChildItem` ahora muestra una "l" en la propiedad **Mode** para indicar un directorio o archivo de vínculo simbólico.

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

### <a name="remove-item"></a>Remove-Item

Quitar los vínculos simbólicos funciona tal como quitar cualquier otro tipo de elemento.

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

Use el parámetro **Force** para quitar los archivos en el directorio de destino y el vínculo simbólico.

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a>New-TemporaryFile

A veces es necesario crear un archivo temporal en los scripts. Ahora puede hacerlo con el cmdlet `New-TemporaryFile`:

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a>Administración de conmutadores de red con PowerShell

Los cmdlet NetworkSwitch, introducidos en WMF 5.0, permiten aplicar la configuración de modificador, LAN virtual (VLAN) y básica del puerto del modificador de red de capa 2 a los modificadores de red certificados con el logotipo de Windows Server 2012 R2. Con estos cmdlets puede hacer lo siguiente:

- Configuración global del modificador, como:
  - Establecer el nombre de host.
  - Establecer el banner del modificador.
  - Mantener la configuración.
  - Habilitar o deshabilitar una característica.

- Configuración de VLAN:
  - Crear o quitar la VLAN.
  - Habilitar o deshabilitar la VLAN.
  - Enumerar la VLAN.
  - Establecer el nombre descriptivo de una VLAN.

- Configuración de puerto de la capa 2:
  - Enumerar los puertos.
  - Habilitar o deshabilitar los puertos.
  - Establecer los modos de puerto y sus propiedades.
  - Agregar o asociar la VLAN al modo de tronco o acceso en el puerto.

Para más información, consulte la documentación de [NetworkSwitchManager](/powershell/module/networkswitchmanager/).

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Generar cmdlets de PowerShell basados en un punto de conexión de OData con ODataUtils

El módulo ODataUtils permite la generación de cmdlets de PowerShell desde los puntos de conexión de REST que admiten OData. El módulo Microsoft.PowerShell.ODataUtils incluye estas características:

- Canalización de información adicional del punto de conexión del lado servidor al lado cliente.
- Compatibilidad con la paginación del lado cliente.
- Filtrado del lado servidor mediante el parámetro -Select.
- Compatibilidad con los encabezados de solicitud web.

Los cmdlets de proxy que genera el cmdlet `Export-ODataEndPointProxy` proporcionan información adicional del punto de conexión de OData del lado servidor en el flujo de **información**.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

En el ejemplo siguiente, recuperamos el producto principal y capturamos la salida en la variable `$infoStream`.

Al especificar el parámetro **IncludeTotalResponseCount**, se obtiene el recuento total de todos los registros **Product** disponibles en el servidor.

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

Puede obtener los registros del servidor en lotes mediante la compatibilidad con la paginación del lado cliente. Resulta útil cuando se necesita obtener una gran cantidad de datos del servidor a través de la red.

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

Los cmdlets de proxy generados admiten el parámetro **Select** que se usa como filtro para recibir solamente las propiedades de registro que el cliente necesita. Este filtrado se produce en el servidor, lo que disminuye la cantidad de datos que se transfieren a través de la red.

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

El cmdlet `Export-ODataEndpointProxy`, y los cmdlets de proxy que genera, ahora admiten el parámetro **Headers**. El encabezado se puede usar para canalizar la información adicional que espera el punto de conexión de OData.

En el ejemplo siguiente, una tabla hash que contiene una clave de suscripción se proporciona al parámetro **Headers**. Este es un ejemplo típico de los servicios que están esperando una clave de suscripción para autenticación.

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
