# Find-RoleCapability

Busca funcionalidades de rol en módulos.

## Descripción
El cmdlet Find-RoleCapability busca funcionalidades de rol de PowerShell en módulos. Find-RoleCapability busca en los módulos de los repositorios registrados. Para cada funcionalidad de rol que este cmdlet encuentre, se devuelve un objeto PSGetRoleCapabilityInfo. Puede pasar un objeto PSGetRoleCapabilityInfo al cmdlet Install-Module para instalar el módulo que contiene la funcionalidad de rol.
Las funcionalidades de rol de PowerShell definen los comandos, las aplicaciones, etc., que están disponibles para un usuario en un punto de conexión de Just Enough Administration (JEA). Las funcionalidades de rol se definen mediante archivos con la extensión .psrc.

- Find-RoleCapability puede filtrar con parámetros de versión: MinimumVersion, RequiredVersion y AllVersions.
  - Estos parámetros se excluyen mutuamente.
  - Estos parámetros de versión solo se permiten con el nombre de módulo único sin ningún carácter comodín.
  - Si no se especifica el parámetro RequiredVersion, Find-RoleCapability devuelve la versión más reciente del módulo que sea igual o mayor que la versión mínima especificada, o la versión más reciente del módulo si no se especifica ninguna versión mínima.
  - Si se especifica el parámetro RequiredVersion, Find-RoleCapability solo devuelve la versión del módulo que coincida exactamente con la versión especificada.
- Find-RoleCapability puede filtrar por los metadatos del módulo con el parámetro -Tag.
- Find-RoleCapability puede filtrar por el idioma de búsqueda específico del repositorio con el parámetro -Filter.
- Find-RoleCapability puede filtrar por los módulos de todos o algunos de los repositorios registrados.

## Sintaxis de cmdlet
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## Referencia de la ayuda en línea de cmdlet

[Find-RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## Comandos de ejemplo
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

<!--HONumber=Aug16_HO3-->


