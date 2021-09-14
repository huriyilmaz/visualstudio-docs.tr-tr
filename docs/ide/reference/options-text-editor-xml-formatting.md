---
title: Seçenekler, Metin Düzenleyici, XML, Biçimlendirme
description: Öğelerin ve özniteliklerin XML belgelerinize nasıl biçimlendirildiklerini belirtmek için XML bölümündeki Biçimlendirme sayfasını kullanmayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628634"
---
# <a name="options-text-editor-xml-formatting"></a>Seçenekler, Metin Düzenleyici, XML, Biçimlendirme

Öğelerin ve **özniteliklerin** XML belgelerinize nasıl biçimlendirildiklerini belirtmek için Biçimlendirme seçenekleri sayfasını kullanın. XML biçimlendirme seçeneklerine erişmek için Araçlar Seçenekler **Metin Düzenleyici**  >    >    >  **XML'i** ve ardından Biçimlendirme'yi **seçin.**

## <a name="attributes"></a>Öznitelikler

**El ile öznitelik biçimlendirmesini koruma**

Öznitelikleri yeniden biçimlendirme. Bu varsayılan ayardır.

> [!NOTE]
> Öznitelikler birden çok satırda ise, düzenleyici üst öğenin girintilemeyle eşleşmesi için her öznitelik satırına girintiler.

**Öznitelikleri her biri ayrı bir satıra hizalama**

İkinci ve sonraki öznitelikleri ilk özniteliğin girintilemeyle eş olacak şekilde dikey olarak hizalar. Aşağıdaki XML metni özniteliklerin nasıl hizalanmasına bir örnektir:

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Otomatik Yeniden Biçimlendirme

**Panodan yapıştır**

Panodan yapıştıran XML metnini yeniden biçimlendirin.

**Bitiş etiketi tamamlandığında**

End etiketi tamamlandığında öğeyi yeniden biçimlendirin.

## <a name="mixed-content"></a>Karışık İçerik

**Karma içeriği varsayılan olarak biçimlendirin.**

İçeriğin bir kapsamda bulunduğu zaman dışında karışık içeriği yeniden biçimlendirmeyi `xml:space="preserve"` deneme. Bu varsayılan ayardır.

Bir öğe bir metin ve işaretleme karışımı içeriyorsa, içerikler karma içerik olarak kabul edilir. Karma içeriğe sahip bir öğenin örneği aşağıda ve ardından ve veserinin yer alan bir örneği ve ardından 2.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML seçenekleri - çeşitli](options-text-editor-xml-miscellaneous.md)
- [Visual Studio'daki XML araçları](../../xml-tools/xml-tools-in-visual-studio.md)
