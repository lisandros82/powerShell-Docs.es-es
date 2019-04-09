---
title: Los verbos aprobados para comandos de PowerShell | Microsoft Docs
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
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293357"
---
# <a name="approved-verbs-for-powershell-commands"></a>Verbos aprobados para comandos de PowerShell

PowerShell usa un par de verbo-nombre de los nombres de los cmdlets y de sus clases derivadas de Microsoft .NET Framework.
Por ejemplo, el `Get-Command` cmdlet de PowerShell se usa para recuperar todos los comandos que están registrados en PowerShell.
La parte verbal del nombre identifica la acción que realiza el cmdlet.
La parte del sustantivo del nombre identifica la entidad en el que se realiza la acción.

> [!NOTE]
> PowerShell usa el término *verbo* para describir una palabra que implica una acción, incluso si esa palabra no es un verbo estándar en el idioma inglés.
> Por ejemplo, el término *New* es un nombre válido de verbo de PowerShell porque implica una acción, aunque no es un verbo en inglés.

## <a name="verb-naming-rules"></a>Reglas de nomenclatura de verbo

En la lista siguiente proporciona instrucciones que se deben considerar cuando se elige el verbo de un nombre de cmdlet:

* Cuando se especifica el verbo, se recomienda usar uno de los nombres de verbo predefinidos proporcionados por PowerShell (alias para estos verbos predefinidos se incluyen en las tablas siguientes).
  Cuando se usa un verbo predefinido, garantizar la coherencia entre los cmdlets que cree, los cmdlets que se proporcionan mediante PowerShell y los cmdlets que están diseñados por otros usuarios.

* Utilice los verbos predefinidos para describir la finalidad de la acción y los parámetros para refinar aún más la acción del cmdlet.

* Para garantizar la coherencia entre los cmdlets, no use un sinónimo de un verbo aprobado.

* Usar solo la forma de cada verbo que aparece en este tema.
  Por ejemplo, use "Get", pero no use "Introducción" o "Obtiene".

* Use casillas Pascal las mayúsculas y minúsculas para los verbos.
  En la grafía Pascal las mayúsculas y minúsculas de la letra inicial de cada palabra en mayúscula, como "ForEach".

* No use los siguientes verbos reservados o los alias.
  Mediante el lenguaje de PowerShell o mediante cmdlets de casos especiales proporcionados con PowerShell, se usan estos verbos.
  - ForEach (foreach)
  - Formato (f)
  - Grupo (gp)
  - Sort (sr)
  - Tee (te)
  - Donde (qu)

## <a name="similar-verbs-for-different-actions"></a>Verbos similar para distintas acciones

Los siguientes verbos similar representan diferentes acciones.

### <a name="new-vs-set"></a>Comparación del precio. Establecer
El `New` verbo se usa para crear un nuevo recurso.
El `Set` verbo se usa para modificar un recurso existente, si lo desea crear el recurso si no existe, como el `Set-Variable` cmdlet.

### <a name="find-vs-search"></a>Buscar vs. Buscar
El `Find` verbo se usa para buscar un objeto.
El `Search` verbo se usa para crear una referencia a un recurso en un contenedor.

### <a name="get-vs-read"></a>Obtener vs. Leer
El `Get` verbo se usa para recuperar un recurso, como un archivo.
El `Read` verbo se utiliza para obtener información de un origen, como un archivo.

### <a name="invoke-vs-start"></a>Invocación de vs. Inicie
El `Invoke` verbo se usa para realizar una operación que generalmente es una operación sincrónica, como la ejecución de un comando.
El `Start` verbo se usa para comenzar una operación que generalmente es una operación asincrónica, como el inicio de un proceso.

### <a name="ping-vs-test"></a>Ping de vs. Test
Use el `Test` verbo.

## <a name="common-verbs"></a>Verbos comunes

