---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: Active Directory de principio a fin
ms.technology: powershell
ms.openlocfilehash: 3108f5dad96ef54feb3cf559fae38812ed46849c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="end-to-end---active-directory"></a><span data-ttu-id="d1652-103">De un extremo a otro: Active Directory</span><span class="sxs-lookup"><span data-stu-id="d1652-103">End to End - Active Directory</span></span>
<span data-ttu-id="d1652-104">Imagine que el ámbito de su programa ha aumentado.</span><span class="sxs-lookup"><span data-stu-id="d1652-104">Imagine the scope of your program has increased.</span></span>
<span data-ttu-id="d1652-105">Ahora es responsable de agregar JEA a controladores de dominio para realizar acciones de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d1652-105">You are now responsible for adding JEA to Domain Controllers to perform Active Directory actions.</span></span>
<span data-ttu-id="d1652-106">El personal del departamento de soporte técnico va a usar JEA para desbloquear cuentas, restablecer contraseñas y otras acciones similares.</span><span class="sxs-lookup"><span data-stu-id="d1652-106">The help desk people are going to use JEA to unlock accounts, reset passwords, and do other similar actions.</span></span>

<span data-ttu-id="d1652-107">Debe exponer un conjunto de comandos completamente nuevo para un grupo diferente de personas.</span><span class="sxs-lookup"><span data-stu-id="d1652-107">You need to expose a completely new set of commands to a different group of people.</span></span>
<span data-ttu-id="d1652-108">Además, tiene que exponer numerosos scripts existentes de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d1652-108">On top of that, you have a bunch of existing Active Directory scripts you need to expose.</span></span>
<span data-ttu-id="d1652-109">Esta sección le guiará por el proceso de creación de una configuración de sesión y funcionalidad de rol para esta tarea.</span><span class="sxs-lookup"><span data-stu-id="d1652-109">This section will walk through authoring a Session Configuration and Role Capability for this task.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1652-110">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="d1652-110">Prerequisites</span></span>
<span data-ttu-id="d1652-111">Para seguir esta sección paso a paso, debe trabajar en un controlador de dominio.</span><span class="sxs-lookup"><span data-stu-id="d1652-111">To follow this section step-by-step, you'll need to be operating on a domain controller.</span></span>
<span data-ttu-id="d1652-112">Si no tiene acceso al controlador de dominio, no se preocupe.</span><span class="sxs-lookup"><span data-stu-id="d1652-112">If you don't have access to your domain controller, don't worry.</span></span>
<span data-ttu-id="d1652-113">Intente seguir los pasos trabajando en otro escenario o rol con el que esté familiarizado.</span><span class="sxs-lookup"><span data-stu-id="d1652-113">Try to follow along with by working against some other scenario or role with which you are familiar.</span></span>
<span data-ttu-id="d1652-114">Si quiere configurar rápidamente un nuevo controlador de dominio, consulte el apéndice [Creación de un controlador de dominio](.\creating-a-domain-controller.md).</span><span class="sxs-lookup"><span data-stu-id="d1652-114">If you want to quickly set up a new domain controller, check out the [Creating a Domain Controller appendix](.\creating-a-domain-controller.md).</span></span>

## <a name="steps-to-make-a-new-role-capability-and-session-configuration"></a><span data-ttu-id="d1652-115">Pasos para crear una nueva funcionalidad de rol y configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="d1652-115">Steps to Make a new Role Capability and Session Configuration</span></span>

<span data-ttu-id="d1652-116">La tarea de crear una nueva funcionalidad de rol puede parecer desalentadora al principio, pero puede dividirse en pasos bastante simples:</span><span class="sxs-lookup"><span data-stu-id="d1652-116">Making a new role capability can seem daunting at first, but it can be broken into fairly simple steps:</span></span>

