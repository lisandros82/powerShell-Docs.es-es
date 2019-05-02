---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Escribir ayuda para configuraciones de DSC
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080193"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="009cc-103">Escribir ayuda para configuraciones de DSC</span><span class="sxs-lookup"><span data-stu-id="009cc-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="009cc-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="009cc-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="009cc-105">Puede usar la ayuda basada en comentarios en configuraciones de DSC.</span><span class="sxs-lookup"><span data-stu-id="009cc-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="009cc-106">Los usuarios pueden acceder a la ayuda mediante una llamada a la **configuración** con `-?`, o mediante el cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="009cc-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="009cc-107">Coloque la ayuda basada en comentarios directamente encima de la palabra clave `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="009cc-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="009cc-108">Puede colocar la ayuda de parámetro en línea con el bloque de comentario, justo encima de la declaración de parámetros o en ambos lugares, como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="009cc-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="009cc-109">Para obtener más información sobre la ayuda basada en comentarios de PowerShell, vea [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="009cc-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="009cc-110">Los entornos de desarrollo de PowerShell, como VSCode y el ISE, también tienen fragmentos de código para que pueda insertar automáticamente las plantillas de bloque de comentario.</span><span class="sxs-lookup"><span data-stu-id="009cc-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="009cc-111">En el ejemplo siguiente se muestran un script que contiene una configuración y ayuda basada en comentarios para dicha configuración.</span><span class="sxs-lookup"><span data-stu-id="009cc-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="009cc-112">En este ejemplo se muestra una configuración con parámetros.</span><span class="sxs-lookup"><span data-stu-id="009cc-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="009cc-113">Para obtener más información sobre cómo usar parámetros en las configuraciones, consulte [Agregar parámetros a una configuración](add-parameters-to-a-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="009cc-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="009cc-114">Ver la ayuda de configuración</span><span class="sxs-lookup"><span data-stu-id="009cc-114">Viewing configuration help</span></span>

<span data-ttu-id="009cc-115">Para ver la ayuda de una configuración, use el cmdlet `Get-Help` con el nombre de la función o escriba el nombre de la función seguido de `-?`.</span><span class="sxs-lookup"><span data-stu-id="009cc-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="009cc-116">A continuación, se muestra el resultado de la configuración anterior cuando se pasa a `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="009cc-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="009cc-117">Los campos de la sintaxis y los atributos de parámetro se generan automáticamente mediante PowerShell.</span><span class="sxs-lookup"><span data-stu-id="009cc-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="009cc-118">Véase también</span><span class="sxs-lookup"><span data-stu-id="009cc-118">See Also</span></span>

- [<span data-ttu-id="009cc-119">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="009cc-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="009cc-120">Escritura, compilación y aplicación de una configuración</span><span class="sxs-lookup"><span data-stu-id="009cc-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="009cc-121">Adición parámetros a una configuración</span><span class="sxs-lookup"><span data-stu-id="009cc-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
