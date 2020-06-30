---
title: Etki Alanı Rollerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c1c62126d65107bb25e3c4a475a794116c47193
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544150"
---
# <a name="properties-of-domain-roles"></a>Etki Alanı Rollerinin Özellikleri
Aşağıdaki tabloda yer alan Özellikler bir etki alanı rolüyle ilişkilendirilir. Etki alanı rolleri hakkında daha fazla bilgi için bkz. [modelleri, sınıfları ve Ilişkileri anlama](../modeling/understanding-models-classes-and-relationships.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Koleksiyon türü|Bu rolün çoğulluğu 0.. * veya 1.. ise \* , bu özellik bağlantıların koleksiyonunu depolamak için kullanılan genel türü özelleştirir.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601>kullanılır|
|Özel Öznitelikler|Burada belirttiğiniz öznitelikler, oluşturulan kod sınıfına öznitelik olarak eklenecektir.|<yok\>|
|Özelliğe gözatılabilir|İse `True` ve ilişkinin çoğulluğu 0.. 1 veya 1.. 1 ise, rol özelliği **Özellikler** penceresinde Kullanıcı tarafından gözatılabilir. Özelliği, ilişki bağlantısının diğer ucundaki öğesinin adını görüntüler.|`True`|
|Özellik Oluşturucu|İse, `True` Bu rol için Program kodundaki ilişkiyi çapraz geçiş yapmak için kullanabileceğiniz bir rol özelliği oluşturulur. Bu yanlışı ayarlarsanız, etki alanı ilişkisinin Statik yöntemlerini kullanarak ilişkiye daha az etkili bir şekilde geçiş yapabilirsiniz.|`True`|
|Özellik alıcısı erişim değiştiricisi|Oluşturulan özelliğin ( `public` , `internal` ,, `private` `protected` veya `protected internal` ) alıcı için erişim değiştiricisi.|`public`|
|Özellik ayarlayıcı erişim değiştiricisi|Oluşturulan özelliğin ( `public` , `internal` ,, `private` `protected` veya `protected internal` ) ayarlayıcı için erişim değiştiricisi.|`public`|
|Çokluk|Karşıt rolü ( `0..1` , `1..1` ,, `0..*` veya) çalabilen model öğelerinin sayısı `1..*` . Çoğulluk veya ise `0..*` `1..*` , oluşturulan özellik bir koleksiyonu temsil eder; Aksi takdirde, oluşturulan özellik tek bir model öğesini temsil eder.|İlişki türüne ve bu ilişkide kaynak veya hedef rol olup olmamasına bağlıdır.|
|Name|Etki alanı rolünün adı. Bu özellik boşluk içeremez.|Bu rolün rol oyuncusunun etki alanı sınıfının adı.|
|Kopyayı yayar|`DoNotPropagateCopy`-Kopyalanmış rol oyuncusunun bu bağlantının bir kopyası olmayacaktır.<br /><br /> `PropagateCopyToLinkOnly`-Kopyalanmış bağlantı var olan karşı rol oyuncusuna işaret eder.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-Kopyalanmış bağlantı, karşı rol yürütücüsünün bir kopyasına işaret eder.|`PropagateCopyToLinkAndOppositeRolePlayer`eklenebilir kaynak roller için.<br /><br /> `DoNotPropagateCopy`diğer roller için.<br /><br /> Daha fazla bilgi için bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md)|
|Silmeyi yayar|`True`ilişkili bağlantı silindiğinde bu rolü yürüten öğeyi silmek için.|`True`bir katıştırma rolünün hedefi için.<br /><br /> `False`diğer roller için.|
|Özellik Adı|Rol oyuncusunun kodunda oluşturulan özelliğin adı. Bu ad boşluk içeremez.|Bu rol sıfırdan bir veya bire bir çokluğa sahipse ters rolün adı; Aksi takdirde, karşıt rolün plurlaştırılan adı.|
|Rol oynatıcı|İlişkide bu rolü çalasağlayan öğenin etki alanı sınıfı. Bu özellik salt okunur durumdadır.|Bu rol için rol oyuncusunun etki alanı sınıfı.|
|Notlar|Etki alanı rolüyle ilişkili resmi olmayan notlar.|<yok\>|
|Kategori|Oluşturulan tasarımcının **Özellikler** penceresinde oluşturulan özelliğin altında göründüğü kategori. Bu özellik boşsa, oluşturulan özellik, **Sair** kategori altında görünür|<yok\>|
|Description|Kodu belgelemek için kullanılan açıklama ve oluşturulan tasarımcının Kullanıcı arabiriminde kullanılır.<br /><br /> Açıklama, rol oynatıcı sınıfında oluşturulan özelliğin IntelliSense araç ipucunda görüntülenir.|`Description for`*rolün tam adı*|
|Görünen Ad|Etki alanı rolü için oluşturulan tasarımcıda görüntülenen ad.|Ad özelliğinin ayarlanmış değeri.|
|Help anahtar sözcüğü|Etki alanı rolü için F1 yardımını dizine eklemek üzere kullanılan isteğe bağlı anahtar sözcük.|\<none>|
|Özellik görünen adı|Oluşturulan rol özelliği için oluşturulan tasarımcıda görüntülenen ad.|Özellik adı özelliğinin ayarlanmış değeri.|

> [!NOTE]
> Bir görünen adının varsayılan değeri, daha önce küçük bir karakter ve ardından başka bir büyük harf karakteri tarafından izlenen her bir büyük/küçük harf öncesinde boşluk ekleyerek ilişkili özellik değerini temel alır.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanı İlişkilerinin Özellikleri](../modeling/properties-of-domain-relationships.md)