PowerShell usa el [System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon) clase de enumeración para definir acciones genéricas que se pueden aplicar a casi cualquier cmdlet.
En la tabla siguiente enumera la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Agregar](/dotnet/api/System.Management.Automation.VerbsCommon.Add) (a)|Agrega un recurso a un contenedor o se adjunta a un elemento a otro elemento. Por ejemplo, el `Add-Content` cmdlet agrega contenido a un archivo. Este verbo se empareja con `Remove`.|Para esta acción, no use verbos como Concatenate Append, adjuntar, o insertar.|
|[Borrar](/dotnet/api/System.Management.Automation.VerbsCommon.Clear) (cl)|Quita todos los recursos de un contenedor, pero no elimina el contenedor. Por ejemplo, el `Clear-Content` cmdlet quita el contenido de un archivo, pero no elimina el archivo.|Para esta acción, no use verbos como vaciado, borrado, versión, desmarcar, anular o anular.|
|[Cerrar](/dotnet/api/System.Management.Automation.VerbsCommon.Close) (cs)|Cambia el estado de un recurso para que sea accesible, inutilizable o no disponible. Este verbo se empareja con `Open.`||
|[Copia](/dotnet/api/System.Management.Automation.VerbsCommon.Copy) (cp)|Copia un recurso a otro nombre o en otro contenedor. Por ejemplo, el `Copy-Item` cmdlet que se usa para tener acceso a los datos almacenados copia un elemento de una ubicación del almacén de datos a otra ubicación.|Para esta acción, no use verbos como duplicado, clonar, replicar o sincronización.|
|[Escriba](/dotnet/api/System.Management.Automation.VerbsCommon.Enter) (et)|Especifica una acción que permite al usuario mover a un recurso. Por ejemplo, el `Enter-PSSession` cmdlet coloca al usuario en una sesión interactiva. Este verbo se empareja con `Exit`.|Para esta acción, no use verbos como inserción o en.|
|[Salida](/dotnet/api/System.Management.Automation.VerbsCommon.Exit) (ex)|Establece el entorno actual o el contexto en el contexto usado recientemente. Por ejemplo, el `Exit-PSSession` cmdlet coloca al usuario en la sesión que se usó para iniciar la sesión interactiva. Este verbo se empareja con `Enter`.|Para esta acción, no use verbos como Pop o Out.|
|[Buscar](/dotnet/api/System.Management.Automation.VerbsCommon.Find) (fd)|Busca un objeto en un contenedor que es desconocido, implícita, opcional o especificada.||
|[Formato](/dotnet/api/System.Management.Automation.VerbsCommon.Format) (f)|Organiza los objetos en un formulario especificado o el diseño.||
|[Obtener](/dotnet/api/System.Management.Automation.VerbsCommon.Get) (g)|Especifica una acción que se recupera un recurso. Este verbo se empareja con `Set`.|Para esta acción, no use verbos como lectura, abierto, Cat, tipo, Dir, obtener, volcado de memoria, adquisición, examinar, buscar o buscar.|
|[Ocultar](/dotnet/api/System.Management.Automation.VerbsCommon.Hide) (h)|Hace que un recurso que no se detecta. Por ejemplo, un cmdlet cuyo nombre incluye el verbo ocultar puede ocultar un servicio de un usuario. Este verbo se empareja con `Show`.|Para esta acción, no use un verbo como bloque.|
|[Únase a](/dotnet/api/System.Management.Automation.VerbsCommon.Join) (j)|Combina los recursos en un recurso. Por ejemplo, el `Join-Path` cmdlet combina una ruta de acceso con uno de sus rutas de acceso secundaria para crear una única ruta de acceso. Este verbo se empareja con `Split`.|Para esta acción, no use verbos como combinar, Unite, conectar o asociar.|
|[Bloqueo](/dotnet/api/System.Management.Automation.VerbsCommon.Lock) (lk)|Protege un recurso. Este verbo se empareja con `Unlock`.|Para esta acción, no use verbos como restringir o seguro.|
|[Mover](/dotnet/api/System.Management.Automation.VerbsCommon.Move) (m)|Mueve un recurso desde una ubicación a otra. Por ejemplo, el `Move-Item` cmdlet mueve un elemento de una ubicación del almacén de datos a otra ubicación.|Para esta acción, no use verbos como transferencia, el nombre o la migración.|
|[Nuevo](/dotnet/api/System.Management.Automation.VerbsCommon.New) (n)|Crea un recurso. (El `Set` verbo también se puede usar al crear un recurso que incluye datos, como el `Set-Variable` cmdlet.)|Para esta acción, no use verbos como crear, generar, compilación, Make o asignar.|
|[Abra](/dotnet/api/System.Management.Automation.VerbsCommon.Open) (Opening, op)|Cambia el estado de un recurso para que sea accesible, disponible o utilizable. Este verbo se empareja con `Close`.||
|[Optimizar](/dotnet/api/System.Management.Automation.VerbsCommon.Optimize) (om)|Aumenta la eficacia de un recurso.||
|[POP](/dotnet/api/System.Management.Automation.VerbsCommon.Pop) (pop)|Quita un elemento de la parte superior de la pila. Por ejemplo, el `Pop-Location` cmdlet cambia la ubicación actual a la ubicación que se insertó más recientemente en la pila.||
|[Insertar](/dotnet/api/System.Management.Automation.VerbsCommon.Push) (pu)|Agrega un elemento a la parte superior de la pila. Por ejemplo, el `Push-Location` cmdlet inserta la ubicación actual en la pila.||
|[Rehacer](/dotnet/api/System.Management.Automation.VerbsCommon.Redo) (re)|Restablece el estado que se deshizo un recurso.||
|[Quitar](/dotnet/api/System.Management.Automation.VerbsCommon.Remove) (r)|Elimina un recurso de un contenedor. Por ejemplo, el `Remove-Variable` cmdlet elimina una variable y su valor. Este verbo se empareja con `Add`.|Para esta acción, no utilizan verbos tales como borrar, cortar, Dispose, descartar ni borrar.|
|[Cambiar el nombre](/dotnet/api/System.Management.Automation.VerbsCommon.Rename) (rn)|Cambia el nombre de un recurso. Por ejemplo, el `Rename-Item` cmdlet, que se utiliza para tener acceso a los datos almacenados, cambia el nombre de un elemento en el almacén de datos.|Para esta acción, no use un verbo, como el cambio.|
|[Restablecer](/dotnet/api/System.Management.Automation.VerbsCommon.Reset) (rs)|Establece un recurso a su estado original.||
|[Búsqueda](/dotnet/api/System.Management.Automation.VerbsCommon.Search) (sr)|Crea una referencia a un recurso en un contenedor.|Para esta acción, no use verbos como buscar o buscar.|
|[Seleccione](/dotnet/api/System.Management.Automation.VerbsCommon.Select) (sc)|Busca un recurso en un contenedor. Por ejemplo, el `Select-String` cmdlet busca texto en cadenas y archivos.|Para esta acción, no use verbos como buscar o buscar.|
|[Establecer](/dotnet/api/System.Management.Automation.VerbsCommon.Set) (s)|Reemplaza los datos en un recurso existente o crea un recurso que contiene algunos datos. Por ejemplo, el `Set-Date` cmdlet cambia la hora del sistema en el equipo local. (El `New` verbo también puede utilizarse para crear un recurso.) Este verbo se empareja con `Get`.|Para esta acción, no use verbos como escritura, Reset, asignar o configurar.|
|[Mostrar](/dotnet/api/System.Management.Automation.VerbsCommon.Show) (sh)|Hace que un recurso sea visible para el usuario. Este verbo se empareja con `Hide`.|Para esta acción, no use verbos como presentación o que se produzcan.|
|[Omitir](/dotnet/api/System.Management.Automation.VerbsCommon.Skip) (sk)|Se omite uno o varios recursos o puntos de una secuencia.|Para esta acción, no use un verbo como omisión o salto.|
|[División](/dotnet/api/System.Management.Automation.VerbsCommon.Split) (sl)|Separa las partes de un recurso. Por ejemplo, el `Split-Path` cmdlet devuelve las distintas partes de una ruta de acceso. Este verbo se empareja con `Join`.|Esta acción, no use un verbo tal independiente.|
|[Paso](/dotnet/api/System.Management.Automation.VerbsCommon.Step) (st)|Se desplaza al siguiente punto o recurso en una secuencia.||
|[Conmutador](/dotnet/api/System.Management.Automation.VerbsCommon.Switch) (sw)|Especifica una acción que alterna entre los dos recursos, como para cambiar entre dos ubicaciones, responsabilidades o Estados.||
|[Deshacer](/dotnet/api/System.Management.Automation.VerbsCommon.Undo) (DES)|Establece un recurso a su estado anterior.||
|[Desbloquear](/dotnet/api/System.Management.Automation.VerbsCommon.Unlock) (Reino Unido)|Libera un recurso que se ha bloqueado. Este verbo se empareja con `Lock`.|Para esta acción, no use verbos como el lanzamiento, Unrestrict o no seguro.|
|[Inspección](/dotnet/api/System.Management.Automation.VerbsCommon.Watch) (CT)|Continuamente inspecciona o supervisa un recurso para los cambios.||

