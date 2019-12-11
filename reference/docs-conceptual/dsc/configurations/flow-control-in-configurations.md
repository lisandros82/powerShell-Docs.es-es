---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Instrucciones condicionales y bucles en las configuraciones
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954082"
---
# <a name="conditional-statements-and-loops-in-configurations"></a>Instrucciones condicionales y bucles en las configuraciones

Puede hacer que sus [configuraciones](configurations.md) sean más dinámicas con las palabras clave de control de flujo de PowerShell. Este artículo le mostrará cómo puede usar instrucciones condicionales y bucles para hacer que sus configuraciones sean más dinámicas. La combinación de condicionales y bucles con [parámetros](add-parameters-to-a-configuration.md) y [datos de configuración](configData.md) le concede más flexibilidad y control al compilar sus configuraciones.

Al igual que una función o un bloque de script, puede usar cualquier lenguaje de PowerShell dentro de una configuración. Las declaraciones que use solo se evaluarán cuando llame a su configuración para compilar un archivo ".mof". Los ejemplos siguientes muestran escenarios sencillos para demostrar conceptos. Los condicionales son bucles que se usan más a menudo con parámetros y datos de configuración.

En este sencillo ejemplo, el bloque de recursos **Service** recupera el estado actual de un servicio en tiempo de compilación para generar un archivo ".mof" que mantiene su estado actual.

> [!NOTE]
> El uso de bloques de recursos dinámicos se anticipará a la eficacia de Intellisense. El analizador de PowerShell no puede determinar si los valores especificados son aceptables hasta que se compile la configuración.

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

Además, puede crear un recurso de bloque **Service** para cada servicio de la máquina actual, mediante el uso de un bucle `foreach`.

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

También puede crear configuraciones solo para máquinas que estén en línea, utilizando una simple instrucción `if`.

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
> Los bloques de recursos dinámicos de los ejemplos anteriores hacen referencia a la máquina actual. En este caso, sería la máquina en la que está creando la configuración, no el nodo de destino.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Resumen

En resumen, puede usar cualquier lenguaje de PowerShell dentro de una configuración.

Esto incluye elementos como:

- Objetos personalizados
- Tablas hash
- Manipulación de cadenas
- Comunicación remota
- WMI y CIM
- Objetos de ActiveDirectory
- y más...

Cualquier código de PowerShell definido en una configuración se evaluará en un tiempo de compilación, pero también puede colocar el código en el script que contiene su configuración. Al importar la configuración, se ejecutará cualquier código fuera del bloque de configuración.

## <a name="see-also"></a>Vea también

- [Adición de parámetros a una configuración](add-parameters-to-a-configuration.md)
- [Separación de los datos de configuración de las configuraciones](configData.md)
