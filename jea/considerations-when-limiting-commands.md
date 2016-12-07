---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: consideraciones al limitar comandos
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="considerations-when-limiting-commands"></a>Consideraciones al limitar comandos
En este paso, hay que hacer hincapié en un aspecto importante.
Es fundamental que todas las funcionalidades que se exponen a través de JEA se encuentren en áreas restringidas por el administrador.
Los usuarios sin privilegios de administrador no deben tener la capacidad de modificar los scripts que se usan a través de puntos de conexión de JEA.

Además, es fundamental que no ofrezca a los usuarios de JEA la posibilidad de sobrescribir configuraciones de JEA y scripts incluidos en una lista blanca dentro de sus sesiones de JEA.
Es muy importante que tenga mucho cuidado al exponer comandos como `Copy-Item`.

