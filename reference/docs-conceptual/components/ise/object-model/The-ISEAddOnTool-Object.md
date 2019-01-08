---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto ISEAddOnTool
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: e091f37601c7a4fdaf5deff8c668b18ee7369e74
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403320"
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="81c41-103">El objeto ISEAddOnTool</span><span class="sxs-lookup"><span data-stu-id="81c41-103">The ISEAddOnTool Object</span></span>

<span data-ttu-id="81c41-104">Un objeto **ISEAddonTool** representa una herramienta de complemento instalada que proporciona funcionalidad adicional a Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="81c41-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="81c41-105">Un ejemplo es la herramienta **Comandos** que se puede mostrar haciendo clic en **Ver** y, después, en **Show Command Add-on** (Mostrar complemento Comandos).</span><span class="sxs-lookup"><span data-stu-id="81c41-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="81c41-106">Esta herramienta es accesible mediante la manipulación de los distintos objetos **ISEAddOnTool** disponibles.</span><span class="sxs-lookup"><span data-stu-id="81c41-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

<span data-ttu-id="81c41-107">Cada herramienta de complemento se puede asociar al panel vertical o al panel horizontal.</span><span class="sxs-lookup"><span data-stu-id="81c41-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="81c41-108">El panel vertical está acoplado al borde derecho de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="81c41-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="81c41-109">El panel horizontal está acoplado al borde inferior.</span><span class="sxs-lookup"><span data-stu-id="81c41-109">The horizontal pane is docked to the bottom edge.</span></span>

<span data-ttu-id="81c41-110">Cada pestaña de PowerShell en Windows PowerShell ISE puede tener instalado su propio conjunto de herramientas de complemento.</span><span class="sxs-lookup"><span data-stu-id="81c41-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="81c41-111">Consulte [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) y [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) para tener acceso a la colección de herramientas disponibles en la pestaña seleccionada actualmente o las mismas propiedades en cualquiera de los objetos **PowerShellTab** del objeto de la colección [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md).</span><span class="sxs-lookup"><span data-stu-id="81c41-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="81c41-112">Métodos</span><span class="sxs-lookup"><span data-stu-id="81c41-112">Methods</span></span>

<span data-ttu-id="81c41-113">No hay disponible ningún método específico de Windows PowerShell ISE para los objetos de esta clase.</span><span class="sxs-lookup"><span data-stu-id="81c41-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="81c41-114">Propiedades</span><span class="sxs-lookup"><span data-stu-id="81c41-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="81c41-115">Control</span><span class="sxs-lookup"><span data-stu-id="81c41-115">Control</span></span>

<span data-ttu-id="81c41-116">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="81c41-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="81c41-117">La propiedad **Control** proporciona acceso de lectura a muchos de los detalles de la herramienta de complemento Comandos.</span><span class="sxs-lookup"><span data-stu-id="81c41-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

```powershell
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher
```

### <a name="isvisible"></a><span data-ttu-id="81c41-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="81c41-118">IsVisible</span></span>

<span data-ttu-id="81c41-119">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="81c41-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="81c41-120">Propiedad booleana que indica si la herramienta de complemento está visible actualmente en el panel asignado.</span><span class="sxs-lookup"><span data-stu-id="81c41-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="81c41-121">Si está visible, puede establecer la propiedad **IsVisible** en **$false** para ocultar la herramienta o establecer la propiedad **IsVisible** en **$true** para hacer que una herramienta de complemento esté visible en su pestaña de PowerShell. Tenga en cuenta que al ocultar una herramienta de complemento, esta deja de ser accesible a través de los objetos **CurrentVisibleHorizontalTool** o **CurrentVisibleVerticalTool** y, por lo tanto, no puede hacerse visible usando esta propiedad en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="81c41-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```powershell
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible = $true
```

### <a name="name"></a><span data-ttu-id="81c41-122">Nombre</span><span class="sxs-lookup"><span data-stu-id="81c41-122">Name</span></span>

<span data-ttu-id="81c41-123">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="81c41-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="81c41-124">Propiedad de solo lectura que obtiene el nombre de la herramienta de complemento.</span><span class="sxs-lookup"><span data-stu-id="81c41-124">The read-only property that gets the name of the add-on tool.</span></span>

```powershell
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.Name
Commands
```

## <a name="see-also"></a><span data-ttu-id="81c41-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="81c41-125">See Also</span></span>

- [<span data-ttu-id="81c41-126">El objeto ISEAddOnToolCollection</span><span class="sxs-lookup"><span data-stu-id="81c41-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="81c41-127">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="81c41-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="81c41-128">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="81c41-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)