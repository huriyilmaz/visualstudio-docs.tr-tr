---
title: Görüntü Şekillerinin Özellikleri
description: Görüntü şekilleri hakkında bilgi edinin ve etki alanı sınıflarının oluşturulmuş bir tasarımcıda nasıl göründüğünü belirtmek için görüntü şekillerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50785a4f37b4f3e9e6eaae1bb2a58dcf206af672
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361920"
---
# <a name="properties-of-image-shapes"></a>Görüntü Şekillerinin Özellikleri

Görüntü şekillerini, etki alanı sınıflarının oluşturulmuş bir tasarımcıda nasıl göründüğünü belirtmek için kullanabilirsiniz. `Image`Sınıfın özelliğini önceden tanımlanmış bir görüntü dosyasına ayarlayarak bir resim şekli tanımlayın. Aşağıdaki biçimler desteklenir:

- .gif

- .jpg

- .jpeg

- .bmp

- . wmf

- . EMF

- .png

Varsayılan olarak, görüntü dosyaları gibi tasarımcı kaynak dosyaları **DSL** projesindeki **kaynaklar** klasöründe bulunur.

Daha fazla bilgi için bkz. [Domain-Specific dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

Resim şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu Rengi|Bu şeklin dolgusu rengi.|Beyaz|
|Doldur gradyanı modu|Bu şeklin doldur gradyanı modu.|Yatay|
|Varsayılan bağlantı noktalarına sahiptir|İse `True` , şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|Yanlış|
|Ana hat rengi|Bu şeklin ana hat rengi.|Siyahi|
|Ana hat kesik çizgi stili|Bu şeklin ana hat kesik çizgi stili (düz, kesik çizgi, nokta, çizgi nokta, çizgi dotdot veya özel).|Düz|
|Ana hat kalınlığı|Bu şeklin ana hat kalınlığı.|0,03125|
|Metin rengi|Bu şekille ilişkilendirilen metin Dekoratörleri için kullanılan renk.|Siyahi|
|Erişim değiştiricisi|Geometri şeklinin (public veya internal) erişim değiştiricisi.|Genel|
|Özel Öznitelikler|Bu şekilden oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Double türevi üretir|Eğer `True` bir temel sınıf ve kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|Yanlış|
|Özel Oluşturucusu vardır|İse `True` , kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|Yanlış|
|Devralma değiştiricisi|Görüntü şeklinden oluşturulan kaynak kodu sınıfının devralım türünü açıklar ( `none` `abstract` veya `sealed` ).|yok|
|Temel resim şekli|Bu şeklin temel sınıfı.|(yok)|
|Ad|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekille ilişkili ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|ToolTip 'in tanımlandığı yer (sabit, değişken veya yok). Düzeltildiğinde, `Fixed Tooltip Text` özelliğin değeri araç ipucu olarak kullanılır; değişken ise, araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkili resmi olmayan notlar.|\<none>|
|Başlangıç yüksekliği|Bu şeklin inç cinsinden başlangıç yüksekliği.|1|
|Başlangıç genişliği|Bu şeklin inç cinsinden başlangıç genişliği.|1,5|
|Özellik olarak gösterilen Fill Color<br /><br /> Sunulma dolgusu gradyan modu<br /><br /> Özellik olarak gösterilen ana hat rengi<br /><br /> Özellik olarak sunulan ana hat kesik çizgi stili<br /><br /> Sunulan ana hat kalınlığı özellik olarak<br /><br /> Metin rengini gösterir|Eğer `True` Kullanıcı, bir şeklin belirtilen özelliğini ayarlayabilir. Bunu ayarlamak için, şekil tanımına sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|Yanlış|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none>|
|Görünen Ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help anahtar sözcüğü|Bu öğe için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<none>|
|Görüntü|Bu şekil için kullanılan resim dosyasının yolu.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))