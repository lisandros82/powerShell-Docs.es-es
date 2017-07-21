---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: psget_moduledependencypopulation
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="6b6a6-103">Lógica para preparar las dependencias de módulo durante la operación de publicación</span><span class="sxs-lookup"><span data-stu-id="6b6a6-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="6b6a6-104">Los módulos indicados como parte de RequiredModules se consideran dependencias.</span><span class="sxs-lookup"><span data-stu-id="6b6a6-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="6b6a6-105">Los módulos indicados como parte de NestedModules, cuya base del módulo no se encuentra bajo la base del módulo especificado, se consideran dependencias.</span><span class="sxs-lookup"><span data-stu-id="6b6a6-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="6b6a6-106">Las dependencias anteriores deben estar disponibles en el mismo repositorio de destino. En caso contrario, se producirá un error en una operación de publicación.</span><span class="sxs-lookup"><span data-stu-id="6b6a6-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="6b6a6-107">Por ejemplo, si "SnippetPx" no está disponible en el repositorio, se producirá el error siguiente.</span><span class="sxs-lookup"><span data-stu-id="6b6a6-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="6b6a6-108">Es posible administrar externamente algunas dependencias de módulo. En este caso, se deben agregar a la entrada ExternalModuleDependencies de la sección PSData del manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="6b6a6-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="6b6a6-109">Parte inferior del mensaje de error anterior</span><span class="sxs-lookup"><span data-stu-id="6b6a6-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="6b6a6-110">*Durante la instalación del módulo, se usa la lista anterior de dependencias preparadas para instalar las dependencias.*</span><span class="sxs-lookup"><span data-stu-id="6b6a6-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="6b6a6-111">*Asegúrese de que las dependencias del módulo están disponibles en $env:PSModulePath en el sistema durante la operación de publicación.*</span><span class="sxs-lookup"><span data-stu-id="6b6a6-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>

