---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: Información general de Just Enough Administration
ms.openlocfilehash: 3dae8b31d4d13ff9033803035c870c02fc7c38ca
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) es una tecnología de seguridad que permite la administración delegada de todo lo que se puede administrar con PowerShell.
Con JEA, se puede hacer lo siguiente:

- **Reducir el número de administradores de las máquinas** aprovechando las cuentas virtuales o las cuentas de servicio administradas de grupo que realizan acciones con privilegios en nombre de usuarios normales.
- **Limitar lo que pueden hacer los usuarios** especificando qué cmdlets, funciones y comandos externos pueden ejecutar.
- **Entender mejor lo que hacen los usuarios** con transcripciones y registros que muestran exactamente qué comandos ha ejecutado un usuario durante su sesión.

**¿Por qué es importante?**

Las cuentas con muchos privilegios usadas para administrar los servidores suponen un grave riesgo de seguridad.
Si un atacante compromete una de estas cuentas, podría iniciar [ataques laterales](http://aka.ms/pth) en toda la organización.
Cada cuenta comprometida puede darles acceso incluso a más cuentas y recursos, lo que los pondría un paso más cerca de robar secretos de la empresa, iniciar un ataque por denegación de servicio y mucho más.

No es siempre fácil quitar privilegios administrativos.
Tenga en cuenta el escenario común en que el rol DNS está instalado en el mismo equipo que el controlador de dominio de Active Directory.
Los administradores DNS necesitan privilegios de administrador local para solucionar problemas con el servidor DNS, pero para ello tiene que hacerlos miembros del grupo de seguridad "Administradores de dominio" con privilegios elevados.
Este enfoque proporciona a los administradores de DNS el control sobre todo el dominio y les permite acceder a todos los recursos de la máquina.

JEA ayuda a resolver este problema al ayudarle a adoptar el principio de *privilegio mínimo*.
Con JEA, puede configurar un punto de conexión de administración para los administradores DNS que les proporcione acceso a todos los comandos de PowerShell que necesitan para realizar su trabajo, pero a nada más.
Esto significa que puede proporcionar el acceso adecuado para reparar una caché DNS dañada o reiniciar el servidor DNS sin concederles involuntariamente derechos en Active Directory, para examinar el sistema de archivos o para ejecutar scripts potencialmente peligrosos.
Y lo que es mejor, cuando la sesión de JEA está configurada para usar cuentas virtuales con privilegios temporales, los administradores DNS pueden conectarse al servidor mediante credenciales *que no sean de administrador* y seguir siendo capaces de ejecutar comandos que normalmente requieren privilegios de administrador.
Esta funcionalidad le permite quitar usuarios de roles de administrador local o de dominio con muchos privilegios y, en su lugar, controlar cuidadosamente qué pueden hacer en cada equipo.

## <a name="get-started-with-jea"></a>Introducción a JEA

Puede empezar a usar JEA hoy mismo en cualquier equipo que ejecute Windows Server 2016 o Windows 10.
También puede ejecutar JEA en sistemas operativos anteriores con una actualización de Windows Management Framework.
Para obtener más información sobre los requisitos para usar JEA y cómo crear, usar y auditar un punto de conexión de JEA, consulte los temas siguientes:

- [Requisitos previos](prerequisites.md): explica cómo configurar su entorno para usar JEA.
- [Funcionalidades de rol](role-capabilities.md): explica cómo crear roles que determinan qué puede hacer un usuario en una sesión de JEA.
- [Configuraciones de sesión](session-configurations.md): explica cómo configurar los puntos de conexión de JEA que asignan usuarios a roles y establecer la identidad de JEA
- [Registrar JEA](register-jea.md): cree un punto de conexión de JEA y póngalo a disposición de los usuarios para que se conecten a él.
- [Uso de JEA](using-jea.md): obtenga información sobre las distintas formas en que puede usar JEA.
- [Consideraciones de seguridad](security-considerations.md): revise los procedimientos recomendados de seguridad y las implicaciones de las opciones de configuración de JEA.
- [Auditoría e informes en JEA](audit-and-report.md): obtenga información sobre cómo auditar y crear informes sobre los puntos de conexión de JEA.

## <a name="samples-and-dsc-resource"></a>Ejemplos y recurso de DSC

En el [repositorio de GitHub de JEA](https://github.com/PowerShell/JEA) puede encontrar configuraciones de JEA de ejemplo y el recurso de DSC de JEA.