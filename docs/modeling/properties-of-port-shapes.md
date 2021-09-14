---
title: Bağlantı Noktası Şekillerinin Özellikleri
description: Bağlantı noktası şekilleri ve oluşturulan tasarımcıda etki alanı sınıflarını temsil etmek için bağlantı noktası şekillerini nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 3aff5311231069b2fa51feebd1124f2b20e8b707
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637494"
---
# <a name="properties-of-port-shapes"></a>Bağlantı Noktası Şekillerinin Özellikleri
Oluşturulan tasarımcıda etki alanı sınıflarını temsil etmek için bağlantı noktası şekillerini kullanabilirsiniz.

 Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için, [bkz. Domain-Specific Dili Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Bağlantı noktası şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu Rengi|Bu şeklin dolgu rengi.|Beyaz|
|Dolgu Gradyan Modu|Bu şeklin dolgu gradyan modu.|Yatay|
|Geometri|Bu şeklin geometrisi (Dikdörtgen, Yuvarlanmış Dikdörtgen, Üç Nokta veya Daire).|Dikdörtgen|
|Varsayılan Bağlantı Noktalarına Sahip|ise, `True` şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|Yanlış|
|Ana Hat Rengi|Bu şeklin ana hat rengi.|Siyahi|
|Çizgi Çizgi Stili|Bu şeklin ana hat çizgi stili (Solid, Dash, Dot, DashDot, DashDotDot veya Custom).|Düz|
|Ana Hat Kalınlığı|Bu şeklin ana hat kalınlığı.|0.03125|
|Metin Rengi|Bu şekille ilişkili metin dekoratörleri için kullanılan renk.|Siyahi|
|Erişim Değiştiricisi|sınıfının erişim düzeyi ( veya `public` `internal` ).|Genel|
|Özel Öznitelikler|Bu şekilde oluşturulan kaynak kod sınıfına öznitelik eklemek için kullanılır.|\<none>|
|Çift Türetilen|ise, `True` hem temel bir sınıf hem de kısmi bir sınıf (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Özel Oluşturucuya Sahip|ise, `True` kaynak kodunda özel bir oluşturucu sağlanır. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Devralma Değiştiricisi|Bağlantı noktası ( veya ) ile oluşturulan kaynak kod sınıfının `none` devralmanın nasıl olduğunu `abstract` `sealed` açıklar.|yok|
|Temel Bağlantı Noktası|Bu şeklin temel sınıfı.|(yok)|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekle bağlı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu Türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya hiçbiri). Sabitse, özellik değeri araç ipucu olarak kullanılır; değişken ise `Fixed Tooltip Text` araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkili resmi olmayan notlar.|\<none>|
|İlk Yükseklik|Bu şeklin ilk yüksekliği inç olarak.|1|
|İlk Genişlik|Bu şeklin inç olarak ilk genişliği.|1,5|
|Dolgu Rengini Özellik Olarak Açığa Çıkar<br /><br /> Açık Dolgu Gradyan Modu<br /><br /> Ana Hat Rengi Özelliği Olarak Açık<br /><br /> Anahat Çizgi Stilini Özellik Olarak Açığa Çıkar<br /><br /> Ana Hat Kalınlığını Özellik Olarak Açığa Çıkar<br /><br /> Metin Rengini Açığa Çıkarır|ise, `True` kullanıcı şeklin belirtilen özelliğini ayarlayabilirsiniz. Bunu ayarlamak için şekil tanımına sağ tıklayın ve Ortaya **Çıkar'ı Ekle'ye tıklayın.**|Yanlış|
|Description|Oluşturulan tasarımcıyı belgeley etmek için kullanılır.|\<none>|
|Görünen Ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Araç İpucu Metni Düzeltildi|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Yardım Anahtar Sözcüğü|Bu şekil için F1 yardım dizinini dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))