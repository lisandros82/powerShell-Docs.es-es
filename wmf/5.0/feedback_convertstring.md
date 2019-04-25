---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057798"
---
# <a name="convert-string"></a><span data-ttu-id="ebf7e-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="ebf7e-102">Convert-String</span></span>
<span data-ttu-id="ebf7e-103">**Convert-String** expone la funcionalidad "reemplazar por arte de magia".</span><span class="sxs-lookup"><span data-stu-id="ebf7e-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="ebf7e-104">Proporcione ejemplos del antes y el después del aspecto que quiere que tenga el texto que se va a buscar y **Convert-String** dará formato al texto automáticamente.</span><span class="sxs-lookup"><span data-stu-id="ebf7e-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="ebf7e-105">Aquí tiene una demostración: tomamos el nombre y el apellido de alguien, los reemplazamos por su apellido, una coma, la inicial del apellido y un punto.</span><span class="sxs-lookup"><span data-stu-id="ebf7e-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="ebf7e-106">Pruébelo con una regex y vea cuánto tarda en hacerlo.</span><span class="sxs-lookup"><span data-stu-id="ebf7e-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
