---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Instrucciones condicionales y bucles en las configuraciones
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736903"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a>Instrucciones condicionales y bucles en una configuración

Puede hacer que sus [configuraciones](configurations.md) sean más dinámicas con las palabras clave de control de flujo de PowerShell. En este artículo se muestra cómo puede usar instrucciones condicionales y bucles para hacer que sus `Configuration` sean más dinámicas. La combinación de instrucciones condicionales y bucles con [parámetros](add-parameters-to-a-configuration.md) y [datos de configuración](configData.md) le concede más flexibilidad y control al compilar sus `Configuration`.

Al igual que una función o un bloque de script, puede usar cualquier lenguaje de PowerShell dentro de una `Configuration`.
Las declaraciones que use solo se evaluarán cuando llame a su `Configuration` para compilar un archivo `.mof`. Los ejemplos siguientes muestran escenarios para demostrar conceptos. Las instrucciones condicionales y bucles se usan más a menudo con parámetros y datos de configuración.

En este ejemplo, el bloque de recursos **Service** recupera el estado actual de un servicio en tiempo de compilación para generar un archivo `.mof` que mantiene su estado actual.

> [!NOTE]
> El uso de bloques de recursos dinámicos se anticipará a la eficacia de Intellisense. El analizador de PowerShell no puede determinar si los valores especificados son aceptables hasta que se compile la `Configuration`.

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

Además, puede crear un bloque de recurso **Service** para cada servicio de la máquina actual, mediante el uso de un bucle `foreach`.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
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

También puede crear una `Configuration` solo para las máquinas que están en línea mediante una instrucción `if`.

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> Los bloques de recursos dinámicos de los ejemplos anteriores hacen referencia a la máquina actual. En este caso, sería la máquina en la que está creando la `Configuration`, no el nodo de destino.

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a>Resumen

En resumen, puede usar cualquier lenguaje de PowerShell dentro de una `Configuration`.

Esto incluye elementos como:

- Objetos personalizados
- Tablas hash
- Manipulación de cadenas
- Comunicación remota
- WMI y CIM
- Objetos de ActiveDirectory
- y más...

Cualquier código de PowerShell definido en una `Configuration` se evalúa en tiempo de compilación, pero también puede colocar código en el script que contiene `Configuration`. Cualquier código fuera del bloque `Configuration` se ejecuta al importar la `Configuration`.

## <a name="see-also"></a>Consulte también

- [Adición de parámetros a una configuración](add-parameters-to-a-configuration.md)
- [Separación de los datos de configuración de las configuraciones](configData.md)