## <a name="communications-verbs"></a>Verbos de comunicaciones

PowerShell usa el [System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications) clase para definir las acciones que se aplican a las comunicaciones.
En la tabla siguiente enumera la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Conectar](/dotnet/api/System.Management.Automation.VerbsCommunications.Connect) (cc)|Crea un vínculo entre un origen y un destino. Este verbo se empareja con `Disconnect`.|Para esta acción, no use verbos como Telnet o unión.|
|[Desconectar](/dotnet/api/System.Management.Automation.VerbsCommunications.Disconnect) (dc)|Rompe el vínculo entre un origen y un destino. Este verbo se empareja con `Connect`.|Para esta acción, no use verbos como salto o de cierre de sesión.|
|[Lectura](/dotnet/api/System.Management.Automation.VerbsCommunications.Read) (rd)|Adquiere la información de un origen. Este verbo se empareja con `Write`.|Para esta acción, no use verbos como adquisición, símbolo del sistema ni obtener.|
|[Recibir](/dotnet/api/System.Management.Automation.VerbsCommunications.Receive) (rc)|Acepta la información enviada desde un origen. Este verbo se empareja con `Send`.|Para esta acción, no utilizan verbos como lectura, Accept, o inspeccionar.|
|[Enviar](/dotnet/api/System.Management.Automation.VerbsCommunications.Send) (sd)|Proporciona información a un destino. Este verbo se empareja con `Receive`.|Para esta acción, no use verbos como Put, difusión, Fax o correo electrónico.|
|[Escribir](/dotnet/api/System.Management.Automation.VerbsCommunications.Write) (ESC)|Agrega información a un destino. Este verbo se empareja con `Read`.|Para esta acción, no use verbos como Put o Print.|

