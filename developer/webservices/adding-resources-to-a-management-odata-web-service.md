---
title: Agregar recursos a un servicio de administración Web de OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858371"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Adición de recursos a un servicio web de Management OData

En este ejemplo se muestra cómo agregar un recurso a un servicio web de IIS Management OData existente mediante el Diseñador de esquemas de OData de administración. El [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) ejemplo crea un servicio web que expone los recursos de proceso y el servidor. En este ejemplo, agregará un recurso de máquina Virtual (VM) para el servicio web.

## <a name="prerequisites"></a>Requisitos previos

En este tema se da por supuesto que ha descargado e instalado la [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) de ejemplo como se describe en [crear un servicio de Windows PowerShell Web](./creating-a-management-odata-web-service.md), y que ha descargado e instalado el [Diseñador de esquemas de OData de administración](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). En este tema también se supone que tiene el módulo de Hyper-V de Windows PowerShell instalado en el equipo donde se configura el extremo de Odata de administración.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Agregar máquina virtual como un recurso para el servicio Web

El primer paso consiste en importar el esquema desde el punto de conexión de OData de administración existente en el Diseñador de esquemas. El siguiente procedimiento describe cómo hacerlo.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importar un esquema existente en el Diseñador de esquemas

1. Abra el Diseñador de esquemas de OData de administración.

2. Desde el **archivo** menú, seleccione **archivo** ; **Nuevo** ; **Archivo**. El **nuevo archivo** aparece el cuadro de diálogo.

3. Haga clic en **modelo de administración de OData**y, a continuación, haga clic en **abierto**.

4. Haga clic en la ventana principal y haga clic en **archivo de esquema** ; **Importación**. El **abierto** aparece el cuadro de diálogo.

5. Navegue hasta la carpeta donde se configura el servicio web de IIS Management OData para la [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) ejemplo. Si utiliza la secuencia de comandos Windows PowerShell con ese ejemplo para configurar el punto de conexión sin modificar el script, que la carpeta es **C:\inetpub\wwwroot\Modata**. Seleccione Schema.mof y haga clic en **abierto**.

   En este momento, abra los archivos Schema.mof y Schema.xml en un editor de texto y tenga en cuenta que contienen asignaciones para los recursos de proceso y servicio. Usa el archivo Schema.mof [Distributed Management Task Force](https://www.dmtf.org/) estándar (DTMF) MOF (Managed Object). El archivo schema.xml usa un esquema XML que se describe en [esquema de asignación de recursos](./resource-mapping-schema.md).

   El siguiente procedimiento describe cómo importar los cmdlets de Hyper-V en el modelo de esquema.

#### <a name="importing-cmdlets-into-the-schema"></a>Importación de cmdlets en el esquema

1. Haga doble clic en un área en blanco de la ventana del Diseñador de esquemas y haga clic en **Cmdlets de importación**. El **Asistente para importación de Cmdlet** aparece el cuadro de diálogo.

2. Asegúrese de que **ordenador** está seleccionada y haga clic en **siguiente**.

3. Asegúrese de que se ha seleccionado instalar módulos de Windows PowerShell y seleccione Hyper-V en la lista desplegable. Haga clic en **siguiente**. Haga clic en **Siguiente**.

4. En el **Cmdlet sustantivo** lista, seleccione **VM**. Haga clic en **Siguiente**.

5. En este ejemplo, enlazamos únicamente los comandos Get y Delete con los cmdlets. Desactive el **crear** y **actualización** casillas de verificación y asegúrese de que el **obtener** y **eliminar** se comprueban las casillas de verificación. Asegúrese de que el `Get-VM` cmdlet está seleccionado para **obtener**y el `Remove-VM` cmdlet está seleccionado para **eliminar**.

6. Dado que los metadatos de los cmdlets de la máquina virtual no especifican un tipo de salida, deberá ejecutar el cmdlet para especificar el tipo de salida. Seleccione **tipo de salida proporcione** y haga clic en **ejecutar el cmdlet**. El **ejecutar el Cmdlet** aparece el cuadro de diálogo. Haga clic en **ejecutar**. El **tipo CLR** cuadro se rellena con el `VirtualMachine` tipo. Haga clic en **Aceptar**, a continuación, haga clic en **siguiente**.

7. De forma predeterminada, se seleccionan todas las propiedades del objeto VirtualMachine. Puede borrar todas las propiedades que no desea como parte de los datos devueltos cuando se solicite este recurso desde el servicio web. Haga clic en **Siguiente**.

8. Debe seleccionar al menos una propiedad que se usará como clave. Seleccione **nombre** en la lista y haga clic en **siguiente**.

9. La siguiente ventana permite asignar propiedades de recurso de OData de administración a las propiedades de los cmdlets subyacentes. El asistente asigna las propiedades con nombres idénticos de forma predeterminada. Por ejemplo, el `ComputerName` propiedad del recurso se asigna a la `ComputerName` propiedad de los cmdlets.  Esto le permite especificar el `ComputerName` propiedad en una solicitud al servicio web y tiene el valor especificado se pasa a la `Get-VM` cmdlet. `Id` y `Name` también se asignan de forma predeterminada.

   10. Haga clic en **siguiente**, a continuación, haga clic en **finalizar**.

       El recurso de máquina virtual ahora aparece en la ventana Esquema del diseñador. Puede examinar las propiedades y las operaciones asociadas con el recurso. A continuación, exportará los archivos de esquema actualizado en el directorio virtual para el servicio web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportación de archivos de esquema desde el Diseñador de esquemas

1. Haga doble clic en un área en blanco de la ventana del Diseñador de esquemas y haga clic en **archivo de esquema** ; **Exportar**. El **Guardar como** aparece el cuadro de diálogo.

2. Navegue hasta el mismo directorio desde donde se importó el archivo MOF. Nombre al archivo el mismo que el archivo MOF original (Schema.mof de forma predeterminada) y haga clic en **guardar**. Confirme que desea sobrescribir el archivo existente.

   Aunque no se indica explícitamente en la **Guardar como** cuadro de diálogo, esto reemplaza el archivo Schema.xml y Schema.mof archivos.

## <a name="next-steps"></a>Pasos a seguir

Antes de que tiene acceso el nuevo recurso de máquina virtual desde el servicio web de IIS Management OData, debe actualizar el archivo RbacConfiguration.xml para permitir el acceso al módulo de Hyper-V de Windows PowerShell como se describe en [autorización basada en roles de configuración de](./configuring-role-based-authorization.md), y también se deberá reiniciar el servicio web.