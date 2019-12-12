---
title: Información general sobre la ayuda actualizable | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366964"
---
# <a name="updatable-help-overview"></a>Información general acerca de la Ayuda actualizable

En este documento se proporciona una introducción básica al diseño y el funcionamiento de la característica de ayuda actualizable de Windows PowerShell. Está diseñado para los autores de módulos y otros usuarios que proporcionan temas de ayuda de Windows PowerShell a los usuarios.

## <a name="introduction"></a>Introducción

Los temas de ayuda de Windows PowerShell son una parte integral de la experiencia con Windows PowerShell. Al igual que los módulos de Windows PowerShell, los temas de ayuda se actualizan y mejoran continuamente los autores y las contribuciones de la comunidad de usuarios de Windows PowerShell.

La característica de *ayuda actualizable* , introducida en Windows PowerShell 3,0, garantiza que los usuarios tengan las versiones más recientes de los temas de ayuda en el símbolo del sistema, incluso en el caso de los comandos integrados de Windows PowerShell, sin necesidad de descargar nuevos módulos ni de ejecutar Windows Update. La ayuda actualizable facilita la actualización al proporcionar cmdlets que descargan las versiones más recientes de los temas de ayuda de Internet e instalarlas en los subdirectorios correctos del equipo local del usuario. Incluso los usuarios que están detrás de firewalls pueden usar los nuevos cmdlets para obtener ayuda actualizada desde un recurso compartido de archivos interno.

La ayuda actualizable es totalmente compatible con todos los módulos de Windows PowerShell en Windows® 8 y Windows Server® 2012, y sus características están disponibles para todos los autores del módulo de Windows PowerShell. La ayuda actualizable solo admite archivos de ayuda basados en XML. No admite la ayuda basada en Comentarios.

La ayuda actualizable incluye las siguientes características.

- El cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) , que determina si los usuarios tienen los archivos de ayuda más recientes para un módulo y, si no es así, descarga los archivos de ayuda más recientes de Internet, los desempaqueta y los instala en los subdirectorios de módulo correctos en el equipo del usuario.
  Los usuarios pueden usar el cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) para ver los temas de ayuda recién instalados inmediatamente.
  No es necesario reiniciar PowerShell.

- El cmdlet [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) , que descarga los archivos de ayuda más recientes desde Internet y los guarda en un directorio del sistema de archivos. Los usuarios pueden usar el cmdlet `Update-Help` para obtener archivos de ayuda del directorio del sistema de archivos y desempaquetarlos e instalarlos en los subdirectorios del módulo en el equipo del usuario. El cmdlet `Save-Help` está diseñado para usuarios que tienen acceso a Internet limitado o no, y para empresas que prefieren limitar el acceso a Internet.

- **Ayuda para un módulo**. Los archivos de ayuda de un módulo se administran y se entregan como una unidad, por lo que los usuarios pueden obtener todos los archivos de ayuda de los módulos que usan. La ayuda actualizable solo se admite en los módulos, no en los complementos de Windows PowerShell.

- **Compatibilidad de versiones**. La ayuda actualizable utiliza la cuarta posición estándar (N1. N2. N3. N4) números de versión. La ayuda actualizable descarga los archivos de ayuda cuando el número de versión de los archivos de ayuda en el equipo del usuario (o en el directorio `Save-Help`) es inferior al número de versión de los archivos de ayuda en la ubicación de Internet.

- **Compatibilidad con varios idiomas**. La ayuda actualizable admite archivos de ayuda de módulo en varias referencias culturales de la interfaz de usuario. Los nombres de archivo de ayuda actualizables incluyen códigos de idioma estándar, como "en-US" y "ja-JP", y los cmdlets `Update-Help` y `Save-Help` colocan los archivos de ayuda en subdirectorios específicos del lenguaje del directorio de módulo.

- **Ayuda generada automáticamente**. El cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) muestra ayuda básica para los comandos que no tienen archivos de ayuda. La ayuda generada automáticamente incluye la sintaxis de comandos y los alias, así como instrucciones para usar la ayuda en línea y la ayuda actualizable.

- **Ayuda en pantalla mejorada**. El acceso sencillo a la ayuda en línea ya no requiere archivos de ayuda. El parámetro **online** del cmdlet `Get-Help` ahora obtiene la dirección URL de un tema de ayuda en línea del valor de la propiedad **HelpUri** de cualquier comando, si no puede encontrar la dirección URL de la ayuda en línea en un archivo de ayuda. Puede rellenar la propiedad **HelpUri** agregando un atributo **HelpUri** al código de cmdlets, funciones y comandos CIM, o mediante **.** Directiva de ayuda basada en comentarios de vínculos en flujos de trabajo y scripts.

  Para que los archivos de ayuda sean actualizables, los módulos de Windows PowerShell en Windows 8 y Windows Server vNext no se adquieren con archivos de ayuda. Los usuarios pueden usar la ayuda actualizable para instalar archivos de ayuda y actualizarlos. Los autores de otros módulos pueden incluir archivos de ayuda en módulos u omitirlos. La compatibilidad con la ayuda actualizable es opcional, pero se recomienda.
