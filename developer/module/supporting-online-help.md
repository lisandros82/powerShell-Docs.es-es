---
title: Compatibilidad con la ayuda en línea | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848081"
---
# <a name="supporting-online-help"></a>Compatibilidad con la ayuda en línea

A partir de Windows PowerShell 3,0, hay dos maneras de admitir la `Get-Help` característica en línea para los comandos de Windows PowerShell. En este tema se explica cómo implementar esta característica para distintos tipos de comandos.

## <a name="about-online-help"></a>Acerca de la ayuda en línea

La ayuda en línea siempre ha sido una parte fundamental de Windows PowerShell. Aunque el `Get-Help` cmdlet muestra temas de ayuda en el símbolo del sistema, muchos usuarios prefieren la experiencia de lectura en línea, como la codificación de colores, los hipervínculos y el uso compartido de ideas en el contenido de la comunidad y en los documentos basados en wiki. Lo más importante, antes de la llegada de la ayuda actualizable, la ayuda en línea proporcionó la versión más actualizada de los archivos de ayuda.

Con la llegada de la ayuda actualizable en Windows PowerShell 3,0, la ayuda en línea sigue desempeñando un papel fundamental. Además de la experiencia de usuario flexible, la ayuda en línea proporciona ayuda a los usuarios que no pueden usar la ayuda actualizable para descargar temas de ayuda.

## <a name="how-get-help--online-works"></a>Funcionamiento de Get-Help-online

Para ayudar a los usuarios a encontrar los temas de ayuda en `Get-Help` línea para los comandos, el comando tiene un parámetro en línea que abre la versión en línea del tema de ayuda para un comando en el explorador de Internet predeterminado del usuario.

Por ejemplo, el siguiente comando abre el tema de ayuda en pantalla `Invoke-Command` para el cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Para implementar `Get-Help` -online, el `Get-Help` cmdlet busca un identificador uniforme de recursos (URI) para el tema de ayuda de la versión en línea en las siguientes ubicaciones.

- El primer vínculo de la sección vínculos relacionados del tema de ayuda para el comando. El tema de ayuda debe instalarse en el equipo del usuario. Esta característica se presentó en Windows PowerShell 2,0.

- La propiedad HelpUri de cualquier comando. La propiedad HelpUri es accesible incluso cuando el tema de ayuda para el comando no está instalado en el equipo del usuario. Esta característica se presentó en Windows PowerShell 3,0.

  `Get-Help`busca un URI en la primera entrada de la sección links relacionado antes de obtener el valor de la propiedad HelpUri. Si el valor de la propiedad es incorrecto o ha cambiado, puede invalidarlo escribiendo un valor diferente en el primer vínculo relacionado. Sin embargo, el primer vínculo relacionado solo funciona cuando los temas de ayuda se instalan en el equipo del usuario.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Agregar un URI al primer vínculo relacionado de un tema de ayuda de comando

Puede admitir `Get-Help` -online para cualquier comando agregando un URI válido a la primera entrada de la sección vínculos relacionados del tema de ayuda basado en XML para el comando. Esta opción solo es válida en los temas de ayuda basados en XML y solo funciona cuando el tema de ayuda está instalado en el equipo del usuario. Cuando se instala el tema de ayuda y se rellena el URI, este valor tiene prioridad sobre la propiedad **HelpUri** del comando.

Para admitir esta característica, el URI debe aparecer en el `maml:uri` elemento bajo el primer `maml:relatedLinks/maml:navigationLink` elemento `maml:relatedLinks` del elemento.

El siguiente XML muestra la ubicación correcta del URI. El texto `maml:linkText` "versión en línea:" del elemento es un procedimiento recomendado, pero no es necesario.

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

## <a name="adding-the-helpuri-property-to-a-command"></a>Agregar la propiedad HelpUri a un comando

En esta sección se muestra cómo agregar la propiedad HelpUri a los comandos de tipos diferentes.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Agregar una propiedad HelpUri a un cmdlet

En el caso de los C#cmdlets escritos en, agregue un atributo **HelpUri** a la clase de cmdlet. El valor del atributo debe ser un URI que comience por "http" o "https".

En el código siguiente se muestra el atributo HelpUri `Get-History` de la clase cmdlet.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Agregar una propiedad HelpUri a una función avanzada

En el caso de las funciones avanzadas, agregue una propiedad **HelpUri** al atributo **CmdletBinding** . El valor de la propiedad debe ser un URI que comience por "http" o "https".

En el código siguiente se muestra el atributo HelpUri de la función New-Calendar.

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Agregar un atributo HelpUri a un comando CIM

En el caso de los comandos CIM, agregue un atributo **HelpUri** al elemento **CmdletMetadata** en el archivo CDXML. El valor del atributo debe ser un URI que comience por "http" o "https".

En el código siguiente se muestra el atributo HelpUri del comando CIM Start-Debug

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Agregar un atributo HelpUri a un flujo de trabajo

En el caso de los flujos de trabajo que se escriben en el lenguaje de Windows PowerShell, agregue un **. ExternalHelp** : Directiva de comentario al código del flujo de trabajo. El valor de la Directiva debe ser un URI que comience por "http" o "https".

> [!NOTE]
> La propiedad HelpUri no es compatible con los flujos de trabajo basados en XAML en Windows PowerShell.

En el código siguiente se muestra el. Directiva ExternalHelp en un archivo de flujo de trabajo.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```