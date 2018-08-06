---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: bcf897730881551ec16ce970de6a1330961b67e6
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268272"
---
# <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

## <a name="synopsis"></a>SINOPSIS

Agrega una nueva regla de autorización al conjunto de reglas de autorización de Windows PowerShell Web Access.

## <a name="syntax"></a>Sintaxis

### <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a>UserGroupNameComputerName

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a>UserNameComputerGroupName

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a>UserNameComputerName

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIPCIÓN

El cmdlet **Add-PswaAuthorizationRule** agrega una nueva regla de autorización al conjunto de reglas de autorización de Windows PowerShell(r) Web Access.

Debe especificar los usuarios, los equipos y los puntos de conexión de Windows PowerShell para esta regla. Puede especificar los usuarios y los equipos ya sea por cuentas de usuario y nombres de equipo concretos o especificando grupos.

Para un equipo que está unido a un dominio de Active Directory, el cmdlet usa el identificador de seguridad (SID) del equipo para crear la regla. Esto le permite usar un nombre corto, un nombre de dominio completo (FQDN) o una dirección IP para el campo **Nombre del equipo** en la página de inicio de sesión.

En el caso de los equipos que no están unidos a un dominio de Active Directory, el cmdlet crea la regla con el nombre del equipo proporcionado por el administrador. Para conectarse correctamente a este equipo, el usuario final debe proporcionar el nombre del equipo tal y como aparece en la regla.

Si hay varios equipos con el mismo nombre en la red, el nombre corto se puede resolver en más de un equipo, lo cual puede generar ambigüedad a la hora de establecer una conexión. Por ejemplo, si existe una regla para el equipo del grupo de trabajo llamado "*Server1*" y se une a la red un equipo nuevo llamado *server1.contoso.com*, la validación con las reglas de autorización se efectúa correctamente y Windows PowerShell Web Access intenta establecer una conexión con el equipo llamado "*Server1*". No se garantiza que se establezca la conexión con el equipo del grupo de trabajo especificado; el intento de conexión podría efectuarse en el grupo de trabajo o en el equipo del dominio denominado "*Server1*". Para reducir la ambigüedad, se recomienda usar el FQDN del equipo de destino siempre que sea posible para crear una regla de autorización.

Las reglas de autorización evalúan la credencial de inicio de sesión principal de los usuarios de Windows PowerShell Web Access, y no las credenciales alternativas (el segundo conjunto de credenciales de la sección **Configuración de conexión opcional** de la página de inicio de sesión). Para ver un ejemplo, vea el ejemplo 6.

## <a name="parameters"></a>Parámetros

### <a name="-computergroupname-string"></a>-ComputerGroupName \<String\>

Especifica el nombre de un grupo de equipos de Active Directory Domain Services (AD DS) o de grupos locales a los que concede acceso esta regla.

|||
|-|-|
| Alias                     | ninguno                  |
| ¿Requerido?                   | true                  |
| ¿Posición?                   | llamada                 |
| Valor predeterminado               | ninguno                  |
| ¿Aceptar canalización?      | True (ByPropertyName) |
| ¿Aceptar caracteres comodín? | falso                 |

### <a name="-computername-string"></a>-ComputerName \<String\>

Especifica el nombre del equipo al que concede acceso esta regla.

|||
|-|-|
| Alias                     | ninguno                  |
| ¿Requerido?                   | true                  |
| ¿Posición?                   | llamada                 |
| Valor predeterminado               | ninguno                  |
| ¿Aceptar canalización?      | True (ByPropertyName) |
| ¿Aceptar caracteres comodín? | falso                 |

### <a name="-configurationname-string"></a>-ConfigurationName \<String\>

Especifica el nombre de la configuración de sesión de Windows PowerShell (también conocida como "espacio de ejecución") a la que concede acceso esta regla.

|||
|-|-|
| Alias                     | ninguno                  |
| ¿Requerido?                   | true                  |
| ¿Posición?                   | llamada                 |
| Valor predeterminado               | ninguno                  |
| ¿Aceptar canalización?      | True (ByPropertyName) |
| ¿Aceptar caracteres comodín? | falso                 |

### <a name="-credential--pscredential"></a>-Credential  \<PSCredential\>

Especifica un objeto **PSCredential** para una cuenta de usuario que quiera usar para cambiar las reglas de autorización de Windows PowerShell Web Access. Si no agrega este parámetro, el cmdlet usará la cuenta del usuario que ha iniciado la sesión. Para obtener un objeto **PSCredential**, necesario para agregar reglas de autorización de forma remota, ejecute el cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).

|||
|-|-|
| Alias                     | ninguno  |
| ¿Requerido?                   | falso |
| ¿Posición?                   | llamada |
| Valor predeterminado               | ninguno  |
| ¿Aceptar canalización?      | falso |
| ¿Aceptar caracteres comodín? | falso |

### <a name="-force"></a>-Force

