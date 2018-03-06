---
ms.date: 2017-06-05
keywords: powershell, cmdlet
title: "Realizar el segundo salto en la comunicación remota de PowerShell"
ms.openlocfilehash: 726b4d1b7a41e9e344347543ecde26da6547bcf3
ms.sourcegitcommit: fff6c0522508eeb408cb055ba4c9337a2759b392
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="making-the-second-hop-in-powershell-remoting"></a>Realizar el segundo salto en la comunicación remota de PowerShell

El "problema del segundo salto" se refiere a una situación similar a la siguiente:

1. Ha iniciado sesión en _ServidorA_.
2. En _ServidorA_, inicia una sesión remota de PowerShell para conectarse a _ServidorB_.
3. Un comando que ejecuta en _ServidorB_ a través de la sesión de comunicación remota de PowerShell intenta obtener acceso a un recurso en _ServidorC_.
4. Se le deniega el acceso al recurso en _ServidorC_, porque no se pasan las credenciales que ha usado para crear la sesión de comunicación remota de PowerShell de _ServidorB_ a _ServidorC_.

Hay varias formas de abordar este problema. En este tema, analizaremos algunas de las soluciones más populares del problema del segundo salto.

## <a name="credssp"></a>CredSSP

Puede usar el [proveedor de compatibilidad para seguridad de credenciales (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) para la autenticación. CredSSP copia en caché las credenciales en el servidor remoto (_ServidorB_), por lo que, al usarlo, le hace vulnerable a los ataques de robos de credenciales. Si el equipo remoto se ve comprometido, el atacante tiene acceso a las credenciales del usuario. CredSSP está deshabilitado de forma predeterminada tanto en el equipo del cliente como del servidor. Debe habilitar CredSSP solo en los entornos de mayor confianza. Por ejemplo, un administrador de dominio que se conecta a un controlador de dominio porque el controlador de dominio es de plena confianza.

Para obtener más información sobre problemas de seguridad cuando se usa CredSSP para la comunicación remota de PowerShell, vea [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) (Sabotaje accidental: tenga cuidado con CredSSP).

Para obtener más información acerca de los ataques de robo de credenciales, consulte [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036) (Mitigación de ataques Pass-the-Hash (PtH) y otros robos de credenciales).

Para obtener un ejemplo sobre cómo habilitar y usar CredSSP para la comunicación remota de PowerShell, consulte [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/) (Usar CredSSP para solucionar el problema del segundo salto).

### <a name="pros"></a>Pros

- Funciona en todos los servidores con Windows Server 2008 o versiones posteriores.

### <a name="cons"></a>Contras

- Tiene vulnerabilidades de seguridad.
- Requiere la configuración de roles de cliente y servidor.

## <a name="kerberos-delegation-unconstrained"></a>Delegación Kerberos (sin restricciones)

También puede usar la delegación Kerberos sin restricciones para realizar el segundo salto. En cambio, este método no proporciona control sobre dónde se usan las credenciales delegadas.

>**Nota:** No se pueden delegar las cuentas de Active Directory que tienen la propiedad **La cuenta es importante y no se puede delegar** establecida. Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).

### <a name="pros"></a>Pros

- No requiere código especial.

### <a name="cons"></a>Contras

- No se admite el segundo salto para WinRM.
- No proporciona ningún control sobre dónde se usan las credenciales, lo que crea una vulnerabilidad de seguridad.

## <a name="kerberos-constrained-delegation"></a>Delegación limitada de Kerberos

Puede usar la delegación limitada heredada (no basada en recursos) para realizar el segundo salto. 

>**Nota:** No se pueden delegar las cuentas de Active Directory que tienen la propiedad **La cuenta es importante y no se puede delegar** establecida. Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).

### <a name="pros"></a>Pros

- No requiere código especial

### <a name="cons"></a>Contras

- No se admite el segundo salto para WinRM.
- Se debe configurar en el objeto de Active Directory del servidor remoto (_ServidorB_).
- Limitado a un dominio. No puede cruzar dominios ni bosques.
- Requiere derechos para actualizar objetos y nombres de entidad de seguridad de servicio (SPN).

## <a name="resource-based-kerberos-constrained-delegation"></a>Delegación limitada de Kerberos basada en recursos