## <a name="data-verbs"></a>Verbos de datos

PowerShell usa el [System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData) clase para definir las acciones que se aplican al control de datos.
En la tabla siguiente enumera la mayoría de los verbos definidos.

|Nombre del verbo (alias)|Acción|Comentarios|
|-------------------------|------------|--------------|
|[Copia de seguridad](/dotnet/api/System.Management.Automation.VerbsData.Backup) (ba)|Almacena los datos mediante la replicación.|Para esta acción, no use verbos como guardar, Burn, Replicate o sincronización.|
|[Punto de comprobación](/dotnet/api/System.Management.Automation.VerbsData.Checkpoint) (ch)|Crea una instantánea del estado actual de los datos o de su configuración.|Para esta acción, no use un verbo, como la diferencia.|
|[Comparar](/dotnet/api/System.Management.Automation.VerbsData.Compare) (cr)|Evalúa los datos de un recurso con los datos de otro recurso.|Para esta acción, no use un verbo, como la diferencia.|
|[Comprimir](/dotnet/api/System.Management.Automation.VerbsData.Compress) (cm)|Compacta los datos de un recurso. Adapta `Expand`.|Para esta acción, no use un verbo como compacto.|
|[Convertir](/dotnet/api/System.Management.Automation.VerbsData.Convert) (VC)|Cambia los datos de una representación a otra cuando el cmdlet admite la conversión bidireccional o cuando el cmdlet admite la conversión entre varios tipos de datos.|Para esta acción, no utilice verbos como cambio, el cambio de tamaño, o volver a muestrear.|
|[ConvertFrom](/dotnet/api/System.Management.Automation.VerbsData.ConvertFrom) (cf)|Convierte a un tipo de entrada (el nombre de cmdlet indica la entrada) principal a uno o varios tipos de salida admitidos.|Para esta acción, no use verbos como exportación, salida o de salida.|
|[ConvertTo](/dotnet/api/System.Management.Automation.VerbsData.ConvertTo) (ct)|Convierte de uno o varios tipos de entrada a un tipo de resultado principal (el nombre de cmdlet indica el tipo de salida).|Para esta acción, no use verbos como importación, la entrada, o en.|
|[Desmontar](/dotnet/api/System.Management.Automation.VerbsData.Dismount) (dm)|Desasocia una entidad con nombre desde una ubicación. Este verbo se empareja con `Mount`.|Para esta acción, no use verbos como desmontar o desvincular.|
|[Editar](/dotnet/api/System.Management.Automation.VerbsData.Edit) (ed)|Modifica los datos existentes agregando o quitando contenido.|Para esta acción, no use verbos como cambio, actualizar o modificar.|
|[Expanda](/dotnet/api/System.Management.Automation.VerbsData.Expand) (en)|Restaura los datos de un recurso que se ha comprimido a su estado original. Este verbo se empareja con `Compress`.|Para esta acción, no use verbos como explosión o sin comprimir.|
|[Exportar](/dotnet/api/System.Management.Automation.VerbsData.Export) (ep)|Encapsula la entrada principal en un almacén de datos persistente, como un archivo, o en un formato de intercambio. Este verbo se empareja con `Import`.|Para esta acción, no use verbos como copia de seguridad o de extracción.|
|[Grupo](/dotnet/api/System.Management.Automation.VerbsData.Group) (gp)|Organiza o asocia uno o varios recursos.|Para esta acción, no use verbos como agregado, organizar, asociar ni poner en correlación.|
|[Importación](/dotnet/api/System.Management.Automation.VerbsData.Import) (ip)|Crea un recurso de datos que se almacenan en un almacén de datos persistente (por ejemplo, un archivo) o en un formato de intercambio. Por ejemplo, el `Import-CSV` cmdlet importa datos desde un archivo de valores separados por comas (CSV) a los objetos que pueden usarse por otros cmdlets. Este verbo se empareja con `Export`.|Para esta acción, no use verbos como la carga masiva o carga.|
|[Inicializar](/dotnet/api/System.Management.Automation.VerbsData.Initialize) (in)|Prepara un recurso para su uso y lo establece en un estado predeterminado.|Para esta acción, no use verbos como borrado, Init, renovar, volver a generar, reinicializar o programa de instalación.|
|[Límite](/dotnet/api/System.Management.Automation.VerbsData.Limit) (l)|Se aplica a las restricciones a un recurso.|Para esta acción, no use un verbo, como la cuota.|
|[Combinar](/dotnet/api/System.Management.Automation.VerbsData.Merge) (mg)|Crea un único recurso de varios recursos.|Para esta acción, no use verbos como combinar o combinación.|
|[Montar](/dotnet/api/System.Management.Automation.VerbsData.Mount) (mt)|Adjunta una entidad con nombre en una ubicación. Este verbo se empareja con `Dismount`.|Para esta acción, no use el verbo Connect.|
|[Out](/dotnet/api/System.Management.Automation.VerbsData.Out) (o)|Envía datos fuera del entorno. Por ejemplo, el `Out-Printer` cmdlet envía datos a una impresora.||
|[Publicar](/dotnet/api/System.Management.Automation.VerbsData.Publish) (pb)|Hace que un recurso disponible para otros usuarios. Este verbo se empareja con `Unpublish`.|Para esta acción, no utilice verbos como implementar, versión, o instalar.|
|[Restaurar](/dotnet/api/System.Management.Automation.VerbsData.Restore) (rr)|Establece un recurso en un estado predefinido, como un estado establecido mediante `Checkpoint`. Por ejemplo, el `Restore-Computer` cmdlet inicia una restauración del sistema en el equipo local.|Para esta acción, no use verbos como reparación, la devolución, deshacer o corrección.|
|[Guardar](/dotnet/api/System.Management.Automation.VerbsData.Save) (sv)|Conserva los datos para evitar la pérdida.||
|[Sincronización](/dotnet/api/System.Management.Automation.VerbsData.Sync) (sy)|Garantiza que dos o más recursos están en el mismo estado.|Para esta acción, no utilice verbos como coerción, se replican o coinciden.|
|[Cancelar la publicación](/dotnet/api/System.Management.Automation.VerbsData.Unpublish) (r)|Hace que un recurso no está disponible para otros usuarios. Este verbo se empareja con `Publish`.|Para esta acción, no utilice verbos como desinstalar, revertir, u ocultar.|
|[Actualización](/dotnet/api/System.Management.Automation.VerbsData.Update) (ud)|Pone un recurso actualizado para mantener su estado, precisión, de conformidad o cumplimiento. Por ejemplo, el `Update-FormatData` cmdlet actualiza y agrega los archivos de formato a la consola de PowerShell actual.|Para esta acción, no use verbos como actualización, renovar, volver a calcular o volver a indexar.|

