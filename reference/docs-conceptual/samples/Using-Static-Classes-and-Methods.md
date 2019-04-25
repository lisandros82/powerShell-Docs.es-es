---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Usar métodos y clases estáticas
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: e4caff63a1ec7295b6fe450c2915baf0cc7e31af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086024"
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="d3a24-103">Usar métodos y clases estáticas</span><span class="sxs-lookup"><span data-stu-id="d3a24-103">Using Static Classes and Methods</span></span>

<span data-ttu-id="d3a24-104">No todas las clases de .NET Framework se pueden crear mediante **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="d3a24-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="d3a24-105">Por ejemplo, si intenta crear un objeto **System.Environment** o **System.Math** con **New-Object**, obtendrá los siguientes mensajes de error:</span><span class="sxs-lookup"><span data-stu-id="d3a24-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="d3a24-106">Estos errores se producen porque no hay ninguna manera de crear un nuevo objeto desde estas clases.</span><span class="sxs-lookup"><span data-stu-id="d3a24-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="d3a24-107">Estas clases son bibliotecas de métodos y propiedades de referencia que no cambian el estado.</span><span class="sxs-lookup"><span data-stu-id="d3a24-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="d3a24-108">No es necesario crearlas, simplemente úselas.</span><span class="sxs-lookup"><span data-stu-id="d3a24-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="d3a24-109">Las clases y métodos de este tipo se denominan *clases estáticas* porque no se crean, destruyen ni modifican.</span><span class="sxs-lookup"><span data-stu-id="d3a24-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="d3a24-110">Para aclarar esto, proporcionaremos algunos ejemplos que usan clases estáticas.</span><span class="sxs-lookup"><span data-stu-id="d3a24-110">To make this clear we will provide examples that use static classes.</span></span>

## <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="d3a24-111">Obtener datos del entorno con System.Environment</span><span class="sxs-lookup"><span data-stu-id="d3a24-111">Getting Environment Data with System.Environment</span></span>

<span data-ttu-id="d3a24-112">Normalmente, el primer paso para trabajar con un objeto en Windows PowerShell es usar Get-Member para averiguar qué miembros contiene.</span><span class="sxs-lookup"><span data-stu-id="d3a24-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="d3a24-113">Con las clases estáticas, el proceso es un poco diferente, porque la clase real no es un objeto.</span><span class="sxs-lookup"><span data-stu-id="d3a24-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="d3a24-114">Hacer referencia a la clase System.Environment estática</span><span class="sxs-lookup"><span data-stu-id="d3a24-114">Referring to the Static System.Environment Class</span></span>

<span data-ttu-id="d3a24-115">Para hacer referencia a una clase estática incluya el nombre de la clase entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="d3a24-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="d3a24-116">Por ejemplo, para hacer referencia a **System.Environment** escriba el nombre entre corchetes.</span><span class="sxs-lookup"><span data-stu-id="d3a24-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="d3a24-117">Al hacerlo, se mostrará alguna información de tipo genérico:</span><span class="sxs-lookup"><span data-stu-id="d3a24-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="d3a24-118">Como mencionamos anteriormente, Windows PowerShell antepone '**System.**' automáticamente</span><span class="sxs-lookup"><span data-stu-id="d3a24-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="d3a24-119">a los nombres de tipos cuando usa **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="d3a24-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="d3a24-120">Lo mismo ocurre cuando se usa un nombre de tipo entre corchetes, por lo que **\[System.Environment] se puede especificar como** **\[Environment]**.</span><span class="sxs-lookup"><span data-stu-id="d3a24-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="d3a24-121">La clase **System.Environment** contiene información general sobre el entorno de trabajo para el proceso actual, que es powershell.exe al trabajar en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3a24-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="d3a24-122">Si intenta ver los detalles de esta clase escribiendo **\[System.Environment] | Get-Member**, el tipo de objeto se indica como **System.RuntimeType**, no como **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="d3a24-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="d3a24-123">Para ver los miembros estáticos con Get-Member, especifique el parámetro **Static**:</span><span class="sxs-lookup"><span data-stu-id="d3a24-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="d3a24-124">Ahora podemos seleccionar las propiedades que queremos ver desde System.Environment.</span><span class="sxs-lookup"><span data-stu-id="d3a24-124">We can now select properties to view from System.Environment.</span></span>

### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="d3a24-125">Visualizar propiedades estáticas de System.Environment</span><span class="sxs-lookup"><span data-stu-id="d3a24-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="d3a24-126">Las propiedades de System.Environment también son estáticas y deben especificarse de manera diferente que las propiedades normales.</span><span class="sxs-lookup"><span data-stu-id="d3a24-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="d3a24-127">Usamos **::** para indicar a Windows PowerShell que queremos trabajar con una propiedad o un método estático.</span><span class="sxs-lookup"><span data-stu-id="d3a24-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="d3a24-128">Para ver el comando que se usó para iniciar Windows PowerShell, comprobamos la propiedad **CommandLine**, para lo cual escribimos:</span><span class="sxs-lookup"><span data-stu-id="d3a24-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="d3a24-129">Para comprobar la versión del sistema operativo, debemos mostrar la propiedad OSVersion. Para ello, escribimos:</span><span class="sxs-lookup"><span data-stu-id="d3a24-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="d3a24-130">Para comprobar si el equipo se está apagando, podemos mostrar la propiedad **HasShutdownStarted**:</span><span class="sxs-lookup"><span data-stu-id="d3a24-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

## <a name="doing-math-with-systemmath"></a><span data-ttu-id="d3a24-131">Operaciones matemáticas con System.Math</span><span class="sxs-lookup"><span data-stu-id="d3a24-131">Doing Math with System.Math</span></span>

<span data-ttu-id="d3a24-132">La clase estática System.Math es útil para realizar algunas operaciones matemáticas.</span><span class="sxs-lookup"><span data-stu-id="d3a24-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="d3a24-133">Los miembros importantes de **System.Math** son principalmente métodos, que podemos mostrar mediante **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="d3a24-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="d3a24-134">System.Math tiene varios métodos con el mismo nombre, pero se distinguen por el tipo de sus parámetros.</span><span class="sxs-lookup"><span data-stu-id="d3a24-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="d3a24-135">Escriba el siguiente comando para enumerar los métodos de la clase **System.Math**.</span><span class="sxs-lookup"><span data-stu-id="d3a24-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="d3a24-136">Muestra varios métodos matemáticos.</span><span class="sxs-lookup"><span data-stu-id="d3a24-136">This displays several mathematical methods.</span></span> <span data-ttu-id="d3a24-137">A continuación, presentamos una lista de comandos que muestran el funcionamiento de algunos de los métodos comunes:</span><span class="sxs-lookup"><span data-stu-id="d3a24-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```