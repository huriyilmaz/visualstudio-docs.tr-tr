---
title: Etki Alanı Rollerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97df4ceca2c511265a51f89c2f39a6595d200abf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748305"
---
# <a name="properties-of-domain-roles"></a>Etki Alanı Rollerinin Özellikleri
Aşağıdaki tabloda yer alan Özellikler bir etki alanı rolüyle ilişkilendirilir. Etki alanı rolleri hakkında daha fazla bilgi için bkz. [modelleri, sınıfları ve Ilişkileri anlama](../modeling/understanding-models-classes-and-relationships.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Koleksiyon türü|Bu rolün çoğulluğu 0.. * veya 1.. \*, bu özellik bağlantıların koleksiyonunu depolamak için kullanılan genel türü özelleştirir.|`(none)`  -  <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> kullanılıyor|
|Özel Öznitelikler|Burada belirttiğiniz öznitelikler, oluşturulan kod sınıfına öznitelik olarak eklenecektir.|< yok \>|
|Özelliğe gözatılabilir|@No__t_0, ve ilişkinin çoğulluğu 0.. 1 veya 1.. 1 ise, rol özelliğine **Özellikler** penceresindeki Kullanıcı tarafından gözatılabilir. Özelliği, ilişki bağlantısının diğer ucundaki öğesinin adını görüntüler.|`True`|
|Özellik Oluşturucu|@No__t_0, bu rol için Program kodundaki ilişkiyi çapraz geçiş yapmak için kullanabileceğiniz bir rol özelliği oluşturulur. Bu yanlışı ayarlarsanız, etki alanı ilişkisinin Statik yöntemlerini kullanarak ilişkiye daha az etkili bir şekilde geçiş yapabilirsiniz.|`True`|
|Özellik alıcısı erişim değiştiricisi|Oluşturulan Özellik (`public`, `internal`, `private`, `protected` veya `protected internal`) için alıcı erişim değiştiricisi.|`public`|
|Özellik ayarlayıcı erişim değiştiricisi|Oluşturulan özellik için ayarlayıcı için erişim değiştiricisi (`public`, `internal`, `private`, `protected` veya `protected internal`).|`public`|
|Çokluk|Karşıt rolü (`0..1`, `1..1`, `0..*` veya `1..*`) oynatabilir olan model öğelerinin sayısı. Çoğulluk `0..*` veya `1..*`, oluşturulan özellik bir koleksiyonu temsil eder; Aksi takdirde, oluşturulan özellik tek bir model öğesini temsil eder.|İlişki türüne ve bu ilişkide kaynak veya hedef rol olup olmamasına bağlıdır.|
|Name|Etki alanı rolünün adı. Bu özellik boşluk içeremez.|Bu rolün rol oyuncusunun etki alanı sınıfının adı.|
|Kopyayı yayar|`DoNotPropagateCopy`-kopyalanmış rol oyuncusunun bu bağlantının bir kopyası olmayacaktır.<br /><br /> `PropagateCopyToLinkOnly`-kopyalanmış bağlantı var olan karşı rol oyuncusuna işaret eder.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-kopyalanmış bağlantı, karşı rol yürütücüsünün bir kopyasına işaret eder.|katıştırın kaynak rolleri için `PropagateCopyToLinkAndOppositeRolePlayer`.<br /><br /> diğer roller için `DoNotPropagateCopy`.<br /><br /> Daha fazla bilgi için bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md)|
|Silmeyi yayar|ilişkili bağlantı silindiğinde bu rolü yürüten öğeyi silmek `True`.|ekleme rolünün hedefi için `True`.<br /><br /> diğer roller için `False`.|
|Özellik adı|Rol oyuncusunun kodunda oluşturulan özelliğin adı. Bu ad boşluk içeremez.|Bu rol sıfırdan bir veya bire bir çokluğa sahipse ters rolün adı; Aksi takdirde, karşıt rolün plurlaştırılan adı.|
|Rol oynatıcı|İlişkide bu rolü çalasağlayan öğenin etki alanı sınıfı. Bu özellik salt okunurdur.|Bu rol için rol oyuncusunun etki alanı sınıfı.|
|Notlar|Etki alanı rolüyle ilişkili resmi olmayan notlar.|< yok \>|
|Kategori|Oluşturulan tasarımcının **Özellikler** penceresinde oluşturulan özelliğin altında göründüğü kategori. Bu özellik boşsa, oluşturulan özellik, **Sair** kategori altında görünür|< yok \>|
|Açıklama|Kodu belgelemek için kullanılan açıklama ve oluşturulan tasarımcının Kullanıcı arabiriminde kullanılır.<br /><br /> Açıklama, rol oynatıcı sınıfında oluşturulan özelliğin IntelliSense araç ipucunda görüntülenir.|*rolün tam adını* `Description for`|
|Görünen ad|Etki alanı rolü için oluşturulan tasarımcıda görüntülenen ad.|Ad özelliğinin ayarlanmış değeri.|
|Help anahtar sözcüğü|Etki alanı rolü için F1 yardımını dizine eklemek üzere kullanılan isteğe bağlı anahtar sözcük.|\<none >|
|Özellik görünen adı|Oluşturulan rol özelliği için oluşturulan tasarımcıda görüntülenen ad.|Özellik adı özelliğinin ayarlanmış değeri.|

> [!NOTE]
> Bir görünen adının varsayılan değeri, daha önce küçük bir karakter ve ardından başka bir büyük harf karakteri tarafından izlenen her bir büyük/küçük harf öncesinde boşluk ekleyerek ilişkili özellik değerini temel alır.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanı İlişkilerinin Özellikleri](../modeling/properties-of-domain-relationships.md)