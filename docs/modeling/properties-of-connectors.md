---
title: Bağlayıcıların Özellikleri
description: Bağlayıcıların, oluşturulan bir tasarımcıda etki alanı ilişkilerini temsil eden ve etki alanına özgü bir dili özelleştirmek ve genişletmek için bu özellikleri kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: bcc53dda3ce19fb962cd7fe30b0dc7e6fdf6e45d6e27f2194750c36425afe166
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370508"
---
# <a name="properties-of-connectors"></a>Bağlayıcıların Özellikleri
Bağlayıcılar, oluşturulan bir tasarımcıda etki alanı ilişkilerini temsil ediyor.

 Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için, bkz. Domain-Specific Dili [Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Bağlayıcılar aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Renk|Bu bağlayıcının rengi.|Siyahi|
|Tire Stili|Bu bağlayıcının çizgi stili (Solid, Dash, Dot, DashDot, DashDot, DashDotDot veya Custom).|Düz|
|Kaynak Uç Stili|Bu bağlayıcının kaynak uç stili (BoşArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond veya None).|Hiçbiri|
|Hedef Uç Stili|Bu bağlayıcının hedef uç stili (BoşArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond veya None).|Hiçbiri|
|Metin Rengi|Bu bağlayıcıyla ilişkili metin dekoratörleri için kullanılan renk.|Siyahi|
|Kalınlık|Bu bağlayıcının çizgi kalınlığı inç olarak ölçülür.|0.03125|
|Erişim Değiştiricisi|sınıfının erişim düzeyi ( veya `public` `internal` ).|Genel|
|Özel Öznitelikler|Bu bağlayıcıdan oluşturulan kaynak kod sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Çift Türetilen|ise, `True` hem temel bir sınıf hem de kısmi bir sınıf (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Özel Oluşturucuya Sahip|ise, `True` kaynak kodunda özel bir oluşturucu sağlanır. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Devralma Değiştiricisi|Bağlayıcıdan oluşturulan kaynak kod sınıfının devralmanın nasıl olduğunu açıklar ( `none` veya `abstract` `sealed` ).|yok|
|Temel Bağlayıcı|Bu bağlayıcının temel sınıfı.|(yok)|
|Name|Bu bağlayıcının adı.|Geçerli ad|
|Ad Alanı|Bu bağlayıcıya bağlı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu Türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya hiçbiri). Sabitse, özellik değeri araç ipucu olarak kullanılır; değişken ise `Fixed Tooltip Text` araç ipucu özel kodda tanımlanır.|\<none>|
|Notlar|Bu bağlayıcıyla ilişkili resmi olmayan notlar.|\<none>|
|Yönlendirme Stili|Bağlayıcıyı yönlendirme için kullanılan stil. Bağlayıcı, `Rectilinear` gerektiğinde doğru açılı dönüşler yapar; `Straight` bağlayıcı bunu gerektirmez.|Dörtgen|
|Renk Olarak Açığa Çıktı Özelliği<br /><br /> Dash Stili Özellik Olarak Açığa Çıktı<br /><br /> Açık Kalınlık Olarak Özelliği<br /><br /> Metin Rengini Ortaya Çıkarır|ise, `True` kullanıcı şeklin belirtilen özelliğini ayarlayabilirsiniz. Bunu ayarlamak için şekil tanımına sağ tıklayın ve Ortaya **Çıkar'ı Ekle'ye tıklayın.**|Yanlış|
|Açıklama|Oluşturulan tasarımcıyı belgeley etmek için kullanılır.|\<none>|
|Görünen Ad|Bu bağlayıcı için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Araç İpucu Metni Düzeltildi|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help Anahtar Sözcüğü|Bu öğe için F1 yardım dizinini dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))