Con la delegación limitada de Kerberos basada en recursos (introducida en Windows Server 2012), configura la delegación de credenciales en el objeto de servidor en que residen los recursos.
En el escenario del segundo salto descrito anteriormente, puede configurar el _ServidorC_ para especificar desde dónde va a aceptar credenciales delegadas.

>**Nota:** No se pueden delegar las cuentas de Active Directory que tienen la propiedad **La cuenta es importante y no se puede delegar** establecida. Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).

### <a name="pros"></a>Pros

- Las credenciales no se almacenan.
- Relativamente fácil de configurar mediante cmdlets de PowerShell, no se requiere ninguna codificación especial.
- No se requiere ningún acceso especial de dominio.
- Funciona en dominios y bosques.
- Código de PowerShell.

### <a name="cons"></a>Contras

- Necesita Windows Server 2012 o versiones posteriores.
- No se admite el segundo salto para WinRM.
- Requiere derechos para actualizar objetos y nombres de entidad de seguridad de servicio (SPN). 

### <a name="example"></a>Ejemplo

Veamos un ejemplo de PowerShell que configura la delegación restringida basada en recursos en el _ServidorC_ para admitir credenciales delegadas de un _ServidorB_.
En este ejemplo, se supone que todos los servidores ejecutan Windows Server 2012 o una versión posterior y que hay al menos un controlador de dominio de Windows Server 2012 en cada dominio a los que pertenecen los servidores.

Antes de que pueda configurar la delegación restringida, debe agregar la característica `RSAT-AD-PowerShell` para instalar el módulo de PowerShell de Active Directory y después importar ese módulo en la sesión:

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
Varios cmdlets disponibles tienen ahora un parámetro **PrincipalsAllowedToDelegateToAccount**:

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName     
----------- ----                 ----------     
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

El parámetro **PrincipalsAllowedToDelegateToAccount** establece el atributo de objeto de Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, que contiene una lista de control de acceso (ACL) que especifica qué cuentas tienen permiso para delegar credenciales a la cuenta asociada (en nuestro ejemplo, será la cuenta del equipo de _Servidor_).

Ahora vamos a configurar las variables que usaremos para representar los servidores:

```powershell
# Set up variables for reuse            
$ServerA = $env:COMPUTERNAME            
$ServerB = Get-ADComputer -Identity ServerB            
$ServerC = Get-ADComputer -Identity ServerC            
```

WinRM (y, por tanto, la comunicación remota de PowerShell) se ejecuta como la cuenta de equipo de forma predeterminada. Puede ver esto si atiende a la propiedad **StartName** del servicio `winrm`:

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

Para que _ServidorC_ permita la delegación desde una sesión de comunicación remota de PowerShell en _ServidorB_, le concederemos acceso al establecer el parámetro **PrincipalsAllowedToDelegateToAccount** en _ServidorC_ al objeto de equipo de _ServidorB_:

```powershell
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB            
            
# Check the value of the attribute directly            
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity            
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access            
            
# Check the value of the attribute indirectly            
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

El [Centro de distribución de claves (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) de Kerberos copia en caché los intentos de acceso denegados (caché negativa) durante 15 minutos. Si _ServidorB_ ha intentado previamente obtener acceso a _ServidorC_, deberá borrar la caché de _ServidorB_ al invocar el comando siguiente:

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    klist purge -li 0x3e7            
}
```

También puede reiniciar el equipo o esperar al menos 15 minutos para borrar la caché.

Después de borrar la caché, puede ejecutar correctamente código desde el _ServidorA_ a través del _ServidorB_ hasta el _ServidorC_:

```powershell
# Capture a credential            
$cred = Get-Credential Contoso\Alice            
            
# Test kerberos double hop            
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    Test-Path \\$($using:ServerC.Name)\C$            
    Get-Process lsass -ComputerName $($using:ServerC.Name)            
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)            
}
```

En este ejemplo, la variable `$using` se usa para hacer visible la variable `$ServerC` en el _ServidorB_. Para obtener más información sobre la variable `$using`, consulte [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).

Para permitir que varios servidores deleguen credenciales en el _ServidorC_, establezca el valor del parámetro **PrincipalsAllowedToDelegateToAccount** en el _ServidorC_ a una matriz:

```powershell
# Set up variables for each server            
$ServerB1 = Get-ADComputer -Identity ServerB1            
$ServerB2 = Get-ADComputer -Identity ServerB2            
$ServerB3 = Get-ADComputer -Identity ServerB3            
$ServerC  = Get-ADComputer -Identity ServerC            
            
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

Si quiere realizar el segundo salto entre dominios, agregue el nombre de dominio completo (FQDN) del controlador del dominio al que pertenece el _ServidorB_:

```powershell
# For ServerC in Contoso domain and ServerB in other domain            
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com            
$ServerC = Get-ADComputer -Identity ServerC            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

Para quitar la capacidad de delegar credenciales en el ServidorC, establezca el valor del parámetro **PrincipalsAllowedToDelegateToAccount** en el _ServidorC_ en `$null`:

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a>Información sobre la delegación limitada de Kerberos basada en recursos

- [Novedades de la autenticación Kerberos](https://technet.microsoft.com/library/hh831747.aspx)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1) (Cómo simplifica Windows Server 2012 el proceso de delegación limitada de Kerberos, parte 1)
- [How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2) (Cómo simplifica Windows Server 2012 el proceso de delegación limitada de Kerberos, parte 2)
- [Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](http://aka.ms/kcdpaper) (Comprender la delegación limitada de Kerberos para implementaciones de proxy de aplicación de Active Directory con la autenticación integrada de Windows)
- [[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx) ([MS-ADA2]: atributos de esquema de Active Directory, atributo M2.210 msDS-AllowedToActOnBehalfOfOtherIdentity)
- [[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx) ([MS-SFU]: Extensiones de protocolo de Kerberos: protocolo de delegación limitada y de servicio para el usuario 1.3.2 S4U2proxy)
- [Delegación limitada de Kerberos basada en recursos](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- [Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/) (Administración remota sin delegación limitada con PrincipalsAllowedToDelegateToAccount)

## <a name="pssessionconfiguration-using-runas"></a>PSSessionConfiguration con RunAs

Puede crear una configuración de sesión en el _ServidorB_ y establecer su parámetro **RunAsCredential**.

Para obtener información sobre el uso de PSSessionConfiguration y RunAs para resolver el problema del segundo salto, consulte [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/) (Otra solución a la comunicación remota de PowerShell de varios saltos).

### <a name="pros"></a>Pros

- Funciona con cualquier servidor con WMF 3.0 o versiones posteriores.

### <a name="cons"></a>Contras

- Requiere la configuración de **PSSessionConfiguration** y **RunAs** en cada servidor intermedio (_ServidorB_).
- Requiere el mantenimiento de la contraseña cuando se usa una cuenta de **ejecución** de dominio

## <a name="just-enough-administration-jea"></a>Just Enough Administration (JEA)

JEA le permite restringir qué comandos puede ejecutar un administrador durante una sesión de PowerShell. Se puede usar para resolver el problema del segundo salto.

Para obtener información sobre JEA, consulte [Just Enough Administration](https://docs.microsoft.com/en-us/powershell/jea/overview).

### <a name="pros"></a>Pros

- No hay mantenimiento de contraseña al usar una cuenta virtual.

### <a name="cons"></a>Contras

- Requiere WMF 5.0 o versiones posteriores.
- Es necesario configurar cada servidor intermedio (_ServidorB_).

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a>Pasar credenciales dentro de un bloque de script de Invoke-Command

Se pueden pasar credenciales dentro del parámetro **ScriptBlock** de una llamada al cmdlet [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command).

### <a name="pros"></a>Pros

- No requiere configuración especial del servidor.
- Funciona en cualquier servidor que ejecute WMF 2.0 o versiones posteriores.

### <a name="cons"></a>Contras

- Se requiere una técnica de código complicada.
- Si ejecuta WMF 2.0, requiere una sintaxis diferente para pasar argumentos a una sesión remota.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, se muestra cómo pasar las credenciales en un bloque de script **Invoke-Command**:

```powershell
# This works without delegation, passing fresh creds            
# Note $Using:Cred in nested request            
$cred = Get-Credential Contoso\Administrator            
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {            
    hostname            
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}            
}
```

## <a name="see-also"></a>Vea también

[Consideraciones de seguridad de comunicación remota de PowerShell](WinRMSecurity.md)








 
