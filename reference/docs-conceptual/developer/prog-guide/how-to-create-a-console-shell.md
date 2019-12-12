---
title: Cómo crear un shell de consola | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360274"
---
# <a name="how-to-create-a-console-shell"></a>Cómo crear un shell de la consola

Windows PowerShell proporciona una herramienta de creación de Shell, también denominada "make-kit", que se usa para crear un shell de consola que no es extensible. Los shells creados con esta nueva herramienta no se pueden ampliar más adelante a través de un complemento de Windows PowerShell.

## <a name="syntax"></a>Sintaxis

Esta es la sintaxis que se usa para ejecutar make-Shell desde un archivo make.

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

Esta es una breve descripción de los parámetros de make-Shell.

> [!CAUTION]
> Make-Shell no admite rutas de acceso UNC a ensamblados.

|Parámetro|Descripción|
|---------------|-----------------|
|-out n. exe|Necesario. Nombre del shell que se va a producir. La ruta de acceso se especifica como parte de este parámetro.<br /><br /> Make-Shell anexará ". exe" a este valor si no se especifica. **PRECAUCIÓN:**  No cree un archivo de salida con el mismo nombre que el archivo. dll al que se hace referencia. Si lo intenta, la herramienta make-Shell crea un archivo. CS con el mismo nombre, lo que sobrescribirá el archivo. CS que contiene el código fuente del cmdlet.|
|-espacio de nombres NS|Necesario. Espacio de nombres que se va a usar para la clase derivada de [System. Management. Automation. namespaces. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) que genera y compila el make-kit.|
|-lib libdirectory1 [, libdirectory2,..]|Los directorios en los que se buscan ensamblados .NET, incluidos los ensamblados de Windows PowerShell, los ensamblados especificados por el parámetro `reference`, los ensamblados a los que hace referencia indirectamente otro ensamblado y los ensamblados de sistema .NET.|
|-Reference CA1. dll [, Ca2. dll,...]|Lista separada por comas de los ensamblados que se van a incluir en el shell. Estos ensamblados incluyen todos los ensamblados de cmdlets y proveedores, así como los ensamblados de recursos que deben cargarse. Si no se especifica este parámetro, se genera un shell que contiene solo los cmdlets y proveedores principales proporcionados por Windows PowerShell.<br /><br /> Los ensamblados se pueden especificar mediante su ruta de acceso completa; de lo contrario, se buscarán usando la ruta de acceso especificada por el parámetro `lib`.|
|-formatdata FD1. Format. ps1xml [, FD2. Format. ps1xml,...]|Lista separada por comas de los datos de formato que se van a incluir en el shell. Si no se especifica este parámetro, se genera un shell que solo contiene los datos de formato proporcionados por Windows PowerShell.|
|-typedata TD1. Type. ps1xml [, TD2. Type. ps1xml,...]|Lista separada por comas de los datos de tipo que se van a incluir en el shell. Si no se especifica este parámetro, se genera un shell que solo contiene los datos de tipo proporcionados por Windows PowerShell.|
|-Source c1.cs [, c2.cs,...]|Nombre de un archivo, proporcionado por el desarrollador del shell, que contiene cualquier código fuente necesario para compilar el shell.<br /><br /> El archivo de código fuente puede contener cualquiera de los siguientes códigos fuente:<br /><br /> -La implementación de administrador de autorización que invalida el administrador de autorización predeterminado. (También se puede proporcionar compilar en un ensamblado).<br />-Declaraciones de atributos informativos de ensamblado: como AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute y AssemblyTrademarkAttribute.|
|-authorizationmanager authorizationManagerType|El tipo que contiene la implementación del administrador de autorización. Esto puede definirse en el código fuente o compilarse en un ensamblado (especificado por el parámetro `reference`). Si no se especifica este parámetro, se utiliza el administrador de seguridad predeterminado. El valor debe ser el nombre de tipo completo, incluidos los espacios de nombres.|
|-win32icon i. ico|Icono del archivo. exe del shell. Si no se especifica, el shell tendrá el icono que incluye el compilador de c# (si existe).|
|-initscript p. ps1|Perfil de inicio del shell. El archivo se incluye "tal cual"; Make-Shell no realiza ninguna comprobación de la validez.|
|-builtinscript S1. PS1 [, S2. ps1,...]|Una lista de scripts integrados para el shell. Estos scripts se detectan antes que los scripts de la ruta de acceso y su contenido no se puede cambiar una vez compilado el shell.<br /><br /> Los archivos se incluyen "tal cual"; Make-Shell no realiza ninguna comprobación de la validez.|
|-Resource resourcefile. txt|El archivo. txt que contiene los recursos de ayuda y banner del shell. El primer recurso se denomina ShellHelp y contiene el texto que se muestra si el Shell se invoca con el parámetro `help`. El segundo recurso se denomina ShellBanner y contiene el texto y la información de copyright que se muestra cuando el Shell se inicia en modo interactivo.<br /><br /> Si no se proporciona este parámetro, o si estos recursos no están presentes, se usa una ayuda y un banner genéricos.|
|-cscflags cscFlags|Marcas que se deben pasar al C# compilador (CSC. exe). Se pasan sin modificar. Si este parámetro incluye espacios, debe ir entre comillas dobles.|
|-?<br /><br /> -help|Muestra el mensaje de copyright y las opciones de línea de comandos de make-Shell.|
|-verbose|Muestra información detallada mientras se crea el shell.|

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)