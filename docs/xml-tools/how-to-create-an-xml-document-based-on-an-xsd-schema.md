---
title: 'Nasıl yapılır: XSD şemasını temel alan XML belgesi oluşturma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f423af7dc4fae7a116acbaf8497c5ee4268653e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645972"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Nasıl yapılır: XSD şemasını temel alan XML belgesi oluşturma

**Örnek XML oluştur** ÖZELLIĞI, XML ŞEMASı (xsd) dosyanızı temel alan örnek bir XML dosyası oluşturur.

Bu seçeneği aşağıdaki senaryolar için kullanabilirsiniz:

- Şemanızda çeşitli yapıların kullanımını anlamak için.

- Şemanın yapması amaçlanan şeyi doğrulamak için.

**Örnek XML oluştur** özelliği yalnızca genel öğelerde kullanılabilir ve geçerlI bir XML şema kümesi gerektirir.

Bu özellik genellikle geçerli XML belgeleri oluşturur. Ancak, şema aşağıdakilerden birini veya birkaçını içeriyorsa, örnek geçerli olmayabilir:

- @No__t_0, `xs:keyref` ve `xs:unique` kimlik kısıtlamaları.

- `xs:pattern` modelleri.

- @No__t_0 türünün Numaralandırmalar.

- `xs:ENTITY`, `xs:ENTITIES` ve `xs:NOTATION` türleri.

Ayrıca, yalnızca bu tür için şemada numaralandırmalar oluşursa `xs:base64Binary` içeriğin üretileceğini aklınızda bulabilirsiniz.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>XSD dosyasını temel alan bir XML örnek belgesi oluşturmak için

1. [Nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. [XML şeması Gezgini](../xml-tools/xml-schema-explorer.md)' nde, `PurchaseOrder` Genel öğesine sağ tıklayın. **Örnek XML oluştur**' u seçin.

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