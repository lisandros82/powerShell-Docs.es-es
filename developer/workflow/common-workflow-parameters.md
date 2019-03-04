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
ms.openlocfilehash: 2aca4483e500432ef9f52804e85678d2268aa4cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856141"
---
# <a name="common-workflow-parameters"></a>Parámetros de flujo de trabajo comunes

Una actividad de flujo de trabajo generada a partir de un cmdlet de Windows PowerShell define un número de parámetros es común a todas las actividades. Un subconjunto de estos parámetros se puede especificar en tiempo de creación para que los autores del flujo de trabajo puedan personalizar actividades. Otro subconjunto de estos parámetros se puede especificar el usuario al llamar a la actividad.

Los parámetros comunes de flujo de trabajo se agrupan en varias categorías, como se indica a continuación.

## <a name="connectivity-parameters"></a>Parámetros de conectividad

|Nombre|Tipo|Descripción|¿Se pueden especificar por el usuario final en tiempo de ejecución?|¿Se pueden especificar por el autor del flujo de trabajo durante la creación?|¿Se pueden especificar por el autor del flujo de trabajo en la creación de instancias?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Una lista de nombres de equipo para que se va a iniciar trabajos.|Sí|Sí|Sí|
|PSCredential|[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|Credencial de autenticación que se utilizará para iniciar sesión en los equipos especificados por el parámetro PSComputerName. Este parámetro es válido solo si se especifica PSComputerName.|Sí|Sí|Sí|
|PSPort|UInt32|El puerto que se usará para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSUseSSL|Booleano|Utilice el protocolo de capa de Sockets seguros (SSL) para establecer una conexión segura con el equipo remoto para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSConfigurationName|Cadena|La configuración de sesión utilizada para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSApplicationName|Cadena|La parte del nombre de aplicación de la conexión URI para la ejecución de flujo de trabajo. Use este parámetro solo cuando no se usa el parámetro ConnectionURI.|Sí|Sí|Sí|
|PSThrottleLimit|UInt32|El número máximo de conexiones simultáneas que se pueden establecer para ejecutar el flujo de trabajo.|Sí|Por determinar|Sí|
|PSConnectionURI|String[]|Una matriz de identificadores URI completo que especifique los puntos de conexión para las sesiones interactivas utilizadas para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSAllowRedirection|Booleano|Especifica si se permite la redirección de esta conexión a un URI alternativo para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Opciones avanzadas para la sesión utilizada para ejecutar el flujo de trabajo.|Sí|Sí|Sí|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Un valor de la [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) enumeración que especifica el mecanismo de autenticación utilizado para autenticar las credenciales del usuario.|Sí|Sí|Sí|
|PSCertificateThumbprint|Cadena|Digital certificado de clave pública (X509) de una cuenta de usuario que tenga permiso para ejecutar el flujo de trabajo.|Sí|Sí|Sí|

### <a name="behavior-parameters"></a>Parámetros de comportamiento