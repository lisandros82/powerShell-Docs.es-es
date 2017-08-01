---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: consideraciones al limitar comandos
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
### <a name="considerations-when-limiting-commands"></a><span data-ttu-id="06676-103">Consideraciones al limitar comandos</span><span class="sxs-lookup"><span data-stu-id="06676-103">Considerations When Limiting Commands</span></span>
<span data-ttu-id="06676-104">En este paso, hay que hacer hincapié en un aspecto importante.</span><span class="sxs-lookup"><span data-stu-id="06676-104">There is one important point to make about this step.</span></span>
<span data-ttu-id="06676-105">Es fundamental que todas las funcionalidades que se exponen a través de JEA se encuentren en áreas restringidas por el administrador.</span><span class="sxs-lookup"><span data-stu-id="06676-105">It is critical that all capabilities exposed through JEA are located in administrator-restricted areas.</span></span>
<span data-ttu-id="06676-106">Los usuarios sin privilegios de administrador no deben tener la capacidad de modificar los scripts que se usan a través de puntos de conexión de JEA.</span><span class="sxs-lookup"><span data-stu-id="06676-106">Non-administrator users should not have the capability to modify the scripts used through JEA endpoints.</span></span>

<span data-ttu-id="06676-107">Además, es fundamental que no ofrezca a los usuarios de JEA la posibilidad de sobrescribir configuraciones de JEA y scripts incluidos en una lista blanca dentro de sus sesiones de JEA.</span><span class="sxs-lookup"><span data-stu-id="06676-107">On a related note, it is critical that you do not give JEA users the ability to overwrite JEA configurations and whitelisted scripts within their JEA sessions.</span></span>
<span data-ttu-id="06676-108">Es muy importante que tenga mucho cuidado al exponer comandos como `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="06676-108">Be extremely careful when exposing commands like `Copy-Item`!</span></span>

