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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Cómo agregar tipos de entrada a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar una sección de entradas a un tema de ayuda del cmdlet de® de Windows PowerShell. En la sección entradas se enumeran las clases .NET de objetos que el cmdlet acepta como entrada de la canalización, ya sea por valor o por nombre de propiedad.

No hay ningún límite en el número de clases que se pueden agregar a una sección de entradas. Los tipos de entrada se incluyen en un \<comando: inputTypes > nodo, donde cada clase se incluye en un elemento \<comando: inputType >.

El esquema incluye dos \<maml: Description > elementos en cada \<comando: inputType > elemento. Sin embargo, el cmdlet `Get-Help` solo muestra el contenido del elemento \<comando: inputType >/\<maml: Description >).

A partir de Windows PowerShell 3,0, el cmdlet `Get-Help` muestra el contenido del elemento \<maml: URI >. Este elemento le permite dirigir a los usuarios a temas que describen la clase .NET.

El siguiente código XML muestra el nodo \<maml: inputTypes >.

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

El siguiente código XML muestra un ejemplo del uso del nodo \<maml: inputTypes > para documentar un tipo de entrada.

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