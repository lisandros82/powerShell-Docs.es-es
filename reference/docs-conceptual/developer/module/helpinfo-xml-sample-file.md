---
title: Archivo de ejemplo XML de HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 11804db56ec47554e82f04fe6954920ad9577370
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360814"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="b9109-102">Archivo de ejemplo de HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="b9109-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="b9109-103">En este tema se muestra un ejemplo de un archivo de información de ayuda actualizable bien formado, conocido comúnmente como "archivo XML de HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="b9109-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="b9109-104">En este archivo de ejemplo, los elementos de referencia cultural de la interfaz de usuario se organizan en orden alfabético por nombre de referencia cultural de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="b9109-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="b9109-105">El orden alfabético es un procedimiento recomendado, pero no es necesario.</span><span class="sxs-lookup"><span data-stu-id="b9109-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="b9109-106">Archivo de ejemplo de HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="b9109-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>http://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```