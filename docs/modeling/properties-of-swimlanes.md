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
ms.openlocfilehash: 0cceeacab44f17eb30184c90f1128b8d2c3528bb
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115361"
---
# <a name="properties-of-swimlanes"></a>Kulvarların Özellikleri
Bir diyagrama kulvarlar ekleyebilirsiniz. Kulvarlar bir diyagramı dikey veya yatay alanlara böler. Kulvarlar içinde görüntülenecek diğer şekilleri tanımlayabilirsiniz. Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Kulvarlar aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Gövde dolgusu rengi|Kulvar gövdesinin dolgusunun rengi.|Beyaz|
|Üst bilgi dolgusu rengi|Kulvar üst bilgisi için olan Fill Color.|Koyu gri|
|Ayırıcı rengi|Ayırıcı çizginin rengi.|Açık gri|
|Ayırıcı çizgisi stili|Ayırıcı çizginin stili (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`veya `Custom`).|`Dash`|
|Ayırıcı kalınlığı|İnç cinsinden Ayırıcı çizginin kalınlığı.|0.03125|
|Metin rengi|Bu Kulvar ile ilişkilendirilen metin Dekoratörleri için kullanılan renk.|Siyah|
|Erişim değiştiricisi|Sınıfın erişim düzeyi (`public` veya `internal`).|Ortak|
|Özel Öznitelikler|Bu kulvara oluşturulan kod sınıfına öznitelikler eklemek için kullanılır.|\<yok >|
|Double türevi üretir|`True`, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları kullanarak özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel Oluşturucusu vardır|`True`, kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Kulvar 'ten oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract` veya `sealed`).|yok|
|Temel kulvar|Bu kulvarın temel sınıfı.|(yok)|
|Name|Bu kulvarın adı.|Geçerli ad|
|Ad alanı|Bu Kulvar ile bağlantılı ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|Araç ipucu nasıl tanımlanır (`fixed`, `variable`veya `none`). `fixed`, `Fixed Tooltip Text` özelliğinin değeri kullanılır; `variable`, araç ipucu özel kodda tanımlanır.|\<yok >|
|Notlar|Bu Kulvar ile ilişkili resmi olmayan notlar.|\<yok >|
|Hizalama|Yatay veya dikey hizalama.|Dikey|
|Başlangıç yüksekliği|Bu kulvarın inç cinsinden başlangıç yüksekliği. Yalnızca yatay kulvarlar için geçerlidir.|0|
|Başlangıç genişliği|Bu kulvarın inç cinsinden başlangıç genişliği. Yalnızca dikey kulvarlar için geçerlidir.|0|
|Metin rengini gösterir|`True`, Kullanıcı oluşturulan Tasarımcıda bir Kulvar rengini ayarlayabilir. Bunu ayarlamak için kulvar şekline sağ tıklayın ve **gösterilen Ekle**' ye tıklayın.|False|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<yok >|
|Görünen Ad|Bu Kulvar sınıfına başvurmak için oluşturulan tasarımcıda görüntülenecek ad.|\<yok >|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<yok >|
|Help anahtar sözcüğü|Bu Kulvar için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<yok >|

## <a name="see-also"></a>Ayrıca bkz.

- [Etki alanına özgü dil araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
