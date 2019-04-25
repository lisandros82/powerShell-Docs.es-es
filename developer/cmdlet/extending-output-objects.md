---
title: Extender los objetos de salida | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068171"
---
# <a name="extending-output-objects"></a>Extensión de los objetos de salida

Puede extender los objetos de .NET Framework que se devuelven mediante los cmdlets, funciones y scripts mediante el uso de archivos de tipos (. ps1xml). Archivos de tipos son archivos basados en XML que le permiten agregar propiedades y métodos a los objetos existentes. Por ejemplo, Windows PowerShell proporciona el archivo Types.ps1xml, que agrega elementos a varios objetos de .NET Framework existentes. El archivo Types.ps1xml se encuentra en el directorio de instalación de Windows PowerShell (`$pshome`). Puede crear su propio archivo de tipos para ampliar aún más los objetos o para ampliar otros objetos. Al extender un objeto mediante el uso de un archivo de tipos, cualquier instancia del objeto se extiende con los nuevos elementos.

## <a name="extending-the-systemarray-object"></a>Extender el objeto System.Array

El ejemplo siguiente muestra cómo Windows PowerShell amplía la [System.Array](/dotnet/api/System.Array) objeto en el archivo Types.ps1xml. De forma predeterminada, [System.Array](/dotnet/api/System.Array) objetos tienen un `Length` propiedad que muestra el número de objetos de la matriz. Sin embargo, dado que el nombre "longitud de" describir claramente la propiedad, Windows PowerShell agrega la `Count` propiedad de alias, que muestra el mismo valor que el `Length` propiedad. El código XML siguiente agrega el `Count` propiedad a la [System.Array](/dotnet/api/System.Array) tipo.

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

Para ver esta nueva propiedad de alias, use un [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) comando en cualquier matriz, como se muestra en el ejemplo siguiente.

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
Puede usar el `Count` propiedad o el `Length` propiedad para determinar cuántos objetos se encuentran en una matriz. Por ejemplo:

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

Para crear un archivo de tipos personalizados, comience por copiar un archivo de tipos existente. El nuevo archivo puede tener cualquier nombre, pero debe tener una extensión de nombre de archivo. ps1xml. Cuando copie el archivo, puede colocar el nuevo archivo en cualquier directorio accesible a Windows PowerShell, pero resulta útil colocar los archivos en el directorio de instalación de Windows PowerShell (`$pshome`) o en un subdirectorio del directorio de instalación.

Para agregar sus propios tipos extendidos en el archivo, agregue un elemento de tipos para cada objeto que se va a extender. Los temas siguientes proporcionan ejemplos.

- Para obtener más información acerca de cómo agregar propiedades y los conjuntos de propiedades, vea [propiedades extendidas](./extending-properties-for-objects.md)

- Para obtener más información acerca de cómo agregar métodos, consulte [métodos extendidos](./defining-default-methods-for-objects.md).

- Para obtener más información acerca de cómo agregar conjuntos de miembros, vea [extendidos miembro establece](./defining-default-member-sets-for-objects.md).

Después de definir sus propios tipos extendidos, utilice uno de los siguientes métodos a disposición de los objetos extendidos:

- Para que el archivo de tipos extendidos disponibles para la sesión actual, utilice el [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet para agregar el nuevo archivo. Si desea que los tipos que tienen prioridad sobre los tipos que se definen en otros tipos de archivos (incluido el archivo Types.ps1xml), use el `PrependData` parámetro de la [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.
- Para que el archivo de tipos extendidos disponible para todas las sesiones futuras, agregue el archivo de tipos a un módulo, exportar la sesión actual o agregar el [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) comando a su perfil de Windows PowerShell.

## <a name="signing-types-files"></a>Firma de tipos de archivos

Archivos de tipos deben estar firmados digitalmente para evitar la modificación porque el código XML puede incluir los bloques de script. Para obtener más información acerca de cómo agregar firmas digitales, vea [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Véase también

[Definir las propiedades predeterminadas para los objetos](./extending-properties-for-objects.md)

[Definir métodos predeterminados para los objetos](./defining-default-methods-for-objects.md)

[Definir conjuntos de miembros de forma predeterminada para los objetos](./defining-default-member-sets-for-objects.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