## <a name="diagnostic-verbs"></a>Verbos de diagnóstico

PowerShell usa el [System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic) clase para definir las acciones que se aplican a los diagnósticos.
En la tabla siguiente enumera la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Depurar](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Debug) (db)|Examina un recurso para diagnosticar los problemas operacionales.|Para esta acción, no use un verbo como diagnosticar.|
|[Medida](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Measure) (ms)|Identifica los recursos consumidos por una operación determinada o recupera las estadísticas sobre un recurso.|Para esta acción, no use verbos como analizar, determinar o calcular.|
|[Ping](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Ping) (pi)|Use el `Test` verbo.||
|[Reparación](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Repair) (rp)|Restaura un recurso a una condición de uso|Para esta acción, no use verbos como corrección o una restauración.|
|[Resolver](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Resolve) (rv)|Una representación taquigrafía de un recurso se asigna a una representación más completa.|Para esta acción, no use verbos como expandir o determinar.|
|[Prueba](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Test) (t)|Comprueba que la operación o la coherencia de un recurso.|Para esta acción, no use verbos como analizar, diagnosticar, residual o comprobar.|
|[Seguimiento](/dotnet/api/System.Management.Automation.VerbsDiagnostic.Trace) (tr)|Realiza un seguimiento de las actividades de un recurso.|Para esta acción, no use verbos como pista, seguimiento, inspeccionar, o bien profundice.|

