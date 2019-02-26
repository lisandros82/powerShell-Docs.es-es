---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Descripción del rol de DSC en una canalización de CI/CD
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803385"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>Descripción del rol de DSC en una canalización de CI/CD

En este artículo se describen los tipos de enfoques que hay disponibles para combinar configuraciones y recursos.
El objetivo de cada escenario es el mismo: reducir la complejidad cuando se prefiere que varias configuraciones alcancen un estado final de implementación de servidor.
Un ejemplo de esto sería cuando varios equipos contribuyen al resultado de una implementación de servidor, como cuando un propietario de la aplicación mantiene el estado de la aplicación y un equipo central libera los cambios realizados en las líneas base de seguridad.
Aquí se detallan los matices de cada enfoque, incluidas las ventajas y los riesgos.

![Canalización](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Tipos de técnicas de creación colaborativa

Hay dos soluciones integradas en el Administrador de configuración local para habilitar este concepto:

| Concepto | Información detallada
|-|-
| Configuraciones parciales | [Documentación](../pull-server/partialConfigs.md)
| Recursos compuestos | [Documentación](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>Comprender el impacto de cada enfoque

Cualquiera de estas soluciones pueden usarse para administrar el resultado de una implementación de servidor.
Pero hay una diferencia importante en el impacto del uso de cada enfoque.

## <a name="partial-configurations"></a>Configuraciones parciales

Al usar configuraciones parciales, el Administrador de configuración local se configura para administrar varias configuraciones de forma independiente.
Las configuraciones se compilan de forma independiente y luego se asignan al nodo.
Para ello hace falta que el Administrador de configuración local esté configurado con antelación con el nombre de cada configuración.

![PartialConfiguration](../images/PartialConfiguration.jpg)

Las configuraciones parciales proporcionan a dos o más equipos el control total de la configuración de un servidor, a menudo sin la ventaja de comunicación o colaboración.

Los clientes nos han informado de que esto puede dar lugar a conflictos de recursos, reemplazos involuntarios y, en última instancia, la pérdida del verdadero control de la configuración del recurso.

Los clientes también nos han informado de que cuando se usa este modelo, los cambios de configuración de los equipos de control no suelen someterse pruebas mediante una canalización de publicación, lo que genera resultados inesperados en la producción.

**Es fundamental que se use una sola canalización para evaluar la publicación de todos los cambios en los servidores.**

En la ilustración de abajo, el equipo B envía su configuración parcial al equipo A. Después, el equipo A realiza sus pruebas en un servidor con las dos configuraciones aplicadas.
En este modelo, solo una entidad tiene permiso para realizar cambios en producción.

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

Cuando se pide al equipo B que realice cambios, este debe enviar una solicitud de incorporación de cambios en el entorno de control de código fuente del equipo A.
Después, el equipo A revisa los cambios mediante la automatización de pruebas y envía la configuración a producción cuando está seguro de que los cambios no provocarán errores en las aplicaciones o los servicios hospedados por el servidor.

## <a name="composite-resources"></a>Recursos compuestos

Un recurso compuesto es simplemente una configuración de DSC empaquetada como un recurso.
No hay ningún requisito especial de configurar el Administrador de configuración local para que acepte los recursos compuestos.
Los recursos se usan dentro de una configuración nueva y una sola compilación da como resultado un archivo MOF.

![CompositeResource](../images/CompositeResource.jpg)

Hay dos escenarios comunes para los recursos compuestos.
El primero consiste en reducir la complejidad y conceptos abstractos únicos.
El segundo es permitir que las líneas base se empaqueten para que un equipo de aplicación pueda implementar de forma segura a través de su canalización de versiones en producción una vez que se hayan superado todas las pruebas.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Los recursos compuestos promueven la composición y la colaboración mediante una canalización durante la compilación de madurez operacional

Es posible que ya esté usando recursos compuestos sin darse cuenta.
Un ejemplo de ello es **ServiceSet**.
Este recurso administra el estado de varios servicios de Windows sin enumerarlos individualmente.
La propiedad Name acepta una matriz de cadenas para proporcionar el nombre de cada servicio.
Cuando se compile la configuración, el MOF contendrá una sección Service única para cada uno de los nombres pasados a ServiceSet.

Las organizaciones pueden tener "agentes" o "middleware" que debe instalarse en todos los servidores.
Un recurso compuesto es la mejor solución para administrar las dependencias, la instalación y la configuración de dichas herramientas y utilidades.

La persona o el equipo responsable de las soluciones que abarcan varios servidores crea una configuración que contiene sus requisitos.
Después, se puede empaquetar la configuración como un recurso compuesto mediante las instrucciones proporcionadas en la documentación del recurso compuesto.
Por último, el nuevo recurso compuesto se debe publicar en una ubicación como un recurso compartido de archivos o una fuente de NuGet donde los equipos de la aplicación puedan usarlo en sus configuraciones.

Cada vez que el equipo publica una nueva versión, aumentaría el número de versión en el manifiesto del módulo para su recurso compuesto.
Los equipos de la aplicación incluyen el recurso compuesto en la configuración que crean para administrar las dependencias de la aplicación.
Cuando los equipos de operaciones/seguridad publican una nueva versión de sus recursos, notifican a los equipos de la aplicación de que hay un cambio nuevo.

Los equipos de la aplicación podrán desencadenar una versión para producción, donde el único cambio son las líneas base.
Pero esto ofrece una oportunidad de evaluar el impacto en las aplicaciones antes de correr el riesgo de una interrupción del servicio.

Nota: Entre los comentarios que hemos recibido sobre el uso de recursos compuestos se criticaba que para hacer cambios hacía falta compilar y publicar un nuevo MOF.
Esto es así por diseño.
Cada nueva versión de configuración debe incluir una referencia estática a una versión específica de cada recurso, y debe ser validada mediante pruebas antes de alcanzar los nodos del servidor de producción.
El proceso de probar y publicar cambios desde el control de código fuente crea un entorno seguro para publicar cambios en lotes pequeños pero frecuentes.

Si quiere saber más sobre el uso de canalizaciones de versiones para administrar la infraestructura básica, vea las notas del producto: [Modelo de canalización de versiones](../further-reading/whitepapers.md).
