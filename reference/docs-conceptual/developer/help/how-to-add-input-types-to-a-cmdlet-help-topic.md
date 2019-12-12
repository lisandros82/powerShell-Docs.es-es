---
title: Cómo agregar tipos de entrada a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361244"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="3c02a-102">Cómo agregar tipos de entrada a un tema de Ayuda del cmdlet</span><span class="sxs-lookup"><span data-stu-id="3c02a-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="3c02a-103">En esta sección se describe cómo agregar una sección de entradas a un tema de ayuda del cmdlet de® de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c02a-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="3c02a-104">En la sección entradas se enumeran las clases .NET de objetos que el cmdlet acepta como entrada de la canalización, ya sea por valor o por nombre de propiedad.</span><span class="sxs-lookup"><span data-stu-id="3c02a-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="3c02a-105">No hay ningún límite en el número de clases que se pueden agregar a una sección de entradas.</span><span class="sxs-lookup"><span data-stu-id="3c02a-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="3c02a-106">Los tipos de entrada se incluyen en un \<comando: inputTypes > nodo, donde cada clase se incluye en un elemento \<comando: inputType >.</span><span class="sxs-lookup"><span data-stu-id="3c02a-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="3c02a-107">El esquema incluye dos \<maml: Description > elementos en cada \<comando: inputType > elemento.</span><span class="sxs-lookup"><span data-stu-id="3c02a-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="3c02a-108">Sin embargo, el cmdlet `Get-Help` solo muestra el contenido del elemento \<comando: inputType >/\<maml: Description >).</span><span class="sxs-lookup"><span data-stu-id="3c02a-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="3c02a-109">A partir de Windows PowerShell 3,0, el cmdlet `Get-Help` muestra el contenido del elemento \<maml: URI >.</span><span class="sxs-lookup"><span data-stu-id="3c02a-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="3c02a-110">Este elemento le permite dirigir a los usuarios a temas que describen la clase .NET.</span><span class="sxs-lookup"><span data-stu-id="3c02a-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="3c02a-111">El siguiente código XML muestra el nodo \<maml: inputTypes >.</span><span class="sxs-lookup"><span data-stu-id="3c02a-111">The following XML shows the \<maml:inputTypes> node.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

<span data-ttu-id="3c02a-112">El siguiente código XML muestra un ejemplo del uso del nodo \<maml: inputTypes > para documentar un tipo de entrada.</span><span class="sxs-lookup"><span data-stu-id="3c02a-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```