## <a name="lifecycle-verbs"></a>Verbos del ciclo de vida

PowerShell usa el [System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) clase para definir las acciones que se aplican al ciclo de vida de un recurso.
En la tabla siguiente enumera la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Aprobar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Approve) (ap)|Confirma o que acepta el estado de un recurso o el proceso.||
|[Assert](/dotnet/api/System.Management.Automation.VerbsLifecycle.Assert) (como)|Confirma el estado de un recurso.|Para esta acción, no use un verbo como Certify.|
|[Compilar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Build) (bd)|Crea un artefacto (normalmente un archivo binario o documento) fuera de un conjunto de archivos de entrada (normalmente el código de origen o documentos declarativos)|Se agregó este verbo en PowerShell v6|
|[Completa](/dotnet/api/system.management.automation.host.buffercelltype?view=powershellsdk-1.1.0) (cp)|Finaliza una operación.||
|[Confirmar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Confirm) (cn)|Confirma, comprueba o valida el estado de un recurso o el proceso.|Para esta acción, no use verbos como confirmación, Acepto, Certify, validar o comprobar.|
|[Denegar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deny) (dn)|Rechaza, objetos, se bloquea o se opone al estado de un recurso o el proceso.|Para esta acción, no use verbos como bloque, objeto, denegar o rechazar.|
|[Implementar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Deploy) (dp)|Envía una aplicación, un sitio Web o una solución a un destino remoto [s] de tal manera que un consumidor de la solución puede tener acceso a él una vez completada la implementación|Se agregó este verbo en PowerShell v6|
|[Deshabilitar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Disable) (d)|Configura un recurso a un estado inactivo o no está disponible. Por ejemplo, el `Disable-PSBreakpoint` cmdlet hace que sea un punto de interrupción inactiva. Este verbo se empareja con `Enable`.|Para esta acción, no use verbos como Halt u ocultar.|
|[Habilitar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Enable) (e)|Configura un recurso a un estado activo o disponible. Por ejemplo, el `Enable-PSBreakpoint` cmdlet activa un punto de interrupción. Este verbo se empareja con `Disable`.|Para esta acción, no use verbos como inicio o inicio.|
|[Instalar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Install) (es)|Coloca un recurso en una ubicación y, opcionalmente, lo inicializa. Este verbo se empareja con `Uninstall`.|Realice esta acción, no un verbo de uso, como la configuración.|
|[Invocar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Invoke) (i)|Realiza una acción, como la ejecución de un comando o un método.|Para esta acción, no use verbos como ejecución o iniciar.|
|[Registrar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Register) (rg)|Crea una entrada para un recurso en un repositorio como una base de datos. Este verbo se empareja con `Unregister`.||
|[Solicitar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Request) (SIS)|Solicita un recurso o solicita permisos.||
|[Reiniciar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Restart) (CRT)|Detiene una operación y comienza de nuevo. Por ejemplo, el `Restart-Service` cmdlet detiene e inicia un servicio.|Para esta acción, no use un verbo, como el reciclaje.|
|[Reanudar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Resume) (ru)|Inicia una operación que se ha suspendido. Por ejemplo, el `Resume-Service` cmdlet inicia un servicio que se ha suspendido. Este verbo se empareja con `Suspend`.||
|[Iniciar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Start) (sa)|Inicia una operación. Por ejemplo, el `Start-Service` cmdlet inicia un servicio. Este verbo se empareja con `Stop`.|Para esta acción, no use verbos como inicio, inicio o inicio.|
|[Detener](/dotnet/api/System.Management.Automation.VerbsLifecycle.Stop) (sp)|Interrumpe una actividad. Este verbo se empareja con `Start`.|Para esta acción, no use verbos como final, Kill, terminar o Cancelar.|
|[Enviar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Submit) (sb)|Presenta un recurso para su aprobación.|Para esta acción, no use un verbo como Post.|
|[Suspender](/dotnet/api/System.Management.Automation.VerbsLifecycle.Suspend) (ss)|Pausa una actividad. Por ejemplo, el `Suspend-Service` cmdlet detiene un servicio. Este verbo se empareja con `Resume`.|Para esta acción, no use un verbo como pausar.|
|[Desinstalar](/dotnet/api/System.Management.Automation.VerbsLifecycle.Uninstall) (us)|Quita un recurso desde una ubicación indicada. Este verbo se empareja con `Install`.||
|[Anular el registro](/dotnet/api/System.Management.Automation.VerbsLifecycle.Unregister) (su)|Quita la entrada para un recurso desde un repositorio. Este verbo se empareja con `Register`.|Para esta acción, no use un verbo, como quitar.|
|[Espere](/dotnet/api/System.Management.Automation.VerbsLifecycle.Wait) (w)|Detiene una operación hasta que se produce un evento especificado. Por ejemplo, el `Wait-Job` cmdlet detiene temporalmente las operaciones hasta que uno o varios de los trabajos en segundo plano están completos.|Para esta acción, no use verbos como modo de suspensión o en pausa.|