Obliga al comando a ejecutarse sin solicitar la confirmación del usuario. También pide confirmación al escribir un nombre de equipo corto o simple (por ejemplo, un nombre que no es un nombre de dominio o un nombre no completo). La confirmación se solicita por motivos de seguridad, de modo que puede usar el nombre simple para agregar un equipo únicamente si dicho equipo se encuentra en un grupo de trabajo.

|||
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | llamada                                |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | falso                                |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-rulename-string"></a>-RuleName \<String\>

Especifica el nombre descriptivo de esta regla.

|||
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | falso                                |
| ¿Posición?                            | llamada                                |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | True (ByPropertyName)                |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-usergroupname-string"></a>-UserGroupName \<String\[\]\>

Especifica el nombre de uno o varios grupos de usuarios en AD DS o en grupos locales a los que concede acceso esta regla.

|||
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | true                                 |
| ¿Posición?                            | llamada                                |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | True (ByPropertyName)                |
| ¿Aceptar caracteres comodín?          | falso                                |

### <a name="-username-string"></a>-UserName \<String\[\]\>

Especifica uno o varios usuarios a los que concede acceso esta regla. El nombre de usuario puede ser una cuenta de usuario local del equipo de la puerta de enlace o un usuario de AD DS. El formato es `domain\user` o `computer\user`.

|||
|-|-|
| Alias                              | ninguno                                 |
| ¿Requerido?                            | true                                 |
| ¿Posición?                            | 1                                    |
| Valor predeterminado                        | ninguno                                 |
| ¿Aceptar canalización?               | True (ByValue, ByPropertyName)       |
| ¿Aceptar caracteres comodín?          | falso                                |

###  <a name="commonparameters"></a>\<CommonParameters\>

Este cmdlet admite los parámetros comunes:

-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.
Para más información, vea [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>ENTRADAS

### <a name="string"></a>Cadena

Este cmdlet acepta como entrada una cadena o una matriz de cadenas.

### <a name="string"></a>String\[\]

Este cmdlet acepta como entrada una cadena o una matriz de cadenas.

## <a name="outputs"></a>Salidas

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Este cmdlet devuelve el objeto de la regla de autorización.

## <a name="examples"></a>EJEMPLOS

### <a name="example-1"></a>EJEMPLO 1

Este ejemplo concede acceso a la configuración de la sesión _PSWAEndpoint_, un espacio de ejecución restringido, en _srv2_ para los usuarios del grupo _SMAdmins_.

> [!NOTE]
> El nombre del equipo debe ser un nombre de dominio completo (FQDN). Los administradores definen una configuración de sesión o espacio de ejecución restringido, que es un intervalo limitado de cmdlets y tareas que los usuarios finales pueden ejecutar. Definir un espacio de ejecución restringido puede impedir que los usuarios puedan obtener acceso a otros equipos que no se encuentran en el espacio de ejecución de Windows PowerShell(r) permitido, lo que garantiza una conexión más segura. Para más información sobre las configuraciones de sesión, consulte [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) o [Instalación y uso de Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>EJEMPLO 2

Este ejemplo concede acceso a la configuración de sesión predeterminada de Windows PowerShell, `Microsoft.PowerShell`, en *srv2* para los usuarios de los usuarios denominados `contoso\user1`, `contoso\user2` y `contoso\user3`.r3. Este cmdlet crea tres reglas (una por persona).

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>EJEMPLO 3

En este ejemplo se muestra cómo se especifican valores de nombre de usuario a través de la canalización.

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>EJEMPLO 4

En este ejemplo se muestra cómo todos los parámetros toman valores de la canalización por nombre de propiedad.

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a>EJEMPLO 5

Este ejemplo agrega una regla para permitir que el usuario local llamado `PswaServer\ChrisLocal` obtenga acceso al servidor llamado **srv1.contoso.com**.

En este ejemplo se muestra un escenario en el que la puerta de enlace está en un grupo de trabajo y el equipo de destino está en un dominio. La regla de autorización se aplica a los usuarios locales de la puerta de enlace. En la página de inicio de sesión de Windows PowerShell Web Access, para autenticarse correctamente, el usuario debe proporcionar un segundo conjunto de credenciales en el área **Configuración de conexión opcional**. El servidor de puerta de enlace usa el conjunto de credenciales adicional para autenticar al usuario en el equipo de destino, un servidor llamado *srv1.contoso.com*.

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a>EJEMPLO 6

Este ejemplo permite que todos los usuarios obtengan acceso a todos los puntos de conexión de todos los equipos. Esto equivale a desactivar las reglas de autorización.

> [!NOTE]
> No se recomienda usar el carácter comodín `*` para las implementaciones de seguridad. Solo debe aplicarse en los entornos de prueba, o bien en las implementaciones en las que la seguridad pueda ser algo laxa.

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a>Véase también

[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)

[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)

[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)

[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)

[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)