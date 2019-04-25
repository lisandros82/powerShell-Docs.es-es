---
title: Los parámetros de seguridad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067440"
---
# <a name="security-parameters"></a>Parámetros de seguridad

En la tabla siguiente se enumera los nombres recomendados y la funcionalidad para los parámetros que se usan para proporcionar información de seguridad para una operación, como los parámetros que especifican la información de clave y los privilegios del certificado.

|Parámetro|Funcionalidad|
|---|---|
|**ACL**<br>Tipo de datos: Cadena|Implemente este parámetro para especificar el nivel de protección para un catálogo o para un identificador uniforme de recursos (URI) del control de acceso.|
|**CertFile**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre de un archivo que contiene uno de los siguientes:<br>: Un certificado x.509 codificado en Base64 o reglas de codificación distinguida (DER)<br>-Un archivo Public Key Cryptography Standards (PKCS) #12 que contiene al menos un certificado y clave|
|**CertIssuerName**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre del emisor de un certificado o para que el usuario puede especificar una subcadena.|
|**CertRequestFile**<br>Tipo de datos: Cadena|Implemente este parámetro para especificar el nombre de un archivo que contiene una solicitud de certificado Base64 o DER codificado PKCS #10.|
|**CertSerialNumber**<br>Tipo de datos: Cadena|Implemente este parámetro para especificar el número de serie que fue emitido por la entidad de certificación.|
|**CertStoreLocation**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar la ubicación del almacén de certificados. Normalmente, la ubicación es una ruta de acceso de archivo.|
|**CertSubjectName**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar al emisor de un certificado o para que el usuario puede especificar una subcadena.|
|**CertUsage**<br>Tipo de datos: Cadena|Implemente este parámetro para especificar el uso de claves o el uso mejorado de clave. La clave se puede representar como un poco de máscara, un poco, un identificador de objeto (OID), o una cadena.|
|**Credencial**<br>Tipo de datos: [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implemente este parámetro para que el cmdlet le pedirá automáticamente al usuario un nombre de usuario o contraseña. Si no se proporciona directamente una credencial completa, se muestra un símbolo del sistema para ambos.|
|**CSPName**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre del proveedor de servicios de certificado (CSP).|
|**CSPType**<br>Tipo de datos: Entero|Implemente este parámetro para que el usuario puede especificar el tipo de CSP.|
|**Grupo**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una colección de entidades de seguridad para el acceso. Para obtener más información, vea la descripción de la **Principal** parámetro.|
|**KeyAlgorithm**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el algoritmo de generación de claves que se usará para la seguridad.|
|**KeyContainerName**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el nombre del contenedor de claves.|
|**KeyLength**<br>Tipo de datos: Entero|Implemente este parámetro para que el usuario puede especificar la longitud de la clave en bits.|
|**Operación**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una acción que se puede realizar en un objeto protegido.|
|**Entidad de seguridad**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar una entidad de identificación única para el acceso.|
|**Privilege**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el derecho de que un cmdlet se debe realizar una operación de una entidad concreta.|
|**Privilegios**<br>Tipo de datos: Matriz de privilegios|Implemente este parámetro para que el usuario puede especificar los derechos que necesita un cmdlet para realizar sus operaciones de una entrada determinada.|
|**Role**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un conjunto de operaciones que pueden realizarse por una entidad.|
|**SaveCred**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que las credenciales que se guardaron anteriormente por el usuario que se usará cuando se especifica el parámetro.|
|**Ámbito**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar el grupo de objetos protegidos para el cmdlet.|
|**SID**<br>Tipo de datos: Cadena|Implemente este parámetro para que el usuario puede especificar un identificador único que representa una entidad de seguridad.|
|**confianza**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que se admiten los niveles de confianza cuando se especifica el parámetro.|
|**TrustLevel**<br>Tipo de datos: Palabra clave|Implemente este parámetro para que el usuario puede especificar el nivel de confianza que se admite. Por ejemplo, los valores posibles incluyen internet, intranet y plena confianza.|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
