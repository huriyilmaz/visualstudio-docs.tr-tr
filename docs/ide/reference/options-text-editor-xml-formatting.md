---
title: Seçenekler, metin düzenleyici, XML, biçimlendirme
description: XML belgelerindeki biçimlendirme sayfasını, öğelerin ve özniteliklerin XML belgelerinizde nasıl biçimlendirileceğini belirtmek için nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 4d870026d55cb092b005b0148f392cf29181380e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117143"
---
# <a name="options-text-editor-xml-formatting"></a>Seçenekler, metin düzenleyici, XML, biçimlendirme

Öğelerin ve özniteliklerin XML belgelerinizde nasıl biçimlendirileceğini belirtmek için **biçimlendirme** seçenekleri sayfasını kullanın. XML biçimlendirme seçeneklerine erişmek için **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **XML**' i seçin ve ardından **biçimlendirme**' yi seçin.

## <a name="attributes"></a>Öznitelikler

**El ile öznitelik biçimlendirmesini koru**

Öznitelikleri yeniden biçimlendirmeyin. Bu varsayılan ayardır.

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

İçeriğin bir kapsamda bulunması dışında, karışık içeriği yeniden biçimlendirme girişimi `xml:space="preserve"` . Bu varsayılan ayardır.

Bir öğe metin ve biçimlendirme karışımı içeriyorsa, içerik karışık içerik olarak kabul edilir. Aşağıda, karışık içerikli bir öğe örneği verilmiştir.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML seçenekleri-çeşitli](options-text-editor-xml-miscellaneous.md)
- [Visual Studio'daki XML araçları](../../xml-tools/xml-tools-in-visual-studio.md)
