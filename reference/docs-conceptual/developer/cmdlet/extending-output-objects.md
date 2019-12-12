---
title: Extender objetos de salida | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369724"
---
# <a name="extending-output-objects"></a>Extensión de los objetos de salida

Puede extender el .NET Framework objetos que devuelven los cmdlets, las funciones y los scripts mediante el uso de archivos de tipos (. ps1xml). Los archivos de tipos son archivos basados en XML que permiten agregar propiedades y métodos a los objetos existentes. Por ejemplo, Windows PowerShell proporciona el archivo Types. ps1xml, que agrega elementos a varios objetos .NET Framework existentes. El archivo Types. ps1xml se encuentra en el directorio de instalación de Windows PowerShell (`$pshome`). Puede crear su propio archivo de tipos para ampliar aún más los objetos o para extender otros objetos. Al extender un objeto mediante el uso de un archivo de tipos, cualquier instancia del objeto se extiende con los nuevos elementos.

## <a name="extending-the-systemarray-object"></a>Extender el objeto System. Array

En el ejemplo siguiente se muestra cómo Windows PowerShell extiende el objeto [System. Array](/dotnet/api/System.Array) en el archivo Types. ps1xml. De forma predeterminada, los objetos [System. Array](/dotnet/api/System.Array) tienen una propiedad `Length` que muestra el número de objetos de la matriz. Sin embargo, dado que el nombre "length" no describe claramente la propiedad, Windows PowerShell agrega la propiedad alias `Count`, que muestra el mismo valor que la propiedad `Length`. El siguiente XML agrega la propiedad `Count` al tipo [System. Array](/dotnet/api/System.Array) .

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

Para ver esta nueva propiedad de alias, utilice un comando [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) en cualquier matriz, como se muestra en el ejemplo siguiente.

```powershell
Get-Member -InputObject (1,2,3,4)
```

El comando devuelve los resultados siguientes.
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
Puede usar la propiedad `Count` o la propiedad `Length` para determinar el número de objetos que hay en una matriz. Por ejemplo:

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a>Archivos de tipos personalizados

Para crear un archivo de tipos personalizado, empiece por copiar un archivo de tipos existente. El nuevo archivo puede tener cualquier nombre, pero debe tener una extensión de nombre de archivo. ps1xml. Al copiar el archivo, puede colocar el nuevo archivo en cualquier directorio que sea accesible para Windows PowerShell, pero resulta útil colocar los archivos en el directorio de instalación de Windows PowerShell (`$pshome`) o en un subdirectorio del directorio de instalación.

Para agregar sus propios tipos extendidos al archivo, agregue un elemento Types para cada objeto que desee extender. En los temas siguientes se proporcionan ejemplos.

- Para obtener más información sobre cómo agregar propiedades y conjuntos de propiedades, consulte [propiedades extendidas](./extending-properties-for-objects.md)

- Para obtener más información sobre cómo agregar métodos, vea [métodos extendidos](./defining-default-methods-for-objects.md).

- Para obtener más información sobre cómo agregar conjuntos de miembros, vea [conjuntos de miembros extendidos](./defining-default-member-sets-for-objects.md).

Después de definir sus propios tipos extendidos, utilice uno de los métodos siguientes para que los objetos extendidos estén disponibles:

- Para que el archivo de tipos extendidos esté disponible en la sesión actual, use el cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) para agregar el nuevo archivo. Si desea que los tipos tengan prioridad sobre los tipos que se definen en otros archivos de tipos (incluido el archivo Types. ps1xml), use el parámetro `PrependData` del cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .
- Para que el archivo de tipos extendidos esté disponible para todas las sesiones futuras, agregue el archivo de tipos a un módulo, exporte la sesión actual o agregue el comando [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) a su perfil de Windows PowerShell.

## <a name="signing-types-files"></a>Archivos de tipos de firma

Los archivos de tipos deben firmarse digitalmente para evitar alteraciones, ya que el código XML puede incluir bloques de scripts. Para obtener más información sobre cómo agregar firmas digitales, vea [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Véase también

[Definir propiedades predeterminadas para objetos](./extending-properties-for-objects.md)

[Definir métodos predeterminados para objetos](./defining-default-methods-for-objects.md)

[Definir conjuntos de miembros predeterminados para objetos](./defining-default-member-sets-for-objects.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
