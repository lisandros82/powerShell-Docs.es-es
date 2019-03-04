---
title: Cómo agregar la devolución de valores a un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859441"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Cómo agregar valores devueltos a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar una sección de salidas a un tema de Ayuda de cmdlet Windows PowerShell®. La sección de salidas muestra las clases de .NET de objetos que el cmdlet devuelve o se pasa por la canalización.

No hay ningún límite al número de clases que se pueden agregar a la sección de salidas. Los tipos de valor devueltos de un cmdlet se incluyen en un \<returnValues: comando > nodo, donde cada clase que se incluyen en un \<returnValue: comando > elemento.

Si un cmdlet no genera ningún resultado, use esta sección para indicar que no hay ninguna salida. Por ejemplo, en lugar del nombre de clase, escribir "None" y proporcione una breve explicación. Si el cmdlet genera resultados condicionalmente, utilice este nodo para explicar las condiciones y describir el resultado condicional.

El esquema incluye dos \<maml:description > elementos de cada \<returnValue: comando > elemento. Sin embargo, el `Get-Help` cmdlet muestra solo el contenido de la \<returnValue: comando > /\<maml:description > elemento.

A partir de Windows PowerShell 3.0, el `Get-Help` cmdlet muestra el contenido de la \<maml: URI > elemento. Este elemento le permite dirigir a los usuarios a temas que describen la clase. NET.

El siguiente XML muestra el \<maml:returnValues > nodo.

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

El siguiente XML muestra un ejemplo del uso de la \<maml:returnValues > nodo en un tipo de salida de un documento.

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



