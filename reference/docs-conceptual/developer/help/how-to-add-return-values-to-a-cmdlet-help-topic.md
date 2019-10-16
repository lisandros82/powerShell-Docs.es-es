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
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Cómo agregar valores devueltos a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar una sección de salidas a un tema de ayuda del cmdlet de® de Windows PowerShell. En la sección salidas se enumeran las clases .NET de objetos que el cmdlet devuelve o pasa por la canalización.

No hay ningún límite en el número de clases que se pueden agregar a la sección de salidas. Los tipos de valor devueltos de un cmdlet se incluyen en un nodo \<command: returnValues >, donde cada clase se incluye en un elemento \<command: returnValue >.

Si un cmdlet no genera ningún resultado, use esta sección para indicar que no hay ninguna salida. Por ejemplo, en lugar del nombre de clase, escriba "none" y proporcione una breve explicación. Si el cmdlet genera la salida de forma condicional, use este nodo para explicar las condiciones y describir la salida condicional.

El esquema incluye dos elementos \<maml: Description > en cada elemento \<command: returnValue >. Sin embargo, el cmdlet `Get-Help` solo muestra el contenido del elemento \<command: returnValue >/\<maml: Description >.

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
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



