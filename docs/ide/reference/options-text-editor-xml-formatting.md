---
title: Seçenekler, Metin Düzenleyicisi, XML, Biçimlendirme
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568145"
---
# <a name="options-text-editor-xml-formatting"></a>Seçenekler, Metin Düzenleyicisi, XML, Biçimlendirme

Öğelerin ve özniteliklerin XML belgelerinizde nasıl biçimlendirilir belirtmek için **Biçimlendirme** seçenekleri sayfasını kullanın. XML biçimlendirme seçeneklerine erişmek için **Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **XML'i**seçin ve ardından **Biçimlendirme'yi**seçin.

## <a name="attributes"></a>Öznitelikler

**El ile öznitelik biçimlendirmeyi koruma**

Nitelikleri yeniden biçimletmeyin. Bu varsayılan ayardır.

> [!NOTE]
> Öznitelikler birden çok satırdaysa, düzenleyici ana öğenin girintisi ile eşleşecek her öznitelik satırı girintisi.

**Öznitelikleri ayrı bir satırda hizalama**

İlk öznitelik girintisi maç için dikey olarak ikinci ve sonraki öznitelikleri hizala. Aşağıdaki XML metni özniteliklerin nasıl hizalanacağının bir örneğidir:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Oto Reformat

**Panodan yapıştır'da**

Reformat XML metni panodan yapıştırıldı.

**Bitiş etiketinin tamamlanmasıüzerine**

Bitiş etiketi tamamlandığında öğeyi yeniden biçime der.

## <a name="mixed-content"></a>Karışık İçerik

**Karışık içeriği varsayılan olarak biçimlendirin.**

İçerik bir `xml:space="preserve"` kapsamda bulunduğu durumlar dışında, karışık içeriği yeniden biçimleme girişiminde bulunun. Bu varsayılan ayardır.

Bir öğe metin ve biçimlendirme nin bir karışımını içeriyorsa, içeriği karışık içerik olarak kabul edilir. Aşağıda karışık içeriğe sahip bir öğe örneği verilmiştir.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML seçenekleri - çeşitli](options-text-editor-xml-miscellaneous.md)
- [Visual Studio'da XML araçları](../../xml-tools/xml-tools-in-visual-studio.md)