1.  <span data-ttu-id="d1652-117">Identificar las tareas que se deben habilitar</span><span class="sxs-lookup"><span data-stu-id="d1652-117">Identify the tasks you need to enable</span></span>
2.  <span data-ttu-id="d1652-118">Restringir las tareas según sea necesario</span><span class="sxs-lookup"><span data-stu-id="d1652-118">Restrict those tasks as necessary</span></span>
3.  <span data-ttu-id="d1652-119">Confirmar que funcionan con JEA</span><span class="sxs-lookup"><span data-stu-id="d1652-119">Confirm they work with JEA</span></span>
4.  <span data-ttu-id="d1652-120">Colocarlas en un archivo de funcionalidad de rol</span><span class="sxs-lookup"><span data-stu-id="d1652-120">Put them in a Role Capability file</span></span>
5.  <span data-ttu-id="d1652-121">Registrar una configuración de sesión que exponga esa funcionalidad de rol</span><span class="sxs-lookup"><span data-stu-id="d1652-121">Register a Session Configuration that exposes that Role Capability</span></span>

## <a name="step-1-identify-what-needs-to-be-exposed"></a><span data-ttu-id="d1652-122">Paso 1: identificar lo que se debe exponer</span><span class="sxs-lookup"><span data-stu-id="d1652-122">Step 1: Identify What Needs to Be Exposed</span></span>
<span data-ttu-id="d1652-123">Antes de crear una nueva funcionalidad de rol o configuración de sesión, debe identificar todas las acciones que los usuarios tendrán que realizar mediante el punto de conexión de JEA, así como la manera en que se llevarán a cabo a través de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1652-123">Before you make a new Role Capability or Session Configuration, you need to identify all of the things users will need to do through the JEA endpoint, as well as how to do them through PowerShell.</span></span>
<span data-ttu-id="d1652-124">Esto implica llevar a cabo una extensa recopilación e investigación de requisitos.</span><span class="sxs-lookup"><span data-stu-id="d1652-124">This will involve a fair amount of requirement gathering and research.</span></span>
<span data-ttu-id="d1652-125">La manera en que realice este proceso dependerá de su organización y de sus objetivos.</span><span class="sxs-lookup"><span data-stu-id="d1652-125">How you go about this process will depend on your organization and goals.</span></span>
<span data-ttu-id="d1652-126">Es importante destacar que la recopilación y la investigación de los requisitos es una parte fundamental del proceso real.</span><span class="sxs-lookup"><span data-stu-id="d1652-126">It is important to call out requirement gathering and research as a critical part of the real world process.</span></span>
<span data-ttu-id="d1652-127">Este podría ser el paso más difícil del proceso de adopción de JEA.</span><span class="sxs-lookup"><span data-stu-id="d1652-127">This may be the most difficult step in the process of adopting JEA.</span></span>

