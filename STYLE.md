# <a name="style-guide-for-powershell-docs"></a><span data-ttu-id="cab89-101">Guía de estilo para PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="cab89-101">Style guide for PowerShell-Docs</span></span>


## <a name="titlesheadings"></a><span data-ttu-id="cab89-102">Títulos y encabezados</span><span class="sxs-lookup"><span data-stu-id="cab89-102">Titles/Headings</span></span>

* <span data-ttu-id="cab89-103">Los títulos y encabezados (todo antecedido por \#) deben ir seguidos de una línea nueva</span><span class="sxs-lookup"><span data-stu-id="cab89-103">Titles/headings (anything preprended by \#) should be followed with a newline</span></span>
* <span data-ttu-id="cab89-104">Solo se debe poner en mayúsculas la primera letra de un título y de todos los nombres propios de ese título</span><span class="sxs-lookup"><span data-stu-id="cab89-104">Only the first letter of a title and any proper nouns in that title should be capitalized</span></span>
* <span data-ttu-id="cab89-105">Solo 1 H1 por documento</span><span class="sxs-lookup"><span data-stu-id="cab89-105">Only 1 H1 per document</span></span>
* <span data-ttu-id="cab89-106">Al editar el contenido de referencia, platyPS recomienda H2 y no se deben agregar o quitar, ya que provocaría una interrupción de la compilación</span><span class="sxs-lookup"><span data-stu-id="cab89-106">When editing reference content, the H2s are prescribed by platyPS and should not be added or removed as it will cause a build break</span></span>
* <span data-ttu-id="cab89-107">Use solo \# encabezados de estilo (en lugar de = o encabezados de estilo \-)</span><span class="sxs-lookup"><span data-stu-id="cab89-107">Only use \# style headers (as opposed to = or \- style headers)</span></span>

### <a name="correct"></a><span data-ttu-id="cab89-108">Correcto</span><span class="sxs-lookup"><span data-stu-id="cab89-108">Correct</span></span>

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a><span data-ttu-id="cab89-109">Incorrecto</span><span class="sxs-lookup"><span data-stu-id="cab89-109">Incorrect</span></span>

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a><span data-ttu-id="cab89-110">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cab89-110">Syntax</span></span>

* <span data-ttu-id="cab89-111">Cuando hablamos de un cmdlet en el párrafo, utilice \\` para resaltar los nombres de cmdlet</span><span class="sxs-lookup"><span data-stu-id="cab89-111">When talking about a cmdlet in paragraph, use \\` to highlight cmdlet names</span></span>
  * <span data-ttu-id="cab89-112">Ejemplo correcto: Este cmdlet `Write-Host` puede ...</span><span class="sxs-lookup"><span data-stu-id="cab89-112">Correct Example: This `Write-Host` Cmdlet can ...</span></span>
  * <span data-ttu-id="cab89-113">Ejemplo incorrecto: Este cmdlet **Write-Host** puede ... y canalizar en el cmdlet out-file para ...</span><span class="sxs-lookup"><span data-stu-id="cab89-113">Incorrect Example: This **Write-Host** Cmdlet can ... and pipeline to out-file Cmdlet to ...</span></span>
* <span data-ttu-id="cab89-114">Al escribir un artículo (en lugar de contenido de referencia), la primera instancia de un nombre de cmdlet debe ser un vínculo a la documentación de dicho cmdlet</span><span class="sxs-lookup"><span data-stu-id="cab89-114">When writing an article (as opposed to reference content), the first instance of a cmdlet name should be a link to the cmdlet documentation</span></span>
* <span data-ttu-id="cab89-115">Todos los bloques de sintaxis de PowerShell deben usar &#96;&#96;&#96;powershell</span><span class="sxs-lookup"><span data-stu-id="cab89-115">All PowerShell syntax blocks should use &#96;&#96;&#96;powershell</span></span>
* <span data-ttu-id="cab89-116">No inicie comandos de PowerShell con "`PS C:\>`"</span><span class="sxs-lookup"><span data-stu-id="cab89-116">Do not start PowerShell commands with "`PS C:\>`"</span></span>
  * <span data-ttu-id="cab89-117">Ejemplo correcto:</span><span class="sxs-lookup"><span data-stu-id="cab89-117">Correct Example:</span></span>
  ```powershell
  Get-Process
  ```
  * <span data-ttu-id="cab89-118">Ejemplo incorrecto:</span><span class="sxs-lookup"><span data-stu-id="cab89-118">Incorrect Example:</span></span>
  ```powershell
  PS C:\> Get-Process
  ```
* <span data-ttu-id="cab89-119">La salida emitida por comandos de PowerShell debe incluir comentarios para evitar que reciba el resaltado de sintaxis</span><span class="sxs-lookup"><span data-stu-id="cab89-119">Output emitted by PowerShell commands should be commented to prevent it from recieving syntax highlighting</span></span>
* <span data-ttu-id="cab89-120">Los nombres de propiedad y de parámetro deben estar en **negrita**</span><span class="sxs-lookup"><span data-stu-id="cab89-120">Property names and parameter names should be in **bold**</span></span>
* <span data-ttu-id="cab89-121">Los cmdlets de PowerShell usan la [grafía Pascal](https://en.wikipedia.org/wiki/PascalCase).</span><span class="sxs-lookup"><span data-stu-id="cab89-121">PowerShell cmdlets are "[Pascal Cased](https://en.wikipedia.org/wiki/PascalCase)".</span></span> <span data-ttu-id="cab89-122">Los verbos se separan de los sustantivos con un guión.</span><span class="sxs-lookup"><span data-stu-id="cab89-122">Verbs are seperated from nouns by a hyphen.</span></span>

## <a name="lists"></a><span data-ttu-id="cab89-123">Listas</span><span class="sxs-lookup"><span data-stu-id="cab89-123">Lists</span></span>

* <span data-ttu-id="cab89-124">No terminar elementos de lista con un punto (a menos que contengan varias oraciones)</span><span class="sxs-lookup"><span data-stu-id="cab89-124">Do not end list items with a period (unless they contain multiple sentences)</span></span>
* <span data-ttu-id="cab89-125">Si la lista contiene varias oraciones, considere la posibilidad de usar un encabezado 3/4/5 (según corresponda) debajo de la idea principal</span><span class="sxs-lookup"><span data-stu-id="cab89-125">If your list contains multiple sentences, consider using a header 3/4/5 (as applicable) underneath your primary idea</span></span>

## <a name="links"></a><span data-ttu-id="cab89-126">Vínculos</span><span class="sxs-lookup"><span data-stu-id="cab89-126">Links</span></span>

* <span data-ttu-id="cab89-127">Los vínculos siempre se marcan mediante la sintaxis MarkDown `[friendlyname](url)`</span><span class="sxs-lookup"><span data-stu-id="cab89-127">Links are always marked up using MarkDown syntax `[friendlyname](url)`</span></span>
* <span data-ttu-id="cab89-128">Los vínculos deben tener un nombre descriptivo cuando sea posible, muy probablemente el título de la página vinculada</span><span class="sxs-lookup"><span data-stu-id="cab89-128">Links should have a a friendly name when applicable, most likely the title of the linked page</span></span>
  * <span data-ttu-id="cab89-129">**Excepción**: vínculos hacia los sitios que no son de Microsoft solo deben tener una dirección URL</span><span class="sxs-lookup"><span data-stu-id="cab89-129">**Exception**: Links going towards non-Microsoft sites should only have a URL</span></span>
* <span data-ttu-id="cab89-130">Todos los elementos de la sección "vínculos relacionados" que se encuentra en la parte inferior deben ser hipervínculos.</span><span class="sxs-lookup"><span data-stu-id="cab89-130">All items in the "related links" section at the bottom should be hyperlinked.</span></span> 

## <a name="line-breaks"></a><span data-ttu-id="cab89-131">Saltos de línea</span><span class="sxs-lookup"><span data-stu-id="cab89-131">Line breaks</span></span>

* <span data-ttu-id="cab89-132">Debe incluir saltos de línea semánticos</span><span class="sxs-lookup"><span data-stu-id="cab89-132">You must include semantic line breaks</span></span>
* <span data-ttu-id="cab89-133">Debe limitar las líneas a 100 caracteres (elemento abierto: herramientas para ayudarnos a validar esto)</span><span class="sxs-lookup"><span data-stu-id="cab89-133">You should limit lines to 100char (Open item: tooling to help us validate this)</span></span>
* <span data-ttu-id="cab89-134">PUEDE quitar saltos de línea adicionales de PS4 +, NO ps3 (necesita validarse)</span><span class="sxs-lookup"><span data-stu-id="cab89-134">You CAN remove additional line breaks for PS4+, NOT ps3 (needs validation)</span></span>
