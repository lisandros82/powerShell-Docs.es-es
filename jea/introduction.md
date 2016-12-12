---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Introducción"
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="introduction"></a>Introducción

##  <a name="motivation"></a>**Motivaciones**  
Cuando le concede a alguien el acceso con privilegios a los sistemas, está ampliando el límite de confianza a esa persona.
Esto es un riesgo, ya que los administradores son una superficie expuesta a ataques.
Los ataques internos y las credenciales robadas son una realidad habitual.

##  <a name="not-a-new-problem"></a>**No es un problema nuevo**  
Es probable que esté muy familiarizado con el principio del privilegio mínimo y que use algún tipo de control de acceso basado en rol (RBAC) con aplicaciones que lo proporcionan.
Pero la eficacia y la facilidad de uso de estas soluciones suelen verse limitadas por su amplio alcance y su imprecisión.
Además, existen lagunas en la cobertura de RBAC.
Por ejemplo, en Windows, el acceso privilegiado es en gran medida un conmutador binario, que le obliga a conceder permisos innecesarios al agregar usuarios al grupo de administradores.

##  <a name="just-enough-administration-jea"></a>**Just Enough Administration (JEA)** 
Proporciona una plataforma de control de acceso basado en rol, RBAC, mediante el acceso remoto a PowerShell.
*Permite a usuarios específicos realizar tareas administrativas específicas en servidores sin concederles derechos de administrador.*
Esto permite llenar el vacío de las soluciones de RBAC existentes y simplifica la administración de las configuraciones.

