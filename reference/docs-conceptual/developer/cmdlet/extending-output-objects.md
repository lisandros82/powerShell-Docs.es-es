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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369724"
---
# <a name="extending-output-objects"></a><span data-ttu-id="54bd0-102">Extensión de los objetos de salida</span><span class="sxs-lookup"><span data-stu-id="54bd0-102">Extending Output Objects</span></span>

<span data-ttu-id="54bd0-103">Puede extender el .NET Framework objetos que devuelven los cmdlets, las funciones y los scripts mediante el uso de archivos de tipos (. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="54bd0-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="54bd0-104">Los archivos de tipos son archivos basados en XML que permiten agregar propiedades y métodos a los objetos existentes.</span><span class="sxs-lookup"><span data-stu-id="54bd0-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="54bd0-105">Por ejemplo, Windows PowerShell proporciona el archivo Types. ps1xml, que agrega elementos a varios objetos .NET Framework existentes.</span><span class="sxs-lookup"><span data-stu-id="54bd0-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="54bd0-106">El archivo Types. ps1xml se encuentra en el directorio de instalación de Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="54bd0-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="54bd0-107">Puede crear su propio archivo de tipos para ampliar aún más los objetos o para extender otros objetos.</span><span class="sxs-lookup"><span data-stu-id="54bd0-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="54bd0-108">Al extender un objeto mediante el uso de un archivo de tipos, cualquier instancia del objeto se extiende con los nuevos elementos.</span><span class="sxs-lookup"><span data-stu-id="54bd0-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="54bd0-109">Extender el objeto System. Array</span><span class="sxs-lookup"><span data-stu-id="54bd0-109">Extending the System.Array Object</span></span>

<span data-ttu-id="54bd0-110">En el ejemplo siguiente se muestra cómo Windows PowerShell extiende el objeto [System. Array](/dotnet/api/System.Array) en el archivo Types. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="54bd0-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="54bd0-111">De forma predeterminada, los objetos [System. Array](/dotnet/api/System.Array) tienen una propiedad `Length` que muestra el número de objetos de la matriz.</span><span class="sxs-lookup"><span data-stu-id="54bd0-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="54bd0-112">Sin embargo, dado que el nombre "length" no describe claramente la propiedad, Windows PowerShell agrega la propiedad de alias `Count`, que muestra el mismo valor que la propiedad `Length`.</span><span class="sxs-lookup"><span data-stu-id="54bd0-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="54bd0-113">El siguiente XML agrega la propiedad `Count` al tipo [System. Array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="54bd0-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="54bd0-114">Para ver esta nueva propiedad de alias, utilice un comando [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) en cualquier matriz, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="54bd0-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="54bd0-115">El comando devuelve los resultados siguientes.</span><span class="sxs-lookup"><span data-stu-id="54bd0-115">The command returns the following results.</span></span>
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
<span data-ttu-id="54bd0-116">Puede usar la propiedad `Count` o la propiedad `Length` para determinar el número de objetos que hay en una matriz.</span><span class="sxs-lookup"><span data-stu-id="54bd0-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="54bd0-117">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="54bd0-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="54bd0-118">Archivos de tipos personalizados</span><span class="sxs-lookup"><span data-stu-id="54bd0-118">Custom Types Files</span></span>

<span data-ttu-id="54bd0-119">Para crear un archivo de tipos personalizado, empiece por copiar un archivo de tipos existente.</span><span class="sxs-lookup"><span data-stu-id="54bd0-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="54bd0-120">El nuevo archivo puede tener cualquier nombre, pero debe tener una extensión de nombre de archivo. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="54bd0-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="54bd0-121">Al copiar el archivo, puede colocar el nuevo archivo en cualquier directorio que sea accesible para Windows PowerShell, pero resulta útil colocar los archivos en el directorio de instalación de Windows PowerShell (`$pshome`) o en un subdirectorio del directorio de instalación.</span><span class="sxs-lookup"><span data-stu-id="54bd0-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="54bd0-122">Para agregar sus propios tipos extendidos al archivo, agregue un elemento Types para cada objeto que desee extender.</span><span class="sxs-lookup"><span data-stu-id="54bd0-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="54bd0-123">En los temas siguientes se proporcionan ejemplos.</span><span class="sxs-lookup"><span data-stu-id="54bd0-123">The following topics provide examples.</span></span>

- <span data-ttu-id="54bd0-124">Para obtener más información sobre cómo agregar propiedades y conjuntos de propiedades, consulte [propiedades extendidas](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="54bd0-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="54bd0-125">Para obtener más información sobre cómo agregar métodos, vea [métodos extendidos](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="54bd0-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="54bd0-126">Para obtener más información sobre cómo agregar conjuntos de miembros, vea [conjuntos de miembros extendidos](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="54bd0-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="54bd0-127">Después de definir sus propios tipos extendidos, utilice uno de los métodos siguientes para que los objetos extendidos estén disponibles:</span><span class="sxs-lookup"><span data-stu-id="54bd0-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="54bd0-128">Para que el archivo de tipos extendidos esté disponible en la sesión actual, use el cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) para agregar el nuevo archivo.</span><span class="sxs-lookup"><span data-stu-id="54bd0-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="54bd0-129">Si desea que los tipos tengan prioridad sobre los tipos que se definen en otros archivos de tipos (incluido el archivo Types. ps1xml), use el parámetro `PrependData` del cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .</span><span class="sxs-lookup"><span data-stu-id="54bd0-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="54bd0-130">Para que el archivo de tipos extendidos esté disponible para todas las sesiones futuras, agregue el archivo de tipos a un módulo, exporte la sesión actual o agregue el comando [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) a su perfil de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="54bd0-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="54bd0-131">Archivos de tipos de firma</span><span class="sxs-lookup"><span data-stu-id="54bd0-131">Signing Types Files</span></span>

<span data-ttu-id="54bd0-132">Los archivos de tipos deben firmarse digitalmente para evitar alteraciones, ya que el código XML puede incluir bloques de scripts.</span><span class="sxs-lookup"><span data-stu-id="54bd0-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="54bd0-133">Para obtener más información sobre cómo agregar firmas digitales, vea [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="54bd0-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="54bd0-134">Véase también</span><span class="sxs-lookup"><span data-stu-id="54bd0-134">See Also</span></span>

[<span data-ttu-id="54bd0-135">Definir propiedades predeterminadas para objetos</span><span class="sxs-lookup"><span data-stu-id="54bd0-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="54bd0-136">Definir métodos predeterminados para objetos</span><span class="sxs-lookup"><span data-stu-id="54bd0-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="54bd0-137">Definir conjuntos de miembros predeterminados para objetos</span><span class="sxs-lookup"><span data-stu-id="54bd0-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="54bd0-138">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="54bd0-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
