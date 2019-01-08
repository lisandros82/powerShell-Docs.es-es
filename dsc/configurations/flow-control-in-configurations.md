---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Instrucciones condicionales y bucles en las configuraciones
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402314"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Instrucciones condicionales y bucles en las configuraciones

Puede hacer su [configuraciones](configurations.md) más dinámico con las palabras clave de control de flujo de PowerShell. En este artículo le mostrará cómo puede usar instrucciones condicionales y bucles para hacer que las configuraciones más dinámicas. Combinación condicionales y bucles con [parámetros](add-parameters-to-a-configuration.md) y [datos de configuración](configData.md) permite más flexibilidad y control al compilar las configuraciones.

Al igual que una función o un bloque de Script, puede usar cualquier lenguaje de PowerShell dentro de una configuración. Solo se evaluarán las instrucciones que se utilizan cuando se llama a la configuración para compilar un archivo ".mof". Los ejemplos siguientes muestran los escenarios sencillos para demostrar conceptos. Instrucciones condicionales son los bucles se utilizan con más frecuencia con parámetros y datos de configuración.

En este sencillo ejemplo, la **servicio** bloque de recursos recupera el estado actual de un servicio en tiempo de compilación para generar un archivo de "MOF" que mantiene su estado actual.

> [!NOTE]
> Uso de bloques de recursos dinámicos adelantan a la eficacia de Intellisense. El analizador de PowerShell no puede determinar si los valores especificados son aceptables, hasta que se compile la configuración.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

Además, puede crear un **servicio** bloquear recursos para cada servicio en el equipo actual, utilizando un `foreach` bucle.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

También sólo se podían crear configuraciones para las máquinas que estén en línea, mediante un sencillo `if` instrucción.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> Bloquea el recurso dinámico en la referencia de los ejemplos anteriores en la máquina actual. En este caso, lo que sería la máquina que se va a crear la configuración, no el nodo de destino.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Resumen

En resumen, puede usar cualquier lenguaje de PowerShell dentro de una configuración.

Esto incluye cosas como:

- Objetos personalizados
- Tablas hash
- Manipulación de cadenas
- Comunicación remota
- WMI y CIM
- Objetos de Active Directory
- y más...

Cualquier código de PowerShell definido en la configuración se evaluará un tiempo de compilación, pero también puede colocar código en el script que contiene la configuración. Al importar la configuración, se ejecutará cualquier código fuera del bloque de configuración.

## <a name="see-also"></a>Vea también

- [Adición de parámetros a una configuración](add-parameters-to-a-configuration.md)
- [Separación de los datos de configuración de las configuraciones](configData.md)
