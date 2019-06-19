---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Crear objetos de .NET y COM New Object
ms.openlocfilehash: 8bb0326d350be634a50897bdcd432e13ec93450c
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030272"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="e49e8-103">Crear objetos .NET y COM (New-Object)</span><span class="sxs-lookup"><span data-stu-id="e49e8-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="e49e8-104">Existen componentes de software con interfaces de .NET Framework y COM que permiten realizar muchas tareas de administración del sistema.</span><span class="sxs-lookup"><span data-stu-id="e49e8-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="e49e8-105">Windows PowerShell le permite usar estos componentes, por lo que no está limitado a las tareas que pueden realizarse mediante cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e49e8-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="e49e8-106">Muchos de los cmdlets de la versión inicial de Windows PowerShell no funcionan en equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="e49e8-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="e49e8-107">Demostraremos cómo superar esta limitación al administrar registros de eventos mediante el uso de la clase **System.Diagnostics.EventLog** de .NET Framework directamente desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e49e8-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="e49e8-108">Usar New-Object para el acceso de registro de eventos</span><span class="sxs-lookup"><span data-stu-id="e49e8-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="e49e8-109">La biblioteca de clases de .NET Framework incluye una clase denominada **System.Diagnostics.EventLog** que se puede usar para administrar registros de eventos.</span><span class="sxs-lookup"><span data-stu-id="e49e8-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="e49e8-110">Puede crear una nueva instancia de una clase de .NET Framework mediante el cmdlet **New-Object** con el parámetro **TypeName**.</span><span class="sxs-lookup"><span data-stu-id="e49e8-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="e49e8-111">Por ejemplo, el comando siguiente crea una referencia de registro de eventos:</span><span class="sxs-lookup"><span data-stu-id="e49e8-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="e49e8-112">Aunque el comando creó una instancia de la clase EventLog, la instancia no incluye ningún dato.</span><span class="sxs-lookup"><span data-stu-id="e49e8-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="e49e8-113">Eso es porque no especificamos un registro de eventos concreto.</span><span class="sxs-lookup"><span data-stu-id="e49e8-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="e49e8-114">¿Cómo se consigue un registro de eventos real?</span><span class="sxs-lookup"><span data-stu-id="e49e8-114">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="e49e8-115">Usar constructores con New-Object</span><span class="sxs-lookup"><span data-stu-id="e49e8-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="e49e8-116">Para hacer referencia a un registro de eventos específico, debe especificar el nombre del registro.</span><span class="sxs-lookup"><span data-stu-id="e49e8-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="e49e8-117">**New-Object** tiene un parámetro **ArgumentList**.</span><span class="sxs-lookup"><span data-stu-id="e49e8-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="e49e8-118">Los argumentos que se pasan como valores a este parámetro se usan en un método de inicio especial del objeto.</span><span class="sxs-lookup"><span data-stu-id="e49e8-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="e49e8-119">El método se llama *constructor* porque se usa para construir el objeto.</span><span class="sxs-lookup"><span data-stu-id="e49e8-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="e49e8-120">Por ejemplo, para obtener una referencia al registro de aplicaciones, especifique la cadena "Application" como argumento:</span><span class="sxs-lookup"><span data-stu-id="e49e8-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="e49e8-121">Puesto que la mayoría de las clases principales de .NET Framework se incluyen en el espacio de nombres del sistema, Windows PowerShell intentará buscar clases que especifique en el espacio de nombres del sistema si no encuentra a una coincidencia para el nombre de tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="e49e8-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="e49e8-122">Esto significa que puede especificar Diagnostics.EventLog en lugar de System.Diagnostics.EventLog.</span><span class="sxs-lookup"><span data-stu-id="e49e8-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="e49e8-123">Almacenar objetos en Variables</span><span class="sxs-lookup"><span data-stu-id="e49e8-123">Storing Objects in Variables</span></span>

