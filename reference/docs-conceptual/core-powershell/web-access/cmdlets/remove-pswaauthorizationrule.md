---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: d316cb98efc730ed3e99f6a5dac2b969e3437129
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2017
---
#  <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

##  <a name="synopsis"></a>SINOPSIS

Quita una regla de autorización especificada de Windows PowerShell® Web Access.

## <a name="syntax"></a>SINTAXIS

###  <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Regla
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPCIÓN

Quita una regla de autorización especificada de Windows PowerShell Web Access.

## <a name="parameters"></a>PARÁMETROS

### <a name="-force"></a>-Force

Ejecuta el cmdlet sin pedir confirmación. De forma predeterminada, el cmdlet pide confirmación antes de continuar.

|||  
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | llamada                                |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | falso                                |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Especifica los identificadores (ID) de una o varias reglas que se van a quitar.

|||  
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | true                                 |
| ¿Posición?                            | 2                                    |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | True (ByValue, ByPropertyName)       |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Especifica las reglas que se van a quitar.

|||  
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | true                                 |
| ¿Posición?                            | 2                                    |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | True (ByValue)                       |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-confirm"></a>-Confirm

Solicita confirmación antes de ejecutar el cmdlet.

|||  
|-|-|
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | llamada                                |
| Valor predeterminado                        | falso                                |
| ¿Aceptar canalización?               | falso                                |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-whatif"></a>-WhatIf

Muestra lo que sucedería si se ejecutara el cmdlet. El cmdlet no se ejecuta.

|||  
|-|-|
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | llamada                                |
| Valor predeterminado                        | falso                                |
| ¿Aceptar canalización?               | falso                                |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.
Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>ENTRADAS

###  <a name="int"></a>int\[\]

Este cmdlet acepta una matriz de enteros o una matriz de objetos PswaAuthorizationRule.

###  <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Este cmdlet acepta una matriz de enteros o una matriz de objetos PswaAuthorizationRule.

##  <a name="outputs"></a>SALIDAS

Este cmdlet no genera ninguna salida.

## <a name="examples"></a>EJEMPLOS

### <a name="example-1"></a>EJEMPLO 1

Este ejemplo quita la regla de autorización con el identificador de *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>EJEMPLO 2 {#example-2 .subHeading}

Este ejemplo quita todas las reglas de autorización y también requiere la confirmación del usuario.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

##  <a name="related-topics"></a>Temas relacionados

-  [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
-  [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
-  [Install-PswaWebApplication](install-pswawebapplication.md)
-  [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
