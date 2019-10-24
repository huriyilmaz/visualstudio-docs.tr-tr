---
title: Görüntü Şekillerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: beb401b4056edd8f1edac5e61d02237c60504cd9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748285"
---
# <a name="properties-of-image-shapes"></a>Görüntü Şekillerinin Özellikleri

Görüntü şekillerini, etki alanı sınıflarının oluşturulmuş bir tasarımcıda nasıl göründüğünü belirtmek için kullanabilirsiniz. Sınıfın `Image` özelliğini önceden tanımlanmış bir görüntü dosyasına ayarlayarak bir resim şekli tanımlayın. Aşağıdaki biçimler desteklenir:

- Resimler

- . jpg

- . jpeg

- . bmp

- . wmf

- . EMF

- . png

Varsayılan olarak, görüntü dosyaları gibi tasarımcı kaynak dosyaları **DSL** projesindeki **kaynaklar** klasöründe bulunur.

Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

Resim şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Rengi doldur|Bu şeklin dolgusu rengi.|be|
|Doldur gradyanı modu|Bu şeklin doldur gradyanı modu.|Yatay|
|Varsayılan bağlantı noktalarına sahiptir|@No__t_0, şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|False|
|Ana hat rengi|Bu şeklin ana hat rengi.|siyah|
|Ana hat kesik çizgi stili|Bu şeklin ana hat kesik çizgi stili (düz, kesik çizgi, nokta, çizgi nokta, çizgi dotdot veya özel).|Sağlam|
|Ana hat kalınlığı|Bu şeklin ana hat kalınlığı.|0,03125|
|Metin rengi|Bu şekille ilişkilendirilen metin Dekoratörleri için kullanılan renk.|siyah|
|Erişim değiştiricisi|Geometri şeklinin (public veya internal) erişim değiştiricisi.|Ortak|
|Özel Öznitelikler|Bu şekilden oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none >|
|Double türevi üretir|@No__t_0, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları kullanarak özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel Oluşturucusu vardır|@No__t_0, kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Görüntü şeklinden oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract` veya `sealed`).|yok|
|Temel resim şekli|Bu şeklin temel sınıfı.|seçim|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekille ilişkili ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|ToolTip 'in tanımlandığı yer (sabit, değişken veya yok). Düzeltildiğinde, `Fixed Tooltip Text` özelliğinin değeri araç ipucu olarak kullanılır; değişken ise, araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkili resmi olmayan notlar.|\<none >|
|Başlangıç yüksekliği|Bu şeklin inç cinsinden başlangıç yüksekliği.|1\.|
|Başlangıç genişliği|Bu şeklin inç cinsinden başlangıç genişliği.|1,5|
|Özellik olarak gösterilen Fill Color<br /><br /> Sunulma dolgusu gradyan modu<br /><br /> Özellik olarak gösterilen ana hat rengi<br /><br /> Özellik olarak sunulan ana hat kesik çizgi stili<br /><br /> Sunulan ana hat kalınlığı özellik olarak<br /><br /> Metin rengini gösterir|@No__t_0, Kullanıcı bir şeklin belirtilen özelliğini ayarlayabilir. Bunu ayarlamak için, şekil tanımına sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|False|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none >|
|Görünen ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none >|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none >|
|Help anahtar sözcüğü|Bu öğe için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<none >|
|Görüntü|Bu şekil için kullanılan resim dosyasının yolu.|\<none >|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)