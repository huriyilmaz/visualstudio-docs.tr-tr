---
title: Seçenekler, metin düzenleyici, XML, biçimlendirme
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ccd5fdee974e7222d1009b508b7ef90758fafcb6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666598"
---
# <a name="options-text-editor-xml-formatting"></a>Seçenekler, metin düzenleyici, XML, biçimlendirme

Öğelerin ve özniteliklerin XML belgelerinizde nasıl biçimlendirileceğini belirtmek için **biçimlendirme** seçenekleri sayfasını kullanın. XML biçimlendirme seçeneklerine erişmek için **araçlar**  > **Seçenekler**  > **metin Düzenleyicisi**  > **XML**' i seçin ve ardından **biçimlendirme**' yi seçin.

## <a name="attributes"></a>Öznitelikler

**El ile öznitelik biçimlendirmesini koru**

Öznitelikleri yeniden biçimlendirmeyin. Bu ayar varsayılandır.

> [!NOTE]
> Öznitelikler birden çok satırda varsa, düzenleyici her bir öznitelik satırını üst öğenin girintilemesi ile eşleşecek şekilde girintiler.

**Öznitelikleri her biri ayrı bir satıra hizalayın**

İkinci ve sonraki öznitelikleri ilk özniteliğin girintilemesi ile eşleşecek şekilde dikey olarak hizalayın. Aşağıdaki XML metni özniteliklerin nasıl hizalandığı hakkında bir örnektir:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Otomatik yeniden Biçimlendir

**Panodan yapıştırılırken**

Panodan yapıştırılan XML metnini yeniden biçimlendirin.

**Bitiş etiketi tamamlandığında**

Bitiş etiketi tamamlandığında öğeyi yeniden biçimlendirin.

## <a name="mixed-content"></a>Karışık Içerik

**Karma içeriği varsayılan olarak biçimlendirin.**

İçeriğin bir `xml:space="preserve"` kapsamında bulunması dışında, karışık içeriği yeniden biçimlendirme girişimi. Bu ayar varsayılandır.

Bir öğe metin ve biçimlendirme karışımı içeriyorsa, içerik karışık içerik olarak kabul edilir. Aşağıda, karışık içerikli bir öğe örneği verilmiştir.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML seçenekleri-çeşitli](options-text-editor-xml-miscellaneous.md)
- [Visual Studio 'da XML araçları](../../xml-tools/xml-tools-in-visual-studio.md)