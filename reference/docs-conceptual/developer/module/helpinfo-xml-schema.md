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
# <a name="helpinfo-xml-schema"></a>Esquema HelpInfo XML

Este tema contiene el esquema XML para los archivos de información de ayuda actualizable, comúnmente conocidos como "archivos XML HelpInfo".

## <a name="helpinfo-xml-schema"></a>Esquema HelpInfo XML

Los archivos XML HelpInfo se basan en el siguiente esquema XML.

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

HelpContentURI contiene el URI de la ubicación de los archivos. CAB de la ayuda para el módulo. El URI debe comenzar por "http" o "https". El URI debe especificar una ubicación de Internet, pero no debe incluir el nombre del archivo. CAB. El valor de **HelpContentURI** puede ser el mismo o distinto del valor de **HelpInfoURI** .

SupportedUICultures representa los archivos de ayuda del módulo en todas las referencias culturales de la interfaz de usuario. Contiene elementos **UICulture** , cada uno de los cuales representa un conjunto de archivos de ayuda para el módulo en una referencia cultural de interfaz de usuario especificada.

UICulture representa un conjunto de archivos de ayuda para el módulo en una referencia cultural de interfaz de usuario especificada. Agregue un elemento **UICulture** para cada referencia cultural de la interfaz de usuario en la que se escriben los archivos de ayuda.

UICultureName contiene el código de idioma para la referencia cultural de la interfaz de usuario en la que se escriben los archivos de ayuda.

UICultureVersion contiene un número de versión de 4 partes en "N1. N2. N3. N4: el formato que representa la versión del archivo CAB de ayuda en la referencia cultural de la interfaz de usuario. Incremente este número de versión cada vez que cargue nuevos archivos. CAB de ayuda en la referencia cultural de la interfaz de usuario especificada por **UICultureName**. Para obtener más información acerca de este valor, vea "clase de versión (sistema)" en MSDN.