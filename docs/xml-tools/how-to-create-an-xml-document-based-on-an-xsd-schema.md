---
title: 'Nasıl Yapılır: Bir XSD Şemasını Temel Alan XML Belgesi Oluşturma'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 799d27716e7ab2dd621dce04375093f4aff375d7
ms.sourcegitcommit: 4d7c883ea3eedd795eeb4a9d3bd3dee82c8e093e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88893365"
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
