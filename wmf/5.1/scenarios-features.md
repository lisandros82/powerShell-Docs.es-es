---
title: "Nuevos escenarios y características de WMF 5.1 (versión preliminar)"
ms.date: 2016-07-06
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: dcccf6880873c3f5c1b58fb1a8c546901b173879
ms.openlocfilehash: 9341b7fc3feea20cc2434065c3e512d1a8dd2b54

---

# Nuevos escenarios y características de WMF 5.1 (versión preliminar) #

> Nota: Esta información es preliminar y está sujeta a cambios.

## Ediciones de PowerShell ##
A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

- **Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.
- **Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.

**Más información acerca de las ediciones de PowerShell**
- [Determine la edición de ejecución de PowerShell]()
- [Declare la compatibilidad de un módulo con versiones específicas de PowerShell]()
- [Filtre los resultados de Get-Module por CompatiblePSEditions]()
- [Impida la ejecución de scripts, a menos que se ejecuten en una edición compatible de PowerShell]()

## Caché de análisis de módulo ##
A partir de WMF 5.1, PowerShell proporciona control sobre el archivo que se utiliza para almacenar en la caché los datos acerca de un módulo, como los comandos que exporta.

De manera predeterminada, esta caché se almacena en el archivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
La caché normalmente se lee en el inicio al buscar un comando y se escribe en un subproceso en segundo plano después de que se importa un módulo.

Para cambiar la ubicación predeterminada de la caché, establezca la variable de entorno PSModuleAnalysisCachePath antes de iniciar PowerShell. Los cambios en esta variable de entorno solo afectarán a los procesos secundarios.
El valor debe asignar un nombre a una ruta de acceso completa (nombre de archivo incluido) en la que PowerShell tiene permiso para crear y escribir archivos.
Para deshabilitar la caché del archivo, establezca este valor en una ubicación no válida, como por ejemplo:

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Esto establece la ruta de acceso en un dispositivo no válido. Si PowerShell no puede escribir en la ruta de acceso, se devuelve ningún error, pero puede se pueden ver informes del error a través de un seguimiento:

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Al escribir en la caché, PowerShell buscará si hay módulos que no existen, con el fin de evitar que la caché sea demasiado grande.
A veces no se desea que se realicen estas comprobaciones, en cuyo caso se pueden desactivar estableciendo

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

El establecimiento de esta variable de entorno surtirá efecto de inmediato en el proceso actual.

##Especificación de la versión del módulo

En WMF 5.1, `using module` se comporta de la misma forma que las restantes construcciones relacionadas con módulos de PowerShell. Antes no había forma de especificar una versión concreta del módulo; si había varias versiones, aparecía un error.


En WMF 5.1:

* Puede utilizar la `ModuleSpecification`tabla hash[ ](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx). Esta tabla hash tiene el mismo formato que `Get-Module -FullyQualifiedName`.

**Ejemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Si hay varias versiones del módulo de multiplicar, PowerShell usa la **misma lógica de resolución** que `Import-Module` y no devuelve ningún error (el mismo comportamiento que `Import-Module` y `Import-DscResource`).

## Mejoras en la consola de PowerShell

En WMF 5.1, se han realizado los siguientes cambios en PowerShell.exe para mejorar la experiencia de la consola:

###Compatibilidad con VT100

