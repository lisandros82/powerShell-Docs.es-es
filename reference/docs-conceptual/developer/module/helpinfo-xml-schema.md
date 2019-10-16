---
title: Esquema XML de HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360744"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="9bf06-102">Esquema HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="9bf06-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="9bf06-103">Este tema contiene el esquema XML para los archivos de información de ayuda actualizable, comúnmente conocidos como "archivos XML HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="9bf06-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="9bf06-104">Esquema HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="9bf06-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="9bf06-105">Los archivos XML HelpInfo se basan en el siguiente esquema XML.</span><span class="sxs-lookup"><span data-stu-id="9bf06-105">HelpInfo XML files are based on the following XML schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="9bf06-106">Elementos XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="9bf06-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="9bf06-107">El archivo XML HelpInfo incluye los siguientes elementos.</span><span class="sxs-lookup"><span data-stu-id="9bf06-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="9bf06-108">HelpContentURI contiene el URI de la ubicación de los archivos. CAB de la ayuda para el módulo.</span><span class="sxs-lookup"><span data-stu-id="9bf06-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="9bf06-109">El URI debe comenzar por "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="9bf06-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="9bf06-110">El URI debe especificar una ubicación de Internet, pero no debe incluir el nombre del archivo. CAB.</span><span class="sxs-lookup"><span data-stu-id="9bf06-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="9bf06-111">El valor de **HelpContentURI** puede ser el mismo o distinto del valor de **HelpInfoURI** .</span><span class="sxs-lookup"><span data-stu-id="9bf06-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="9bf06-112">SupportedUICultures representa los archivos de ayuda del módulo en todas las referencias culturales de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9bf06-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="9bf06-113">Contiene elementos **UICulture** , cada uno de los cuales representa un conjunto de archivos de ayuda para el módulo en una referencia cultural de interfaz de usuario especificada.</span><span class="sxs-lookup"><span data-stu-id="9bf06-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="9bf06-114">UICulture representa un conjunto de archivos de ayuda para el módulo en una referencia cultural de interfaz de usuario especificada.</span><span class="sxs-lookup"><span data-stu-id="9bf06-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="9bf06-115">Agregue un elemento **UICulture** para cada referencia cultural de la interfaz de usuario en la que se escriben los archivos de ayuda.</span><span class="sxs-lookup"><span data-stu-id="9bf06-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="9bf06-116">UICultureName contiene el código de idioma para la referencia cultural de la interfaz de usuario en la que se escriben los archivos de ayuda.</span><span class="sxs-lookup"><span data-stu-id="9bf06-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="9bf06-117">UICultureVersion contiene un número de versión de 4 partes en "N1. N2. N3. N4: el formato que representa la versión del archivo CAB de ayuda en la referencia cultural de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9bf06-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="9bf06-118">Incremente este número de versión cada vez que cargue nuevos archivos. CAB de ayuda en la referencia cultural de la interfaz de usuario especificada por **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="9bf06-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="9bf06-119">Para obtener más información acerca de este valor, vea "clase de versión (sistema)" en MSDN.</span><span class="sxs-lookup"><span data-stu-id="9bf06-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>