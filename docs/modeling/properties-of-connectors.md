---
title: Bağlayıcıların Özellikleri
description: Bağlayıcıların oluşturulmuş bir tasarımcıda etki alanı ilişkilerini temsil ettiğini ve bu özellikleri, etki alanına özgü bir dili özelleştirmek ve genişletmek için kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: ada7d2c78b818c18c9fdf21618ce66595eb9acfd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100770"
---
# <a name="properties-of-connectors"></a>Bağlayıcıların Özellikleri
Bağlayıcılar, oluşturulan bir tasarımcıda etki alanı ilişkilerini temsil eder.

 Daha fazla bilgi için bkz. [Domain-Specific dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Bağlayıcılar aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Renk|Bu bağlayıcının rengi.|Siyahi|
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
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none>|
|Görünen Ad|Bu bağlayıcı için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help anahtar sözcüğü|Bu öğe için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))