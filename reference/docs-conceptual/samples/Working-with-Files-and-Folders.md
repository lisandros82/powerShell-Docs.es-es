---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabajar con archivos y carpetas
ms.openlocfilehash: 743e261d2f5e8bfa39f2731fca7fea6e5678c711
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "70215522"
---
# <a name="working-with-files-and-folders"></a>Trabajar con archivos y carpetas

Navegar a través de unidades de Windows PowerShell y manipular los elementos son procesos similares al de manipulación de archivos y carpetas en unidades de disco físico de Windows. En esta sección explicaremos cómo usar PowerShell para abordar tareas específicas de manipulación de archivos y carpetas.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Enumerar todos los archivos y carpetas de una carpeta

Puede obtener todos los elementos directamente dentro de una carpeta mediante **Get-ChildItem**. Agregue el parámetro **Force** opcional para mostrar elementos ocultos o del sistema. Por ejemplo, este comando muestra el contenido directo de la unidad C de Windows PowerShell (que es la misma que la unidad física de Windows C):

```powershell
Get-ChildItem -Path C:\ -Force
```

El comando muestra solo los elementos contenidos directamente, lo que se parece a usar el comando **DIR** de Cmd.exe o **ls** en un shell de UNIX. Para mostrar los elementos contenidos, también es preciso especificar el parámetro **-Recurse**. (Este proceso puede tardar mucho tiempo en completarse). Para mostrar todo el contenido de la unidad C:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** puede filtrar elementos con sus parámetros **Path**, **Filter**, **Include** y **Exclude**, pero estos suelen basarse solo en el nombre. Puede realizar un filtrado complejo basado en otras propiedades de elementos mediante **Where-Object**.

El siguiente comando busca todos los ejecutables en la carpeta Archivos de programa que se modificaron por última vez después del 1 de octubre de 2005, cuyo tamaño no es inferior a 1 megabyte ni superior a 10 megabytes:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Compartir archivos y carpetas

La copia se realiza con **Copy-Item**. El comando siguiente realiza una copia de seguridad de C:\\boot.ini en C:\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Si el archivo de destino ya existe, se produce un error en el intento de copia. Para sobrescribir un destino preexistente, use el parámetro **Force**:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Este comando funciona aunque el destino sea de solo lectura.

La copia de carpetas funciona del mismo modo. Este comando copia la carpeta C:\\temp\\test1 en la nueva carpeta c:\\temp\\DeleteMe de forma recursiva:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

También puede copiar una selección de elementos. El siguiente comando copia todos los archivos .txt de cualquier ubicación en c:\\data en c:\\temp\\text:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Todavía puede usar otras herramientas para realizar copias del sistema de archivos. Todos los objetos XCOPY, ROBOCOPY y COM, como **Scripting.FileSystemObject**, funcionan en Windows PowerShell. Por ejemplo, puede usar la clase **Scripting.FileSystem COM** de Windows Script Host para realizar una copia de seguridad de C:\\boot.ini en C:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Crear archivos y carpetas

La creación de nuevos elementos funciona igual en todos los proveedores de Windows PowerShell. Si un proveedor de Windows PowerShell tiene más de un tipo de elemento (por ejemplo, el proveedor FileSystem de Windows PowerShell distingue entre directorios y archivos), debe especificar el tipo de elemento.

Este comando crea una nueva carpeta C:\\temp\\Nueva carpeta:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Este comando crea un nuevo archivo vacío C:\\temp\\Nueva carpeta\\file.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Quitar todos los archivos y carpetas de una carpeta

Puede quitar los elementos contenidos mediante **Remove-Item**, pero se le pedirá que confirme la eliminación si el elemento contiene algo más. Por ejemplo, si intenta eliminar la carpeta C:\\temp\\DeleteMe que contiene otros elementos, Windows PowerShell le pedirá confirmación antes de eliminar la carpeta:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Si no quiere que se le solicite confirmación por cada elemento contenido, especifique el parámetro **Recurse**:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a>Asignación de una carpeta local como una unidad

También puede asignar una carpeta local mediante el comando **New-PSDrive**. El siguiente comando crea una unidad local P: con raíz en el directorio local Archivos de programa, visible solo desde la sesión de PowerShell:

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

Al igual que con las unidades de red, las unidades asignadas dentro de Windows PowerShell son visibles inmediatamente en el shell de Windows PowerShell.
Para crear una unidad asignada visible desde el Explorador de archivos, se necesita el parámetro **-Persist**. Sin embargo, solo se pueden usar rutas de acceso remotas con Persist.


## <a name="reading-a-text-file-into-an-array"></a>Leer un archivo de texto en una matriz

Uno de los formatos de almacenamiento más comunes para los datos de texto es en un archivo con líneas separadas que se tratan como elementos de datos distintos. El cmdlet **Get-Content** puede usarse para leer un archivo completo en un solo paso, como se muestra aquí:

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-Content** ya trata los datos leídos del archivo como una matriz con un elemento por línea de contenido del archivo. Para confirmarlo, compruebe la **longitud** del contenido devuelto:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Este comando es más útil para obtener listas de información en Windows PowerShell directamente. Por ejemplo, podría almacenar una lista de nombres de equipo o direcciones IP en un archivo C:\\temp\\domainMembers.txt, con un nombre en cada línea del archivo. Puede usar **Get-Content** para recuperar el contenido del archivo y colocarlo en la variable **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** es ahora una matriz que contiene un nombre de equipo en cada elemento.
