---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: Información general de Just Enough Administration
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017706"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) es una tecnología de seguridad que permite la administración delegada de todo lo que administra PowerShell. Con JEA, se puede hacer lo siguiente:

- **Reducir el número de administradores de las máquinas** mediante cuentas virtuales o cuentas de servicio administradas por grupos para realizar acciones con privilegios en nombre de usuarios normales.
- **Limitar lo que pueden hacer los usuarios** especificando qué cmdlets, funciones y comandos externos pueden ejecutar.
- **Entender mejor lo que hacen los usuarios** con transcripciones y registros que muestran exactamente qué comandos ha ejecutado un usuario durante su sesión.

**¿Por qué es importante JEA?**

Las cuentas con muchos privilegios usadas para administrar los servidores suponen un grave riesgo de seguridad. Si un atacante compromete una de estas cuentas, podría iniciar [ataques laterales](https://aka.ms/pth) en toda la organización. Cada cuenta comprometida puede dar a un atacante acceso incluso a más cuentas y recursos, y ponerle un paso más cerca de robar secretos de la empresa, iniciar un ataque por denegación de servicio y mucho más.

No siempre es fácil quitar privilegios administrativos. Tenga en cuenta el escenario común en que el rol DNS está instalado en el mismo equipo que el controlador de dominio de Active Directory. Los administradores de DNS necesitan privilegios de administrador local para solucionar problemas con el servidor DNS. Pero para ello, debe convertirlos en miembros del grupo de seguridad con privilegios elevados **Admins. del dominio**. Este enfoque proporciona a los administradores de DNS el control sobre todo el dominio y les permite acceder a todos los recursos de la máquina.

JEA resuelve este problema a través del principio de **privilegios mínimos**. Con JEA, puede configurar un punto de conexión de administración para los administradores de DNS que les proporcione acceso solo a los comandos de PowerShell que necesitan para realizar su trabajo. Esto significa que puede proporcionar el acceso adecuado para reparar una caché DNS dañada o reiniciar el servidor DNS sin concederles involuntariamente derechos en Active Directory, para examinar el sistema de archivos o para ejecutar scripts potencialmente peligrosos. Y lo que es mejor, cuando la sesión de JEA está configurada para usar cuentas virtuales con privilegios temporales, los administradores de DNS pueden conectarse al servidor mediante credenciales **que no sean de administrador** y seguir ejecutando comandos que normalmente requieren privilegios de administrador. JEA permite quitar usuarios de roles de administrador local o de dominio con muchos privilegios, y controlar cuidadosamente qué pueden hacer en cada equipo.

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre los requisitos para usar JEA, vea el artículo de [requisitos previos](prerequisites.md).

## <a name="samples-and-dsc-resource"></a>Ejemplos y recurso de DSC

En el [repositorio de GitHub de JEA](https://github.com/PowerShell/JEA) puede encontrar configuraciones de JEA de ejemplo y el recurso de DSC de JEA.
