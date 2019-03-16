---
title: Información general de la Ayuda actualizable | Microsoft Docs
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057610"
---
# <a name="updatable-help-overview"></a>Información general acerca de la Ayuda actualizable

Este documento proporciona una introducción básica al diseño y funcionamiento de la característica de ayuda actualizable de Windows PowerShell. Está diseñado para los autores de módulos y otros que entreguen los temas de Ayuda de Windows PowerShell para los usuarios.

## <a name="introduction"></a>Introducción

Temas de Ayuda de Windows PowerShell son una parte integral de la experiencia con Windows PowerShell. Similar a los módulos de Windows PowerShell, temas de ayuda se actualiza continuamente y mejorados por los autores y las contribuciones de la Comunidad de usuarios de Windows PowerShell.

El *ayuda actualizable* nueva característica de Windows PowerShell 3.0, se garantiza que los usuarios tengan las versiones más recientes de los temas de ayuda en el símbolo del sistema, incluso para los comandos de Windows PowerShell integrados, sin tener que descargar nuevos módulos o ejecute Windows Update. La Ayuda actualizable facilita la actualización simple, ya que proporciona cmdlets que descargue las versiones más recientes de los temas de Ayuda desde Internet e instalarlos en los subdirectorios correctos en el equipo del usuario local. Incluso los usuarios que están detrás de firewalls pueden usar los nuevos cmdlets para obtener ayuda actualizada de un recurso compartido de archivos interno.

La Ayuda actualizable es totalmente compatible con todos los módulos de Windows PowerShell en Windows® 8 y Windows Server® 2012 y sus características están disponibles para todos los autores del módulo de Windows PowerShell. La Ayuda actualizable admite solo los archivos de ayuda basado en XML. No se admite Ayuda basada en comentarios.

La Ayuda actualizable incluye las siguientes características.

- El [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet, que determina si los usuarios tienen la Ayuda más reciente de archivos para un módulo y, si no, descarga los archivos de ayuda más recientes desde Internet, desempaqueta y lo instala en los subdirectorios de módulo correcto en el equipo del usuario.
  Los usuarios pueden usar el [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet para ver los temas de Ayuda instalado recientemente inmediatamente.
  No es necesario reiniciar PowerShell.

- El [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet, que descarga la Ayuda más reciente de archivos desde Internet y los guarda en un directorio de sistema de archivos. Los usuarios pueden usar el `Update-Help` cmdlet para obtener los archivos de Ayuda desde el directorio de sistema de archivos y desempaquetar e instalarlos en los subdirectorios de módulo en el equipo del usuario. El `Save-Help` cmdlet está diseñado para los usuarios que tienen una limitada o sin acceso a Internet y para las empresas que prefieren limitar el acceso a Internet.

- **Ayuda para un módulo**. Se administran y se entregan como una unidad, de modo que los usuarios pueden obtener todos los archivos de ayuda para los módulos que usan archivos de Ayuda de un módulo. La Ayuda actualizable solo se admite para los módulos, no para los complementos de Windows PowerShell.

- **Compatibilidad con la versión**. La Ayuda actualizable usa estándar cuatro posiciones (N1. N2. N3. Números de versión N4). La Ayuda actualizable descarga los archivos de ayuda cuando el número de versión de la Ayuda de los archivos en el equipo del usuario (o en el `Save-Help` directory) es menor que el número de versión de los archivos de ayuda en la ubicación de Internet.

- **Compatibilidad con varios lenguaje**. La Ayuda actualizable es compatible con los archivos de Ayuda del módulo en varias referencias culturales de interfaz de usuario. La Ayuda actualizable nombres de archivo incluyen códigos de lenguaje estándar, como "en-US" y "ja-JP" y el `Update-Help` y `Save-Help` cmdlets colocar los archivos de ayuda en los subdirectorios específicos del lenguaje del directorio de módulo.

- **La Ayuda generada automáticamente**. El [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet muestra la Ayuda básica para los comandos que no tiene archivos de ayuda. La Ayuda generada automáticamente incluye la sintaxis del comando y los alias e instrucciones para usar Ayuda en línea y la Ayuda actualizable.

- **Mejorada ayuda en línea**. Fácil acceso a la Ayuda en línea ya no requiere archivos de ayuda. El **Online** parámetro de la `Get-Help` cmdlet ahora obtiene la dirección URL de un tema de ayuda en línea desde el valor de la **HelpUri** propiedad de cualquier comando, si no encuentra la dirección URL de ayuda en línea en un archivo de ayuda. Puede rellenar el **HelpUri** propiedad agregando un **HelpUri** atributo en el código de los cmdlets, funciones y comandos CIM, o mediante el **. Vínculo** directiva ayuda basada en comentarios en los flujos de trabajo y scripts.

  Para hacer nuestros archivos de ayuda actualizable, los módulos de Windows PowerShell en Windows 8 y Windows Server vNext no se suministran con archivos de ayuda. Los usuarios pueden usar la Ayuda actualizable para instalar los archivos de ayuda y actualizarlos. Los autores de otros módulos pueden incluir los archivos de ayuda en los módulos u omitirlos. Compatibilidad con ayuda actualizable es opcional pero recomendado.