<span data-ttu-id="e49e8-124">Es posible que desee almacenar una referencia a un objeto, para poder usarla en el shell actual.</span><span class="sxs-lookup"><span data-stu-id="e49e8-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="e49e8-125">Aunque Windows PowerShell permite realizar muchas tareas con las canalizaciones, lo que reduce la necesidad de variables, almacenar referencias a objetos en variables puede facilitar la manipulación de esos objetos en determinadas ocasiones.</span><span class="sxs-lookup"><span data-stu-id="e49e8-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="e49e8-126">Windows PowerShell le permite crear variables que básicamente se denominan objetos.</span><span class="sxs-lookup"><span data-stu-id="e49e8-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="e49e8-127">La salida de cualquier comando válido de Windows PowerShell puede almacenarse en una variable.</span><span class="sxs-lookup"><span data-stu-id="e49e8-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="e49e8-128">Los nombres de variable siempre comienzan por $.</span><span class="sxs-lookup"><span data-stu-id="e49e8-128">Variable names always begin with $.</span></span> <span data-ttu-id="e49e8-129">Si desea almacenar la referencia del registro de aplicaciones en una variable denominada $AppLog, escriba el nombre de la variable, seguido de un signo igual y, a continuación, escriba el comando usado para crear el objeto de registro de aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="e49e8-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="e49e8-130">Si luego escribe $AppLog, puede ver que contiene el registro de aplicaciones:</span><span class="sxs-lookup"><span data-stu-id="e49e8-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="e49e8-131">Acceder a un registro de eventos remoto con New-Object</span><span class="sxs-lookup"><span data-stu-id="e49e8-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="e49e8-132">Los comandos usados en la sección anterior son para el equipo local; el cmdlet **Get-EventLog** puede hacerlo.</span><span class="sxs-lookup"><span data-stu-id="e49e8-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="e49e8-133">Para acceder al registro de aplicaciones en un equipo remoto, debe proporcionar el nombre del registro y un nombre de equipo (o dirección IP) como argumentos.</span><span class="sxs-lookup"><span data-stu-id="e49e8-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="e49e8-134">Ahora que tenemos una referencia a un registro de eventos almacenado en la variable $RemoteAppLog, ¿qué tareas podemos realizar en él?</span><span class="sxs-lookup"><span data-stu-id="e49e8-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="e49e8-135">Borrar un registro de eventos con los métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="e49e8-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="e49e8-136">Los objetos suelen tener métodos que se puedan llamar para realizar tareas.</span><span class="sxs-lookup"><span data-stu-id="e49e8-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="e49e8-137">Puede usar **Get-Member** para mostrar los métodos asociados a un objeto.</span><span class="sxs-lookup"><span data-stu-id="e49e8-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="e49e8-138">El siguiente comando y la salida seleccionada muestran algunos de los métodos de la clase EventLog:</span><span class="sxs-lookup"><span data-stu-id="e49e8-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="e49e8-139">El método **Clear()** se puede usar para borrar el registro de eventos.</span><span class="sxs-lookup"><span data-stu-id="e49e8-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="e49e8-140">Al llamar a un método, siempre debe seguir el nombre del método con paréntesis, aunque este no requiera argumentos.</span><span class="sxs-lookup"><span data-stu-id="e49e8-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="e49e8-141">Esto permite que Windows PowerShell distinga entre el método y una propiedad potencial con el mismo nombre.</span><span class="sxs-lookup"><span data-stu-id="e49e8-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="e49e8-142">Escriba lo siguiente para llamar al método **Clear**:</span><span class="sxs-lookup"><span data-stu-id="e49e8-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="e49e8-143">Escriba lo siguiente para mostrar el registro.</span><span class="sxs-lookup"><span data-stu-id="e49e8-143">Type the following to display the log.</span></span> <span data-ttu-id="e49e8-144">Verá que se ha borrado el registro de eventos y ahora tiene 0 entradas en lugar de 262:</span><span class="sxs-lookup"><span data-stu-id="e49e8-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="e49e8-145">Crear objetos COM con New-Object</span><span class="sxs-lookup"><span data-stu-id="e49e8-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="e49e8-146">Puede usar **New-Object** para trabajar con componentes del Modelo de objetos componentes (COM).</span><span class="sxs-lookup"><span data-stu-id="e49e8-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="e49e8-147">Los componentes van desde las distintas bibliotecas incluidas con Windows Script Host (WSH) hasta las aplicaciones de ActiveX, como Internet Explorer, que están instaladas en la mayoría de los sistemas.</span><span class="sxs-lookup"><span data-stu-id="e49e8-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="e49e8-148">**New-Object** usa contenedores RCW de .NET Framework para crear objetos COM, por lo que tiene las mismas limitaciones que .NET Framework al llamar a objetos COM.</span><span class="sxs-lookup"><span data-stu-id="e49e8-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="e49e8-149">Para crear un objeto COM, debe especificar el parámetro **ComObject** con el identificador de programación o *ProgID* de la clase COM que quiere usar.</span><span class="sxs-lookup"><span data-stu-id="e49e8-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="e49e8-150">Una explicación completa de las limitaciones del uso de COM y determinar qué ProgID están disponibles en un sistema está fuera del ámbito de esta guía de usuario, pero la mayoría de los objetos conocidos de entornos como WSH pueden usarse en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e49e8-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="e49e8-151">Puede crear los objetos WSH mediante la especificación de estos objetos ProgID: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary** y **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="e49e8-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="e49e8-152">Los siguientes comandos crean estos objetos:</span><span class="sxs-lookup"><span data-stu-id="e49e8-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="e49e8-153">Aunque la mayor parte de la funcionalidad de estas clases está disponible de otras maneras en Windows PowerShell, algunas tareas como la creación de accesos directos son aún más fáciles con las clases de WSH.</span><span class="sxs-lookup"><span data-stu-id="e49e8-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="e49e8-154">Crear un acceso directo de escritorio con WScript.Shell</span><span class="sxs-lookup"><span data-stu-id="e49e8-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="e49e8-155">Una tarea que se puede realizar rápidamente con un objeto COM es crear un acceso directo.</span><span class="sxs-lookup"><span data-stu-id="e49e8-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="e49e8-156">Supongamos que desea crear un acceso directo en el escritorio que se vincule a la carpeta principal de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e49e8-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="e49e8-157">Primero debe crear una referencia a **WScript.Shell**, que se almacenará en una variable denominada **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="e49e8-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="e49e8-158">Get-Member funciona con los objetos COM, de modo que puede escribir lo siguiente para explorar los miembros del objeto:</span><span class="sxs-lookup"><span data-stu-id="e49e8-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="e49e8-159">**Get-Member** tiene un parámetro **InputObject** opcional que puede usar en lugar de las canalizaciones para proporcionar la entrada a **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="e49e8-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="e49e8-160">Obtendría la misma salida mostrada anteriormente si en su lugar usara el comando **Get-Member -InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="e49e8-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="e49e8-161">Si usa **InputObject**, trata su argumento como un solo elemento.</span><span class="sxs-lookup"><span data-stu-id="e49e8-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="e49e8-162">Esto significa que si tiene varios objetos en una variable, **Get-Member** los trata como una matriz de objetos.</span><span class="sxs-lookup"><span data-stu-id="e49e8-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="e49e8-163">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e49e8-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="e49e8-164">El método **WScript.Shell CreateShortcut** acepta un solo argumento, la ruta de acceso al archivo de acceso directo que se va a crear.</span><span class="sxs-lookup"><span data-stu-id="e49e8-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="e49e8-165">Podríamos escribir la ruta de acceso completa al escritorio, pero hay una manera más fácil.</span><span class="sxs-lookup"><span data-stu-id="e49e8-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="e49e8-166">El escritorio suele representarse con una carpeta denominada Desktop dentro de la carpeta principal del usuario actual.</span><span class="sxs-lookup"><span data-stu-id="e49e8-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="e49e8-167">Windows PowerShell tiene una variable **$Home** que contiene la ruta de acceso a esta carpeta.</span><span class="sxs-lookup"><span data-stu-id="e49e8-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="e49e8-168">Podemos especificar la ruta de acceso a la carpeta principal mediante esta variable y, después, agregar el nombre de la carpeta Desktop y el nombre del acceso directo que crearemos escribiéndolo:</span><span class="sxs-lookup"><span data-stu-id="e49e8-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="e49e8-169">Si usa algo parecido a un nombre de variable entre comillas dobles, Windows PowerShell intenta sustituir un valor coincidente.</span><span class="sxs-lookup"><span data-stu-id="e49e8-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="e49e8-170">Si usa comillas simples, Windows PowerShell no intenta sustituir el valor de la variable.</span><span class="sxs-lookup"><span data-stu-id="e49e8-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="e49e8-171">Por ejemplo, intente escribir los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="e49e8-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="e49e8-172">Ahora tenemos una variable denominada **$lnk** que contiene una nueva referencia de acceso directo.</span><span class="sxs-lookup"><span data-stu-id="e49e8-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="e49e8-173">Si quiere ver sus miembros, puede canalizarla a **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="e49e8-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="e49e8-174">La salida siguiente muestra los miembros que debemos usar para terminar de crear el acceso directo:</span><span class="sxs-lookup"><span data-stu-id="e49e8-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="e49e8-175">Es preciso especificar **TargetPath**, que es la carpeta de aplicación de Windows PowerShell y, luego, guardar el acceso directo **$lnk** llamando al método **Save**.</span><span class="sxs-lookup"><span data-stu-id="e49e8-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="e49e8-176">La ruta de acceso de la carpeta de la aplicación de Windows PowerShell se almacena en la variable **$PSHome**, por lo que podemos escribir lo siguiente para hacerlo:</span><span class="sxs-lookup"><span data-stu-id="e49e8-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="e49e8-177">Usar Internet Explorer desde Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e49e8-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="e49e8-178">Muchas aplicaciones (incluida la familia de aplicaciones de Microsoft Office e Internet Explorer) pueden automatizarse mediante COM.</span><span class="sxs-lookup"><span data-stu-id="e49e8-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="e49e8-179">Internet Explorer muestra algunas de las técnicas y problemas típicos que implica trabajar con aplicaciones basadas en COM.</span><span class="sxs-lookup"><span data-stu-id="e49e8-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="e49e8-180">Una instancia de Internet Explorer se crea especificando el ProgID de Internet Explorer, **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="e49e8-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="e49e8-181">Este comando inicia Internet Explorer, pero no hace que sea visible.</span><span class="sxs-lookup"><span data-stu-id="e49e8-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="e49e8-182">Si escribe Get-Process, puede ver que se está ejecutando un proceso denominado iexplore.</span><span class="sxs-lookup"><span data-stu-id="e49e8-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="e49e8-183">De hecho, si sale de Windows PowerShell, el proceso se seguirá ejecutando.</span><span class="sxs-lookup"><span data-stu-id="e49e8-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="e49e8-184">Debe reiniciar el equipo o usar una herramienta como el Administrador de tareas para finalizar el proceso de iexplore.</span><span class="sxs-lookup"><span data-stu-id="e49e8-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="e49e8-185">Los objetos COM que se inician como procesos independientes, denominados normalmente *ejecutables de ActiveX*, pueden mostrar o no una ventana de interfaz de usuario al iniciarse.</span><span class="sxs-lookup"><span data-stu-id="e49e8-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="e49e8-186">Si crean una ventana, pero no la hacen visible, como Internet Explorer, el enfoque se moverá generalmente al escritorio de Windows y debe hacer que la ventana sea visible para interactuar con ella.</span><span class="sxs-lookup"><span data-stu-id="e49e8-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="e49e8-187">Si escribe **$ie | Get-Member**, podrá ver las propiedades y los métodos de Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="e49e8-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="e49e8-188">Para ver la ventana de Internet Explorer, establezca la propiedad Visible en $true escribiendo:</span><span class="sxs-lookup"><span data-stu-id="e49e8-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="e49e8-189">A continuación, puede navegar a una dirección web específica mediante el método Navigate:</span><span class="sxs-lookup"><span data-stu-id="e49e8-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="e49e8-190">Con otros miembros del modelo de objetos de Internet Explorer, es posible recuperar el contenido de texto de la página web.</span><span class="sxs-lookup"><span data-stu-id="e49e8-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="e49e8-191">El siguiente comando mostrará el texto HTML en el cuerpo de la página web actual:</span><span class="sxs-lookup"><span data-stu-id="e49e8-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="e49e8-192">Para cerrar Internet Explorer desde PowerShell, llame a su método Quit():</span><span class="sxs-lookup"><span data-stu-id="e49e8-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="e49e8-193">Se forzará el cierre.</span><span class="sxs-lookup"><span data-stu-id="e49e8-193">This will force it to close.</span></span> <span data-ttu-id="e49e8-194">La variable $ie ya no contiene una referencia válida, aunque parece ser un objeto COM.</span><span class="sxs-lookup"><span data-stu-id="e49e8-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="e49e8-195">Si intenta usarla, obtendrá un error de automatización:</span><span class="sxs-lookup"><span data-stu-id="e49e8-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="e49e8-196">Puede quitar la referencia restante con un comando como $ie = $null, o bien escribir lo siguiente para quitarla completamente:</span><span class="sxs-lookup"><span data-stu-id="e49e8-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="e49e8-197">No hay un estándar común para determinar si los ejecutables de ActiveX se cierran o se siguen ejecutando cuando se quita una referencia a uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="e49e8-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="e49e8-198">Que la aplicación se cierre o no dependerá de las circunstancias, como, por ejemplo, si la aplicación es visible, si está ejecutando en ella un documento editado e incluso si Windows PowerShell todavía se está ejecutando.</span><span class="sxs-lookup"><span data-stu-id="e49e8-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="e49e8-199">Por este motivo, debe probar el comportamiento de finalización de cada ejecutable de ActiveX que quiere usar en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e49e8-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="e49e8-200">Obtener advertencias sobre los objetos COM ajustados por .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e49e8-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="e49e8-201">En algunos casos, un objeto COM puede tener un *contenedor RCW* de .NET Framework asociado, que se usará en **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="e49e8-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="e49e8-202">Dado que el comportamiento del RCW puede ser diferente del comportamiento del objeto COM normal, **New-Object** tiene un parámetro **Strict** para advertirle del acceso del RCW.</span><span class="sxs-lookup"><span data-stu-id="e49e8-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="e49e8-203">Si especifica el parámetro **Strict** y, a continuación, crea un objeto COM que usa un RCW, recibirá un mensaje de advertencia:</span><span class="sxs-lookup"><span data-stu-id="e49e8-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="e49e8-204">Aunque el objeto se creará de todos modos, se le advertirá que no es un objeto COM estándar.</span><span class="sxs-lookup"><span data-stu-id="e49e8-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>
