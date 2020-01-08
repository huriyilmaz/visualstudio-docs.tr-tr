---
title: 'Örnek XSD dosyası: satınalma siparişi şeması'
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: f92b63b5-ec61-43b5-ae1e-63432a7a7e30
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d841b75b58dc977b5141dce0b8c7275e4a3ced8a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592574"
---
# <a name="sample-xsd-file-purchase-order-schema"></a>Örnek XSD dosyası: satınalma siparişi şeması

Aşağıdaki XSD dosyası, XSD şema Tasarımcısı belgelerindeki çeşitli örneklerde kullanılır. Bu dosya bir satın alma Siparişi şemadır.

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
          xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
          targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
          elementFormDefault="qualified">
  <xsd:element name='comment' type='xsd:string'/>

  <xsd:element name='purchaseOrder' type='tns:PurchaseOrderType'/>

  <xsd:complexType name='USAddress'>
    <xsd:annotation>
      <xsd:documentation>
        Purchase order schema for Example.Microsoft.com.
      </xsd:documentation>
    </xsd:annotation>
    <xsd:sequence>
      <xsd:element name='name'   type='xsd:string'/>
      <xsd:element name='street' type='xsd:string'/>
      <xsd:element name='city'   type='xsd:string'/>
      <xsd:element name='state'  type='xsd:string'/>
      <xsd:element name='zip'    type='xsd:decimal'/>
    </xsd:sequence>
    <xsd:attribute name='country' type='xsd:NMTOKEN' fixed='US'/>
  </xsd:complexType>

  <xsd:simpleType name='SKU'>
    <xsd:restriction base='xsd:string'>
      <xsd:pattern value='\d{3}\w{3}'/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:complexType name='Items'>
    <xsd:sequence>
      <xsd:element name='item' minOccurs='0' maxOccurs='unbounded'>
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name='productName' type='xsd:string'/>
            <xsd:element name='quantity'>
              <xsd:simpleType>
                <xsd:restriction base='xsd:positiveInteger'>
                  <xsd:minInclusive value='1'/>
                  <xsd:maxExclusive value='100'/>
                </xsd:restriction>
              </xsd:simpleType>
            </xsd:element>
            <xsd:element name='USPrice'  type='xsd:decimal'/>
            <xsd:element ref='tns:comment'/>
            <xsd:element name='shipDate' type='xsd:date' minOccurs='0'/>
          </xsd:sequence>
          <xsd:attribute name='partNum' type='tns:SKU'/>
        </xsd:complexType>
      </xsd:element>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name='PurchaseOrderType'>
    <xsd:sequence>
      <xsd:element name='shipTo' type='tns:USAddress'/>
      <xsd:element name='billTo' type='tns:USAddress'/>
      <xsd:element ref='tns:comment' minOccurs='0'/>
      <xsd:element name='items'  type='tns:Items'/>
    </xsd:sequence>
    <xsd:attribute name='orderDate' type='xsd:date'/>
    <xsd:attribute name='confirmDate' type='xsd:date' use='required'/>
  </xsd:complexType>
</xsd:schema>
```

> [!NOTE]
> Burada adı geçen örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, konumlar ve olaylar hayal ürünüdür. Gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yerler veya etkinliklerle hiçbir ilişki amaçlanmamıştır veya oluşturulmamalıdır.
