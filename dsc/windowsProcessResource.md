---
title: Recurso de DSC WindowsProcess
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 97714d3fa9a1c00fb3d2e79cc873280ca945a840
ms.openlocfilehash: 0fe5e7d9679d44bb50c897badf8c6517b95049e2

---

# Recurso de DSC WindowsProcess

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso **WindowsProcess** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino.

## Sintaxis

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## Propiedades
|  Propiedad  |  Descripción   | 
|---|---| 
| Argumentos| Indica una cadena de argumentos que se pasa al proceso tal cual. Si necesita pasar varios argumentos, colóquelos en esta cadena.| 
| Ruta| La ruta de acceso al ejecutable del proceso. Si este es el nombre de archivo del ejecutable (no la ruta de acceso completa), el recurso de DSC buscará la variable **Path** del entorno (`$env:Path`) para buscar el archivo ejecutable. Si el valor de esta propiedad es una ruta completa, DSC no usará la variable de entorno **Path** para buscar el archivo y generará un error si la ruta de acceso no existe. No se permiten rutas de acceso relativas.| 
| Credential| Indica las credenciales para iniciar el proceso.| 
| Ensure| Indica si existe el proceso. Establezca esta propiedad en "Present" para asegurarse de que el proceso exista. De lo contrario, establézcala en "Absent". El valor predeterminado es "Present".| 
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`` .| 
| StandardErrorPath| Indica la ruta de acceso del directorio donde se escribirá el error estándar. Se sobrescribirá cualquier archivo existente en la ubicación.| 
| StandardInputPath| Indica la ubicación de entrada estándar.| 
| StandardOutputPath| Indica la ubicación donde se escribirá la salida estándar. Se sobrescribirá cualquier archivo existente en la ubicación.| 
| WorkingDirectory| Indica la ubicación que se utilizará como directorio de trabajo actual del proceso.| 




<!--HONumber=Jul16_HO1-->


