---
title: Bağlayıcıların Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7bf5492d7da845b65904959cb57737fd438c28b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532281"
---
# <a name="properties-of-connectors"></a>Bağlayıcıların Özellikleri
Bağlayıcılar, oluşturulan bir tasarımcıda etki alanı ilişkilerini temsil eder.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Bağlayıcılar aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Color|Bu bağlayıcının rengi.|Siyahi|
|Kesik çizgi stili|Bu bağlayıcının çizgisi için çizgi stili (düz, kesik çizgi, nokta, çizgi nokta, çizgi dotdot veya özel).|Düz|
|Kaynak uç stili|Bu bağlayıcının kaynak uç stili (Hollowok, EmptyArrow, Filledok, Emptyelmas, FilledDiamond veya None).|Hiçbiri|
|Hedef bitiş stili|Bu bağlayıcının hedef uç stili (Hollowok, EmptyArrow, Filledok, Emptyelmas, FilledDiamond veya None).|Hiçbiri|
|Metin rengi|Bu bağlayıcı ile ilişkilendirilen metin Dekoratörleri için kullanılan renk.|Siyahi|
|Kalınlık|Bu bağlayıcının inç cinsinden ölçülen çizgi kalınlığı.|0,03125|
|Erişim değiştiricisi|Sınıfın erişim düzeyi ( `public` veya `internal` ).|Genel|
|Özel Öznitelikler|Bu bağlayıcıdan oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Double türevi üretir|Eğer `True` bir temel sınıf ve kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|Yanlış|
|Özel Oluşturucusu vardır|İse `True` , kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|Yanlış|
|Devralma değiştiricisi|Bağlayıcıdan oluşturulan kaynak kodu sınıfının devralım türünü açıklar ( `none` `abstract` veya `sealed` ).|yok|
|Temel bağlayıcı|Bu bağlayıcının temel sınıfı.|(yok)|
|Name|Bu bağlayıcının adı.|Geçerli ad|
|Ad Alanı|Bu bağlayıcıyla ilişkili ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya yok). Düzeltildiğinde, `Fixed Tooltip Text` özelliğin değeri araç ipucu olarak kullanılır; değişken ise, araç ipucu özel kodda tanımlanır.|\<none>|
|Notlar|Bu bağlayıcı ile ilişkili resmi olmayan notlar.|\<none>|
|Yönlendirme stili|Bağlayıcıyı yönlendirmek için kullanılan stil. `Rectilinear`Bağlayıcı, gereken şekilde doğru dönüşler yapar; bir `Straight` bağlayıcı değildir.|Rectilinear|
|Özellik olarak sunulan renk<br /><br /> Özellik olarak açığa çıkarılan kesik çizgi stili<br /><br /> Özellik olarak sunulma kalınlığı<br /><br /> Metin rengini gösterir|Eğer `True` Kullanıcı, bir şeklin belirtilen özelliğini ayarlayabilir. Bunu ayarlamak için, şekil tanımına sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|Yanlış|
|Description|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none>|
|Görünen Ad|Bu bağlayıcı için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help anahtar sözcüğü|Bu öğe için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)