## <a name="security-verbs"></a>Verbos de seguridad

PowerShell usa el [System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity) clase para definir las acciones que se aplican a la seguridad.
En la tabla siguiente enumera la mayoría de los verbos definidos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Bloque](/dotnet/api/System.Management.Automation.VerbsSecurity.Block) (bl)|Restringe el acceso a un recurso. Este verbo se empareja con `Unblock`.|Para esta acción, no use verbos como impedir, limitar o denegar.|
|[GRANT](/dotnet/api/System.Management.Automation.VerbsSecurity.Grant) (gr)|Permite el acceso a un recurso. Este verbo se empareja con `Revoke`.|Para esta acción, no use verbos como permitir o habilitar.|
|[Proteger](/dotnet/api/System.Management.Automation.VerbsSecurity.Protect) (pt)|Protege un recurso frente a ataques o pérdida. Este verbo se empareja con `Unprotect`.|Para esta acción, no use verbos como cifrar, proteger o sellar.|
|[Revocar](/dotnet/api/System.Management.Automation.VerbsSecurity.Revoke) (rk)|Especifica una acción que no permite el acceso a un recurso. Este verbo se empareja con `Grant`.|Para esta acción, no use verbos como eliminar o deshabilitar.|
|[Desbloquear](/dotnet/api/System.Management.Automation.VerbsSecurity.Unblock) (ul)|Quita las restricciones a un recurso. Este verbo se empareja con `Block`.|Para esta acción, no use verbos como borrar o permitir.|
|[Desproteger](/dotnet/api/System.Management.Automation.VerbsSecurity.Unprotect) (hasta)|Quita un recurso que se agregaron para impedir ataques o pérdida de las medidas de seguridad. Este verbo se empareja con `Protect`.|Para esta acción, no use verbos como descifrado o Unseal.|

