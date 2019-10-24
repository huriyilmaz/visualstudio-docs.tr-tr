---
title: Bağlayıcıların Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ba4a9b4ec2e0941b4f8ae924766e8c401342dfd
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748327"
---
# <a name="properties-of-connectors"></a>Bağlayıcıların Özellikleri
Bağlayıcılar, oluşturulan bir tasarımcıda etki alanı ilişkilerini temsil eder.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Bağlayıcılar aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Renk|Bu bağlayıcının rengi.|siyah|
|Kesik çizgi stili|Bu bağlayıcının çizgisi için çizgi stili (düz, kesik çizgi, nokta, çizgi nokta, çizgi dotdot veya özel).|Sağlam|
|Kaynak uç stili|Bu bağlayıcının kaynak uç stili (Hollowok, EmptyArrow, Filledok, Emptyelmas, FilledDiamond veya None).|Yok.|
|Hedef bitiş stili|Bu bağlayıcının hedef uç stili (Hollowok, EmptyArrow, Filledok, Emptyelmas, FilledDiamond veya None).|Yok.|
|Metin rengi|Bu bağlayıcı ile ilişkilendirilen metin Dekoratörleri için kullanılan renk.|siyah|
|Kalınlığı|Bu bağlayıcının inç cinsinden ölçülen çizgi kalınlığı.|0,03125|
|Erişim değiştiricisi|Sınıfın erişim düzeyi (`public` veya `internal`).|Ortak|
|Özel Öznitelikler|Bu bağlayıcıdan oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none >|
|Double türevi üretir|@No__t_0, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları kullanarak özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel Oluşturucusu vardır|@No__t_0, kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Bağlayıcıdan oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract` veya `sealed`).|yok|
|Temel bağlayıcı|Bu bağlayıcının temel sınıfı.|seçim|
|Name|Bu bağlayıcının adı.|Geçerli ad|
|Ad Alanı|Bu bağlayıcıyla ilişkili ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya yok). Düzeltildiğinde, `Fixed Tooltip Text` özelliğinin değeri araç ipucu olarak kullanılır; değişken ise, araç ipucu özel kodda tanımlanır.|\<none >|
|Notlar|Bu bağlayıcı ile ilişkili resmi olmayan notlar.|\<none >|
|Yönlendirme stili|Bağlayıcıyı yönlendirmek için kullanılan stil. @No__t_0 bağlayıcı, gereken şekilde doğru dönüşler yapar; `Straight` Bağlayıcısı değildir.|Rectilinear|
|Özellik olarak sunulan renk<br /><br /> Özellik olarak açığa çıkarılan kesik çizgi stili<br /><br /> Özellik olarak sunulma kalınlığı<br /><br /> Metin rengini gösterir|@No__t_0, Kullanıcı bir şeklin belirtilen özelliğini ayarlayabilir. Bunu ayarlamak için, şekil tanımına sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|False|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none >|
|Görünen ad|Bu bağlayıcı için oluşturulan tasarımcıda görüntülenecek ad.|\<none >|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none >|
|Help anahtar sözcüğü|Bu öğe için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<none >|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)