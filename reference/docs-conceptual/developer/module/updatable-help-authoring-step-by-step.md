---
title: 'Creación de ayuda actualizable: paso a paso | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: a5290265f3d729504983b95195c793b88c4a2613
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995979"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="2a564-102">Creación de la Ayuda actualizable: paso a paso</span><span class="sxs-lookup"><span data-stu-id="2a564-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="2a564-103">En este documento se enumeran los pasos del proceso de creación de la ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="2a564-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="2a564-104">Creación de ayuda actualizable: paso a paso</span><span class="sxs-lookup"><span data-stu-id="2a564-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="2a564-105">La ayuda actualizable está diseñada para los usuarios finales, pero también proporciona importantes ventajas a los autores de módulos y escritores de ayuda, incluida la capacidad de agregar contenido, corregir errores, proporcionar varias culturas de la interfaz de usuario y responder a las solicitudes y los comentarios de los usuarios, mucho después de la el módulo se ha enviado.</span><span class="sxs-lookup"><span data-stu-id="2a564-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="2a564-106">En este tema se explica cómo empaquetar y cargar archivos de ayuda para que los usuarios puedan descargarlos e instalarlos mediante los cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="2a564-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="2a564-107">En los pasos siguientes se proporciona información general sobre el proceso de compatibilidad con la ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="2a564-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="2a564-108">Paso 1: buscar un sitio de Internet para los archivos de ayuda</span><span class="sxs-lookup"><span data-stu-id="2a564-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="2a564-109">El primer paso para crear la ayuda actualizable es encontrar una ubicación de Internet para los archivos de ayuda del módulo.</span><span class="sxs-lookup"><span data-stu-id="2a564-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="2a564-110">En realidad, puede usar dos ubicaciones diferentes.</span><span class="sxs-lookup"><span data-stu-id="2a564-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="2a564-111">Puede conservar el archivo de información de ayuda (HelpInfo XML) en una ubicación de Internet y los archivos. CAB de contenido de la ayuda en otra ubicación de Internet.</span><span class="sxs-lookup"><span data-stu-id="2a564-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="2a564-112">Todos los archivos CAB de contenido de ayuda de un módulo deben estar en la misma ubicación.</span><span class="sxs-lookup"><span data-stu-id="2a564-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="2a564-113">Puede colocar archivos CAB de contenido de ayuda para distintos módulos en la misma ubicación.</span><span class="sxs-lookup"><span data-stu-id="2a564-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="2a564-114">Paso 2: agregar una clave de HelpInfoURI al manifiesto del módulo</span><span class="sxs-lookup"><span data-stu-id="2a564-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="2a564-115">Agregue una clave **HelpInfoURI** al manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="2a564-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="2a564-116">El valor de la clave es el identificador uniforme de recursos (URI) de la ubicación del archivo de información XML HelpInfo para el módulo.</span><span class="sxs-lookup"><span data-stu-id="2a564-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="2a564-117">Por seguridad, la dirección debe comenzar con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="2a564-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="2a564-118">El URI debe especificar una ubicación de Internet, pero no debe incluir el nombre de archivo XML de HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="2a564-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="2a564-119">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="2a564-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="2a564-120">Paso 3: crear un archivo XML de HelpInfo</span><span class="sxs-lookup"><span data-stu-id="2a564-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="2a564-121">El archivo de información XML HelpInfo contiene el URI de la ubicación de Internet de los archivos de ayuda y los números de versión de los archivos de ayuda más recientes para el módulo en cada referencia cultural de interfaz de usuario admitida.</span><span class="sxs-lookup"><span data-stu-id="2a564-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="2a564-122">Cada módulo de Windows PowerShell tiene un archivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="2a564-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="2a564-123">Al actualizar los archivos de ayuda, se edita o reemplaza el archivo XML HelpInfo; no agrega otro.</span><span class="sxs-lookup"><span data-stu-id="2a564-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="2a564-124">Para obtener más información, vea [Cómo crear un archivo XML de HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="2a564-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="2a564-125">Paso 4: firmar los archivos de ayuda</span><span class="sxs-lookup"><span data-stu-id="2a564-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="2a564-126">No se requieren firmas digitales, pero se recomiendan las prácticas recomendadas cada vez que comparta archivos.</span><span class="sxs-lookup"><span data-stu-id="2a564-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="2a564-127">Paso 5: crear archivos. CAB</span><span class="sxs-lookup"><span data-stu-id="2a564-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="2a564-128">Use una herramienta que cree archivos contenedores (. cab), como MakeCab. exe, para crear un. Archivo. CAB que contiene los archivos de ayuda del módulo.</span><span class="sxs-lookup"><span data-stu-id="2a564-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="2a564-129">Cree un archivo CAB independiente para los archivos de ayuda en cada referencia cultural de interfaz de usuario admitida.</span><span class="sxs-lookup"><span data-stu-id="2a564-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="2a564-130">Para obtener más información, vea [Cómo preparar archivos. cab de ayuda actualizable](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="2a564-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="2a564-131">Paso 6: carga de los archivos</span><span class="sxs-lookup"><span data-stu-id="2a564-131">Step 6: Upload your files</span></span>

<span data-ttu-id="2a564-132">Para publicar archivos de ayuda nuevos o actualizados, cargue los archivos. CAB en la ubicación de Internet especificada por el elemento **HelpContentUri** en el archivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="2a564-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="2a564-133">Después, cargue el archivo XML HelpInfo en la ubicación de Internet especificada por el valor de la clave **HelpInfoUri** en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="2a564-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
