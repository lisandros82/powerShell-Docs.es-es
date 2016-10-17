---
title: "plantilla de ejemplo de una característica o escritura de escenario"
contributor: KeithB
translationtype: Human Translation
ms.sourcegitcommit: 8c55ca4b972c8d708a09b922f27eec585ddc33d0
ms.openlocfilehash: 025565404b60cebefac27e51c70d70edb5e47bc9

---

>Nota: Especifique un título descriptivo propuesto y una breve descripción

## Mejoras de PowerShellGet ##
Los cmdlets del módulo PowerShellGet se han actualizado considerablemente en WMF 5.1. Ahora se admiten los escenarios siguientes:

- **Compatibilidad con proxy:** ahora se admite el uso de los cmdlets PowerShellGet con un proxy interno, con la adición de los parámetros Proxy y ProxyCredential a todos los cmdlets Find-, Install-, Save- y Publish- del módulo PowerShellGet (por ejemplo, Find-Module, Install-Module, Save-Module y Publish-Module). 
- **Aplicación de la firma de catálogo:** todos los cmdlets PowerShellGet ahora buscan y aplican la actualización de módulos firmados. Los cmdlets PowerShellGet comprobarán los módulos firmados mediante los nuevos cmdlets Catalog para asegurarse de que el módulo no se ha modificado en tránsito y de que las actualizaciones del módulo solo proceden del publicador original. Esto afecta a los cmdlets Install-Module y Update-Module. 
- **Funcionalidades de rol para compartir y adquirir:** las funcionalidades de rol son las definiciones de punto de conexión que se usan para configurar Just Enough Administration para restringir, y se compartirán a través de la Galería de PowerShell en módulos de PowerShell. Los cmdlets incluyen Find-RoleCapability y New-PSRoleCapabilityFile. 
- **Buscar comando:** Find-Command permite a los usuarios localizar el módulo en la Galería de PowerShell que contenga el comando que buscan. 
- **Repositorios autenticados:** la fuente de administración de paquetes de Visual Studio requiere autenticación, algo que ahora se admite mediante los cmdlets PowerShellGet.

A través de los comentarios de los usuarios se han identificado áreas adicionales de mejora que se han abordado en la versión 5.1, entre las que se incluyen las siguientes:

- **Cambios de Install-Script:** la ubicación que Install-Script usa no se agrega a la ruta de acceso de usuario automáticamente en la versión 5.1. Este cambio se realizó en la versión independiente de PowerShellGet y ahora se incluye en WMF 5.1.
- **Agregar campos de metadatos a scripts existentes:** se puede usar Update-ScriptFileInfo en scripts existentes para agregar los campos de metadatos predeterminados que se necesitan para publicar en PowerShellGallery. Antes, los usuarios debían combinar esto manualmente en un script existente.
- **Publicar un módulo con una versión inferior en la Galería:** ahora es posible publicar un módulo con un número de versión inferior al de la última versión superior en la Galería mediante Publish-Module. Si un publicador lanzaba la versión 2.0.0 de su módulo con cambios importantes respecto a las versiones 1.x, no podía lanzar fácilmente una corrección para la versión 1.5.0. Ahora, puede publicar una versión 1.5.1, lo que mejorará la compatibilidad para el mantenimiento de los módulos de la Galería de PowerShell. 
- **Comprobar la sobrescritura de comandos al instalar scripts y módulos:** Install-Module e Install-Script ahora comprobarán si contienen comandos que ya están presentes en el sistema y, si es así, generarán un error de manera predeterminada. 
- **Arrancar Nuget en cmdlets Publish-:** antes no se podía instalar automáticamente el proveedor de Nuget al usar Publish-Module o Publish-Script, lo que dificultaba determinadas tareas de automatización. Ahora, los usuarios pueden agregar -Force a los comandos Publish- para omitir la confirmación. 

>Nota: Los detalles adicionales sobre nuevos conceptos, implementación, ejemplos, etc., se deben vincular a la documentación técnica canónica

**Más información sobre el uso de PowerShellGet**
- [About-CatalogSigning]()
- []()
- [Filtre los resultados de Get-Module por CompatiblePSEditions]()
- [Impida la ejecución de scripts, a menos que se ejecuten en una edición compatible de PowerShell]()






<!--HONumber=Aug16_HO3-->


