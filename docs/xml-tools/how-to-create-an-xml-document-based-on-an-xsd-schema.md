---
title: 'Nasıl Yapılır: Bir XSD Şemasını Temel Alan XML Belgesi Oluşturma'
description: Bir XSD şemasına dayalı bir XML belgesi oluşturmak için örnek XML oluştur özelliğini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: b057b4fa8670e1b7ed4c1f320a2e32b488fca172
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025114"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Nasıl yapılır: XSD şemasını temel alan XML belgesi oluşturma

**Örnek XML oluştur** ÖZELLIĞI, XML ŞEMASı (xsd) dosyanızı temel alan örnek bir XML dosyası oluşturur.

Bu seçeneği aşağıdaki senaryolar için kullanabilirsiniz:

- Şemanızda çeşitli yapıların kullanımını anlamak için.

- Şemanın yapması amaçlanan şeyi doğrulamak için.

**Örnek XML oluştur** özelliği yalnızca genel öğelerde kullanılabilir ve geçerlI bir XML şema kümesi gerektirir.

Bu özellik genellikle geçerli XML belgeleri oluşturur. Ancak, şema aşağıdakilerden birini veya birkaçını içeriyorsa, örnek geçerli olmayabilir:

- `xs:key`, `xs:keyref` Ve `xs:unique` Kimlik kısıtlamaları.

- `xs:pattern` lerle.

- Türün numaralandırmalar `xs:QName` .

- `xs:ENTITY`, `xs:ENTITIES` ve `xs:NOTATION` türleri.

Ayrıca, `xs:base64Binary` içeriğin yalnızca bu tür için şemada numaralandırmalar oluşması durumunda üretilecek olduğunu unutmayın.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>XSD dosyasını temel alan bir XML örnek belgesi oluşturmak için

1. [Nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. [XML şema Gezgini](../xml-tools/xml-schema-explorer.md)' nde, Genel öğesine sağ tıklayın `PurchaseOrder` ve **örnek XML oluştur**' u seçin.

     Bu seçeneği belirlediğinizde, PurchaseOrder. Aşağıdaki örnek XML içeriğine sahip *XML* dosyası oluşturulacak ve XML düzenleyicisinde açılacak:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```
