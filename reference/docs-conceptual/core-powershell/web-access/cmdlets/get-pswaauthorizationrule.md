---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: eb9f42ab4d9cec111e03a096b2f00740e97ee1b7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>SINOPSIS

Devuelve un conjunto de las reglas de autorización de Windows PowerShell® Web Access.

## <a name="syntax"></a>Sintaxis

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Nombre
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPCIÓN

El cmdlet **Get-PswaAuthorizationRule** devuelve un conjunto de las reglas de autorización de Windows PowerShell® Web Access.
Si no se especifica ni el parámetro **Id** ni el parámetro **RuleName**, este cmdlet mostrará todas las reglas. El parámetro **Id** se puede usar para filtrar los resultados.

## <a name="parameters"></a>PARÁMETROS

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Especifica los identificadores (ID) de las reglas que debe obtener este cmdlet. Si no se especifica ningún identificador, este cmdlet devolverá todas las reglas de autorización.

|||  
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | 2                                    |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | True (ByValue, ByPropertyName)       |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String\[\]&gt;

Especifica los nombres de las reglas de autorización que se van a recuperar. Este parámetro devuelve todas las reglas que coinciden exactamente con los nombres de las reglas de las cadenas de esta matriz.

|||  
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | true                                 |
| ¿Posición?                            | 2                                    |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | True (ByValue, ByPropertyName)       |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.
Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

### <a name="int"></a>int\[\]

Este cmdlet acepta como entrada una matriz de enteros o una matriz de valores de cadena.

### <a name="string"></a>String\[\]

Este cmdlet acepta como entrada una matriz de enteros o una matriz de valores de cadena.

## <a name="outputs"></a>SALIDAS

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Este cmdlet genera un objeto PswaAuthorizationRule como salida.


## <a name="examples"></a>EJEMPLOS

### <a name="example-1"></a>EJEMPLO 1

Este ejemplo obtiene todas las reglas.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>EJEMPLO 2

Este ejemplo obtiene una regla con un identificador de *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>EJEMPLO 3 {#example-3 .subHeading}

En este ejemplo se muestra cómo el cmdlet acepta un valor de la canalización.
En este cmdlet se pasa un identificador y un nombre de regla.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>Temas relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
