# Save-Script

El cmdlet Save-Script permite revisar el archivo de script, para lo cual debe guardarse en una ubicación especificada.

## Descripción

El cmdlet Save-Script guarda el script especificado.

## Sintaxis de cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## Referencia de la ayuda en línea de cmdlet

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## Comandos de ejemplo

### Ejemplo 1: guardar un script desde un repositorio
Este comando guarda la versión más reciente del script Fabrikam-ClientScript desde el repositorio GalleryINT en la carpeta local C:\ScriptSharingDemo.

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### Ejemplo 2: guardar una versión de un script mediante la canalización desde el cmdlet Find-Script

El primer comando busca la versión 1.5 de Fabrikam-ClientScript desde el repositorio GalleryINT y lo guarda en la carpeta C:\ScriptSharingDemo.

El segundo comando valida los metadatos de script guardados.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```


<!--HONumber=Aug16_HO3-->


