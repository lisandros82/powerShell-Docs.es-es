---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219273"
---
# <a name="convert-string"></a><span data-ttu-id="57ee3-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="57ee3-102">Convert-String</span></span>
<span data-ttu-id="57ee3-103">**Convert-String** expone la funcionalidad "reemplazar por arte de magia".</span><span class="sxs-lookup"><span data-stu-id="57ee3-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="57ee3-104">Proporcione ejemplos del antes y el después del aspecto que quiere que tenga el texto que se va a buscar y **Convert-String** dará formato al texto automáticamente.</span><span class="sxs-lookup"><span data-stu-id="57ee3-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="57ee3-105">Aquí tiene una demostración: tomamos el nombre y el apellido de alguien, los reemplazamos por su apellido, una coma, la inicial del apellido y un punto.</span><span class="sxs-lookup"><span data-stu-id="57ee3-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="57ee3-106">Pruébelo con una regex y vea cuánto tarda en hacerlo.</span><span class="sxs-lookup"><span data-stu-id="57ee3-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
