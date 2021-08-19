---
title: 'Örnek XSD Dosyası: Basit Şema'
description: XSD Şema Tasarımcısı belgelerinde çeşitli örneklerde kullanılan basit bir satın alma siparişi şeması için örnek XSD dosyasını görüntüleme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: f7e1dde1-b4f6-4371-add4-935b68ec77d7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 60ce74d0d9463870ea021470fb3a46909fe6416f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114478"
---
# <a name="sample-xsd-file-simple-schema"></a>Örnek XSD dosyası: Basit şema

Aşağıdaki XSD dosyası, XSD Şema Tasarımcısı belgelerinde çeşitli örneklerde kullanılır. Bu dosya basit bir satın alma siparişi şemasıdır.

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
           elementFormDefault="qualified">
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>
 <xsd:complexType name="PurchaseOrderType">
  <xsd:sequence>
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>
   <xsd:element name="BillTo" type="tns:USAddress"/>
  </xsd:sequence>
  <xsd:attribute name="OrderDate" type="xsd:date"/>
 </xsd:complexType>

 <xsd:complexType name="USAddress">
  <xsd:sequence>
   <xsd:element name="name"   type="xsd:string"/>
   <xsd:element name="street" type="xsd:string"/>
   <xsd:element name="city"   type="xsd:string"/>
   <xsd:element name="state"  type="xsd:string"/>
   <xsd:element name="zip"    type="xsd:integer"/>
  </xsd:sequence>
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>
 </xsd:complexType>
</xsd:schema>
```

> [!NOTE]
> Burada gösterilen örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, yerler ve olaylar kurgusaldır. Herhangi bir gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yer veya olayla ilişki amaçlanan veya düşünülen bir ilişki yoktur.
