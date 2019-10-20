---
title: XML parçacıkları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669358"
---
# <a name="xml-snippets"></a>XML Kod Parçacıkları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML Düzenleyicisi, XML dosyalarını daha hızlı bir şekilde oluşturmanıza olanak sağlayan *XML parçacıkları*adlı bir özellik sunar. XML parçacıklarını dosyalarınıza ekleyerek yeniden kullanabilirsiniz. XML şeması tanım dili (XSD) şemasına göre XML verileri de oluşturabilirsiniz.

## <a name="reusable-xml-snippets"></a>Yeniden kullanılabilir XML parçacıkları
 XML Düzenleyicisi, bazı ortak görevleri kapsayan çok sayıda kod parçacığı içerir. Bu sayede XML dosyalarını daha kolay bir şekilde oluşturabilirsiniz. Örneğin, bir XML şeması yazıyorsanız, "karmaşık tür dizisi öğesi" ve "basit tür öğesi" parçacıkları kullanılarak dosyanıza aşağıdaki XML metni eklenir. Daha sonra `name` değerini gereksinimlerinize uyacak şekilde değiştirirsiniz.

```
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

 Kod parçacıklarını iki şekilde ekleyebilirsiniz. **Kod parçacığı Ekle** komutu, Imleç konumuna XML kod parçacığını ekler. Komutuyla **çevreleme** , XML kod parçacığını seçili metnin çevresinde sarmalanmış. Her iki komut de **düzenleme** menüsünün altındaki **IntelliSense** alt menüsünde veya düzenleyici kısayol menüsünden kullanılabilir.

 Daha fazla bilgi için bkz. [nasıl yapılır: XML kod parçacıkları kullanma](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Şema tarafından oluşturulan XML parçacıkları
 XML Düzenleyicisi, xml şemasından bir XML parçacığı oluşturma özelliğine de sahiptir. Bu özellik, bir öğeyi bu öğe için şema bilgilerden oluşturulan XML öğeleriyle doldurmanıza olanak sağlar.

 Daha fazla bilgi için bkz. [nasıl yapılır: XML ŞEMASıNDAN XML parçacığı oluşturma](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Yeni XML parçacıkları oluşturma
 @No__t_0 Visual Studio 'da bulunan kod parçacıklarına ek olarak, kendi XML kod parçacıklarını da oluşturabilir ve kullanabilirsiniz.

 Daha fazla bilgi için bkz. [nasıl yapılır: XML parçacıkları oluşturma](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)
