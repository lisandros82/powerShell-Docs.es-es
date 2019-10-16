---
title: Creación de un cmdlet para obtener acceso a un almacén de datos
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 7acccbd48dcfb654b11e448a1f24835ad3668fae
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365724"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Creación de un cmdlet para obtener acceso a un almacén de datos

En esta sección se describe cómo crear un cmdlet que acceda a los datos almacenados mediante un proveedor de Windows PowerShell. Este tipo de cmdlet usa la infraestructura del proveedor de Windows PowerShell del tiempo de ejecución de Windows PowerShell y, por lo tanto, la clase de cmdlet debe derivar de la clase base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

El cmdlet Select-Str que se describe aquí puede buscar y seleccionar cadenas en un archivo u objeto. Los patrones que se usan para identificar la cadena se pueden especificar explícitamente mediante el parámetro `Path` del cmdlet o implícitamente a través del parámetro `Script`.

El cmdlet está diseñado para usar cualquier proveedor de Windows PowerShell que derive de [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider). Por ejemplo, el cmdlet puede especificar el proveedor del sistema de archivos o el proveedor de variables proporcionado por Windows PowerShell. Para más información aboutWindows los proveedores de PowerShell, consulte [diseño del proveedor de Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md).

## <a name="defining-the-cmdlet-class"></a>Definir la clase de cmdlet

El primer paso en la creación de un cmdlet es siempre nombrar el cmdlet y declarar la clase .NET que implementa el cmdlet. Este cmdlet detecta ciertas cadenas, por lo que el nombre del verbo elegido aquí es "Select", definido por la clase [System. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) . El nombre de sustantivo "STR" se usa porque el cmdlet actúa en las cadenas. En la declaración siguiente, tenga en cuenta que el verbo de cmdlet y el nombre de sustantivo se reflejan en el nombre de la clase de cmdlet. Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

La clase .NET de este cmdlet debe derivarse de la clase base [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) , ya que proporciona la compatibilidad necesaria para que el motor en tiempo de ejecución de Windows PowerShell exponga la infraestructura del proveedor de Windows PowerShell. Tenga en cuenta que este cmdlet también hace uso de las clases de expresiones regulares .NET Framework, como [System. Text. RegularExpressions. Regex](/dotnet/api/System.Text.RegularExpressions.Regex).

El código siguiente es la definición de clase de este cmdlet Select-Str.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

Este cmdlet define un conjunto de parámetros predeterminado agregando la palabra clave del atributo `DefaultParameterSetName` a la declaración de clase. Se usa el conjunto de parámetros predeterminado `PatternParameterSet` cuando no se especifica el parámetro `Script`. Para obtener más información sobre este conjunto de parámetros, vea la descripción de los parámetros `Pattern` y `Script` en la sección siguiente.

## <a name="defining-parameters-for-data-access"></a>Definir parámetros para el acceso a datos

Este cmdlet define varios parámetros que permiten al usuario obtener acceso a los datos almacenados y examinarlos. Estos parámetros incluyen un parámetro `Path` que indica la ubicación del almacén de datos, un parámetro `Pattern` que especifica el patrón que se va a usar en la búsqueda y otros parámetros que admiten el modo en que se realiza la búsqueda.

> [!NOTE]
> Para obtener más información sobre los conceptos básicos de la definición de parámetros, vea [agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md).

### <a name="declaring-the-path-parameter"></a>Declarar el parámetro Path

Para buscar el almacén de datos, este cmdlet debe usar una ruta de acceso de Windows PowerShell para identificar el proveedor de Windows PowerShell que está diseñado para acceder al almacén de datos. Por lo tanto, define un parámetro `Path` de la matriz de cadenas de tipo para indicar la ubicación del proveedor.

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

Tenga en cuenta que este parámetro pertenece a dos conjuntos de parámetros diferentes y que tiene un alias.

