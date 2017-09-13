---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 60055b6755a31397c49686ea9ee1a69ada3516de
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="7d287-102">Cmdlets de sintaxis de mensajes de cifrado (CMS)</span><span class="sxs-lookup"><span data-stu-id="7d287-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="7d287-103">Los cmdlets de sintaxis de mensajes de cifrado admiten el cifrado y descifrado de contenido mediante el formato estándar IETF para proteger los mensajes de forma criptográfica según se documenta en [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="7d287-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

<span data-ttu-id="7d287-104">El estándar de cifrado de CMS implementa la criptografía de clave pública, donde las claves usadas para cifrar contenido (la *clave pública*) y las claves usadas para descifrar contenido (la *clave privada*) son independientes.</span><span class="sxs-lookup"><span data-stu-id="7d287-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="7d287-105">La clave pública se puede compartir y no se considera información confidencial.</span><span class="sxs-lookup"><span data-stu-id="7d287-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="7d287-106">Si cualquier contenido está cifrado con esta clave pública, solo su clave privada puede descifrarlo.</span><span class="sxs-lookup"><span data-stu-id="7d287-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="7d287-107">Para obtener más información, consulte [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography) (Criptografía mediante claves públicas).</span><span class="sxs-lookup"><span data-stu-id="7d287-107">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="7d287-108">Para que puedan reconocerse en PowerShell, los certificados de cifrado requieren un identificador de uso de claves único (EKU) para identificarlos como certificados de cifrado de datos (por ejemplo, los identificadores de "Firma de código" y "Correo cifrado").</span><span class="sxs-lookup"><span data-stu-id="7d287-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="7d287-109">Este es un ejemplo de cómo crear un certificado adecuado para el cifrado del documento:</span><span class="sxs-lookup"><span data-stu-id="7d287-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

<span data-ttu-id="7d287-110">A continuación, ejecute:</span><span class="sxs-lookup"><span data-stu-id="7d287-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="7d287-111">Ahora puede cifrar y descifrar el contenido:</span><span class="sxs-lookup"><span data-stu-id="7d287-111">And you can now encrypt and decrypt content:</span></span>

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

<span data-ttu-id="7d287-112">Cualquier parámetro de tipo **CMSMessageRecipient** admite identificadores en los siguientes formatos:</span><span class="sxs-lookup"><span data-stu-id="7d287-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="7d287-113">Un certificado real (tal y como se recuperó del proveedor de certificados).</span><span class="sxs-lookup"><span data-stu-id="7d287-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="7d287-114">Ruta de acceso al archivo que contiene el certificado.</span><span class="sxs-lookup"><span data-stu-id="7d287-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="7d287-115">Ruta de acceso a un directorio que contiene el certificado.</span><span class="sxs-lookup"><span data-stu-id="7d287-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="7d287-116">Huella digital del certificado (usada para buscar en el almacén de certificados).</span><span class="sxs-lookup"><span data-stu-id="7d287-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="7d287-117">Nombre de asunto del certificado (usado para buscar en el almacén de certificados).</span><span class="sxs-lookup"><span data-stu-id="7d287-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="7d287-118">Para ver los certificados de cifrado del documento en el proveedor de certificados, puede usar el parámetro dinámico **-DocumentEncryptionCert**:</span><span class="sxs-lookup"><span data-stu-id="7d287-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```

