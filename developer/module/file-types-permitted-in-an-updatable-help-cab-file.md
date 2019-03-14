---
title: Archivo CAB de ayudar a los tipos de archivo permitidos en un actualizable | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794253"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="82820-102">Tipos de archivo permitidos en un archivo CAB de Ayuda actualizable</span><span class="sxs-lookup"><span data-stu-id="82820-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="82820-103">En este tema se enumeran y describen los requisitos de contenido para archivos CAB de ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="82820-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="82820-104">Requisitos del archivo CAB de ayuda actualizable</span><span class="sxs-lookup"><span data-stu-id="82820-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="82820-105">Contenido del archivo CAB sin comprimir se limita a 1 GB de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="82820-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="82820-106">Para omitir este límite, los usuarios tienen que usar el **Force** parámetro de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="82820-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="82820-107">Para garantizar la seguridad de los archivos de ayuda que se descargan de Internet, un archivo .cab de ayuda actualizable puede incluir solo los tipos de archivo que se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="82820-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="82820-108">El [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valida todos los archivos con los esquemas del tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="82820-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="82820-109">Si el `Update-Help` cmdlet encuentra un archivo que no es válido o no es un tipo permitido, no se instala el archivo no válido y se detiene la instalación de archivos desde el archivo CAB en el equipo del usuario.</span><span class="sxs-lookup"><span data-stu-id="82820-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="82820-110">Temas de Ayuda basados en XML para los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="82820-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="82820-111">Temas de Ayuda basados en XML de scripts y funciones.</span><span class="sxs-lookup"><span data-stu-id="82820-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="82820-112">Temas de Ayuda basados en XML para los proveedores de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82820-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="82820-113">Basado en texto temas de ayuda, como temas de ayuda.</span><span class="sxs-lookup"><span data-stu-id="82820-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="82820-114">El [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comprueba el contenido del archivo CAB Cuando desempaquete el archivo CAB.</span><span class="sxs-lookup"><span data-stu-id="82820-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="82820-115">Si `Update-Help` busca los tipos de archivo no compatible en un archivo .cab de ayuda actualizable, se genera un error de terminación y detiene la operación.</span><span class="sxs-lookup"><span data-stu-id="82820-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="82820-116">No instala los archivos de Ayuda desde el archivo CAB, incluso los tipos de archivo compatibles.</span><span class="sxs-lookup"><span data-stu-id="82820-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>