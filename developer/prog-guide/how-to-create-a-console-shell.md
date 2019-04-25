---
title: Cómo crear un Shell de la consola | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081601"
---
# <a name="how-to-create-a-console-shell"></a>Cómo crear un shell de la consola

Windows PowerShell proporciona una herramienta de creación Shell, que también se denomina el "make-kit", que se usa para crear un shell de consola que no es extensible. Shells creados con esta nueva herramienta no pueden ampliarse más adelante a través de un complemento de Windows PowerShell.

## <a name="syntax"></a>Sintaxis

Esta es la sintaxis utilizada para ejecutar el Shell de Make desde dentro de un archivo make.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parámetros

Aquí es una breve descripción de los parámetros de Make-Shell.

> [!CAUTION]
> Asegúrese de Shell no admiten las rutas de acceso UNC a los ensamblados.

|Parámetro|Descripción|
|---------------|-----------------|
|-out n.exe|Obligatorio. El nombre del shell para generar. La ruta de acceso se especifica como parte de este parámetro.<br /><br /> Asegúrese de shell anexará ".exe" a este valor si no se especifica. **Precaución:**  No cree un archivo de salida con el mismo nombre que el archivo .dll que se hace referencia. Si intenta hacer esto, la herramienta de creación Shell crea un archivo .cs con el mismo nombre, lo que sobrescribirá el archivo .cs que tiene el código fuente de cmdlet.|
|el espacio de nombres - ns|Obligatorio. El espacio de nombres que se usará para la clase derivada [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) clase que el kit de make genera y compila.|
|-lib libdirectory1[,libdirectory2,..]|Los directorios que se buscan los ensamblados. NET, incluidos los ensamblados de Windows PowerShell, los ensamblados especificados por el `reference` parámetro ensamblados al que hace referencia indirectamente el otro ensamblado y los ensamblados de .NET del sistema.|
|-referencia ca1.dll[,ca2.dll,...]|Una lista separada por comas de los ensamblados que se van a incluir en el shell. Estos ensamblados incluye todos los cmdlet y ensamblados de proveedor, así como los ensamblados de recursos que se deben cargar. Si no se especifica este parámetro, se genera un shell que contiene solo los proveedores de Windows PowerShell y cmdlets principales.<br /><br /> Se pueden especificar los ensamblados mediante su ruta de acceso completa, en caso contrario, se buscarán para el uso de la ruta de acceso especificada por el `lib` parámetro.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|Una lista separada por comas de los datos de formato debe incluir en el shell. Si no se especifica este parámetro, se genera un shell que contiene solo los datos de formato proporcionados por Windows PowerShell.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|Una lista separada por comas de los datos de tipo para incluir en el shell. Si no se especifica este parámetro, se genera un shell que contiene solo los datos de tipo proporcionados por Windows PowerShell.|
|-origen c1.cs [, c2.cs,...]|El nombre de un archivo, proporcionado por el desarrollador de shell, que contiene cualquier código fuente necesario para compilar el shell.<br /><br /> El archivo de código fuente puede contener cualquiera del código fuente siguientes:<br /><br /> -La implementación del Administrador de autorización que reemplaza el Administrador de autorización de forma predeterminada. (Esto podría también ser suministrado compila en un ensamblado.)<br />: Las declaraciones de atributos informativos de ensamblado: como el AssemblyCompanyAttribute AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, y AssemblyTrademarkAttribute.|
|-dicho administrador authorizationManagerType|El tipo que contiene la implementación del Administrador de autorización. Esto se puede definir en el código fuente, o compila en un ensamblado (especificado por el `reference` parámetro). Si no se especifica este parámetro, se utiliza el Administrador de seguridad predeterminado. El valor debe ser el nombre de tipo completo, incluidos los espacios de nombres.|
|-win32icon i.ico|El icono para el archivo .exe para el shell. Si no se especifica, el shell tendrá el icono que el compilador de c# incluye (si existe).|
|-initscript p.ps1|El perfil de inicio para el shell. Se incluye el archivo "como-es"; Asegúrese de shell, se realiza ninguna comprobación de validez.|
|-s1.ps1[,s2.ps1 builtinscript,...]|Una lista de secuencias de comandos integrados para el shell. Estos scripts se detectan antes de secuencias de comandos en la ruta de acceso y su contenido no se puede cambiar una vez que el shell se ha creado.<br /><br /> Los archivos se incluyen "como-es"; Asegúrese de shell, se realiza ninguna comprobación de validez.|
|-recursos resourcefile.txt|El archivo .txt que contiene los recursos de ayuda y de banner para el shell. El primer recurso denominado ShellHelp y contiene el texto que aparece si se invoca el comando de shell con el `help` parámetro. El segundo recurso se denomina ShellBanner y contiene el texto y la información de copyright muestra cuando el shell se inicia en modo interactivo.<br /><br /> Si no se proporciona este parámetro, o estos recursos no están presentes, se utilizan un ayuda genérico y banner.|
|-cscflags cscFlags|Marcas que se deben pasar a la C# compilador (csc.exe). Estos se pasan a través sin cambios. Si este parámetro incluye espacios, debe ser entre comillas dobles.|
|-?<br /><br /> -Ayuda|Muestra el mensaje de copyright y opciones de línea de comandos de Shell de la marca.|
|-verbose|Muestra información detallada mientras se crea el shell.|

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)