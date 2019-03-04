---
title: Cómo agregar tipos de entrada a un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860811"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Cómo agregar tipos de entrada a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar una sección de entradas a un tema de Ayuda de cmdlet Windows PowerShell®. La sección de entradas enumera las clases de .NET de objetos que el cmdlet acepta como entrada de la canalización, por valor o por nombre de propiedad.

No hay ningún límite al número de clases que se pueden agregar a una sección de entradas. Se incluyen los tipos de entrada en un \<inputTypes: comando > nodo, donde cada clase que se incluyen en un \<inputType: comando > elemento.

El esquema incluye dos \<maml:description > elementos de cada \<inputType: comando > elemento. Sin embargo, el `Get-Help` cmdlet muestra solo el contenido de la \<inputType: comando > /\<maml:description >) elemento.

A partir de Windows PowerShell 3.0, el `Get-Help` cmdlet muestra el contenido de la \<maml: URI > elemento. Este elemento le permite dirigir a los usuarios a temas que describen la clase. NET.

El siguiente XML muestra el \<maml:inputTypes > nodo.

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

El siguiente XML muestra un ejemplo del uso de la \<maml:inputTypes > nodo para documentar un tipo de entrada.

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