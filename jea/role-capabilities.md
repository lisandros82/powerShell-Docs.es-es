---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Funcionalidades de rol de JEA
ms.openlocfilehash: b93d206680de485d6cb7a8cb26d63afda5bf8421
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055060"
---
# <a name="jea-role-capabilities"></a>Funcionalidades de rol de JEA

> Se aplica a: Windows PowerShell 5.0

Al crear un punto de conexión de JEA, deberá definir una o varias "funcionalidades de rol" que describan *qué* puede hacer un usuario en una sesión de JEA.
Una funcionalidad de rol es un archivo de datos de PowerShell con la extensión .psrc que muestra los cmdlets, las funciones, los proveedores y los programas externos que deben estar disponibles para los usuarios que se conectan.

En este tema, se describe cómo crear un archivo de funcionalidad de rol de PowerShell para los usuarios de JEA.

## <a name="determine-which-commands-to-allow"></a>Determinar los comandos permitidos

El primer paso al crear un archivo de funcionalidad de rol es tener en cuenta a qué necesitarán acceso los usuarios a los que se les asigna el rol.
Este proceso de recopilación de requisitos puede llevar un tiempo, pero es un proceso muy importante.
Conceder acceso a los usuarios a muy pocos cmdlets y funciones puede impedirles llevar a cabo su trabajo.
Permitir el acceso a demasiados cmdlets y funciones puede ocasionar que los usuarios hagan más de lo esperado con sus privilegios de administrador implícitos, lo que empeora su posición en materia de seguridad.

La forma de afrontar este proceso dependerá de la organización y los objetivos, pero las siguientes sugerencias pueden ayudarle a asegurarse de ir por el buen camino.

1. **Identifique** los comandos que usan los usuarios para realizar su trabajo. Esto puede implicar encuestar al personal de TI, comprobar los scripts de automatización o analizar registros o transcripciones de sesión de PowerShell.
2. **Actualice** el uso de herramientas de línea de comandos por equivalentes de PowerShell, siempre que sea posible, para tener la mejor experiencia de personalización de JEA y auditoría. No se pueden restringir programas externos con la misma minuciosidad que los cmdlets y las funciones que son nativos de PowerShell en JEA.
3. **Restrinja** el ámbito de los cmdlets si es necesario para permitir solo parámetros o valores de parámetros específicos. Esto es especialmente importante si los usuarios solo deberían poder administrar parte de un sistema.
4. **Cree** funciones personalizadas para reemplazar comandos complejos o que sean difíciles de restringir en JEA. Una función sencilla que encapsule un comando complejo o aplique lógica de validación adicional puede ofrecer un mayor control para simplificar los administradores y usuarios finales.
5. **Pruebe** la lista con ámbito de los comandos permitidos con los usuarios o los servicios de automatización y ajústela según sea necesario.

Es importante recordar que los comandos en una sesión de JEA se ejecutan a menudo con privilegios de administrador o, si no, con privilegios elevados.
Es importante seleccionar los comandos disponibles para asegurarse de que el punto de conexión de JEA no permita que el usuario que se conecta eleve sus permisos.
A continuación se muestran algunos ejemplos de comandos que pueden usarse de forma malintencionada si se permiten en un estado sin restricciones.
Tenga en cuenta que esta lista no es exhaustiva y solo se debe usar a modo de precaución previa.

### <a name="examples-of-potentially-dangerous-commands"></a>Ejemplos de comandos potencialmente peligrosos

Riesgo | Ejemplo | Comandos relacionados
-----|---------|-----------------
Conceder al usuario que se conecta privilegios de administrador para omitir JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Ejecutar código arbitrario, como malware, vulnerabilidad de seguridad o scripts personalizados para omitir protecciones | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Crear un archivo de funcionalidad de rol

Puede crear un archivo de funcionalidad de rol de PowerShell con el cmdlet [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile).

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

El archivo de funcionalidad de rol resultante se puede abrir en un editor de texto y modificar para permitir los comandos que quiera para el rol.
La documentación de ayuda de PowerShell contiene varios ejemplos de cómo configurar el archivo.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Permitir funciones y cmdlets de PowerShell

