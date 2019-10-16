---
title: Cómo agregar valores devueltos a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367804"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="f2b3b-102">Cómo agregar valores devueltos a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f2b3b-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="f2b3b-103">En esta sección se describe cómo agregar una sección de salidas a un tema de ayuda del cmdlet de® de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="f2b3b-104">En la sección salidas se enumeran las clases .NET de objetos que el cmdlet devuelve o pasa por la canalización.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="f2b3b-105">No hay ningún límite en el número de clases que se pueden agregar a la sección de salidas.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="f2b3b-106">Los tipos de valor devueltos de un cmdlet se incluyen en un nodo \<command: returnValues >, donde cada clase se incluye en un elemento \<command: returnValue >.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="f2b3b-107">Si un cmdlet no genera ningún resultado, use esta sección para indicar que no hay ninguna salida.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="f2b3b-108">Por ejemplo, en lugar del nombre de clase, escriba "none" y proporcione una breve explicación.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="f2b3b-109">Si el cmdlet genera la salida de forma condicional, use este nodo para explicar las condiciones y describir la salida condicional.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="f2b3b-110">El esquema incluye dos elementos \<maml: Description > en cada elemento \<command: returnValue >.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="f2b3b-111">Sin embargo, el cmdlet `Get-Help` solo muestra el contenido del elemento \<command: returnValue >/\<maml: Description >.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="f2b3b-112">A partir de Windows PowerShell 3,0, el cmdlet `Get-Help` muestra el contenido del elemento \<maml: URI >.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="f2b3b-113">Este elemento le permite dirigir a los usuarios a temas que describen la clase .NET.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="f2b3b-114">El siguiente código XML muestra el nodo \<maml: returnValues >.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-114">The following XML shows the \<maml:returnValues> node.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

<span data-ttu-id="f2b3b-115">El siguiente código XML muestra un ejemplo del uso del nodo \<maml: returnValues > para documentar un tipo de salida.</span><span class="sxs-lookup"><span data-stu-id="f2b3b-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



