---
title: Parámetros de seguridad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369504"
---
# <a name="security-parameters"></a>Parámetros de seguridad

En la tabla siguiente se enumeran los nombres y la funcionalidad recomendados para los parámetros que se usan para proporcionar información de seguridad para una operación, como los parámetros que especifican la información de privilegios y claves de certificado.

|Parámetro|Funcionalidad|
|---|---|
|**ACL**<br>Tipo de datos: cadena|Implemente este parámetro para especificar el nivel de control de acceso de protección para un catálogo o para un identificador uniforme de recursos (URI).|
|**Archivo CERTFILE**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre de un archivo que contenga uno de los siguientes elementos:<br>-Un certificado x. 509 codificado de base64 o reglas de codificación distinguida (DER)<br>-Un archivo #12 de estándares de criptografía de clave pública (PKCS) que contiene al menos un certificado y una clave.|
|**CertIssuerName**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre del emisor de un certificado o para que el usuario pueda especificar una subcadena.|
|**CertRequestFile**<br>Tipo de datos: cadena|Implemente este parámetro para especificar el nombre de un archivo que contiene una solicitud de certificado PKCS #10 codificada en base64 o DER.|
|**CertSerialNumber**<br>Tipo de datos: cadena|Implemente este parámetro para especificar el número de serie emitido por la entidad de certificación.|
|**CertStoreLocation**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar la ubicación del almacén de certificados. La ubicación suele ser una ruta de acceso de archivo.|
|**CertSubjectName**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el emisor de un certificado o para que el usuario pueda especificar una subcadena.|
|**CertUsage**<br>Tipo de datos: cadena|Implemente este parámetro para especificar el uso de la clave o el uso mejorado de la clave. La clave se puede representar como una máscara de bits, un bit, un identificador de objeto (OID) o una cadena.|
|**Caja**<br>Tipo de datos: [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implemente este parámetro para que el cmdlet solicite automáticamente al usuario un nombre de usuario o una contraseña. Si no se proporciona directamente una credencial completa, se mostrará un símbolo del sistema.|
|**CSPName**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre del proveedor de servicios de certificados (CSP).|
|**CSPType**<br>Tipo de datos: entero|Implemente este parámetro para que el usuario pueda especificar el tipo de CSP.|
|**Grupo**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una colección de entidades de seguridad para el acceso. Para obtener más información, vea la descripción del parámetro **principal** .|
|**KeyAlgorithm**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el algoritmo de generación de claves que se va a utilizar para la seguridad.|
|**KeyContainerName**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el nombre del contenedor de claves.|
|**KeyLength**<br>Tipo de datos: entero|Implemente este parámetro para que el usuario pueda especificar la longitud de la clave en bits.|
|**Sesión**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una acción que se puede realizar en un objeto protegido.|
|**Entidad**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar una entidad identificable única para el acceso.|
|**Privilegia**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el derecho que un cmdlet debe realizar una operación para una entidad determinada.|
|**Privilegios**<br>Tipo de datos: matriz de privilegios|Implemente este parámetro para que el usuario pueda especificar los derechos que un cmdlet necesita para realizar su operación para una entrada determinada.|
|**Role**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un conjunto de operaciones que puede realizar una entidad.|
|**SaveCred**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se usen las credenciales que se guardaron previamente por el usuario cuando se especifica el parámetro.|
|**ID**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar el grupo de objetos protegidos para el cmdlet.|
|**Junction**<br>Tipo de datos: cadena|Implemente este parámetro para que el usuario pueda especificar un identificador único que representa una entidad de seguridad.|
|**Confiar**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se admitan los niveles de confianza cuando se especifique el parámetro.|
|**TrustLevel**<br>Tipo de datos: palabra clave|Implemente este parámetro para que el usuario pueda especificar el nivel de confianza que se admite. Por ejemplo, los valores posibles son Internet, intranet y FullTrust.|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
