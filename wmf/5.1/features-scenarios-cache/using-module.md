---
title: FullyQuilifiedModuleName para 'using module'
author: jaimeo
contributor: vors
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: e09cfe0994ac523fd10658955731a93b6c176c88

---

FullyQuilifiedModuleName para 'using module'
=========================

Ahora `using module` se comporta de la misma forma que las restantes construcciones relacionadas con módulos de PowerShell.

Problemas de WMF 5.0
----------

* El usuario no tiene ninguna forma de especificar la versión del módulo en `using module`.
* Si hay multiplicar las versiones del módulo en el sistema, el usuario recibirá un error.

WMF 5.1
----------

* El usuario puede utilizar la `ModuleSpecification`[tabla hash](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx). Esta tabla hash tiene el mismo formato que `Get-Module -FullyQualifiedName`

**Ejemplo:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Si hay varias versiones del módulo de multiplicar, Powershell usa la **misma lógica de resolución** que `Import-Module` y no genera errores.

* Esto alinea `using module` con `Import-Module` y `Import-DscResource`.



<!--HONumber=Aug16_HO3-->


