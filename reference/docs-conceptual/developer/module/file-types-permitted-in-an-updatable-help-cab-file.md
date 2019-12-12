---
title: Tipos de archivo permitidos en un archivo CAB de ayuda actualizable | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367264"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Tipos de archivo permitidos en un archivo CAB de Ayuda actualizable

En este tema se enumeran y describen los requisitos de contenido para los archivos. CAB de ayuda actualizable.

## <a name="updatable-help-cab-file-requirements"></a>Requisitos del archivo. CAB de ayuda actualizable

El contenido del archivo. CAB sin comprimir está limitado a 1 GB de forma predeterminada. Para omitir este límite, los usuarios tienen que usar el parámetro **Force** de los cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

Para garantizar la seguridad de los archivos de ayuda que se descargan de Internet, un archivo CAB de ayuda actualizable solo puede incluir los tipos de archivo que se enumeran a continuación. El cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) valida todos los archivos con respecto a los esquemas del tema de ayuda. Si el cmdlet de `Update-Help` encuentra un archivo que no es válido o no es un tipo permitido, no instala el archivo no válido y deja de instalar archivos desde el archivo. CAB en el equipo del usuario.

- Temas de ayuda basados en XML para cmdlets de.

- Temas de ayuda basados en XML para scripts y funciones.

- Temas de ayuda basados en XML para los proveedores de Windows PowerShell.

- Temas de ayuda basados en texto, como acerca de los temas.

[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comprueba el contenido del archivo. cab al desempaquetarlo. Si `Update-Help` encuentra tipos de archivo no compatibles en un archivo CAB de ayuda actualizable, genera un error de terminación y detiene la operación. No instala los archivos de ayuda del archivo. CAB, ni los de los tipos de archivos compatibles.