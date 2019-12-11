---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Ver la estructura del objeto Get Member
ms.openlocfilehash: 80b36abd303a708195f12d96511e616178d11b5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030706"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="85fbc-103">Ver la estructura del objeto (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="85fbc-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="85fbc-104">Dado que los objetos desempeñan una función esencial en Windows PowerShell, existen varios comandos nativos diseñados para trabajar con tipos de objetos arbitrarios.</span><span class="sxs-lookup"><span data-stu-id="85fbc-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="85fbc-105">El más importante es el comando **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="85fbc-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="85fbc-106">Es la técnica más sencilla para analizar los objetos que devuelve un comando es canalizar la salida del comando al cmdlet **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="85fbc-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="85fbc-107">El cmdlet **Get-Member** muestra el nombre formal del tipo de objeto y una lista completa de sus miembros.</span><span class="sxs-lookup"><span data-stu-id="85fbc-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="85fbc-108">En ocasiones, el número de elementos devuelto puede ser excesivo.</span><span class="sxs-lookup"><span data-stu-id="85fbc-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="85fbc-109">Por ejemplo, un objeto de proceso puede tener más de 100 miembros.</span><span class="sxs-lookup"><span data-stu-id="85fbc-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="85fbc-110">Para ver a todos los miembros de un objeto de proceso y paginar la salida para verla completamente, escriba:</span><span class="sxs-lookup"><span data-stu-id="85fbc-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="85fbc-111">La salida de este comando tendrá un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="85fbc-111">The output from this command will look something like this:</span></span>

```output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

<span data-ttu-id="85fbc-112">Podemos hacer que esta larga lista de información sea más fácil de usar mediante el filtrado de los elementos que quiere ver.</span><span class="sxs-lookup"><span data-stu-id="85fbc-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="85fbc-113">El comando **Get-Member** permite mostrar solo los miembros que son propiedades.</span><span class="sxs-lookup"><span data-stu-id="85fbc-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="85fbc-114">Existen varios formatos de propiedades.</span><span class="sxs-lookup"><span data-stu-id="85fbc-114">There are several forms of properties.</span></span> <span data-ttu-id="85fbc-115">El cmdlet muestra las propiedades de cualquier tipo si se establece el parámetro **Get-MemberMemberType** en el valor **Properties**.</span><span class="sxs-lookup"><span data-stu-id="85fbc-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="85fbc-116">La lista resultante todavía es muy larga, pero un poco más fácil de administrar:</span><span class="sxs-lookup"><span data-stu-id="85fbc-116">The resulting list is still very long, but a bit more manageable:</span></span>

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> <span data-ttu-id="85fbc-117">Los valores permitidos de MemberType son AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet y All.</span><span class="sxs-lookup"><span data-stu-id="85fbc-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="85fbc-118">Existen más de 60 propiedades para un proceso.</span><span class="sxs-lookup"><span data-stu-id="85fbc-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="85fbc-119">La razón por la que Windows PowerShell suele mostrar solo un conjunto de propiedades para cualquier objeto conocido, es que en caso de mostrarlos todos se generaría una cantidad de información imposible de administrar.</span><span class="sxs-lookup"><span data-stu-id="85fbc-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="85fbc-120">Windows PowerShell determina cómo mostrar un tipo de objeto mediante la información almacenada en archivos XML cuyos nombres terminan con .format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="85fbc-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="85fbc-121">Los datos de formato de objetos de proceso, que son objetos System.Diagnostics.Process de .NET, se almacenan en DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="85fbc-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="85fbc-122">Si necesita consultar propiedades distintas de las que Windows PowerShell muestra de forma predeterminada, deberá formatear los datos de salida personalmente.</span><span class="sxs-lookup"><span data-stu-id="85fbc-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="85fbc-123">Esto se puede hacer mediante los cmdlets de formato.</span><span class="sxs-lookup"><span data-stu-id="85fbc-123">This can be done by using the format cmdlets.</span></span>
