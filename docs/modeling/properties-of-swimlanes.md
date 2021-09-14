---
title: Kulvarların Özellikleri
description: Kullanların bir diyagramı dikey veya yatay alanlara nasıl böldüklerini ve kullanların içinde görüntülenecek diğer şekilleri nasıl tanımlayabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 27df14cad337fcb1ce1dffaeab1d501a6ff549e3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637497"
---
# <a name="properties-of-swimlanes"></a>Kulvarların Özellikleri
Bir diyagrama kullanlar eklersiniz. Kulanlar diyagramı dikey veya yatay alanlara böler. Kulanların içinde görüntülenecek diğer şekilleri tanımlayabilirsiniz. Daha fazla bilgi için [bkz. How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Bu özellikleri kullanma hakkında daha fazla bilgi için, [bkz. Domain-Specific Dili Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Kulanlar aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Gövde DolguSu Rengi|Kulan gövdesinin dolgu rengi.|Beyaz|
|Üst Bilgi Dolgu Rengi|Kulan üst bilgisi için dolgu rengi.|DarkGray|
|Ayırıcı Renk|Ayırıcı çizginin rengi.|LightGray|
|Ayırıcı Çizgi Stili|Ayırıcı çizginin stili ( `Solid` , , , , veya `Dash` `Dot` `DashDot` `DashDotDot` `Custom` ).|`Dash`|
|Ayırıcı Kalınlığı|Ayırıcı çizginin inç olarak kalınlığı.|0.03125|
|Metin Rengi|Bu kullanın ilişkili metin dekoratörleri için kullanılan renk.|Siyahi|
|Erişim Değiştiricisi|sınıfının erişim düzeyi ( veya `public` `internal` ).|Genel|
|Özel Öznitelikler|Bu kullandan oluşturulan kod sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Çift Türetilen|ise, `True` hem temel bir sınıf hem de kısmi bir sınıf (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Özel Oluşturucuya Sahip|ise, `True` kaynak kodunda özel bir oluşturucu sağlanır. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Devralma Değiştiricisi|Kullandan ( veya ) oluşturulan kaynak kod sınıfının `none` devralmanın nasıl olduğunu `abstract` `sealed` açıklar.|yok|
|Taban Kullanı|Bu kullanın temel sınıfı.|(yok)|
|Name|Bu kulistenin adı.|Geçerli ad|
|Ad Alanı|Bu kullana bağlı olan ad alanı.|Geçerli ad alanı|
|Araç İpucu Türü|Araç ipucu nasıl tanımlanır ( `fixed` , `variable` veya `none` ). ise, `fixed` özelliğinin değeri `Fixed Tooltip Text` kullanılır; ise `variable` araç ipucu özel kodda tanımlanır.|\<none>|
|Notlar|Bu kullayla ilişkili resmi olmayan notlar.|\<none>|
|Hizalama|Yatay veya dikey hizalama.|Dikey|
|İlk Yükseklik|Bu kullanın ilk yüksekliği inç olarak. Yalnızca yatay kulanlar için geçerlidir.|0|
|İlk Genişlik|Bu kullanın inç olarak ilk genişliği. Yalnızca dikey kulanlar için geçerlidir.|0|
|Metin Rengini Açığa Çıkarır|ise, `True` kullanıcı oluşturulan tasarımcıda kullanın rengini ayarlamayı da sağlar. Bunu ayarlamak için kullana şekline sağ tıklayın ve Ortaya **Çıkar'ı Ekle'ye tıklayın.**|Yanlış|
|Description|Oluşturulan tasarımcıyı belgeley etmek için kullanılır.|\<none>|
|Görünen Ad|Bu kuliste sınıfına başvurmak için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Araç İpucu Metni Düzeltildi|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Yardım Anahtar Sözcüğü|Bu kullana F1 yardım dizinini eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))