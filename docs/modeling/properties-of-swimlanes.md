---
title: Kulvarların Özellikleri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ec27b9b4f90b1f3ec75edef6dca01b1ed7b8adf
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90807852"
---
# <a name="properties-of-swimlanes"></a>Kulvarların Özellikleri
Bir diyagrama kulvarlar ekleyebilirsiniz. Kulvarlar bir diyagramı dikey veya yatay alanlara böler. Kulvarlar içinde görüntülenecek diğer şekilleri tanımlayabilirsiniz. Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Kulvarlar aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Gövde dolgusu rengi|Kulvar gövdesinin dolgusunun rengi.|Beyaz|
|Üst bilgi dolgusu rengi|Kulvar üst bilgisi için olan Fill Color.|Koyu gri|
|Ayırıcı rengi|Ayırıcı çizginin rengi.|Açık gri|
|Ayırıcı çizgisi stili|Ayırıcı çizginin stili ( `Solid` , `Dash` ,, `Dot` `DashDot` , `DashDotDot` veya `Custom` ).|`Dash`|
|Ayırıcı kalınlığı|İnç cinsinden Ayırıcı çizginin kalınlığı.|0,03125|
|Metin rengi|Bu Kulvar ile ilişkilendirilen metin Dekoratörleri için kullanılan renk.|Siyahi|
|Erişim değiştiricisi|Sınıfın erişim düzeyi ( `public` veya `internal` ).|Ortak|
|Özel Öznitelikler|Bu kulvara oluşturulan kod sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Double türevi üretir|Eğer `True` bir temel sınıf ve kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|Yanlış|
|Özel Oluşturucusu vardır|İse `True` , kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|Yanlış|
|Devralma değiştiricisi|Kulvardan (veya) oluşturulan kaynak kodu sınıfının devralım türünü açıklar `none` `abstract` `sealed` .|yok|
|Temel kulvar|Bu kulvarın temel sınıfı.|(yok)|
|Name|Bu kulvarın adı.|Geçerli ad|
|Ad Alanı|Bu Kulvar ile bağlantılı ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|Araç ipucu nasıl tanımlanır ( `fixed` , `variable` , veya `none` ). `fixed`Daha sonra `Fixed Tooltip Text` özelliğin değeri kullanılır; varsa `variable` , araç ipucu özel kodda tanımlanır.|\<none>|
|Notlar|Bu Kulvar ile ilişkili resmi olmayan notlar.|\<none>|
|Hizalama|Yatay veya dikey hizalama.|Dikey|
|Başlangıç yüksekliği|Bu kulvarın inç cinsinden başlangıç yüksekliği. Yalnızca yatay kulvarlar için geçerlidir.|0|
|Başlangıç genişliği|Bu kulvarın inç cinsinden başlangıç genişliği. Yalnızca dikey kulvarlar için geçerlidir.|0|
|Metin rengini gösterir|İse `True` , Kullanıcı oluşturulan Tasarımcıda bir Kulvar rengini ayarlayabilir. Bunu ayarlamak için kulvar şekline sağ tıklayın ve **gösterilen Ekle**' ye tıklayın.|Yanlış|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none>|
|Görünen Ad|Bu Kulvar sınıfına başvurmak için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help anahtar sözcüğü|Bu Kulvar için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))