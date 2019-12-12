---
title: Agregar recursos a un servicio Web Management OData | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359824"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Adición de recursos a un servicio web de Management OData

En este ejemplo se muestra cómo agregar un recurso a un servicio Web de administración de OData existente mediante el diseñador de esquemas de Management OData. En el ejemplo [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) se crea un servicio Web que expone el proceso y los recursos del servidor. En este ejemplo, agregará un recurso de máquina virtual (VM) al servicio Web.

## <a name="prerequisites"></a>Requisitos previos

En este tema se supone que ha descargado e instalado el ejemplo [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) tal como se describe en [creación de un servicio Web de Windows PowerShell](./creating-a-management-odata-web-service.md)y que ha descargado e instalado el [Diseñador de esquemas OData de administración](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). En este tema también se supone que tiene el módulo de Windows PowerShell de Hyper-V instalado en el equipo en el que configuró el punto de conexión de oData de administración.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Agregar una máquina virtual como un recurso al servicio Web

El primer paso consiste en importar el esquema del extremo de administración de OData existente en el diseñador de esquemas. En el procedimiento siguiente se describe cómo hacerlo.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importar un esquema existente en el diseñador de esquemas

1. Abra el diseñador de esquemas OData de administración.

2. En el menú **archivo** , seleccione **archivo** ; **Nuevo** ; **Archivo**. Aparecerá el cuadro de diálogo **nuevo archivo** .

3. Haga clic en **Management OData Model**y, a continuación, haga clic en **abrir**.

4. Haga clic con el botón derecho en la ventana principal y haga clic en **archivo de esquema** ; **Importar**. Aparece el cuadro de diálogo **abrir** .

5. Navegue hasta la carpeta donde configuró el servicio Web de Management OData para el ejemplo [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) . Si usó el script de Windows PowerShell que se proporciona con ese ejemplo para configurar el punto de conexión sin modificar el script, esa carpeta es **C:\inetpub\wwwroot\Modata**. Seleccione Schema. mof y haga clic en **abrir**.

   En este momento, abra los archivos Schema. mof y Schema. XML en un editor de texto y observe que contienen asignaciones para los recursos de proceso y servicio. El archivo Schema. mof usa el estándar de objetos administrados (MOF) del [equipo de administración distribuida](https://www.dmtf.org/) (DTMF). El archivo Schema. xml utiliza un esquema XML que se describe en el [esquema de asignación de recursos](./resource-mapping-schema.md).

   En el procedimiento siguiente se describe cómo importar los cmdlets de Hyper-V en al modelo de esquema.

#### <a name="importing-cmdlets-into-the-schema"></a>Importación de cmdlets en el esquema

1. Haga clic con el botón secundario en un área en blanco de la ventana del diseñador de esquemas y haga clic en **importar cmdlets**. Aparece el cuadro de diálogo **Asistente para importar cmdlets** .

2. Asegúrese de que el **equipo local** está seleccionado y haga clic en **siguiente**.

3. Asegúrese de que está seleccionado módulos de Windows PowerShell instalados y seleccione Hyper-V en la lista desplegable. Haga clic en **Siguiente**. Haga clic en **Siguiente**.

4. En la lista de **nombres de cmdlet** , seleccione **VM**. Haga clic en **Siguiente**.

5. En este ejemplo, solo se enlazarán los comandos GET y DELETE con cmdlets. Desactive las casillas **crear** y **Actualizar** y asegúrese de que estén activadas las casillas **obtener** y **eliminar** . Asegúrese de que el cmdlet `Get-VM` está seleccionado para **Get**y el cmdlet `Remove-VM` está seleccionado para **eliminar**.

6. Dado que los metadatos de los cmdlets de máquina virtual no especifican un tipo de salida, deberá ejecutar el cmdlet para especificar el tipo de salida. Seleccione **proporcionar el tipo de salida** y haga clic en **Ejecutar cmdlet**. Aparece el cuadro de diálogo **Ejecutar cmdlet** . Haga clic en **Ejecutar**. El cuadro **tipo CLR** se rellena con el tipo de `VirtualMachine`. Haga clic en **Aceptar**y, a continuación, en **siguiente**.

7. De forma predeterminada, se seleccionan todas las propiedades del objeto VirtualMachine. Puede borrar cualquier propiedad que no desee como parte de los datos que se devuelven al solicitar este recurso desde el servicio Web. Haga clic en **Siguiente**.

8. Debe seleccionar al menos una propiedad para usarla como clave. Seleccione **nombre** en la lista y haga clic en **siguiente**.

9. La siguiente ventana permite asignar propiedades del recurso de OData de administración a las propiedades de los cmdlets subyacentes. De forma predeterminada, el asistente asigna propiedades con nombres idénticos. Por ejemplo, la propiedad `ComputerName` del recurso se asigna a la propiedad `ComputerName` de los cmdlets.  Esto le permite especificar la propiedad `ComputerName` en una solicitud al servicio Web y hacer que el valor que especifique se pase al cmdlet `Get-VM`. también se asignan `Id` y `Name` de forma predeterminada.

   10. Haga clic en **siguiente**y, a continuación, en **Finalizar**.

       El recurso de VM aparece ahora en la ventana del diseñador de esquemas. Puede examinar las propiedades y las operaciones asociadas al recurso. A continuación, exportará los archivos de esquema actualizados en el directorio virtual para el servicio Web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportar archivos de esquema desde el diseñador de esquemas

1. Haga clic con el botón secundario en un área en blanco de la ventana del diseñador de esquemas y haga clic en **archivo de esquema** ; **Exportar**. Aparece el cuadro de diálogo **Guardar como** .

2. Navegue al mismo directorio desde el que importó el archivo MOF. Asigne al archivo el mismo nombre que el archivo MOF original (Schema. mof de forma predeterminada) y haga clic en **Guardar**. Confirme que desea sobrescribir el archivo existente.

   Aunque no se indica explícitamente en el cuadro de diálogo **Guardar como** , reemplaza los archivos Schema. mof y Schema. Xml.

## <a name="next-steps"></a>Pasos a seguir

Antes de tener acceso al nuevo recurso de máquina virtual desde el servicio Web de Management OData, debe actualizar el archivo RbacConfiguration. XML para permitir el acceso al módulo de Windows PowerShell de Hyper-V, tal como se describe en configuración de la [autorización basada en roles](./configuring-role-based-authorization.md), y también tendrá que reiniciar el servicio Web.