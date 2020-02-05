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
ms.openlocfilehash: ad0fe5c63b145c681f14328d5ef5a8784a035e26
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995929"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Cómo agregar valores devueltos a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar una sección de salidas a un tema de ayuda del cmdlet de® de Windows PowerShell. En la sección salidas se enumeran las clases .NET de objetos que el cmdlet devuelve o pasa por la canalización.

No hay ningún límite en el número de clases que se pueden agregar a la sección de salidas. Los tipos de valor devueltos de un cmdlet se incluyen en un \<comando: returnValues > nodo, donde cada clase se incluye en un elemento \<comando: returnValue >.

Si un cmdlet no genera ningún resultado, use esta sección para indicar que no hay ninguna salida. Por ejemplo, en lugar del nombre de clase, escriba "none" y proporcione una breve explicación. Si el cmdlet genera la salida de forma condicional, use este nodo para explicar las condiciones y describir la salida condicional.

El esquema incluye dos \<maml: Description > elementos en cada \<comando: returnValue > elemento. Sin embargo, el cmdlet `Get-Help` muestra solo el contenido del comando \<: returnValue >/\<maml: Description > elemento.

A partir de Windows PowerShell 3,0, el cmdlet `Get-Help` muestra el contenido del elemento \<maml: URI >. Este elemento le permite dirigir a los usuarios a temas que describen la clase .NET.

El siguiente código XML muestra el nodo \<maml: returnValues >.

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

El siguiente código XML muestra un ejemplo del uso del nodo \<maml: returnValues > para documentar un tipo de salida.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



