---
title: Ejemplos de ayuda basada en comentarios | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: 30e98bfcf06b1720005a73ee8294aeba7e1ae066
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367824"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="2c558-102">Ejemplos de la Ayuda basada en comentarios</span><span class="sxs-lookup"><span data-stu-id="2c558-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="2c558-103">En este tema se incluye un ejemplo que muestra cómo usar la ayuda basada en comentarios para scripts y funciones.</span><span class="sxs-lookup"><span data-stu-id="2c558-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="2c558-104">Ejemplo 1: ayuda basada en comentarios para una función</span><span class="sxs-lookup"><span data-stu-id="2c558-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="2c558-105">La siguiente función de ejemplo incluye ayuda basada en Comentarios.</span><span class="sxs-lookup"><span data-stu-id="2c558-105">The following sample function includes comment-based Help.</span></span>

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="2c558-106">En el resultado siguiente se muestran los resultados de un comando Get-Help que muestra la ayuda de la función Add-Extension.</span><span class="sxs-lookup"><span data-stu-id="2c558-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="2c558-107">Ejemplo 2: ayuda basada en comentarios para un script</span><span class="sxs-lookup"><span data-stu-id="2c558-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="2c558-108">La siguiente función de ejemplo incluye ayuda basada en Comentarios.</span><span class="sxs-lookup"><span data-stu-id="2c558-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="2c558-109">Observe las líneas en blanco entre el **#>** de cierre y la instrucción `Param`.</span><span class="sxs-lookup"><span data-stu-id="2c558-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="2c558-110">En un script que no tiene una instrucción `Param`, debe haber al menos dos líneas en blanco entre el comentario final en el tema de ayuda y la primera declaración de función.</span><span class="sxs-lookup"><span data-stu-id="2c558-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="2c558-111">Sin estas líneas en blanco, Get-Help asocia el tema de ayuda a la función, en lugar del script.</span><span class="sxs-lookup"><span data-stu-id="2c558-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="2c558-112">El siguiente comando obtiene la ayuda del script.</span><span class="sxs-lookup"><span data-stu-id="2c558-112">The following command gets the script Help.</span></span> <span data-ttu-id="2c558-113">Dado que el script no es un directorio que aparece en la variable de entorno PATH, el comando Get-Help que obtiene la ayuda de script debe especificar la ruta de acceso del script.</span><span class="sxs-lookup"><span data-stu-id="2c558-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="2c558-114">Ejemplo 3: descripciones de parámetros en una instrucción param</span><span class="sxs-lookup"><span data-stu-id="2c558-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="2c558-115">En este ejemplo se muestra cómo insertar parameterdescriptions en la instrucción `Param` de una función o un script.</span><span class="sxs-lookup"><span data-stu-id="2c558-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="2c558-116">Este formato es muy útil cuando las descripciones de los parámetros son breves.</span><span class="sxs-lookup"><span data-stu-id="2c558-116">This format is most useful when the parameter descriptions are brief.</span></span>

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

<span data-ttu-id="2c558-117">Los resultados son los mismos que en el ejemplo 1.</span><span class="sxs-lookup"><span data-stu-id="2c558-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="2c558-118">Get-Help interpreta las descripciones de los parámetros como si estuvieran acompañados de la palabra clave `.Parameter`.</span><span class="sxs-lookup"><span data-stu-id="2c558-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="2c558-119">Ejemplo 4: redirigir a un archivo XML</span><span class="sxs-lookup"><span data-stu-id="2c558-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="2c558-120">Puede escribir temas de ayuda basados en XML para funciones y scripts.</span><span class="sxs-lookup"><span data-stu-id="2c558-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="2c558-121">Aunque la ayuda basada en comentarios es más fácil de implementar, es necesaria la ayuda basada en XML si desea tener un control más preciso sobre el contenido de la ayuda o si va a traducir los temas de ayuda en varios idiomas. En el ejemplo siguiente se muestran las primeras líneas del script Update-Month. ps1.</span><span class="sxs-lookup"><span data-stu-id="2c558-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="2c558-122">El script usa la palabra clave `.ExternalHelp` para especificar la ruta de acceso a un tema de ayuda basado en XML para el script.</span><span class="sxs-lookup"><span data-stu-id="2c558-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="2c558-123">En el ejemplo siguiente se muestra el uso de la palabra clave `.ExternalHelp` en una función.</span><span class="sxs-lookup"><span data-stu-id="2c558-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="2c558-124">Ejemplo 5: redirigir a un tema de ayuda diferente</span><span class="sxs-lookup"><span data-stu-id="2c558-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="2c558-125">El código siguiente es un extracto desde el principio de la función integrada `Help` en Windows PowerShell, que muestra una pantalla de texto de ayuda cada vez.</span><span class="sxs-lookup"><span data-stu-id="2c558-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="2c558-126">Dado que el tema de ayuda del cmdlet Get-Help describe la función Help, la función Help usa las palabras clave `.ForwardHelpTargetName` y `.ForwardHelpCategory` para redirigir al usuario al tema de ayuda del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="2c558-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

<span data-ttu-id="2c558-127">El siguiente comando usa esta característica.</span><span class="sxs-lookup"><span data-stu-id="2c558-127">The following command uses this feature.</span></span> <span data-ttu-id="2c558-128">Cuando un usuario escribe un comando get-help para la función de ayuda, Get-Help muestra el tema de ayuda para el cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="2c558-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```