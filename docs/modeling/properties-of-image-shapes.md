---
title: Görüntü Şekillerinin Özellikleri
description: Görüntü şekilleri hakkında bilgi edinmek ve etki alanı sınıflarını oluşturulan tasarımcıda nasıl görüntüleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 60061af52e6344cc500d2c00dbeb11b350f3fc8c35560b26ef7bc524e1198a13
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410963"
---
# <a name="properties-of-image-shapes"></a>Görüntü Şekillerinin Özellikleri

Etki alanı sınıflarını oluşturulan tasarımcıda nasıl görüneceklerini belirtmek için görüntü şekillerini kullanabilirsiniz. Sınıfının özelliğini önceden tanımlanmış bir `Image` görüntü dosyası olarak ayarlayarak bir görüntü şekli tanımlayın. Aşağıdaki biçimler de desteklemektedir:

- .gif

- .jpg

- .jpeg

- .bmp

- Wmf

- Emf

- .png

Varsayılan olarak, görüntü dosyaları gibi tasarımcı kaynak dosyaları Dsl **projesinin Kaynaklar** **klasöründe** bulunur.

Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için, bkz. Domain-Specific Dili [Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

Görüntü şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu Rengi|Bu şeklin dolgu rengi.|Beyaz|
|Dolgu Gradyan Modu|Bu şeklin dolgu gradyan modu.|Yatay|
|Varsayılan Bağlantı Noktalarına Sahip|ise, `True` şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|Yanlış|
|Ana Hat Rengi|Bu şeklin ana hat rengi.|Siyahi|
|Çizgi Çizgi Stili|Bu şeklin ana hat çizgi stili (Solid, Dash, Dot, DashDot, DashDotDot veya Custom).|Düz|
|Ana Hat Kalınlığı|Bu şeklin ana hat kalınlığı.|0.03125|
|Metin Rengi|Bu şekille ilişkili metin dekoratörleri için kullanılan renk.|Siyahi|
|Erişim Değiştiricisi|Geometri şeklinin erişim değiştiricisi (genel veya iç).|Genel|
|Özel Öznitelikler|Bu şekilde oluşturulan kaynak kod sınıfına öznitelik eklemek için kullanılır.|\<none>|
|Çift Türetilen|ise, `True` hem temel bir sınıf hem de kısmi bir sınıf (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Özel Oluşturucuya Sahip|ise, `True` kaynak kodunda özel bir oluşturucu sağlanır. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Devralma Değiştiricisi|Görüntü şeklinden ( veya ) oluşturulan kaynak kod sınıfının `none` devralmanın nasıl olduğunu `abstract` `sealed` açıklar.|yok|
|Temel Görüntü Şekli|Bu şeklin temel sınıfı.|(yok)|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekle bağlı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu Türü|Araç ipucu tanımlandığı yer (sabit, değişken veya hiçbiri). Sabitse, özellik değeri araç ipucu olarak kullanılır; değişken ise `Fixed Tooltip Text` araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkili resmi olmayan notlar.|\<none>|
|İlk Yükseklik|Bu şeklin ilk yüksekliği inç olarak.|1|
|İlk Genişlik|Bu şeklin inç olarak ilk genişliği.|1,5|
|Dolgu Rengini Özellik Olarak Açığa Çıkar<br /><br /> Açık Dolgu Gradyan Modu<br /><br /> Ana Hat Rengi Özelliği Olarak Açık<br /><br /> Anahat Çizgi Stilini Özellik Olarak Açığa Çıkar<br /><br /> Ana Hat Kalınlığını Özellik Olarak Açığa Çıkar<br /><br /> Metin Rengini Ortaya Çıkarır|ise, `True` kullanıcı şeklin belirtilen özelliğini ayarlayabilirsiniz. Bunu ayarlamak için şekil tanımına sağ tıklayın ve Ortaya **Çıkar'ı Ekle'ye tıklayın.**|Yanlış|
|Açıklama|Oluşturulan tasarımcıyı belge oluşturmak için kullanılır.|\<none>|
|Görünen Ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Araç İpucu Metni Düzeltildi|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Yardım Anahtar Sözcüğü|Bu öğe için F1 yardım dizinini dizine eklemek için kullanılan anahtar sözcük.|\<none>|
|Görüntü|Bu şekil için kullanılan görüntü dosyasının yolu.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))