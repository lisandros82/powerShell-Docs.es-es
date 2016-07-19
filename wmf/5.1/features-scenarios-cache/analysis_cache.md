# Caché de análisis de módulo #

A partir de la versión 5.1, PowerShell proporciona el siguiente control sobre el archivo que se utiliza para almacenar en la caché los datos acerca de un módulo, como los comandos que exporta.

De manera predeterminada, esta caché se almacena en el archivo `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
La caché normalmente se lee en el inicio al buscar un comando y se escribe en un subproceso en segundo plano después de que se importa un módulo.

Para cambiar la ubicación predeterminada de la caché, establezca la variable de entorno PSModuleAnalysisCachePath antes de iniciar PowerShell. Los cambios en esta variable de entorno solo afectarán a los procesos secundarios.
El valor debe asignar un nombre a una ruta de acceso completa (nombre de archivo incluido) en la que PowerShell tiene permiso para crear y escribir archivos.
Para deshabilitar la caché del archivo, este valor se puede establecer en una ubicación no válida, como por ejemplo

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Esto establece la ruta de acceso en un dispositivo no válido. No se devuelve un error si PowerShell no puede escribir en la ruta de acceso, aunque puede se pueden ver informes del error a través de un seguimiento:

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Al escribir en la caché, PowerShell buscará si hay módulos que no existen, con el fin de evitar que la caché sea demasiado grande.
A veces no se desea que se realicen estas comprobaciones, en cuyo caso se pueden desactivar estableciendo

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

El establecimiento de esta variable de entorno surtirá efecto de inmediato en el proceso actual.

<!--HONumber=Jul16_HO1-->


