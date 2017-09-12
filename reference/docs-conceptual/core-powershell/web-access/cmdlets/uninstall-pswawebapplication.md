---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 5fe608b3bfbb90f842f16c1f5a8c51879589cf6d
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>SINOPSIS

Desinstala la aplicación web de Windows PowerShell®.

## <a name="syntax"></a>SINTAXIS

### <a name="default"></a>Valor predeterminado
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPCIÓN

El cmdlet **Uninstall-PswaWebApplication** desinstala la aplicación web de Windows PowerShell y quita de IIS el sitio web. El cmdlet no desinstala IIS ni ninguna otra característica instalada, ya que eran necesarias para que se ejecutara Windows PowerShell.

## <a name="parameters"></a>PARÁMETROS

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Indica que se han eliminado los certificados de prueba creados por el cmdlet **Install\_PswaWebApplication** (con el parámetro **UseTestCertificate**).
Solo se quita el certificado de prueba que tiene el mismo nombre que el que ha creado el cmdlet **Install-PswaWebApplication**.

|||  
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | llamada                                |
| Valor predeterminado                        | true                                 |
| ¿Aceptar canalización?               | falso                                |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;String&gt;

Especifica el nombre de la aplicación web que se va a desinstalar.

|||  
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | 1                                    |
| Valor predeterminado                        | pswa                                 |
| ¿Aceptar canalización?               | falso                                |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;String&gt;

Especifica el nombre del sitio web donde está instalada la aplicación web.

|||  
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | llamada                                |
| Valor predeterminado                        | Sitio web predeterminado                     |
| ¿Aceptar canalización?               | falso                                |
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

Muestra lo que sucedería si se ejecutara el cmdlet.
El cmdlet no se ejecuta.

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

Este cmdlet no toma ninguna entrada.

## <a name="outputs"></a>SALIDAS

Este cmdlet no devuelve ningún resultado.

## <a name="examples"></a>EJEMPLOS

### <a name="example-1"></a>EJEMPLO 1

Este comando desinstala la aplicación web de Windows PowerShell.
Puede usar este cmdlet para desinstalar la aplicación web de Windows PowerShell si la instaló con los valores predeterminados.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>EJEMPLO 2

Este comando desinstala la aplicación web de Windows PowerShell y elimina el certificado de prueba asociado a la aplicación.
Puede usar este cmdlet para desinstalar la aplicación web de Windows PowerShell si la instaló con los valores predeterminados y creó un certificado de prueba.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>EJEMPLO 3 {#example-3 .subHeading}

Este comando desinstala la aplicación web de Windows PowerShell si durante la instalación se especificó una aplicación y un sitio web personalizados.
El comando quita el sitio web denominado *MySite* y la aplicación denominada *TestApplication* y especifica que también se eliminan los certificados de prueba asociados a la aplicación.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Temas relacionados

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
