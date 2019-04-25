---
title: Esquema XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082471"
---
# <a name="helpinfo-xml-schema"></a>Esquema HelpInfo XML

Este tema contiene el esquema XML para archivos de información de ayuda actualizable, comúnmente denominados "Archivos XML HelpInfo".

## <a name="helpinfo-xml-schema"></a>Esquema HelpInfo XML

Archivos XML HelpInfo se basan en el siguiente esquema XML.

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

## <a name="helpinfo-xml-elements"></a>Elementos XML HelpInfo

El archivo XML HelpInfo incluye los siguientes elementos.

HelpContentURI contiene el URI de la ubicación de la Ayuda de los archivos .cab para el módulo. El URI debe comenzar por "http" o "https". El URI debe especificar una ubicación de Internet, pero no debe incluir el nombre del archivo CAB. El **HelpContentURI** valor puede ser igual o diferente de la **HelpInfoURI** valor.

SupportedUICultures representa los archivos de Ayuda del módulo en todas las referencias culturales de interfaz de usuario. Contiene **UICulture** elementos, cada uno de los cuales representa un conjunto de archivos de ayuda para el módulo en una referencia cultural de interfaz de usuario especificada.

UICulture representa un conjunto de archivos de ayuda para el módulo en una referencia cultural de interfaz de usuario especificada. Agregar un **UICulture** (elemento) para cada referencia cultural de interfaz de usuario en el que se escriben los archivos de ayuda.

UICultureName contiene el código de idioma para la referencia cultural de interfaz de usuario en el que se escriben los archivos de ayuda.

UICultureVersion contiene un número de versión de 4 partes en "N1. N2. N3. N4 "formato que representa la versión del archivo CAB de ayuda en la referencia cultural de interfaz de usuario. Incremente el número de versión cada vez que carga archivos CAB en la referencia cultural de interfaz de usuario especificado por la nueva ayuda **UICultureName**. Para obtener más información acerca de este valor, vea "Clase de versión (sistema)" en MSDN.