Dos atributos [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaran que el parámetro `Path` pertenece al `ScriptParameterSet` y `PatternParameterSet`. Para obtener más información sobre los conjuntos de parámetros, vea [Agregar conjuntos de parámetros a un cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

El atributo [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) declara un alias `PSPath` para el parámetro `Path`. Se recomienda encarecidamente declarar este alias para la coherencia con otros cmdlets que tienen acceso a los proveedores de Windows PowerShell. Para más información aboutWindows las rutas de acceso de PowerShell, consulte "conceptos de la ruta de PowerShell" en [Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="declaring-the-pattern-parameter"></a>Declarar el parámetro Pattern

Para especificar los patrones que se van a buscar, este cmdlet declara un parámetro `Pattern` que es una matriz de cadenas. Se devuelve un resultado positivo cuando se encuentra cualquiera de los patrones en el almacén de datos. Tenga en cuenta que estos patrones se pueden compilar en una matriz de expresiones regulares compiladas o en una matriz de patrones comodín que se usan para las búsquedas literales.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

Cuando se especifica este parámetro, el cmdlet usa el conjunto de parámetros predeterminado `PatternParameterSet`. En este caso, el cmdlet usa los patrones especificados aquí para seleccionar cadenas. Por el contrario, el parámetro `Script` también podría usarse para proporcionar un script que contenga los patrones. Los parámetros `Script` y `Pattern` definen dos conjuntos de parámetros independientes, por lo que son mutuamente excluyentes.

### <a name="declaring-search-support-parameters"></a>Declarar parámetros de compatibilidad de búsqueda

Este cmdlet define los siguientes parámetros de soporte técnico que se pueden usar para modificar las capacidades de búsqueda del cmdlet.

El parámetro `Script` especifica un bloque de script que se puede usar para proporcionar un mecanismo de búsqueda alternativo para el cmdlet. El script debe contener los patrones que se usan para buscar coincidencias y devolver un objeto [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) . Tenga en cuenta que este parámetro es también el parámetro único que identifica el conjunto de parámetros `ScriptParameterSet`. Cuando el tiempo de ejecución de Windows PowerShell ve este parámetro, solo usa los parámetros que pertenecen al conjunto de parámetros `ScriptParameterSet`.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

El parámetro `SimpleMatch` es un parámetro de modificador que indica si el cmdlet debe coincidir explícitamente con los patrones a medida que se proporcionan. Cuando el usuario especifica el parámetro en la línea de comandos (`true`), el cmdlet usa los patrones a medida que se proporcionan. Si no se especifica el parámetro (`false`), el cmdlet usa expresiones regulares. El valor predeterminado de este parámetro es `false`.

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

El parámetro `CaseSensitive` es un parámetro de modificador que indica si se realiza una búsqueda con distinción de mayúsculas y minúsculas. Cuando el usuario especifica el parámetro en la línea de comandos (`true`), el cmdlet comprueba si hay caracteres en mayúsculas y minúsculas al comparar patrones. Si no se especifica el parámetro (`false`), el cmdlet no distingue entre mayúsculas y minúsculas. Por ejemplo, "Perfile" y "Perfile" se devolverían como aciertos positivos. El valor predeterminado de este parámetro es `false`.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

Los parámetros `Exclude` y `Include` identifican los elementos que se excluyen explícitamente o se incluyen en la búsqueda. De forma predeterminada, el cmdlet buscará en todos los elementos del almacén de datos. Sin embargo, para limitar la búsqueda realizada por el cmdlet, estos parámetros se pueden usar para indicar explícitamente que los elementos que se van a incluir en la búsqueda se han omitido.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a>Declarar conjuntos de parámetros

Este cmdlet usa dos conjuntos de parámetros (`ScriptParameterSet` y `PatternParameterSet`, que es el valor predeterminado), como los nombres de dos conjuntos de parámetros que se usan en el acceso a datos. `PatternParameterSet` es el conjunto de parámetros predeterminado y se usa cuando se especifica el parámetro `Pattern`. `ScriptParameterSet` se usa cuando el usuario especifica un mecanismo de búsqueda alternativo a través del parámetro `Script`. Para obtener más información sobre los conjuntos de parámetros, vea [Agregar conjuntos de parámetros a un cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

## <a name="overriding-input-processing-methods"></a>Reemplazar métodos de procesamiento de entrada

Los cmdlets deben invalidar uno o varios métodos de procesamiento de entrada para la clase [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Para obtener más información acerca de los métodos de procesamiento de entrada, consulte [crear el primer cmdlet](./creating-a-cmdlet-without-parameters.md).

Este cmdlet invalida el método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para compilar una matriz de expresiones regulares compiladas en el inicio. Esto aumenta el rendimiento durante las búsquedas que no utilizan la coincidencia simple.

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

Este cmdlet también invalida el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) para procesar las selecciones de cadena que el usuario realiza en la línea de comandos. Escribe los resultados de la selección de cadena en forma de un objeto personalizado llamando a un método **MatchString** privado.

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a>Acceder al contenido

El cmdlet debe abrir el proveedor indicado por la ruta de acceso de Windows PowerShell para que pueda acceder a los datos. El objeto [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) del espacio de ejecución se usa para el acceso al proveedor, mientras que la propiedad [System. Management. Automation. PSCmdlet. Invokeprovider *](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) del cmdlet se usa para abrir el proveedor. El acceso al contenido se proporciona mediante la recuperación del objeto [System. Management. Automation. Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) para el proveedor abierto.

Este cmdlet Select-Str de ejemplo usa la propiedad [System. Management. Automation. Providerintrinsics. Content *](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) para exponer el contenido que se va a examinar. Después, puede llamar al método [System. Management. Automation. Contentcmdletproviderintrinsics. getReader *](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) , pasando la ruta de acceso de Windows PowerShell necesaria.

## <a name="code-sample"></a>Código de ejemplo

En el código siguiente se muestra la implementación de esta versión de este cmdlet Select-Str. Tenga en cuenta que este código incluye la clase de cmdlet, los métodos privados usados por el cmdlet y el código de complemento de Windows PowerShell que se usa para registrar el cmdlet. Para obtener más información sobre el registro del cmdlet, consulte [compilar el cmdlet](#defining-the-cmdlet-class).

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a>Compilación del cmdlet

Después de implementar un cmdlet, debe registrarlo con Windows PowerShell a través de un complemento de Windows PowerShell. Para obtener más información acerca del registro de cmdlets, consulte [Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Prueba del cmdlet

Cuando el cmdlet se ha registrado con Windows PowerShell, puede probarlo mediante su ejecución en la línea de comandos. El siguiente procedimiento se puede usar para probar el cmdlet Select-Str de ejemplo.

1. Inicie Windows PowerShell y busque en el archivo de notas apariciones de líneas con la expresión ".NET". Tenga en cuenta que las comillas alrededor del nombre de la ruta de acceso solo son necesarias si la ruta de acceso consta de más de una palabra.

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    Aparece el siguiente resultado.

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. Busque en el archivo de notas las apariciones de las líneas con la palabra "sobre", seguido de cualquier otro texto. El parámetro `SimpleMatch` usa el valor predeterminado de `false`. La búsqueda no distingue entre mayúsculas y minúsculas porque el parámetro `CaseSensitive` está establecido en `false`.

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    Aparece el siguiente resultado.

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. Busque en el archivo de notas utilizando una expresión regular como modelo. El cmdlet busca caracteres alfabéticos y espacios en blanco entre paréntesis.

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    Aparece el siguiente resultado.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. Realice una búsqueda con distinción de mayúsculas y minúsculas del archivo de notas en busca de apariciones de la palabra "parámetro".

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    Aparece el siguiente resultado.

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. Busque en el proveedor de variables incluido en Windows PowerShell las variables que tengan valores numéricos de 0 a 9.

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    Aparece el siguiente resultado.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. Use un bloque de script para buscar la cadena "pos" en el archivo SelectStrCommandSample.cs. La función **cmatch** para el script realiza una coincidencia de patrón sin distinción entre mayúsculas y minúsculas.

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    Aparece el siguiente resultado.

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a>Véase también

[Cómo crear un cmdlet de Windows PowerShell](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Creación del primer cmdlet](./creating-a-cmdlet-without-parameters.md)

[Creación de un cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md)

[Diseño del proveedor de Windows PowerShell](../prog-guide/designing-your-windows-powershell-provider.md)

[Cómo funciona Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Cómo registrar cmdlets, proveedores y aplicaciones host](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
