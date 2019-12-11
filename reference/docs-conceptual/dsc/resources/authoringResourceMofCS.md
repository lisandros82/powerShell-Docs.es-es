---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Creación de un recurso de DSC en C#
ms.openlocfilehash: a19559c225dd91eceed397df91dd584a577cd7d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417698"
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="3b02c-103">Creación de un recurso de DSC en C\#</span><span class="sxs-lookup"><span data-stu-id="3b02c-103">Authoring a DSC resource in C\#</span></span>

> <span data-ttu-id="3b02c-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3b02c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="3b02c-105">Normalmente, un recurso personalizado de configuración de estado deseado (DSC) de Windows PowerShell se implementa en un script de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b02c-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="3b02c-106">Sin embargo, también puede implementar la funcionalidad de un recurso de DSC personalizado mediante la escritura de cmdlets en C#.</span><span class="sxs-lookup"><span data-stu-id="3b02c-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="3b02c-107">Para ver una introducción sobre la escritura de cmdlets en C#, consulte [Escribir un cmdlet de Windows PowerShell](/powershell/scripting/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3b02c-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](/powershell/scripting/developer/windows-powershell).</span></span>

<span data-ttu-id="3b02c-108">Además de implementar el recurso en C# como cmdlets, el proceso de creación del esquema MOF, la creación de la estructura de carpetas, la importación y la utilización del recurso personalizado de DSC son idénticos a cómo se describen en [Escribir un recurso de DSC personalizado con MOF](authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="3b02c-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="3b02c-109">Escribir un recurso basado en cmdlets</span><span class="sxs-lookup"><span data-stu-id="3b02c-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="3b02c-110">En este ejemplo, se implementará un recurso simple que administra un archivo de texto y su contenido.</span><span class="sxs-lookup"><span data-stu-id="3b02c-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="3b02c-111">Escribir el esquema MOF</span><span class="sxs-lookup"><span data-stu-id="3b02c-111">Writing the MOF schema</span></span>

<span data-ttu-id="3b02c-112">A continuación se muestra la definición del recurso MOF.</span><span class="sxs-lookup"><span data-stu-id="3b02c-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="3b02c-113">Configurar el proyecto de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b02c-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="3b02c-114">Configurar un proyecto de cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b02c-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="3b02c-115">Abra Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b02c-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="3b02c-116">Cree un proyecto de C# y proporcione el nombre.</span><span class="sxs-lookup"><span data-stu-id="3b02c-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="3b02c-117">Seleccione **Biblioteca de clases** en las plantillas de proyecto disponibles.</span><span class="sxs-lookup"><span data-stu-id="3b02c-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="3b02c-118">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="3b02c-118">Click **Ok**.</span></span>
1. <span data-ttu-id="3b02c-119">Agregue al proyecto una referencia de ensamblado a System.Automation.Management.dll.</span><span class="sxs-lookup"><span data-stu-id="3b02c-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="3b02c-120">Cambie el nombre del ensamblado para que coincida con el nombre del recurso.</span><span class="sxs-lookup"><span data-stu-id="3b02c-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="3b02c-121">En este caso, el ensamblado debe tener como nombre **MSFT_XDemoFile**.</span><span class="sxs-lookup"><span data-stu-id="3b02c-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="3b02c-122">Escribir el código del cmdlet</span><span class="sxs-lookup"><span data-stu-id="3b02c-122">Writing the cmdlet code</span></span>

<span data-ttu-id="3b02c-123">El siguiente código de C# implementa los cmdlets **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="3b02c-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a><span data-ttu-id="3b02c-124">Implementar el recurso</span><span class="sxs-lookup"><span data-stu-id="3b02c-124">Deploying the resource</span></span>

<span data-ttu-id="3b02c-125">El archivo dll compilado debe guardarse en una estructura de archivos similar a un recurso de script.</span><span class="sxs-lookup"><span data-stu-id="3b02c-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="3b02c-126">A continuación se muestra la estructura de carpetas de este recurso.</span><span class="sxs-lookup"><span data-stu-id="3b02c-126">The following is the folder structure for this resource.</span></span>

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a><span data-ttu-id="3b02c-127">Véase también</span><span class="sxs-lookup"><span data-stu-id="3b02c-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="3b02c-128">Conceptos</span><span class="sxs-lookup"><span data-stu-id="3b02c-128">Concepts</span></span>
[<span data-ttu-id="3b02c-129">Escribir un recurso de DSC personalizado con MOF</span><span class="sxs-lookup"><span data-stu-id="3b02c-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="3b02c-130">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="3b02c-130">Other Resources</span></span>
[<span data-ttu-id="3b02c-131">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b02c-131">Writing a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/windows-powershell)
