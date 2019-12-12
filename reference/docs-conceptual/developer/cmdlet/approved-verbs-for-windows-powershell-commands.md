---
title: Verbos aprobados para comandos de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- action names [PowerShell SDK]
- verb names [PowerShell SDK]
- cmdlets [PowerShell SDK], verb names
ms.assetid: 2d4e58a9-05bc-437c-86b9-d8d55cba7d48
caps.latest.revision: 36
ms.openlocfilehash: 4475b3f5e15826efbe8bab867011985cd7e2e1ae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370034"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbos aprobados para comandos de PowerShell

PowerShell usa un par verbo-sustantivo para los nombres de los cmdlets y para sus clases de marco de Microsoft .NET derivadas.
Por ejemplo, el cmdlet `Get-Command` proporcionado por PowerShell se usa para recuperar todos los comandos que están registrados en PowerShell.
La parte del verbo del nombre identifica la acción que realiza el cmdlet.
La parte nominal del nombre identifica la entidad en la que se realiza la acción.

> [!NOTE]
> PowerShell usa el término *verbo* para describir una palabra que implica una acción incluso si esa palabra no es un verbo estándar en el idioma inglés.
> Por ejemplo, el término *nuevo* es un nombre de verbo de PowerShell válido porque implica una acción aunque no sea un verbo en el idioma inglés.

## <a name="verb-naming-rules"></a>Reglas de nomenclatura de verbos

En la lista siguiente se proporcionan directrices que se deben tener en cuenta al elegir el verbo para un nombre de cmdlet:

* Al especificar el verbo, se recomienda usar uno de los nombres de verbo predefinidos proporcionados por PowerShell (los alias de estos verbos predefinidos se incluyen en las tablas siguientes).
  Cuando se usa un verbo predefinido, se garantiza la coherencia entre los cmdlets que se crean, los cmdlets que proporciona PowerShell y los cmdlets que están diseñados por otros usuarios.

* Use los verbos predefinidos para describir el ámbito general de la acción y use los parámetros para refinar aún más la acción del cmdlet.

* Para aplicar la coherencia entre los cmdlets, no use un sinónimo de un verbo aprobado.

* Use solo el formulario de cada verbo que se muestra en este tema.
  Por ejemplo, use "Get", pero no use "Get" o "Get".

* Use la grafía Pascal para los verbos.
  En Pascal, la letra inicial de cada palabra se pone en mayúsculas, como "ForEach".

* No utilice los siguientes verbos o alias reservados.
  Estos verbos los usa el lenguaje de PowerShell o los cmdlets de casos especiales que proporciona PowerShell.
  - ForEach (foreach)
  - Formato (f)
  - Grupo (GP)
  - Ordenar (Sr)
  - Tee (te)
  - Dónde (qu)

## <a name="similar-verbs-for-different-actions"></a>Verbos similares para diferentes acciones

Los siguientes verbos similares representan acciones diferentes.

### <a name="new-vs-set"></a>Nuevo frente a conjunto
El verbo `New` se usa para crear un nuevo recurso.
El verbo `Set` se utiliza para modificar un recurso existente y, opcionalmente, puede crear el recurso si no existe, como el cmdlet `Set-Variable`.

### <a name="find-vs-search"></a>Buscar vs. Search
El verbo `Find` se utiliza para buscar un objeto.
El verbo `Search` se usa para crear una referencia a un recurso en un contenedor.

### <a name="get-vs-read"></a>Obtener y leer
El verbo `Get` se usa para recuperar un recurso, como un archivo.
El verbo `Read` se usa para obtener información de un origen, como un archivo.

### <a name="invoke-vs-start"></a>Invocar frente a Inicio
El verbo `Invoke` se utiliza para realizar una operación que normalmente es una operación sincrónica, como la ejecución de un comando.
El verbo `Start` se usa para iniciar una operación que normalmente es una operación asincrónica, como iniciar un proceso.

### <a name="ping-vs-test"></a>Ping frente a prueba
Utilice el verbo `Test`.

## <a name="common-verbs"></a>Verbos comunes

