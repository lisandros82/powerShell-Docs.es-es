---
title: Cómo probar la ayuda actualizable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367154"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="fee92-102">Cómo probar la Ayuda actualizable</span><span class="sxs-lookup"><span data-stu-id="fee92-102">How to Test Updatable Help</span></span>

<span data-ttu-id="fee92-103">En este tema se describen los métodos para probar la ayuda actualizable de un módulo.</span><span class="sxs-lookup"><span data-stu-id="fee92-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="fee92-104">Usar verbose para detectar errores</span><span class="sxs-lookup"><span data-stu-id="fee92-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="fee92-105">Después de cargar el archivo XML y los archivos. CAB de HelpInfo para el módulo, pruebe los archivos mediante la ejecución de un comando [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) con el parámetro **verbose** .</span><span class="sxs-lookup"><span data-stu-id="fee92-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="fee92-106">El parámetro **verbose** dirige `Update-Help` para informar de los pasos críticos en sus acciones, desde leer la clave **HelpInfoUri** en el manifiesto del módulo hasta validar los tipos de archivo en el archivo CAB Desempaquetado y colocar los archivos en el directorio del módulo específico del idioma.</span><span class="sxs-lookup"><span data-stu-id="fee92-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="fee92-107">Cuando se resuelvan todos los mensajes detallados, ejecute un comando `Update-Help` con el parámetro **Debug** .</span><span class="sxs-lookup"><span data-stu-id="fee92-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="fee92-108">Este parámetro debe detectar cualquier problema restante con los archivos de ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="fee92-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>