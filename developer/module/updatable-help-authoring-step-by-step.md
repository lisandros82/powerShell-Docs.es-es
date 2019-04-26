---
title: 'Creación de la Ayuda actualizable: Paso a paso | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082131"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="198aa-102">Creación de la Ayuda actualizable: paso a paso</span><span class="sxs-lookup"><span data-stu-id="198aa-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="198aa-103">En este documentos se enumeran los pasos del proceso de creación de ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="198aa-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="198aa-104">La Ayuda actualizable de creación: paso a paso</span><span class="sxs-lookup"><span data-stu-id="198aa-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="198aa-105">La Ayuda actualizable está diseñada para usuarios finales, pero también proporciona ventajas importantes a los autores de módulos y escritores de ayuda, incluida la capacidad para agregar contenido, corregirán los errores, entregar en varias referencias culturales de interfaz de usuario y responden a solicitudes y los comentarios del usuario después de la módulo se ha enviado.</span><span class="sxs-lookup"><span data-stu-id="198aa-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="198aa-106">En este tema se explica cómo empaqueta y ayuda de la carga de archivos para que los usuarios pueden descargarlas e instalarlas mediante el uso de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="198aa-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="198aa-107">Los pasos siguientes proporcionan una visión general del proceso de compatibilidad con la Ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="198aa-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="198aa-108">Paso 1: Buscar un sitio de Internet para los archivos de ayuda</span><span class="sxs-lookup"><span data-stu-id="198aa-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="198aa-109">El primer paso en la creación de la Ayuda actualizable es buscar una ubicación de Internet para los archivos de Ayuda de su módulo.</span><span class="sxs-lookup"><span data-stu-id="198aa-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="198aa-110">En realidad, puede usar dos ubicaciones diferentes.</span><span class="sxs-lookup"><span data-stu-id="198aa-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="198aa-111">Puede mantener el archivo de información de su módulo ayuda (HelpInfo XML: se describe a continuación) en una ubicación de Internet y los archivos CAB contenidos de ayuda en otra ubicación de Internet.</span><span class="sxs-lookup"><span data-stu-id="198aa-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="198aa-112">Todos los archivos de CAB contenido ayuda para un módulo deben estar en la misma ubicación.</span><span class="sxs-lookup"><span data-stu-id="198aa-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="198aa-113">Puede colocar archivos CAB contenidos de ayuda para los distintos módulos en la misma ubicación.</span><span class="sxs-lookup"><span data-stu-id="198aa-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="198aa-114">Paso 2: Agregar una clave HelpInfoURI al manifiesto de módulo</span><span class="sxs-lookup"><span data-stu-id="198aa-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="198aa-115">Agregar un **HelpInfoURI** clave al manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="198aa-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="198aa-116">El valor de la clave es el identificador uniforme de recursos (URI) de la ubicación del archivo de información XML HelpInfo para el módulo.</span><span class="sxs-lookup"><span data-stu-id="198aa-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="198aa-117">Para la seguridad, la dirección debe comenzar con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="198aa-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="198aa-118">El URI debe especificar una ubicación de Internet, pero no debe incluir el nombre del archivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="198aa-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="198aa-119">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="198aa-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="198aa-120">Paso 3: Cree un archivo XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="198aa-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="198aa-121">El archivo de información XML HelpInfo contiene el URI de la ubicación de Internet de los archivos de ayuda y los números de versión de los archivos de ayuda más recientes para el módulo en cada referencia cultural de interfaz de usuario admitida.</span><span class="sxs-lookup"><span data-stu-id="198aa-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="198aa-122">Cada módulo de Windows PowerShell tiene un archivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="198aa-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="198aa-123">Al actualizar los archivos de ayuda, editar o reemplazar el archivo XML HelpInfo; No agregue otro.</span><span class="sxs-lookup"><span data-stu-id="198aa-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="198aa-124">Para obtener más información, consulte [cómo crear un archivo de XML HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="198aa-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="198aa-125">Paso 4: Firme los archivos de ayuda</span><span class="sxs-lookup"><span data-stu-id="198aa-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="198aa-126">Las firmas digitales no son necesarias, pero son una práctica recomendada cuando el uso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="198aa-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="198aa-127">Paso 5: Crear archivos CAB</span><span class="sxs-lookup"><span data-stu-id="198aa-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="198aa-128">Usar una herramienta que crea archivos de contenedor (.cab), como MakeCab.exe para crear una. Archivo CAB que contiene los archivos de ayuda para el módulo.</span><span class="sxs-lookup"><span data-stu-id="198aa-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="198aa-129">Cree un archivo .cab independiente para los archivos de ayuda en cada referencia cultural de interfaz de usuario admitida.</span><span class="sxs-lookup"><span data-stu-id="198aa-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="198aa-130">Para obtener más información, consulte [cómo preparar actualizable ayudan a los archivos CAB](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="198aa-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="198aa-131">Paso 6: Cargar los archivos</span><span class="sxs-lookup"><span data-stu-id="198aa-131">Step 6: Upload your files</span></span>

<span data-ttu-id="198aa-132">Para publicar los archivos de ayuda nuevos o actualizados, cargar los archivos .cab a la ubicación de Internet que se especifica mediante el **HelpContentUri** elemento en el archivo XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="198aa-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="198aa-133">A continuación, cargue el archivo XML HelpInfo para la ubicación de Internet que se especifica mediante el valor de la **HelpInfoUri** clave en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="198aa-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
