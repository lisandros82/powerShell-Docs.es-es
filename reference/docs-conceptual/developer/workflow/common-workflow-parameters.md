---
title: Parámetros comunes de flujo de trabajo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366054"
---
# <a name="common-workflow-parameters"></a>Parámetros de flujo de trabajo comunes

Una actividad de flujo de trabajo generada a partir de un cmdlet de Windows PowerShell define una serie de parámetros que son comunes a todas las actividades. Se puede especificar un subconjunto de estos parámetros en el momento de la creación para que los autores del flujo de trabajo puedan personalizar las actividades. El usuario puede especificar otro subconjunto de estos parámetros al llamar a la actividad.

Los parámetros de flujo de trabajo comunes se agrupan en varias categorías como se indica a continuación.

## <a name="connectivity-parameters"></a>Parámetros de conectividad

|Name|Tipo|Descripción|¿Se puede especificar el usuario final en tiempo de ejecución?|¿Se puede especificar mediante el autor del flujo de trabajo en el momento de la creación?|¿Se puede especificar mediante el autor del flujo de trabajo en la creación de instancias?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Una lista de nombres de equipo para los que se van a iniciar trabajos.|Sí|Sí|Sí|
|PSCredential|[System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Credencial de autenticación que se va a usar para iniciar sesión en los equipos especificados por el parámetro PSComputerName. Este parámetro es válido solo si se especifica PSComputerName.|Sí|Sí|Sí|
|PSPort|UInt32|Puerto que se va a utilizar para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSUseSSL|Booleano|Use el protocolo Capa de sockets seguros (SSL) para establecer una conexión segura con el equipo remoto para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSConfigurationName|Cadena|La configuración de sesión utilizada para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSApplicationName|Cadena|La parte del nombre de la aplicación del URI de conexión para la ejecución del flujo de trabajo. Use este parámetro solo si no usa el parámetro ConnectionURI.|Sí|Sí|Sí|
|PSThrottleLimit|UInt32|Número máximo de conexiones simultáneas que se pueden establecer para ejecutar el flujo de trabajo.|Sí|Por determinar|Sí|
|PSConnectionURI|String[]|Matriz de identificadores URI completos que especifican los puntos de conexión de las sesiones interactivas utilizadas para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSAllowRedirection|Booleano|Especifica si se permite la redirección de esta conexión a un URI alternativo para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSSessionOption|[System. Management. Automation. Remoting. Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Opciones avanzadas de la sesión usada para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSAuthentication|[System. Management. Automation. espacios de Authenticationmechanism.](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Un valor de la enumeración [System. Management. Automation. espacios de Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) que especifica el mecanismo de autenticación usado para autenticar las credenciales del usuario.|Sí|Sí|Sí|
|PSCertificateThumbprint|Cadena|El certificado de clave pública digital (X509) de una cuenta de usuario que tiene permiso para ejecutar el flujo de trabajo.|Sí|Sí|Sí|

### <a name="behavior-parameters"></a>Parámetros de comportamiento