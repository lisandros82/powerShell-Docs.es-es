---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_moduledependencypopulation
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: a6ace8faebd6f37d3c41ee5a3fef2bda70b8c651

---

# Lógica para preparar las dependencias de módulo durante la operación de publicación
1.  Los módulos indicados como parte de RequiredModules se consideran dependencias.
2.  Los módulos indicados como parte de NestedModules, cuya base del módulo no se encuentra bajo la base del módulo especificado, se consideran dependencias.

3.  Las dependencias anteriores deben estar disponibles en el mismo repositorio de destino. En caso contrario, se producirá un error en una operación de publicación.
    Por ejemplo, si "SnippetPx" no está disponible en el repositorio, se producirá el error siguiente.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Es posible administrar externamente algunas dependencias de módulo. En este caso, se deben agregar a la entrada ExternalModuleDependencies de la sección PSData del manifiesto del módulo.
    Parte inferior del mensaje de error anterior
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Durante la instalación del módulo, se usa la lista anterior de dependencias preparadas para instalar las dependencias.*

*Asegúrese de que las dependencias del módulo están disponibles en $env:PSModulePath en el sistema durante la operación de publicación.*




<!--HONumber=Oct16_HO2-->