Para autorizar a los usuarios a ejecutar funciones o cmdlets de PowerShell, agregue el nombre del cmdlet o de la función en los campos VisibleCmdlets o VisibleFunctions.
Si no está seguro de si un comando es un cmdlet o una función, puede ejecutar `Get-Command <name>` y comprobar la propiedad "CommandType" de la salida.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

A veces, el ámbito de un cmdlet o una función específicos es demasiado amplio para las necesidades de los usuarios.
Por ejemplo, es probable que un administrador de DNS solo necesite acceso para reiniciar el servicio DNS.
En un entorno de varios inquilinos en el que a los inquilinos se les concede acceso a herramientas de administración de autoservicio, los inquilinos deberían limitarse a administrar con sus propios recursos.
En estos casos, puede restringir los parámetros que se exponen mediante la función o el cmdlet.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

En escenarios más avanzados, es posible que también deba restringir los valores que puede proporcionar un usuario a estos parámetros.
Las funcionalidades de rol le permiten definir un conjunto de valores permitidos o un patrón de expresión regular que se evalúa para determinar si se permite una entrada específica.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Los [parámetros comunes de PowerShell](https://technet.microsoft.com/library/hh847884.aspx) se permiten siempre, incluso si restringe los parámetros disponibles.
> No debería enumerarlos de forma explícita en el campo Parameters.

En la siguiente tabla, se describen las distintas formas en que puede personalizar un cmdlet o una función visibles.
Puede combinar cualquiera de los siguientes en el campo VisibleCmdlets.

Ejemplo                                                                                      | Caso de uso
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` o `@{ Name = 'My-Func' }`                                                       | Permite al usuario ejecutar `My-Func` sin restricciones en los parámetros.
`'MyModule\My-Func'`                                                                         | Permite al usuario ejecutar `My-Func` desde el módulo `MyModule` sin restricciones en los parámetros.
`'My-*'`                                                                                     | Permite al usuario ejecutar cualquier cmdlet o función con el verbo `My`.
`'*-Func'`                                                                                   | Permite al usuario ejecutar cualquier cmdlet o función con el sustantivo `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Permite al usuario ejecutar `My-Func` con los parámetros `Param1` o `Param2`. Para estos parámetros, se puede proporcionar cualquier valor.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Permite al usuario ejecutar `My-Func` con el parámetro `Param1`. Para este parámetro, solo se pueden especificar "Value1" y "Value2".
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Permite al usuario ejecutar `My-Func` con el parámetro `Param1`. Para este parámetro, se puede especificar cualquier valor que comience por "contoso".

> [!WARNING]
> En los mejores procedimientos recomendados de seguridad, se recomienda no usar caracteres comodín al definir cmdlets o funciones visibles.
> En su lugar, debe enumerar de forma explícita cada comando de confianza para asegurarse de que ningún otro comando que comparta el mismo esquema de nombre se autorice de forma involuntaria.

No se pueden aplicar ValidatePattern y ValidateSet en el mismo cmdlet o función.

Si lo hace, ValidatePattern invalidará a ValidateSet.

Para obtener más información sobre ValidatePattern, consulte [esta publicación de *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) y el contenido de referencia de las [expresiones regulares de PowerShell](https://technet.microsoft.com/library/hh847880.aspx).

### <a name="allowing-external-commands-and-powershell-scripts"></a>Permitir comandos externos y scripts de PowerShell

Para permitir que los usuarios ejecuten archivos ejecutables y scripts de PowerShell (.ps1) en una sesión de JEA, tendrá que agregar la ruta de acceso completa de cada programa en el campo VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Se aconseja, siempre que sea posible, que se usen equivalentes de función o cmdlet de PowerShell de los ejecutables externos que autorice, ya que tiene control sobre los parámetros que se permiten con funciones y cmdlets de PowerShell.

Muchos ejecutables le permiten leer el estado actual y, después, cambiarlo al proporcionar parámetros diferentes.

Pongamos de ejemplo el rol de un administrador del servidor de archivos que quiera comprobar los recursos compartidos de red que se hospedan en el equipo local.
Una forma de comprobarlo es usar `net share`.
En cambio, permitir net.exe es muy peligroso, ya que el administrador podría usar fácilmente el comando para obtener privilegios de administrador con `net group Administrators unprivilegedjeauser /add`.
Un mejor enfoque es permitir [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx), que ofrece el mismo resultado pero con un ámbito mucho más limitado.

Al poner comandos externos a disposición de los usuarios en una sesión de JEA, especifique siempre la ruta de acceso completa al ejecutable para asegurarse de que no se ejecute en su lugar un programa con un nombre parecido (y potencialmente malintencionado) ubicado en otra parte del sistema.

### <a name="allowing-access-to-powershell-providers"></a>Permitir el acceso a proveedores de PowerShell

De manera predeterminada, no hay ningún proveedor de PowerShell disponible en las sesiones de JEA.

Esto es principalmente para reducir el riesgo de que se revele información confidencial y opciones de configuración al usuario que se conecta.

Cuando sea necesario, puede permitir el acceso a los proveedores de PowerShell mediante el comando `VisibleProviders`.
Para obtener una lista completa de proveedores, ejecute `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Para realizar tareas sencillas que requieren acceso al sistema de archivos, el Registro, el almacén de certificados u otros proveedores de información confidencial, también puede escribir una función personalizada que sea adecuada para trabajar con el proveedor en nombre del usuario.
Los cmdlets, las funciones y los programas externos que están disponibles en una sesión de JEA no están sujetos a las mismas restricciones que JEA, pueden tener acceso a cualquier proveedor de manera predeterminada.
Asimismo, considere el uso de la [unidad de usuario](session-configurations.md#user-drive) al copiar archivos desde/en un punto de conexión de JEA.

### <a name="creating-custom-functions"></a>Crear funciones personalizadas

Puede crear funciones personalizadas en un archivo de funcionalidad de rol para simplificar tareas complejas para los usuarios finales.
Las funciones personalizadas también son útiles cuando se requiere una lógica de validación avanzada para los valores de parámetros de cmdlet.
Puede escribir funciones simples en el campo **FunctionDefinitions**:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> No olvide agregar el nombre de las funciones personalizadas en el campo **VisibleFunctions** para que las puedan ejecutar los usuarios de JEA.

El cuerpo (bloque de script) de las funciones personalizadas se ejecuta en el modo de lenguaje predeterminado del sistema y no está sujeto a restricciones de lenguaje de JEA.
Esto significa que las funciones pueden tener acceso al sistema de archivos y al Registro y ejecutar comandos que no se han hecho visibles en el archivo de funcionalidad de rol.
Tenga cuidado para evitar que se ejecute código arbitrario al usar parámetros y para evitar canalizar la entrada del usuario directamente en cmdlets como `Invoke-Expression`.

En el ejemplo anterior, se habrá dado cuenta de que se usa el nombre de módulo completo (FQMN) `Microsoft.PowerShell.Utility\Select-Object` en lugar de la forma abreviada `Select-Object`.
Las funciones definidas en los archivos de funcionalidad de función siguen dependiendo del ámbito de las sesiones de JEA, que incluye las funciones de proxy que crea JEA para restringir comandos existentes.

Select-Object es un cmdlet restringido y predeterminado en todas las sesiones de JEA que no le permite seleccionar propiedades arbitrarias en objetos.
Para usar Select-Object sin restricciones en funciones, debe solicitar de forma explícita la implementación completa al especificar el FQMN.
Cualquier cmdlet sin restricciones en una sesión de JEA tendrá el mismo comportamiento que cuando se invoca desde una función, de acuerdo con la [precedencia de comando](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence) de PowerShell.

Si está escribiendo una gran cantidad de funciones personalizadas, puede ser más fácil colocarlas en un [módulo de script de PowerShell](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).
Después, puede hacer visibles esas funciones en la sesión de JEA mediante el campo VisibleFunctions como lo haría con módulos integrados y de terceros.

## <a name="place-role-capabilities-in-a-module"></a>Colocar funcionalidades de rol en un módulo

Para que PowerShell encuentre un archivo de funcionalidad de rol, debe estar almacenado en una carpeta "RoleCapabilities" de un módulo de PowerShell.
El módulo se puede almacenar en cualquier carpeta incluida en la variable de entorno `$env:PSModulePath`, pero no debe colocarlo en System32 (reservado para módulos integrados) ni en una carpeta en que los usuarios que se conectan y no sean de confianza puedan modificar los archivos.
A continuación se muestra un ejemplo de cómo crear un módulo de script de PowerShell básico denominado *ContosoJEA* en la ruta de acceso "Archivos de programa".

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Consulte [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) (Descripción de un módulo de PowerShell) para obtener más información sobre la variable de entorno PSModulePath, los manifiestos de módulo y los módulos de PowerShell.

## <a name="updating-role-capabilities"></a>Actualizar funcionalidades de rol

Puede actualizar un archivo de funcionalidad de rol en cualquier momento; para ello, solo tiene que guardar los cambios realizados en el archivo de funcionalidad de rol.
Cualquier sesión de JEA nueva iniciada después de que se haya actualizado la funcionalidad de rol reflejará las funcionalidades revisadas.

Por esto es tan importante controlar el acceso a la carpeta de funcionalidades de rol.
Solo los administradores de plena confianza deberían poder cambiar los archivos de funcionalidad de rol.
Si un usuario que no sea de confianza puede cambiar los archivos de funcionalidad de rol, puede proporcionarse acceso fácilmente a cmdlets que le permitan elevar sus privilegios.

Para administradores que quieran bloquear el acceso a las funcionalidades de rol, asegúrese de que el sistema local tenga acceso de lectura a los archivos de funcionalidad de rol y a los módulos contenedores.

## <a name="how-role-capabilities-are-merged"></a>Cómo se combinan las funcionalidades de rol

Se les puede conceder acceso a los usuarios a varias funcionalidades de rol cuando entran en una sesión de JEA según las asignaciones de rol del [archivo de configuración de sesión](session-configurations.md).
Cuando esto sucede, JEA intenta dar al usuario el conjunto de comandos *más permisivo* permitido por cualquiera de los roles.

**VisibleCmdlets y VisibleFunctions**

La lógica de combinación más compleja afecta a los cmdlets y funciones, que pueden tener sus parámetros y valores de parámetro limitados en JEA.

Estas son las reglas:

1. Si un cmdlet solo está visible en un rol, será visible para el usuario con cualquier restricción de parámetro correspondiente.
2. Si un cmdlet está visible en más de un rol, y todos los roles tienen las mismas restricciones en el cmdlet, el cmdlet estará visible para el usuario con esas restricciones.
3. Si un cmdlet está visible en más de un rol, y todos los roles permiten un conjunto diferente de parámetros, el usuario podrá ver el cmdlet y todos los parámetros definidos en cada rol. Si un rol no tiene restricciones en los parámetros, se permitirán todos los parámetros.
4. Si un rol define un conjunto o patrón validado para un parámetro de cmdlet y el otro rol permite el parámetro pero no restringe los valores de parámetro, se omitirá el patrón o conjunto validado.
5. Si se define un conjunto validado para el mismo parámetro de cmdlet en más de un rol, se permitirán todos los valores de todos los conjuntos validados.
6. Si se define un patrón validado para el mismo parámetro de cmdlet en más de un rol, se permitirán todos los valores que coincidan con cualquiera de los patrones.
7. Si se define un conjunto validado en uno o varios roles y se define un patrón validado en otro rol para el mismo parámetro de cmdlet, se omite el conjunto validado y se aplica la regla (6) a los demás patrones validados.

A continuación se muestra un ejemplo de cómo se combinan los roles según estas reglas:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Todos los demás campos del archivo de funcionalidad de rol se agregan simplemente a un conjunto acumulativo de alias, proveedores, scripts de inicio y comandos externos permitidos.
Cualquier comando, alias, proveedor o script disponible en una funcionalidad de rol estará disponible para el usuario de JEA.

Asegúrese de que el conjunto combinado de proveedores de una funcionalidad de rol y cmdlets/funciones/comandos de otra no permitan que los usuarios que se conectan obtengan acceso involuntario a recursos del sistema.
Por ejemplo, si un rol permite el cmdlet `Remove-Item` y otro permite el proveedor `FileSystem`, corre el riesgo de que un usuario de JEA elimine archivos arbitrarios de su equipo.
Puede encontrar información adicional sobre cómo identificar los permisos efectivos de los usuarios en el [tema de auditoría de JEA](audit-and-report.md).

## <a name="next-steps"></a>Pasos siguientes

- [Crear un archivo de configuración de sesión](session-configurations.md)