## <a name="other-verbs"></a>Otros verbos

PowerShell usa el [System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther) clase para definir los nombres de verbo canónico que no caben en una categoría de nombre del verbo específico como comunes, las comunicaciones, datos, del ciclo de vida o nombres de verbo de seguridad verbos.

|Verbo (alias)|Acción|Comentarios|
|--------------------|------------|--------------|
|[Use](/dotnet/api/System.Management.Automation.VerbsOther.Use) (u)|Usa o incluye un recurso para hacer algo.||

## <a name="see-also"></a>Véase también

[System.Management.Automation.VerbsCommon](/dotnet/api/System.Management.Automation.VerbsCommon)

[System.Management.Automation.VerbsCommunications](/dotnet/api/System.Management.Automation.VerbsCommunications)

[System.Management.Automation.VerbsData](/dotnet/api/System.Management.Automation.VerbsData)

[System.Management.Automation.VerbsDiagnostic](/dotnet/api/System.Management.Automation.VerbsDiagnostic)

[System.Management.Automation.VerbsLifeCycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)

[System.Management.Automation.VerbsSecurity](/dotnet/api/System.Management.Automation.VerbsSecurity)

[System.Management.Automation.VerbsOther](/dotnet/api/System.Management.Automation.VerbsOther)

[Declaración de cmdlet](./cmdlet-class-declaration.md)

[Guía del programador de Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md)

[Shell de SDK de Windows PowerShell](../windows-powershell-reference.md)