Windows 10 agregó compatibilidad con [secuencias de escape de VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
PowerShell ignorará ciertas secuencias de escape con formato VT100 al calcular los anchos de tabla.

PowerShell también agregó una nueva API que puede utilizarse al dar formato al código para determinar si se admite VT100. Por ejemplo:

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
Esta es un [ejemplo](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo que se puede utilizar para resaltar las coincidencias de Select-String.
Guarde el ejemplo en un archivo denominado `MatchInfo.format.ps1xml` y para usarlo, en su perfil o en cualquier otro lugar, ejecute `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Tenga en cuenta que las secuencias de escape VT100 solo se admiten a partir de la actualización de aniversario de Windows 10, no en los sistemas anteriores.   

### Compatibilidad con el modo VI en PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) agrega compatibilidad con el modo VI. Para utilizar el modo VI, ejecute `Set-PSReadline -EditMode vi`.

### Stdin redirigido con entrada interactiva 

En versiones anteriores, a partir de PowerShell con `powershell -File -` se requería cuando se redirigía stdin y deseaba especificar los comandos de forma interactiva.

Con WMF 5.1, este opción, que es difícil de detectar, no es necesaria, y podrá iniciar PowerShell sin opciones, por ejemplo, `powershell`.

Tenga en cuenta que PSReadline no admite stdin redirigido y la experiencia de edición de línea de comandos integrada con stdin redirigido es extremadamente limitada, por ejemplo, las teclas de dirección no funcionan.  Una futura versión de PSReadline debería solucionar este problema.   

##Mejoras del motor de PowerShell

En WMF 5.1, se han implementado las siguientes mejoras al motor central de PowerShell:


## Rendimiento ##

El rendimiento ha mejorado en algunas áreas importantes:

- Inicio
- La canalización en cmdlets como ForEach-Object y Where-Object es aproximadamente un 50 % más rápido 

Algunas mejoras del ejemplo (los resultados pueden variar en función del hardware): 

| Escenario | Tiempo de 5.0 (ms) | Tiempo de 5.1 (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Primera ejecución de PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Caché de análisis de comandos integrada: `powershell -command "Unknown-Command"` | 7000 | 520 |
| `1..1000000 | % { }` | 1400 | 750 |
  
> [!NOTE]  
> Un cambio relacionado con el inicio puede afectar a algunos escenarios no compatibles. PowerShell ya no lee los archivos `$pshome\*.ps1xml`: estos archivos se han convertido en C# para evitar la sobrecarga de archivos y de la CPU que supone procesar los archivos XML. Los archivos aún existen para proporcionar compatibilidad con V2 en paralelo, por lo que si se cambia el contenido de los archivos, esto no tendrá ningún efecto en V5, solo en V2. Tenga en cuenta que el cambio del contenido de estos archivos nunca ha sido un escenario compatible.

Otro cambio visible es la forma en que PowerShell almacena en caché tanto comandos exportados como otra información de los módulos instalados en un sistema. Antes, la memoria caché se almacenaba en el directorio `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. En WMF 5.1, la memoria caché es un único archivo `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Para más información, consulte [analysis_cache.md]().



## Correcciones de errores ##

Se han corregido los siguientes errores importantes:

### La detección automática de módulos usa plenamente `$env:PSModulePath` ###

La detección automática de módulos (carga de módulos automáticamente sin un cmdlet Import-Module explícito al llamar a un comando) se introdujo en WMF 3. Cuando se introdujo, PowerShell comprobaba los comandos en `$PSHome\Modules` antes de usar `$env:PSModulePath`.

WMF 5.1 cambia este comportamiento para usar `$env:PSModulePath` completamente. Esto permite que un módulo creado por el usuario que define los comandos que proporciona PowerShell (por ejemplo, `Get-ChildItem`) se cargue automáticamente y reemplace correctamente el comando integrado.

### El redireccionamiento de archivos deja de integrar como parte del código `-Encoding Unicode` ###

En todas las versiones anteriores de PowerShell, era imposible controlar la codificación de archivos utilizada por el operador de redireccionamiento de archivos (p. ej., `get-childitem > out.txt` porque PowerShell agregó `-Encoding Unicode`).

A partir de WMF 5.1, se puede cambiar la codificación de archivos del redireccionamiento mediante el establecimiento de `$PSDefaultParameterValues`, p. ej.

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Se ha corregido una regresión en el acceso de los miembros de `System.Reflection.TypeInfo` ###

Una regresión introducida en WMF 5.0 interrumpía el acceso de los miembros de `System.Reflection.RuntimeType`, por ejemplo, `[int].ImplementedInterfaces`.
Este error se ha corregido en WMF 5.1.


### Se han corregido algunos problemas con objetos COM ###

WMF 5.0 introdujo un nuevo enlazador COM para invocar métodos en objetos COM y acceder a propiedades de objetos COM.
Este nuevo enlazador ha mejorado considerablemente el rendimiento, pero también ha presentado algunos errores que se han corregido en WMF 5.1.

#### Las conversiones de argumentos no siempre se realizaban correctamente ####

En el ejemplo siguiente:

```
$obj = new-object -com wscript.shell
$obj.SendKeys([char]173)
```

El método SendKeys espera una cadena, pero PowerShell no ha convertido el carácter en una cadena, lo que aplaza la conversión a IDispatch:: Invoke, que usa VariantChangeType para realizar la conversión, lo que en este ejemplo provocó el envío de las claves '1', '7' y '3', en lugar de la clave Volume.Mute, que era la que se esperaba.

#### Los objetos COM enumerables no siempre se controlan correctamente ####

PowerShell normalmente enumera la mayoría de los objetos enumerables, pero una regresión introducida en WMF 5.0 impidió la enumeración de objetos COM que implementan IEnumerable.  Por ejemplo:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

En el ejemplo anterior, WMF 5.0 escribió incorrectamente Scripting.Dictionary en la canalización, en lugar de enumerar los pares clave/valor.


### `[ordered]` no se permitía en las clases ###

WMF5 introdujo clases con una validación de los literales de tipo que se usan en las clases.  `[ordered]` parece un literal de tipo, pero no es un verdadero tipo .Net.  WMF5 informaba incorrectamente de un error en `[ordered]` dentro de una clase:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### Los temas de ayuda con varias versiones no funcionan ###

Antes de WMF 5.1, si había varias versiones de un módulo instaladas y todas compartían un tema de ayuda, por ejemplo, about_PSReadline, `help about_PSReadline` devolvía varios temas sin ninguna forma obvia de ver la ayuda real.

WMF 5.1 corrige este problema, para lo que devuelve la ayuda de la versión más reciente del tema.

Get-Help no proporciona una forma de especificar para qué versión se desea la ayuda. Para solucionar este problema, navegue hasta el directorio modules y vea la ayuda directamente con una herramienta como su editor favorito. 

## Mejoras de OneGet
WMF 5.1 incluye varias correcciones y mejoras para solucionar algunos problemas con que se topaban los usuarios en la versión 5.0 de WMF. 

###Alias version quitado

**Escenario**: si tiene las versiones 1.0 y 2.0 de un paquete, P1, instaladas en el sistema y desea desinstalar la versión 1.0, ejecutaría "uninstall-package -name P1 -version 1.0" y esperaría que se desinstalara la versión 1.0 después de ejecutar el cmdlet. Sin embargo, el resultado es que se desinstala la versión 2.0. 
    
Esto se debe a que el parámetro "-version" es un alias del parámetro"-minimumversion". Cuando OneGet busca un paquete cualificado con la versión mínima 1.0, devuelve la versión más reciente. Este comportamiento es el esperable en los casos normales, ya que el resultado que se suele desear es que se busque la versión más reciente. Sin embargo, no se debe aplicar al caso uninstall-package.
    
**Solución**: en WMF 5.1, se quita completamente el alias - version en OneGet y PowerShellGet. 

###Varios mensajes para arrancar el proveedor de NuGet

**Escenario**: la primera vez que se ejecutan Find-Module, Install-module u otro cmdlet de OneGet en un equipo, OneGet intenta arrancar el proveedor de NuGet, ya que el proveedor de PowerShellGet también usa el proveedor de NuGet para descargar los módulos de PowerShell. Luego, OneGet pide permiso al usuario para instalar al proveedor de NuGet. Una vez que el usuario selecciona "yes" en el arranque, se instalará la versión más reciente del proveedor de NuGet. 
    
Sin embargo, en algunos casos, si tiene una versión anterior del proveedor de NuGet instalada en el equipo, a veces se carga primero la versión anterior de NuGet en la sesión de PowerShell (esa es la condición de carrera en OneGet). Sin embargo, PowerShellGet requiere la versión posterior del proveedor de NuGet para funcionar, por lo que PowerShellGet solicita OneGet para volver a arrancar el proveedor de NuGet. Esto genera varios mensajes para arrancar el proveedor de NuGet.

**Solución**: en WMF 5.1, OneGet carga la versión más reciente del proveedor de NuGet para evitar varios mensajes de arranque del proveedor de NuGet.

Otra posible solución es la eliminación manual de la versión anterior del proveedor de NuGet (NuGet-Anycpu.exe) desde $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies


###Compatibilidad con OneGet en equipos con acceso solo a la intranet

**Escenario**: en WMF 5.0, OneGet no era compatible con equipos que solo tuvieran acceso a la intranet (pero no a Internet).

**Solución**: en WMF 5.1, puede seguir estos pasos para que los equipos de la intranet usen OneGet:

1. Descargue el proveedor de NuGet desde otro equipo con conexión a Internet mediante Install-PackageProvider NuGet.

2. Busque el proveedor de NuGet en $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget o $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget. 

3. Copie los archivos binarios a una carpeta o ubicación de recurso compartido de red a la que pueda acceder el equipo de la intranet y luego instale el proveedor de NuGet con "Install-PackageProvider NuGet -Source <Path to folder>".


###Mejoras del registro de eventos

Al instalar paquetes, se cambia el estado del equipo. En WMF 5.1, OneGet registra eventos en el registro de eventos de Windows para las actividades de instalar, desinstalar y guardar paquete. El canal Evento es lo mismo que para PowerShell, es decir, Microsoft-Windows-PowerShell, operativo.

###Compatibilidad con la autenticación básica

En WMF 5.1, OneGet admite la búsqueda e instalación de paquetes de un repositorio que requiera autenticación básica. Puede proporcionar sus credenciales a los cmdlets Find-Package e Install-Package. Por ejemplo:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
###Compatibilidad para usar OneGet detrás de un proxy

En WMF 5.1, OneGet usa nuevos parámetros de proxy: - ProxyCredential y - Proxy. Mediante estos parámetros, es posible especificar la dirección URL y las credenciales del proxy en los cmdlets de OneGet. De forma predeterminada, se utiliza la configuración del proxy del sistema. Por ejemplo:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO1-->


