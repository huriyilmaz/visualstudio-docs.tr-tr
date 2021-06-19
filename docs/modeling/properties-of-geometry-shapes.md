---
title: Geometri Şekillerinin Özellikleri
description: Etki alanı sınıflarının örneklerinin etki alanına özgü bir dilde nasıl görüntülendiğinden belirtmek için geometri şekillerini nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94eb9ed8050b8a95fde712db4e98bd48f40a72ee
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390391"
---
# <a name="properties-of-geometry-shapes"></a>Geometri Şekillerinin Özellikleri
Etki alanı sınıflarının örneklerinin etki alanına özgü bir dilde nasıl görüntülendiğinden belirtmek için geometri şekillerini kullanabilirsiniz. Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için, [bkz. Domain-Specific Dili Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Geometri şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu Rengi|Bu şeklin dolgu rengi.|Beyaz|
|Dolgu Gradyan Modu|Bu şeklin dolgu gradyan modu (Yatay, Dikey, İleri Çapraz, Ters Çapraz veya Hiçbiri).|Yatay|
|Geometri|Bu şeklin geometrisi (Dikdörtgen, Yuvarlanmış Dikdörtgen, Üç Nokta veya Daire).|Dikdörtgen|
|Varsayılan Bağlantı Noktalarına Sahip|ise, `True` şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|Yanlış|
|Ana Hat Rengi|Bu şeklin ana hat rengi.|Siyahi|
|Çizgi Çizgi Stili|Bu şeklin ana hat çizgi stili (Solid, Dash, Dot, DashDot, DashDotDot veya Custom).|Düz|
|Ana Hat Kalınlığı|Bu şeklin ana hat kalınlığı.|0.03125|
|Metin Rengi|Bu şekille ilişkili metin dekoratörleri için kullanılan renk.|Siyahi|
|Erişim Değiştiricisi|Sınıfın erişim değiştiricisi (genel veya iç).|Genel|
|Özel Öznitelikler|Bu şekil için oluşturulan kaynak kod sınıfına öznitelik eklemek için kullanılır.|\<none>|
|Çift Türetilen|ise, `True` hem temel bir sınıf hem de kısmi bir sınıf (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Özel Oluşturucuya Sahip|ise, `True` kaynak kodunda özel bir oluşturucu sağlanır. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Devralma Değiştiricisi|Şekil ( veya ) ile oluşturulan kaynak kod sınıfının `none` devralmanın nasıl olduğunu `abstract` `sealed` açıklar.|yok|
|Temel Geometri Şekli|Bu şeklin temel sınıfı.|(yok)|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekle bağlı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu Türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya hiçbiri). Sabitse, özellik değeri araç ipucu olarak kullanılır; değişken ise `Fixed Tooltip Text` araç ipucu özel kodda tanımlanır.|Hiçbiri|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar.|\<none>|
|İlk Yükseklik|Bu şeklin ilk yüksekliği inç olarak.|1|
|İlk Genişlik|Bu şeklin inç olarak ilk genişliği.|1,5|
|Dolgu Rengini Özellik Olarak Açığa Çıkar<br /><br /> Açık Dolgu Gradyan Modu<br /><br /> Ana Hat Rengi Özelliği Olarak Açık<br /><br /> Anahat Çizgi Stilini Özellik Olarak Açığa Çıkar<br /><br /> Ana Hat Kalınlığını Özellik Olarak Açığa Çıkar<br /><br /> Metin Rengini Ortaya Çıkarır|ise, `True` kullanıcı şeklin belirtilen özelliğini ayarlayabilirsiniz. Bunu ayarlamak için şekil tanımına sağ tıklayın ve Ortaya **Çıkar'ı Ekle'ye tıklayın.**|Yanlış|
|Açıklama|Oluşturulan tasarımcıyı belgeley etmek için kullanılan açıklama.|\<none>|
|Görünen Ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Araç İpucu Metni Düzeltildi|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help Anahtar Sözcüğü|Bu şekil için F1 yardım dizinini dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))