PowerShell usa la clase de enumeración [System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) para definir acciones genéricas que se pueden aplicar a casi cualquier cmdlet.
En la tabla siguiente se enumeran la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Agregar](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Agrega un recurso a un contenedor o adjunta un elemento a otro elemento. Por ejemplo, el cmdlet `Add-Content` agrega contenido a un archivo. Este verbo se empareja con `Remove`.|Para esta acción, no utilice verbos como anexar, adjuntar, concatenar o insertar.|
|[Clear](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Quita todos los recursos de un contenedor, pero no elimina el contenedor. Por ejemplo, el cmdlet `Clear-Content` quita el contenido de un archivo, pero no elimina el archivo.|Para esta acción, no utilice verbos como vaciar, borrar, liberar, Desmarcar, no establecer o anular.|
|[Cerrar](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (CS)|Cambia el estado de un recurso para que sea inaccesible, no disponible o inutilizable. Este verbo se empareja con `Open.`||
|[Copiar](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (CP)|Copia un recurso en otro nombre o en otro contenedor. Por ejemplo, el cmdlet `Copy-Item` que se usa para tener acceso a los datos almacenados copia un elemento de una ubicación del almacén de datos en otra ubicación.|En esta acción, no use verbos como duplicar, clonar, replicar o sincronizar.|
|[Entrar](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Especifica una acción que permite al usuario moverse a un recurso. Por ejemplo, el cmdlet `Enter-PSSession` coloca el usuario en una sesión interactiva. Este verbo se empareja con `Exit`.|Para esta acción, no utilice verbos como la operación de presionar o en.|
|[Salir](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ej.)|Establece el entorno o contexto actual en el contexto usado más recientemente. Por ejemplo, el cmdlet `Exit-PSSession` coloca al usuario en la sesión que se usó para iniciar la sesión interactiva. Este verbo se empareja con `Enter`.|Para esta acción, no use verbos como pop o out.|
|[Buscar](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (FD)|Busca un objeto en un contenedor desconocido, implícito, opcional o especificado.||
|[Formato](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Organiza los objetos en un formulario o diseño especificado.||
|[Obtener](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Especifica una acción que recupera un recurso. Este verbo se empareja con `Set`.|En esta acción, no use verbos como leer, abrir, CAT, escribir, dir, obtener, volcar, adquirir, examinar, buscar o buscar.|
|[Ocultar](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Hace que un recurso no se detecte. Por ejemplo, un cmdlet cuyo nombre incluya el verbo ocultar podría ocultar un servicio de un usuario. Este verbo se empareja con `Show`.|Para esta acción, no use un verbo como bloque.|
|[Join](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combina recursos en un recurso. Por ejemplo, el cmdlet `Join-Path` combina una ruta de acceso con una de sus rutas de acceso secundarias para crear una única ruta de acceso. Este verbo se empareja con `Split`.|En esta acción, no use verbos como combinar, unir, conectar o asociar.|
|[Bloqueo](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (LK)|Protege un recurso. Este verbo se empareja con `Unlock`.|Para esta acción, no utilice verbos como Restrict o Secure.|
|[Move](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Mueve un recurso de una ubicación a otra. Por ejemplo, el cmdlet `Move-Item` mueve un elemento de una ubicación del almacén de datos a otra ubicación.|En esta acción, no utilice verbos como Transfer, Name o Migrate.|
|[Nuevo](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Crea un recurso. (También se puede usar el verbo `Set` al crear un recurso que incluya datos, como el cmdlet `Set-Variable`).|En esta acción, no use verbos como crear, generar, compilar, hacer o asignar.|
|[Abrir](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (OP)|Cambia el estado de un recurso para que sea accesible, disponible o utilizable. Este verbo se empareja con `Close`.||
|[Optimizar](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (OM)|Aumenta la eficacia de un recurso.||
|[Pop](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Quita un elemento de la parte superior de una pila. Por ejemplo, el cmdlet `Pop-Location` cambia la ubicación actual a la ubicación que se insertó más recientemente en la pila.||
|[Inserciones](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (PU)|Agrega un elemento a la parte superior de una pila. Por ejemplo, el cmdlet `Push-Location` envía la ubicación actual en la pila.||
|[Rehacer](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Restablece un recurso al estado que se deshizo.||
|[Quitar](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Elimina un recurso de un contenedor. Por ejemplo, el cmdlet `Remove-Variable` elimina una variable y su valor. Este verbo se empareja con `Add`.|En esta acción, no use verbos como borrar, cortar, desechar, descartar o borrar.|
|[Cambiar nombre](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (RN)|Cambia el nombre de un recurso. Por ejemplo, el cmdlet `Rename-Item`, que se usa para tener acceso a los datos almacenados, cambia el nombre de un elemento en el almacén de datos.|Para esta acción, no use un verbo como Change.|
|[Restablecer](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (RS)|Vuelve a establecer un recurso en su estado original.||
|[Buscar](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (Sr)|Crea una referencia a un recurso en un contenedor.|Para esta acción, no use verbos como buscar o buscar.|
|[Select](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (SC)|Busca un recurso en un contenedor. Por ejemplo, el cmdlet `Select-String` busca texto en cadenas y archivos.|Para esta acción, no use verbos como buscar o buscar.|
|[Conjuntos](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Reemplaza los datos de un recurso existente o crea un recurso que contiene algunos datos. Por ejemplo, el cmdlet `Set-Date` cambia la hora del sistema en el equipo local. (El verbo `New` también se puede usar para crear un recurso). Este verbo se empareja con `Get`.|En esta acción, no use verbos como escribir, restablecer, asignar o configurar.|
|[Mostrar](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (SH)|Hace que un recurso sea visible para el usuario. Este verbo se empareja con `Hide`.|Para esta acción, no utilice verbos como mostrar o producir.|
|[Omitir](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (SK)|Omite uno o varios recursos o puntos de una secuencia.|Para esta acción, no use un verbo como bypass o salto.|
|[División](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (SL)|Separa partes de un recurso. Por ejemplo, el cmdlet `Split-Path` devuelve partes diferentes de una ruta de acceso. Este verbo se empareja con `Join`.|Para esta acción, no use un verbo como por separado.|
|[Paso](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (St)|Se desplaza al siguiente punto o recurso de una secuencia.||
|[Conmutador](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (SW)|Especifica una acción que alterna entre dos recursos, como cambiar entre dos ubicaciones, responsabilidades o Estados.||
|[Deshacer](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (un)|Establece un recurso en su estado anterior.||
|[Desbloquear](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (RU)|Libera un recurso que estaba bloqueado. Este verbo se empareja con `Lock`.|En esta acción, no use verbos como release, unrestrict o unsecure.|
|[Inspección](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (CT)|Inspecciona o supervisa continuamente los cambios de un recurso.||

## <a name="communications-verbs"></a>Verbos de comunicaciones

PowerShell usa la clase [System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) para definir las acciones que se aplican a las comunicaciones.
En la tabla siguiente se enumeran la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Conectar](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (CC)|Crea un vínculo entre un origen y un destino. Este verbo se empareja con `Disconnect`.|Para esta acción, no utilice verbos como join o Telnet.|
|[Desconectar](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (DC)|Rompe el vínculo entre un origen y un destino. Este verbo se empareja con `Connect`.|Para esta acción, no utilice verbos como break o Logoff.|
|[Lectura](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (RD)|Adquiere información de un origen. Este verbo se empareja con `Write`.|Para esta acción, no use verbos como adquirir, preguntar u obtener.|
|[Recibir](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (RC)|Acepta información enviada desde un origen. Este verbo se empareja con `Send`.|Para esta acción, no use verbos como leer, aceptar o inspeccionar.|
|[Enviar](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (SD)|Proporciona información a un destino. Este verbo se empareja con `Receive`.|En esta acción, no utilice verbos como Put, Broadcast, mail o fax.|
|[Escritura](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (WR)|Agrega información a un destino. Este verbo se empareja con `Read`.|Para esta acción, no utilice verbos como Put o print.|

## <a name="data-verbs"></a>Verbos de datos

PowerShell usa la clase [System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData) para definir las acciones que se aplican al control de datos.
En la tabla siguiente se enumeran la mayoría de los verbos definidos.

|Nombre de verbo (alias)|Acción|Comentarios|
|-------------------------|------------|--------------|
|[Copia de seguridad](/dotnet/api/System.Management.Automation.VerbsData.Backup) (BA)|Almacena los datos mediante su replicación.|En esta acción, no use verbos como guardar, grabar, replicar o sincronizar.|
|[Punto de control](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (CH)|Crea una instantánea del estado actual de los datos o de su configuración.|Para esta acción, no use un verbo como diff.|
|[Comparar](/dotnet/api/System.Management.Automation.VerbsData.Compare) (CR)|Evalúa los datos de un recurso con respecto a los datos de otro recurso.|Para esta acción, no use un verbo como diff.|
|[Comprimir](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compacta los datos de un recurso. Pares con `Expand`.|Para esta acción, no use un verbo como Compact.|
|[Convertir](/dotnet/api/System.Management.Automation.VerbsData.Convert) (CV)|Cambia los datos de una representación a otra cuando el cmdlet admite la conversión bidireccional o cuando el cmdlet admite la conversión entre varios tipos de datos.|En esta acción, no use verbos como cambiar, cambiar el tamaño o volver a muestrear.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (CF)|Convierte un tipo principal de entrada (el nombre del cmdlet indica la entrada) en uno o más tipos de salida admitidos.|Para esta acción, no utilice verbos como exportar, salida o out.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (CT)|Convierte de uno o más tipos de entrada a un tipo de salida principal (el nombre del cmdlet indica el tipo de salida).|Para esta acción, no utilice verbos como importar, entrada o en.|
|[Desmontar](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (DM)|Desasocia una entidad con nombre de una ubicación. Este verbo se empareja con `Mount`.|En esta acción, no use verbos como desmontar o desvincular.|
|[Editar](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ED)|Modifica los datos existentes agregando o quitando contenido.|En esta acción, no use verbos como cambiar, actualizar o modificar.|
|[Expandir](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Restaura los datos de un recurso que se ha comprimido a su estado original. Este verbo se empareja con `Compress`.|En esta acción, no use verbos como explosionar o descomprimir.|
|[Exportar](/dotnet/api/System.Management.Automation.VerbsData.Export) (EP)|Encapsula la entrada principal en un almacén de datos persistente, como un archivo, o en un formato de intercambio. Este verbo se empareja con `Import`.|Para esta acción, no utilice verbos como Extract o backup.|
|[Grupo](/dotnet/api/System.Management.Automation.VerbsData.Group) (GP)|Organiza o asocia uno o más recursos.|En esta acción, no use verbos como Aggregate, Arrange, Associate o correlacionate.|
|[Importar](/dotnet/api/System.Management.Automation.VerbsData.Import) (IP)|Crea un recurso a partir de los datos que se almacenan en un almacén de datos persistente (por ejemplo, un archivo) o en un formato de intercambio. Por ejemplo, el cmdlet `Import-CSV` importa datos de un archivo de valores separados por comas (CSV) a objetos que otros cmdlets pueden usar. Este verbo se empareja con `Export`.|Para esta acción, no utilice verbos como la carga masiva o la carga.|
|[Inicializar](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (en)|Prepara un recurso para su uso y lo establece en un estado predeterminado.|En esta acción, no use verbos como borrar, inicializar, renovar, recompilar, reinicializar o configurar.|
|[Límite](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Aplica las restricciones a un recurso.|Para esta acción, no use un verbo como quota.|
|[Merge](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Crea un recurso único a partir de varios recursos.|Para esta acción, no utilice verbos como combinar o combinar.|
|[Montaje](/dotnet/api/System.Management.Automation.VerbsData.Mount) (MT)|Adjunta una entidad con nombre a una ubicación. Este verbo se empareja con `Dismount`.|Para esta acción, no utilice el verbo CONNECT.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Envía datos fuera del entorno. Por ejemplo, el cmdlet `Out-Printer` envía datos a una impresora.||
|[Publicar](/dotnet/api/System.Management.Automation.VerbsData.Publish) (PB)|Hace que un recurso esté disponible para otros usuarios. Este verbo se empareja con `Unpublish`.|En esta acción, no use verbos como deploy, Release o install.|
|[Restore](/dotnet/api/System.Management.Automation.VerbsData.Restore) (RR)|Establece un recurso en un estado predefinido, como un estado establecido por `Checkpoint`. Por ejemplo, el cmdlet `Restore-Computer` inicia una restauración del sistema en el equipo local.|Para esta acción, no utilice verbos como reparar, devolver, deshacer o corregir.|
|[Guardar](/dotnet/api/System.Management.Automation.VerbsData.Save) (SV)|Conserva los datos para evitar pérdidas.||
|[Sync](/dotnet/api/System.Management.Automation.VerbsData.Sync) (SY)|Garantiza que dos o más recursos se encuentran en el mismo estado.|Para esta acción, no utilice verbos como replicar, forzar o buscar coincidencias.|
|[Anular publicación](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (UB)|Hace que un recurso no esté disponible para otros usuarios. Este verbo se empareja con `Publish`.|En esta acción, no use verbos como desinstalar, revertir u ocultar.|
|[Actualizar](/dotnet/api/System.Management.Automation.VerbsData.Update) (Ud)|Pone un recurso al día para mantener su estado, precisión, conformidad o cumplimiento. Por ejemplo, el cmdlet `Update-FormatData` actualiza y agrega archivos de formato a la consola de PowerShell actual.|En esta acción, no use verbos como actualizar, renovar, recalcular o volver a indizar.|

## <a name="diagnostic-verbs"></a>Verbos de diagnóstico

PowerShell usa la clase [System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) para definir las acciones que se aplican a los diagnósticos.
En la tabla siguiente se enumeran la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Depurar](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (dB)|Examina un recurso para diagnosticar problemas operativos.|Para esta acción, no use un verbo como diagnosticar.|
|[Medida](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (MS)|Identifica los recursos utilizados por una operación especificada o recupera estadísticas de un recurso.|En esta acción, no utilice verbos como calcular, determinar o analizar.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (PI)|Utilice el verbo `Test`.||
|[Reparación](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (RP)|Restaura un recurso a una condición utilizable|Para esta acción, no utilice verbos como corregir o restaurar.|
|[Resolver](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (RV)|Asigna una representación abreviada de un recurso a una representación más completa.|Para esta acción, no utilice verbos como expandir o determinar.|
|[Prueba](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Comprueba la operación o la coherencia de un recurso.|En esta acción, no use verbos como diagnosticar, analizar, salvar o comprobar.|
|[Seguimiento](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (TR)|Realiza un seguimiento de las actividades de un recurso.|En esta acción, no use verbos como realizar un seguimiento, seguir, inspeccionar o profundizar.|

## <a name="lifecycle-verbs"></a>Verbos del ciclo de vida

PowerShell usa la clase [System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) para definir las acciones que se aplican al ciclo de vida de un recurso.
En la tabla siguiente se enumeran la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Aprobar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (AP)|Confirma o acepta el estado de un recurso o un proceso.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (as)|Confirma el estado de un recurso.|Para esta acción, no use un verbo como Certificate.|
|[Compilación](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (BD)|Crea un artefacto (normalmente un archivo binario o documento) fuera de algún conjunto de archivos de entrada (normalmente código fuente o documentos declarativos).|Este verbo se agregó en PowerShell V6|
|[Completar](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (CP)|Concluye una operación.||
|[Confirmar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (CN)|Confirma, comprueba o valida el estado de un recurso o un proceso.|En esta acción, no use verbos como confirmar, aceptar, certificar, validar o comprobar.|
|[Deny](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (DN)|Rechaza, objetos, bloques o se opone al estado de un recurso o un proceso.|Para esta acción, no utilice verbos como bloque, objeto, rechazar o rechazar.|
|[Implementar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (DP)|Envía una aplicación, un sitio web o una solución a un destino remoto [s] de tal forma que un consumidor de esa solución pueda acceder a ella una vez completada la implementación.|Este verbo se agregó en PowerShell V6|
|[Deshabilitar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configura un recurso en un estado no disponible o inactivo. Por ejemplo, el cmdlet `Disable-PSBreakpoint` hace que un punto de interrupción esté inactivo. Este verbo se empareja con `Enable`.|Para esta acción, no use verbos como detener u ocultar.|
|[Habilitar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configura un recurso en un estado disponible o activo. Por ejemplo, el cmdlet `Enable-PSBreakpoint` hace que un punto de interrupción esté activo. Este verbo se empareja con `Disable`.|Para esta acción, no use verbos como iniciar o iniciar.|
|[Instalar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (es)|Coloca un recurso en una ubicación y, opcionalmente, lo inicializa. Este verbo se empareja con `Uninstall`.|Para esta acción, no use un verbo de uso como, por ejemplo, el programa de instalación.|
|[Invocar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Realiza una acción, como ejecutar un comando o un método.|Para esta acción, no use verbos como ejecutar o iniciar.|
|[Registrar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (RG)|Crea una entrada para un recurso en un repositorio, como una base de datos. Este verbo se empareja con `Unregister`.||
|[Solicitud](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (PET)|Solicita un recurso o solicita permisos.||
|[Reiniciar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (RT)|Detiene una operación y, a continuación, la inicia de nuevo. Por ejemplo, el cmdlet `Restart-Service` se detiene y, a continuación, inicia un servicio.|Para esta acción, no use un verbo como reciclar.|
|[Reanudar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (RU)|Inicia una operación que se ha suspendido. Por ejemplo, el cmdlet `Resume-Service` inicia un servicio que se ha suspendido. Este verbo se empareja con `Suspend`.||
|[Iniciar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (SA)|Inicia una operación. Por ejemplo, el cmdlet `Start-Service` inicia un servicio. Este verbo se empareja con `Stop`.|Para esta acción, no use verbos como iniciar, iniciar o arrancar.|
|[Detener](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (SP)|Interrumpe una actividad. Este verbo se empareja con `Start`.|En esta acción, no use verbos como finalizar, eliminar, terminar o cancelar.|
|[Enviar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (SB)|Presenta un recurso para su aprobación.|Para esta acción, no use un verbo como post.|
|[Suspender](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (SS)|Pausa una actividad. Por ejemplo, el cmdlet `Suspend-Service` pausa un servicio. Este verbo se empareja con `Resume`.|Para esta acción, no use un verbo como pausar.|
|[Desinstalar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (EE. UU.)|Quita un recurso de una ubicación indicada. Este verbo se empareja con `Install`.||
|[Anular el registro](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (su)|Quita la entrada de un recurso de un repositorio. Este verbo se empareja con `Register`.|Para esta acción, no use un verbo como Remove.|
|[Esperar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Pausa una operación hasta que se produce un evento especificado. Por ejemplo, el cmdlet `Wait-Job` detiene las operaciones hasta que se completan uno o varios de los trabajos en segundo plano.|Para esta acción, no utilice verbos como Sleep o PAUSE.|

## <a name="security-verbs"></a>Verbos de seguridad

PowerShell usa la clase [System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) para definir las acciones que se aplican a la seguridad.
En la tabla siguiente se enumeran la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Bloque](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (BL)|Restringe el acceso a un recurso. Este verbo se empareja con `Unblock`.|Para esta acción, no utilice verbos como evitar, limitar o denegar.|
|[Grant](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Permite el acceso a un recurso. Este verbo se empareja con `Revoke`.|Para esta acción, no use verbos como permitir o habilitar.|
|[Proteger](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (PT)|Protege a un recurso de ataques o pérdidas. Este verbo se empareja con `Unprotect`.|Para esta acción, no utilice verbos como cifrar, proteger o sellar.|
|[REVOKE](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (RK)|Especifica una acción que no permite el acceso a un recurso. Este verbo se empareja con `Grant`.|Para esta acción, no use verbos como quitar o deshabilitar.|
|[Desbloquear](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (UL)|Quita las restricciones a un recurso. Este verbo se empareja con `Block`.|Para esta acción, no use verbos como borrar o permitir.|
|[Desproteger](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (arriba)|Quita las medidas de seguridad de un recurso que se han agregado para impedir que se produzcan ataques o pérdidas. Este verbo se empareja con `Protect`.|Para esta acción, no utilice verbos como descifrar o desproteger.|

## <a name="other-verbs"></a>Otros verbos

PowerShell usa la clase [System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) para definir nombres de verbo canónicos que no se ajustan a una categoría de nombre de verbo específica, como los verbos de nombres comunes, de comunicaciones, de datos, de ciclo de vida o de verbos de seguridad.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Usar](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Utiliza o incluye un recurso para hacer algo.||

## <a name="see-also"></a>Véase también

[System. Management. Automation. VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System. Management. Automation. VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System. Management. Automation. VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System. Management. Automation. VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System. Management. Automation. VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System. Management. Automation. VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System. Management. Automation. VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Declaración de cmdlet](./cmdlet-class-declaration.md)

[Guía del programador de Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[SDK de Windows PowerShell Shell](../windows-powershell-reference.md)