### <a name="find-resources"></a><span data-ttu-id="d1652-128">Buscar recursos</span><span class="sxs-lookup"><span data-stu-id="d1652-128">Find Resources</span></span>
<span data-ttu-id="d1652-129">A continuación se indica una serie de recursos en línea que podría haber encontrado en su investigación para crear un punto de conexión de administración de Active Directory:</span><span class="sxs-lookup"><span data-stu-id="d1652-129">Here is a set of online resources that might have come up in your research on creating an Active Directory management endpoint:</span></span>
-   [<span data-ttu-id="d1652-130">Introducción a Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1652-130">Active Directory PowerShell Overview</span></span>](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [<span data-ttu-id="d1652-131">Guía de comandos de Powershell para Active Directory</span><span class="sxs-lookup"><span data-stu-id="d1652-131">CMD to PowerShell Guide for Active Directory</span></span>](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### <a name="make-a-list"></a><span data-ttu-id="d1652-132">Hacer una lista</span><span class="sxs-lookup"><span data-stu-id="d1652-132">Make a List</span></span>
<span data-ttu-id="d1652-133">A continuación se muestran diez acciones con las que trabajará en el resto de la sección.</span><span class="sxs-lookup"><span data-stu-id="d1652-133">Here is a set of ten actions that you will be working from in the remainder of this section.</span></span>
<span data-ttu-id="d1652-134">Tenga en cuenta que se trata básicamente de un ejemplo y que los requisitos de las organizaciones podrían ser diferentes:</span><span class="sxs-lookup"><span data-stu-id="d1652-134">Keep in mind this is simply an example, your organizations requirements may be different:</span></span>

|<span data-ttu-id="d1652-135">Acción</span><span class="sxs-lookup"><span data-stu-id="d1652-135">Action</span></span>                                                         |<span data-ttu-id="d1652-136">Comando de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1652-136">PowerShell Command</span></span>                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|<span data-ttu-id="d1652-137">Desbloquear cuenta</span><span class="sxs-lookup"><span data-stu-id="d1652-137">Account Unlock</span></span>                                                 |`Unlock-ADAccount`                                             |
|<span data-ttu-id="d1652-138">Restablecimiento de contraseña</span><span class="sxs-lookup"><span data-stu-id="d1652-138">Password Reset</span></span>                                                 |<span data-ttu-id="d1652-139">`Set-ADAccountPassword` y `Set-ADUser -ChangePasswordAtLogon`</span><span class="sxs-lookup"><span data-stu-id="d1652-139">`Set-ADAccountPassword` and `Set-ADUser -ChangePasswordAtLogon`</span></span>|
|<span data-ttu-id="d1652-140">Cambiar el cargo de un usuario</span><span class="sxs-lookup"><span data-stu-id="d1652-140">Change a User's Title</span></span>                                          |`Set-ADUser -Title`                                            |  
|<span data-ttu-id="d1652-141">Buscar cuentas de AD que estén bloqueadas, deshabilitadas, inactivas, etc.</span><span class="sxs-lookup"><span data-stu-id="d1652-141">Find AD Accounts that are locked out, disabled, inactive, etc.</span></span> |`Search-ADAccount`                                             |
|<span data-ttu-id="d1652-142">Agregar un usuario a un grupo</span><span class="sxs-lookup"><span data-stu-id="d1652-142">Add User to Group</span></span>                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|<span data-ttu-id="d1652-143">Quitar un usuario de un grupo</span><span class="sxs-lookup"><span data-stu-id="d1652-143">Remove User from Group</span></span>                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|<span data-ttu-id="d1652-144">Habilitar una cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="d1652-144">Enable a user account</span></span>                                          |`Enable-ADAccount`                                             |
|<span data-ttu-id="d1652-145">Deshabilitar una cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="d1652-145">Disable a user account</span></span>                                         |`Disable-ADAccount`                                            |

## <a name="step-2-restrict-tasks-as-necessary"></a><span data-ttu-id="d1652-146">Paso 2: restringir las tareas según sea necesario</span><span class="sxs-lookup"><span data-stu-id="d1652-146">Step 2: Restrict Tasks as Necessary</span></span>

<span data-ttu-id="d1652-147">Ahora que tiene la lista de acciones, debe considerar detenidamente las capacidades de cada comando.</span><span class="sxs-lookup"><span data-stu-id="d1652-147">Now that you have your list of actions, you need to think through the capabilities of each command.</span></span>
<span data-ttu-id="d1652-148">Hay dos razones importantes para hacerlo:</span><span class="sxs-lookup"><span data-stu-id="d1652-148">There are two important reasons to do this:</span></span>

1.  <span data-ttu-id="d1652-149">Es fácil proporcionar a los usuarios más funcionalidades de las previstas.</span><span class="sxs-lookup"><span data-stu-id="d1652-149">It is easy to give users more capabilities than you intend.</span></span>
<span data-ttu-id="d1652-150">Por ejemplo, `Set-ADUser` es un comando increíblemente eficaz y flexible.</span><span class="sxs-lookup"><span data-stu-id="d1652-150">For example, `Set-ADUser` is an incredibly powerful and flexible command.</span></span>
<span data-ttu-id="d1652-151">Probablemente no le interese exponer todo lo que puede hacer para ayudar a los usuarios del departamento de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="d1652-151">You may not want to expose everything it can do to help desk users.</span></span>  

2.  <span data-ttu-id="d1652-152">Peor aún, es posible exponer los comandos que permiten a los usuarios evitar las restricciones de JEA.</span><span class="sxs-lookup"><span data-stu-id="d1652-152">Even worse, it's possible to expose commands that allow users to escape JEA's restrictions.</span></span>
<span data-ttu-id="d1652-153">Si esto ocurre, JEA deja de funcionar como límite de seguridad.</span><span class="sxs-lookup"><span data-stu-id="d1652-153">If this happens, JEA ceases to function as a security boundary.</span></span>
<span data-ttu-id="d1652-154">Tenga cuidado al seleccionar comandos.</span><span class="sxs-lookup"><span data-stu-id="d1652-154">Please be careful when selecting commands.</span></span>
<span data-ttu-id="d1652-155">Por ejemplo, Invoke-Expression permitirá que los usuarios ejecuten código sin restricciones.</span><span class="sxs-lookup"><span data-stu-id="d1652-155">For example, Invoke-Expression will allow users to run unrestricted code.</span></span>
<span data-ttu-id="d1652-156">Para obtener más información sobre este tema, consulte la sección Consideraciones al limitar comandos.</span><span class="sxs-lookup"><span data-stu-id="d1652-156">For more discussion on this topic, check out the Considerations When Restricting Commands section.</span></span>

<span data-ttu-id="d1652-157">Después de revisar cada comando, decide restringir lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d1652-157">After reviewing each command, you decide to restrict the following:</span></span>

1.  <span data-ttu-id="d1652-158">`Set-ADUser` solo se debe poder ejecutar con el parámetro -Title</span><span class="sxs-lookup"><span data-stu-id="d1652-158">`Set-ADUser` should only be allowed to run with the -Title parameter</span></span>

2.  <span data-ttu-id="d1652-159">`Add-ADGroupMember` y `Remove-ADGroupMember` solo deben funcionar con determinados grupos</span><span class="sxs-lookup"><span data-stu-id="d1652-159">`Add-ADGroupMember` and `Remove-ADGroupMember` should only work with certain groups</span></span>

### <a name="step-3-confirm-the-tasks-work-with-jea"></a><span data-ttu-id="d1652-160">Paso 3: confirmar que las tareas funcionan con JEA</span><span class="sxs-lookup"><span data-stu-id="d1652-160">Step 3: Confirm the Tasks Work with JEA</span></span>
<span data-ttu-id="d1652-161">En realidad, el uso de estos cmdlets podría no ser sencillo en el entorno de JEA restringido.</span><span class="sxs-lookup"><span data-stu-id="d1652-161">Actually using those cmdlets may not be straightforward in the restricted JEA environment.</span></span>
<span data-ttu-id="d1652-162">JEA se ejecuta en el modo *NoLanguage* que, entre otras cosas, impide que los usuarios usen variables.</span><span class="sxs-lookup"><span data-stu-id="d1652-162">JEA runs in *NoLanguage* mode which, among other things, prevents users from using variables.</span></span>
<span data-ttu-id="d1652-163">Para asegurarse de que los usuarios finales tengan una experiencia sin problemas, es importante comprobar ciertas cosas.</span><span class="sxs-lookup"><span data-stu-id="d1652-163">In order to ensure that end users have a smooth experience, it's important to check for a few things.</span></span>

<span data-ttu-id="d1652-164">Por ejemplo, considere el comando `Set-ADAccountPassword`.</span><span class="sxs-lookup"><span data-stu-id="d1652-164">As an example, consider `Set-ADAccountPassword`.</span></span>
<span data-ttu-id="d1652-165">El parámetro -NewPassword requiere una cadena segura.</span><span class="sxs-lookup"><span data-stu-id="d1652-165">The -NewPassword parameter requires a secure string.</span></span>
<span data-ttu-id="d1652-166">A menudo, los usuarios crean una cadena segura y la pasan como variable (como puede verse más abajo):</span><span class="sxs-lookup"><span data-stu-id="d1652-166">Often, users create a secure string and pass it in as a variable (as below):</span></span>

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

<span data-ttu-id="d1652-167">Pero el modo *NoLanguage* impide el uso de variables.</span><span class="sxs-lookup"><span data-stu-id="d1652-167">However, *NoLanguage* mode prevents the usage of variables.</span></span>
<span data-ttu-id="d1652-168">Puede evitar esta restricción de dos maneras:</span><span class="sxs-lookup"><span data-stu-id="d1652-168">You can get around this restriction in two ways:</span></span>

1.  <span data-ttu-id="d1652-169">Puede requerir a los usuarios que ejecuten el comando sin asignar variables.</span><span class="sxs-lookup"><span data-stu-id="d1652-169">You can require users run the command without assigning variables.</span></span>
<span data-ttu-id="d1652-170">Esto es fácil de configurar, pero puede ser complicado para los operadores que usan el punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="d1652-170">This is easy to configure, but can be painful for the operators using the endpoint.</span></span>
<span data-ttu-id="d1652-171">A nadie le gusta la idea de tener que escribir lo siguiente cada vez que restablece una contraseña.</span><span class="sxs-lookup"><span data-stu-id="d1652-171">Who wants to type this out every time you reset a password?</span></span>
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  <span data-ttu-id="d1652-172">Puede ajustar la complejidad de un script o una función que exponga a los usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="d1652-172">You can wrap the complexity in a script or a function that you expose to end users.</span></span>
<span data-ttu-id="d1652-173">Los scripts y las funciones que se exponen se ejecutan en un contexto sin restricciones; puede escribir funciones que usen variables y llamen a otros comandos sin ningún problema.</span><span class="sxs-lookup"><span data-stu-id="d1652-173">Scripts and functions that you expose run in an unrestricted context; you can write functions that use variables and call other commands without any issue.</span></span>
<span data-ttu-id="d1652-174">Este enfoque simplifica la experiencia del usuario final, evita errores, reduce los conocimientos necesarios de PowerShell y reduce la exposición involuntaria de demasiadas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="d1652-174">This approach simplifies the end user experience, prevents errors, reduces required PowerShell knowledge, and reduces unintentionally exposing excess functionality.</span></span>
<span data-ttu-id="d1652-175">La única desventaja es el costo de crear y mantener la función.</span><span class="sxs-lookup"><span data-stu-id="d1652-175">The only downside is the cost of authoring and maintaining the function.</span></span>

### <a name="aside-adding-a-function-to-your-module"></a><span data-ttu-id="d1652-176">Inciso: Agregar una función al módulo</span><span class="sxs-lookup"><span data-stu-id="d1652-176">Aside: Adding a Function to your Module</span></span>
<span data-ttu-id="d1652-177">Si adopta el segundo enfoque, tendrá que escribir una función de PowerShell denominada `Reset-ContosoUserPassword`.</span><span class="sxs-lookup"><span data-stu-id="d1652-177">Taking approach #2, you are going to write a PowerShell function called `Reset-ContosoUserPassword`.</span></span>
<span data-ttu-id="d1652-178">Esta función se encarga de todo lo que debe ocurrir cuando se restablece una contraseña de usuario.</span><span class="sxs-lookup"><span data-stu-id="d1652-178">This function is going to do everything that needs to happen when you reset a user's password.</span></span>
<span data-ttu-id="d1652-179">En su organización, esto podría obligarle a hacer cosas sofisticadas y complicadas.</span><span class="sxs-lookup"><span data-stu-id="d1652-179">In your organization, this may involve doing fancy and complicated things.</span></span>
<span data-ttu-id="d1652-180">Ya que esto es solo un ejemplo, el comando simplemente restablecerá la contraseña y solicitará al usuario que cambie la contraseña al iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="d1652-180">Because this is just an example, your command will just reset the password and require the user change the password at logon.</span></span>
<span data-ttu-id="d1652-181">Lo colocaremos en el módulo Contoso_AD_Module que creó en la última sección.</span><span class="sxs-lookup"><span data-stu-id="d1652-181">We will put it in the Contoso_AD_Module module you made in the last section.</span></span>

1. <span data-ttu-id="d1652-182">En PowerShell ISE, abra "Contoso_AD_Module.psm1".</span><span class="sxs-lookup"><span data-stu-id="d1652-182">In PowerShell ISE, open "Contoso_AD_Module.psm1"</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. <span data-ttu-id="d1652-183">Pulse Ctrl+J para abrir el menú de fragmentos de código.</span><span class="sxs-lookup"><span data-stu-id="d1652-183">Press Crtl+J to open the snippets menu.</span></span>

3. <span data-ttu-id="d1652-184">Pulse la tecla abajo hasta que encuentre "function" y pulse ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="d1652-184">Key down until you find "function" and press enter.</span></span>
<span data-ttu-id="d1652-185">Esto mostrará un esqueleto muy básico de una función.</span><span class="sxs-lookup"><span data-stu-id="d1652-185">This puts up a super basic skeleton of a function.</span></span>

4. <span data-ttu-id="d1652-186">Cambie el nombre de la función a "Reset-ContosoUserPassword".</span><span class="sxs-lookup"><span data-stu-id="d1652-186">Rename the function "Reset-ContosoUserPassword".</span></span>  

5. <span data-ttu-id="d1652-187">Cambie el nombre de uno de los parámetros a "Identity" y elimine el segundo.</span><span class="sxs-lookup"><span data-stu-id="d1652-187">Rename one of the parameters "Identity" and delete the second.</span></span>

6. <span data-ttu-id="d1652-188">Copie lo siguiente en el cuerpo de la función.</span><span class="sxs-lookup"><span data-stu-id="d1652-188">Copy the following into the body of the function.</span></span>
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. <span data-ttu-id="d1652-189">Guarde el archivo.</span><span class="sxs-lookup"><span data-stu-id="d1652-189">Save the file.</span></span>
<span data-ttu-id="d1652-190">Debería obtener un resultado parecido a este:</span><span class="sxs-lookup"><span data-stu-id="d1652-190">You should end up with something that looks like this:</span></span>
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
<span data-ttu-id="d1652-191">Ahora, los usuarios pueden llamar simplemente a `Reset-ContosoUserPassword` y no tienen que recordar la sintaxis para crear una cadena segura de insertada.</span><span class="sxs-lookup"><span data-stu-id="d1652-191">Now, your users can simply call `Reset-ContosoUserPassword` and not have to remember the syntax to create a secure string inline.</span></span>

## <a name="step-4-edit-the-role-capability-file"></a><span data-ttu-id="d1652-192">Paso 4: editar el archivo de funcionalidad de rol</span><span class="sxs-lookup"><span data-stu-id="d1652-192">Step 4: Edit the Role Capability File</span></span>
<span data-ttu-id="d1652-193">En la sección [Creación de funcionalidades de rol](./role-capabilities.md#role-capability-creation), creó un archivo de funcionalidad de rol en blanco.</span><span class="sxs-lookup"><span data-stu-id="d1652-193">In the [Role Capability Creation](./role-capabilities.md#role-capability-creation) section, you created a blank Role Capability file.</span></span>
<span data-ttu-id="d1652-194">En esta sección, rellenará los valores de ese archivo.</span><span class="sxs-lookup"><span data-stu-id="d1652-194">In this section, you will fill in the values in that file.</span></span>

<span data-ttu-id="d1652-195">En primer lugar, abra el archivo de funcionalidad de rol en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d1652-195">Start by opening the role capability file in PowerShell ISE.</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
<span data-ttu-id="d1652-196">Actualice el archivo con los cambios siguientes:</span><span class="sxs-lookup"><span data-stu-id="d1652-196">Update the file with the following changes:</span></span>
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

<span data-ttu-id="d1652-197">Hay algunos aspectos que debe tener en cuenta sobre lo anterior:</span><span class="sxs-lookup"><span data-stu-id="d1652-197">There are a few things to note about the above:</span></span>
1.  <span data-ttu-id="d1652-198">PowerShell intentará cargar automáticamente los módulos necesarios para la funcionalidad de rol.</span><span class="sxs-lookup"><span data-stu-id="d1652-198">PowerShell will attempt to auto-load the modules needed for your Role Capability.</span></span>
<span data-ttu-id="d1652-199">Podría tener que mostrar explícitamente los nombres de los módulos en el campo "ModulesToImport" si experimenta problemas con un módulo porque no se carga automáticamente.</span><span class="sxs-lookup"><span data-stu-id="d1652-199">You may need to explicitly list module names in the "ModulesToImport" field if you notice problems with a module not being autoloaded.</span></span>

2.  <span data-ttu-id="d1652-200">Si no está seguro de si un comando es un cmdlet o una función, ejecute `Get-Command` y observe la propiedad "CommandType"</span><span class="sxs-lookup"><span data-stu-id="d1652-200">If you aren't sure if a command is a cmdlet or a function, run `Get-Command` and look at the "CommandType" property</span></span>

3.  <span data-ttu-id="d1652-201">ValidatePattern permite usar una expresión regular para restringir los argumentos del parámetro si no resulta sencillo definir un conjunto de valores permitidos.</span><span class="sxs-lookup"><span data-stu-id="d1652-201">The ValidatePattern allows you to use a regular expression to restrict parameter arguments if it is not easy to define a set of allowable values.</span></span>
<span data-ttu-id="d1652-202">No puede definir ValidatePattern y ValidateSet para un solo parámetro.</span><span class="sxs-lookup"><span data-stu-id="d1652-202">You cannot define both a ValidatePattern and ValidateSet for a single parameter.</span></span>

## <a name="step-5-register-a-new-session-configuration"></a><span data-ttu-id="d1652-203">Paso 5: registrar una nueva configuración de sesión</span><span class="sxs-lookup"><span data-stu-id="d1652-203">Step 5: Register a new Session Configuration</span></span>
<span data-ttu-id="d1652-204">A continuación, creará un nuevo archivo de configuración de sesión que expondrá la funcionalidad de rol a los miembros del grupo "JEA_NonAdmin_HelpDesk" de AD.</span><span class="sxs-lookup"><span data-stu-id="d1652-204">Next, you will create a new session configuration file that will expose your Role Capability to members of the "JEA_NonAdmin_HelpDesk" AD group.</span></span>

<span data-ttu-id="d1652-205">Primero cree y abra un nuevo archivo de configuración de sesión en blanco en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d1652-205">Start by creating and opening a new blank Session Configuration file in PowerShell ISE.</span></span>
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
<span data-ttu-id="d1652-206">Modifique los campos siguientes en el archivo PSSC.</span><span class="sxs-lookup"><span data-stu-id="d1652-206">Modify the following fields in the PSSC file.</span></span>
<span data-ttu-id="d1652-207">Si trabaja en su propio entorno, debe reemplazar "CONTOSO\JEA_NonAdmins_Helpdesk" por su propio usuario o grupo sin privilegios de administrador.</span><span class="sxs-lookup"><span data-stu-id="d1652-207">If you are working in your own environment, you should replace "CONTOSO\JEA_NonAdmins_Helpdesk" with your own non-administrator user or group.</span></span>
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
<span data-ttu-id="d1652-208">Guarde y registre la configuración de sesión.</span><span class="sxs-lookup"><span data-stu-id="d1652-208">Save and register the Session Configuration</span></span>
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## <a name="test-it-out"></a><span data-ttu-id="d1652-209">Pruébela</span><span class="sxs-lookup"><span data-stu-id="d1652-209">Test It Out!</span></span>
<span data-ttu-id="d1652-210">Obtenga las credenciales de usuario sin privilegios de administrador:</span><span class="sxs-lookup"><span data-stu-id="d1652-210">Get your non-administrator user credentials:</span></span>
```PowerShell
$HelpDeskCred = Get-Credential
```
<span data-ttu-id="d1652-211">Si ha seguido la sección [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) (Configuración de usuarios y grupos), las credenciales serán:</span><span class="sxs-lookup"><span data-stu-id="d1652-211">If you followed the [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) section, the credentials will be:</span></span>
-   <span data-ttu-id="d1652-212">Nombre de usuario = "HelpDeskUser"</span><span class="sxs-lookup"><span data-stu-id="d1652-212">Username = "HelpDeskUser"</span></span>
-   <span data-ttu-id="d1652-213">Contraseña = "pa$$w0rd"</span><span class="sxs-lookup"><span data-stu-id="d1652-213">Password = "pa$$w0rd"</span></span>

<span data-ttu-id="d1652-214">Obtenga acceso de manera remota al punto de conexión del departamento de soporte técnico de AD mediante la credencial sin privilegios de administrador:</span><span class="sxs-lookup"><span data-stu-id="d1652-214">Remote into the ADHelpdesk endpoint using the non-admin credential:</span></span>
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
<span data-ttu-id="d1652-215">Use Set-ADUser para restablecer el cargo de un usuario.</span><span class="sxs-lookup"><span data-stu-id="d1652-215">Use Set-ADUser to reset a user's title.</span></span>
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
<span data-ttu-id="d1652-216">Compruebe que el cargo ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="d1652-216">Verify that the title has changed.</span></span>
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
<span data-ttu-id="d1652-217">Ahora, use Add-ADGroupMember para agregar un usuario a TestGroup.</span><span class="sxs-lookup"><span data-stu-id="d1652-217">Now, use Add-ADGroupMember to add a user to the TestGroup.</span></span>
<span data-ttu-id="d1652-218">Nota: Asegúrese de haber creado con antelación el grupo denominado TestGroup.</span><span class="sxs-lookup"><span data-stu-id="d1652-218">Note: make sure you've created the TestGroup beforehand.</span></span>
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
<span data-ttu-id="d1652-219">Salga de la sesión:</span><span class="sxs-lookup"><span data-stu-id="d1652-219">Exit the session:</span></span>
```PowerShell
Exit-PSSession
```
## <a name="key-concepts"></a><span data-ttu-id="d1652-220">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="d1652-220">Key Concepts</span></span>
<span data-ttu-id="d1652-221">**Modo NoLanguage**: cuando PowerShell está en modo "NoLanguage", los usuarios solo pueden ejecutar comandos; no pueden usar elementos del lenguaje.</span><span class="sxs-lookup"><span data-stu-id="d1652-221">**NoLanguage Mode**: When PowerShell is in "NoLanguage" mode, users may only run commands; they cannot use any language elements.</span></span>
<span data-ttu-id="d1652-222">Para más información, vea `Get-Help about_Language_Modes`.</span><span class="sxs-lookup"><span data-stu-id="d1652-222">For more information, run `Get-Help about_Language_Modes`.</span></span>

<span data-ttu-id="d1652-223">**Funciones de PowerShell**: las funciones de PowerShell son fragmentos de código de PowerShell que se puede llamar por su nombre.</span><span class="sxs-lookup"><span data-stu-id="d1652-223">**PowerShell Functions**: PowerShell functions are bits of PowerShell code that you can call by name.</span></span>
<span data-ttu-id="d1652-224">Para más información, vea `Get-Help about_Functions`.</span><span class="sxs-lookup"><span data-stu-id="d1652-224">For more information, run `Get-Help about_Functions`.</span></span>

<span data-ttu-id="d1652-225">**ValidateSet/ValidatePattern**: al exponer un comando, puede restringir los argumentos válidos para parámetros específicos.</span><span class="sxs-lookup"><span data-stu-id="d1652-225">**ValidateSet/ValidatePattern**: When exposing a command, you can restrict valid arguments for specific parameters.</span></span>
<span data-ttu-id="d1652-226">ValidateSet es una lista específica de argumentos válidos.</span><span class="sxs-lookup"><span data-stu-id="d1652-226">A ValidateSet is a specific list of valid arguments.</span></span>
<span data-ttu-id="d1652-227">ValidatePattern es una expresión regular con la que deben coincidir los argumentos de ese parámetro.</span><span class="sxs-lookup"><span data-stu-id="d1652-227">A ValidatePattern is a regular expression that the arguments for that parameter must match.</span></span>

