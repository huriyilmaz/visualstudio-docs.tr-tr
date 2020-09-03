---
title: Biçimlendirme, XML, metin düzenleyici, Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670967"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Biçimlendirme, XML, Metin Düzenleyici, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu iletişim kutusu, XML Düzenleyicisi için biçimlendirme ayarlarını belirtmenize olanak tanır. **Seçenekler** Iletişim kutusuna **Araçlar** menüsünden erişebilirsiniz.

> [!NOTE]
> Bu ayarlar, **metin düzenleyici** klasörünü, **XML** klasörünü ve ardından **Seçenekler** iletişim kutusundan **biçimlendirme** seçeneğini belirlediğinizde kullanılabilir.

## <a name="attributes"></a>Öznitelikler
 **El ile öznitelik biçimlendirmesini koru** Öznitelikler yeniden biçimlendirilmedi. Bu varsayılan seçenektir.

> [!NOTE]
> Öznitelikler birden çok satırda varsa, düzenleyici her bir öznitelik satırını üst öğenin girintilemesi ile eşleşecek şekilde girintiler.

 **Öznitelikleri her biri kendi satırlarına hizalayın** İkinci ve sonraki öznitelikleri ilk özniteliğin girintilemesi ile eşleşecek şekilde dikey olarak hizalar. Aşağıdaki XML metni özniteliklerin nasıl hizalandığı hakkında bir örnektir.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Otomatik yeniden Biçimlendir
 **Panodan yapıştırılırken** Panodan yapıştırılan XML metnini yeniden biçimlendirir.

 **Bitiş etiketi tamamlandığında** Bitiş etiketi tamamlandığında öğeyi yeniden biçimlendirir.

## <a name="mixed-content"></a>Karışık Içerik
 **Karma içeriği varsayılan olarak koru** Düzenleyicinin karışık içeriği yeniden biçimlendirir olup olmadığını belirler. Varsayılan olarak düzenleyici, içeriğin bir kapsamda bulunması dışında, karışık içeriği yeniden biçimlendirmeye çalışır `xml:space="preserve"` .

 Bir öğe metin ve biçimlendirme karışımı içeriyorsa, içerik karışık içerik olarak kabul edilir. Aşağıda, karışık içerikli bir öğe örneği verilmiştir.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML belgesi özellikleri, Özellikler penceresi](../xml-tools/xml-document-properties-properties-window.md) [XML Düzenleyicisi bileşenleri](../xml-tools/xml-editor-components.md)
