---
title: 'Nasıl yapılır: XSD şemasını temel alan XML belgesi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e48c48d6711a1eb21157122d13790e22688855
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670943"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Nasıl Yapılır: Bir XSD Şemasını Temel Alan XML Belgesi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>XSD dosyasını temel alan bir XML örnek belgesi oluşturmak için

1. [Nasıl yapılır: xsd şema dosyası oluşturma ve düzenleme](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)bölümündeki adımları izleyin.

2. [XML şeması Gezgini](../xml-tools/xml-schema-explorer.md)' nde, Genel öğesine sağ tıklayın `PurchaseOrder` . **Örnek XML oluştur**' u seçin.

     Bu seçeneği belirlediğinizde, XML düzenleyicisinde aşağıdaki örnek XML içeriğine sahip PurchaseOrder.xml dosyası oluşturulur ve açılır:

    ```
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

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Verileriyle Çalışma](../xml-tools/working-with-xml-data.md)
