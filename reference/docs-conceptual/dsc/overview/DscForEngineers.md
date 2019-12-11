---
ms.date: 10/13/2017
keywords: dsc,powershell,configuration,setup
title: Información general sobre la configuración de estado deseado para ingenieros
ms.openlocfilehash: 0e599c2218cd2df29dbd0529006be5e1ef17ce5f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953802"
---
# <a name="desired-state-configuration-overview-for-engineers"></a>Información general sobre la configuración de estado deseado para ingenieros

Este documento está pensado para que los equipos de operaciones y desarrolladores comprendan los beneficios de la configuración de estado deseado (DSC) de PowerShell.
Para una vista de nivel superior del valor que ofrece DSC, consulte [Información general sobre la configuración de estado deseado para responsables de toma de decisiones](decisionMaker.md)

## <a name="benefits-of-desired-state-configuration"></a>Beneficios de la configuración de estado deseado

DSC existe para:

- Disminuir la complejidad del scripting en Windows
- Aumentar la velocidad de la iteración

El concepto de "implementación continua" es cada vez más importante.
La implementación continua se refiere a la capacidad de realizar implementaciones con frecuencia, potencialmente muchas veces al día.
El propósito de estas implementaciones no es corregir algo, sino publicar rápidamente algún contenido.
Al obtener características nuevas durante todo el desarrollo y hasta la operación de la manera más fluida y confiable posible, puede disminuir el tiempo para recuperar la inversión de la nueva lógica de negocios.

La migración hacia la informática en la nube implica una solución de implementación que use un modelo de plantilla "declarativa", donde se declare un entorno de estado final como texto y se publique en un motor de implementación.
Esta técnica de implementación permite realizar un cambio rápido, a gran escala, que resista la amenaza de errores, porque en cualquier momento la implementación se puede repetir de manera coherente para garantizar un estado final.
La creación de las herramientas y los servicios que admiten este estilo de operaciones mediante la automatización es una respuesta a estos cambios.

DSC es una plataforma que ofrece implementación, configuración y cumplimiento declarativos e idempotentes (repetibles).
La plataforma de DSC le permite asegurarse de que los componentes del centro de datos tienen la configuración correcta, lo que permite evitar errores y previene costosas fallas en la implementación.
Si las configuraciones de DSC se tratan como parte del código de la aplicación, DSC permite la implementación continua.
La configuración de DSC se debe actualizar como parte de la aplicación, lo que garantiza que el conocimiento necesario para implementar la aplicación siempre esté actualizado y listo para usar.

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a>"Ya tengo PowerShell. ¿Por qué necesito la configuración de estado deseado?"

La configuración de DSC separa la intención ("lo que quiero hacer") de la ejecución ("cómo quiero hacerlo").
Esto significa que la lógica de ejecución está contenida en los recursos.
No es necesario que los usuarios sepan cómo implementar una característica si hay disponible un recurso de DSC para esa característica.
Esto permite que el usuario se centre en la estructura de la implementación.

Como ejemplo, los scripts de PowerShell deben verse similares al siguiente:
```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```
Este script es simple, entendible y sencillo.
Sin embargo, si intenta poner ese script en el entorno de producción, se encontrará con varios problemas.
¿Qué sucede si el script se ejecuta dos veces seguidas?
¿Qué pasa sin Antonio tenía anteriormente acceso completo al recurso compartido?

Para compensar por estos problemas, una versión "real" del script se verá un poco más similar a lo siguiente:
```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @psboundparameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($psboundparameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

Este script es más complejo, con un importante control de errores y lógica.
El script es más complejo porque ya no indica lo que desea hacer, sino *cómo hacerlo*.

DSC le permite indicar qué es lo que quiere que se haga y la lógica subyacente se abstrae.

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

El script tiene un formato limpio y es fácil de leer.
El control de errores y las rutas lógicas siguen presentes en la implementación de [recursos](../resources/resources.md), pero son invisibles para el autor del script.

## <a name="separating-environment-from-structure"></a>Separación del entorno de la estructura

Un patrón común en DevOps es tener varios entornos para la implementación.
Por ejemplo, es posible que haya un entorno "dev" (desarrollo) que se usa para crear un prototipo de código nuevo.
El código del entorno "dev" (desarrollo) pasa a un entorno "test" (prueba), en el que otras personas comprueban la funcionalidad nueva.
Finalmente, el código pasa a "prod" (producción), el entorno de producción del sitio activo.

Las configuraciones de DSC adaptan esta canalización de dev-test-prod a través del uso de los [datos de configuración](../configurations/configData.md).
Esto abstrae aún más la diferencia entre la estructura de la configuración de los nodos que se administran.
Por ejemplo, puede definir una configuración que requiere un servidor SQL Server, un servidor IIS y un servidor de nivel intermedio.
Independientemente de cuáles son los nodos que reciben las distintas partes de esta configuración, siempre existirán estos tres elementos.
Puede usar los datos de configuración para apuntar los tres elementos a la misma máquina en un entorno de desarrollo, separarlos a tres máquinas distintas en un entorno de prueba y, por último, a todos los servidores de producción del entorno de producción.
Para implementar los distintos entornos, puede invocar **Start-DscConfiguration** con los datos de configuración correctos correspondientes al entorno que desea tener como destino.

## <a name="see-also"></a>Véase también

[Configuraciones](../configurations/configurations.md)

[Datos de configuración](../configurations/configData.md)

[Recursos](../resources/resources.md)
