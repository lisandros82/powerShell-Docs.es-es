---
title: Compatibilidad con la Ayuda en línea | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857921"
---
# <a name="supporting-online-help"></a>Compatibilidad con la ayuda en línea

A partir de Windows PowerShell 3.0, hay dos maneras para admitir la `Get-Help` características en línea de comandos de Windows PowerShell. Este tema explica cómo implementar esta característica para los tipos de comandos diferente.

## <a name="about-online-help"></a>Acerca de la Ayuda en línea

Ayuda en línea siempre ha sido una parte fundamental de Windows PowerShell. Aunque el `Get-Help` cmdlet muestra los temas de ayuda en el símbolo del sistema, muchos usuarios prefieren la experiencia de lectura en pantalla, como la codificación en colores, hipervínculos y para compartir ideas en el contenido de la Comunidad y documentos basados en la wiki. Lo más importante, antes de la llegada de ayuda actualizable, ayuda en línea que proporciona la versión más actualizada de los archivos de ayuda.

Con la llegada de la Ayuda actualizable en Windows PowerShell 3.0, ayuda en línea sigue desempeñando un papel fundamental. Además de la experiencia de usuario flexible, ayuda en línea proporciona ayuda a los usuarios que no lo hace o no se pueden usar la Ayuda actualizable para descargar los temas de ayuda.

## <a name="how-get-help--online-works"></a>Cómo Get-Help-Online Works

Para ayudar a los usuarios a encontrar los temas de ayuda en línea de comandos, el `Get-Help` comando tiene un parámetro en línea que se abre la versión en línea de tema de ayuda para un comando en el Explorador de Internet predeterminado del usuario.

Por ejemplo, el comando siguiente abre el tema de ayuda en línea el `Invoke-Command` cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Para implementar `Get-Help` -en línea, el `Get-Help` cmdlet busca para un identificador uniforme de recursos (URI) para el tema de Ayuda de la versión en línea en las siguientes ubicaciones.

- El primer vínculo en la sección vínculos relacionados del tema de ayuda para el comando. El tema de ayuda debe instalarse en el equipo del usuario. Esta característica se introdujo en Windows PowerShell 2.0.

- La propiedad HelpUri de los comandos. La propiedad HelpUri es accesible, incluso cuando el tema de ayuda para el comando no está instalado en el equipo del usuario. Esta característica se introdujo en Windows PowerShell 3.0.

  `Get-Help` Busca un URI en la primera entrada en la sección vínculos relacionados antes de obtener el valor de la propiedad HelpUri. Si el valor de propiedad no es correcto o ha cambiado, puede invalidarlo especificando un valor diferente en el primer vínculo relacionado. Sin embargo, el primer vínculo relacionado sólo funciona si los temas de ayuda se instalan en el equipo del usuario.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Adición de un URI para el primer vínculo relacionado de un tema de Ayuda del comando

Puede admitir `Get-Help` -Online para cualquier comando mediante la adición de un URI válido para la primera entrada en la sección vínculos relacionados del tema de ayuda basado en XML para el comando. Esta opción solo es válida en los temas de Ayuda basados en XML y solo funciona si el tema de ayuda está instalado en el equipo del usuario. Cuando se instala el tema de ayuda y el URI se rellena, este valor tiene prioridad sobre la **HelpUri** propiedad del comando. Para obtener información acerca de los temas de Ayuda basados en XML para los comandos, vea [Writing XML-Based temas de ayuda para los comandos](../help/writing-xml-based-help-topics-for-commands.md).

Para admitir esta característica, el URI debe aparecer en el `maml:uri` elemento debajo del primer `maml:relatedLinks/maml:navigationLink` elemento en el `maml:relatedLinks` elemento.

El siguiente XML muestra la posición correcta de la dirección URI. La "versión en línea:" texto en el `maml:linkText` elemento es una práctica recomendada, pero no es necesario.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Adición de la propiedad HelpUri a un comando

En esta sección se muestra cómo agregar la propiedad HelpUri a los comandos de diferentes tipos.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Agregar una propiedad HelpUri a un Cmdlet

Para los cmdlets que se escriben C#, agregue un **HelpUri** a la clase de Cmdlet. El valor del atributo debe ser un URI que empieza por "http" o "https".

El código siguiente muestra el atributo HelpUri de los `Get-History` clase del cmdlet.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Agregar una propiedad HelpUri a una función avanzada

Para las funciones avanzadas, agregue un **HelpUri** propiedad a la **CmdletBinding** atributo. El valor de la propiedad debe ser un URI que empieza por "http" o "https".

El código siguiente muestra el atributo HelpUri de la función New-calendario

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Agregar un atributo HelpUri a un comando CIM

Para los comandos CIM, agregue un **HelpUri** atributo a la **CmdletMetadata** elemento en el archivo CDXML. El valor del atributo debe ser un URI que empieza por "http" o "https".

El código siguiente muestra el atributo HelpUri del comando Start-Debug CIM

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Agregar un atributo HelpUri a un flujo de trabajo

Para los flujos de trabajo que se escriben en el lenguaje de Windows PowerShell, agregue un **. ExternalHelp** comment (directiva) en el código de flujo de trabajo. El valor de la directiva debe ser un URI que empieza por "http" o "https".

> [!NOTE]
> No se admite la propiedad HelpUri de los flujos de trabajo basados en XAML en Windows PowerShell.

El código siguiente muestra el. Directiva ExternalHelp en un archivo de flujo de trabajo.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```