---
title: XML kod parçacıkları
description: XML kod parçacıklarını yeniden kullanarak ve dosyalarınıza ekerek XML dosyalarını daha hızlı derlemenize olanak sağlayan XML kod parçacıkları özelliği hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 3077cd59a9ab9e051a1e11e9bb1d19117cc0feb7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031854"
---
# <a name="xml-snippets"></a>XML kod parçacıkları

XML düzenleyicisi, XML dosyalarını daha hızlı *derlemenizi* sağlayan XML kod parçacıkları adlı bir özellik sunar. XML kod parçacıklarını dosyalarınıza ek olarak yeniden kullanabilirsiniz. Xml şema tanımlama dili (XSD) şemasını temel alan XML verileri de oluşturabilirsiniz.

## <a name="reusable-xml-snippets"></a>Yeniden kullanılabilir XML kod parçacıkları

XML düzenleyicisi bazı yaygın görevleri içeren birçok kod parçacığı içerir. Bu, XML dosyalarını daha kolay oluşturmanıza olanak sağlar. Örneğin, bir XML şeması yazarsanız, "Karmaşık Tür Dizisi Öğesi" ve "Basit Tür Öğesi" kod parçacıklarını kullanarak dosyanıza aşağıdaki XML metnini ekler. Ardından değeri, `name` ihtiyaçlarınıza uyacak şekilde değiştirebilirsiniz.

```xml
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

Kod parçacıklarını iki şekilde ekleyebilirsiniz. Kod **Parçacığı Ekle** komutu XML kod parçacığını imleç konumunda ekler. Surround **With komutu,** XML kod parçacığını seçili metnin çevresini sarmalar. Her iki komut da Düzenle menüsünün altındaki  **IntelliSense** alt menüsünden veya düzenleyicinin sağ tıklama menüsünden kullanılabilir.

Daha fazla bilgi için, [bkz. How to: Use XML snippets](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Şema tarafından oluşturulan XML kod parçacıkları

XML düzenleyicisi ayrıca bir XML şemasından XML kod parçacığı oluşturma özelliğine de sahip. Bu özellik, bir öğeyi bu öğenin şema bilgilerinden oluşturulan XML öğeleriyle doldurmak için izin verir. Daha fazla bilgi için, [bkz. How to: Generate an XML snippet from an XML schema](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Yeni XML kod parçacıkları oluşturma

Varsayılan olarak, Visual Studio'ye dahil edilen kod parçacıklarına ek olarak kendi XML kod parçacıklarınızı da oluşturabilir ve kullanabilirsiniz. Daha fazla bilgi için, [bkz. How to: Create XML snippets](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod parçacıkları Visual Studio](../ide/code-snippets.md)
- [XML düzenleyicisi](../xml-tools/xml-editor.md)
