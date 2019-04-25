---
title: Archivo CAB de ayudar a los tipos de archivo permitidos en un actualizable | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082454"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Tipos de archivo permitidos en un archivo CAB de Ayuda actualizable

En este tema se enumeran y describen los requisitos de contenido para archivos CAB de ayuda actualizable.

## <a name="updatable-help-cab-file-requirements"></a>Requisitos del archivo CAB de ayuda actualizable

Contenido del archivo CAB sin comprimir se limita a 1 GB de forma predeterminada. Para omitir este límite, los usuarios tienen que usar el **Force** parámetro de la [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.

Para garantizar la seguridad de los archivos de ayuda que se descargan de Internet, un archivo .cab de ayuda actualizable puede incluir solo los tipos de archivo que se enumeran a continuación. El [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet valida todos los archivos con los esquemas del tema de ayuda. Si el `Update-Help` cmdlet encuentra un archivo que no es válido o no es un tipo permitido, no se instala el archivo no válido y se detiene la instalación de archivos desde el archivo CAB en el equipo del usuario.

- Temas de Ayuda basados en XML para los cmdlets.

- Temas de Ayuda basados en XML de scripts y funciones.

- Temas de Ayuda basados en XML para los proveedores de Windows PowerShell.

- Basado en texto temas de ayuda, como temas de ayuda.

El [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comprueba el contenido del archivo CAB Cuando desempaquete el archivo CAB. Si `Update-Help` busca los tipos de archivo no compatible en un archivo .cab de ayuda actualizable, se genera un error de terminación y detiene la operación. No instala los archivos de Ayuda desde el archivo CAB, incluso los tipos de archivo compatibles.