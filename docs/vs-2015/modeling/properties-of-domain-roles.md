---
title: Etki alanı rollerinin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0cddfb3d5c95e5636e9dac069106e3010bedff8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671461"
---
# <a name="properties-of-domain-roles"></a>Etki Alanı Rollerinin Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki tabloda yer alan Özellikler bir etki alanı rolüyle ilişkilendirilir. Etki alanı rolleri hakkında daha fazla bilgi için bkz. [modelleri, sınıfları ve Ilişkileri anlama](../modeling/understanding-models-classes-and-relationships.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|--------------|-----------------|-------------|
|Koleksiyon türü|Bu rolün çoğulluğu 0.. * veya 1.. \*, bu özellik bağlantıların koleksiyonunu depolamak için kullanılan genel türü özelleştirir.|`(none)`  -  <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> kullanılıyor|
|Özel Öznitelikler|Burada belirttiğiniz öznitelikler, oluşturulan kod sınıfına öznitelik olarak eklenecektir.|\<none >|
|Özelliğe gözatılabilir|@No__t_0, ve ilişkinin çoğulluğu 0.. 1 veya 1.. 1 ise, rol özelliğine **Özellikler** penceresindeki Kullanıcı tarafından gözatılabilir. Özelliği, ilişki bağlantısının diğer ucundaki öğesinin adını görüntüler.|`True`|
|Özellik Oluşturucu|@No__t_0, bu rol için Program kodundaki ilişkiyi çapraz geçiş yapmak için kullanabileceğiniz bir rol özelliği oluşturulur. Bu yanlışı ayarlarsanız, etki alanı ilişkisinin Statik yöntemlerini kullanarak ilişkiye daha az etkili bir şekilde geçiş yapabilirsiniz.|`True`|
|Özellik alıcısı erişim değiştiricisi|Oluşturulan Özellik (`public`, `internal`, `private`, `protected` veya `protected internal`) için alıcı erişim değiştiricisi.|`public`|
|Özellik ayarlayıcı erişim değiştiricisi|Oluşturulan özellik için ayarlayıcı için erişim değiştiricisi (`public`, `internal`, `private`, `protected` veya `protected internal`).|`public`|
|Çokluk|Karşıt rolü (`0..1`, `1..1`, `0..*` veya `1..*`) oynatabilir olan model öğelerinin sayısı. Çoğulluk `0..*` veya `1..*`, oluşturulan özellik bir koleksiyonu temsil eder; Aksi takdirde, oluşturulan özellik tek bir model öğesini temsil eder.|İlişki türüne ve bu ilişkide kaynak veya hedef rol olup olmamasına bağlıdır.|
|Name|Etki alanı rolünün adı. Bu özellik boşluk içeremez.|Bu rolün rol oyuncusunun etki alanı sınıfının adı.|
|Kopyayı yayar|`DoNotPropagateCopy`-kopyalanmış rol oyuncusunun bu bağlantının bir kopyası olmayacaktır.<br /><br /> `PropagateCopyToLinkOnly`-kopyalanmış bağlantı var olan karşı rol oyuncusuna işaret eder.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-kopyalanmış bağlantı, karşı rol yürütücüsünün bir kopyasına işaret eder.|katıştırın kaynak rolleri için `PropagateCopyToLinkAndOppositeRolePlayer`.<br /><br /> diğer roller için `DoNotPropagateCopy`.<br /><br /> Daha fazla bilgi için bkz. [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md)|
|Silmeyi yayar|ilişkili bağlantı silindiğinde bu rolü yürüten öğeyi silmek `True`.|ekleme rolünün hedefi için `True`.<br /><br /> diğer roller için `False`.<br /><br /> Daha fazla bilgi için bkz. [silme davranışını özelleştirme](../modeling/customizing-deletion-behavior.md).|
|Özellik adı|Rol oyuncusunun kodunda oluşturulan özelliğin adı. Bu ad boşluk içeremez.|Bu rol sıfırdan bir veya bire bir çokluğa sahipse ters rolün adı; Aksi takdirde, karşıt rolün plurlaştırılan adı.|
|Rol oynatıcı|İlişkide bu rolü çalasağlayan öğenin etki alanı sınıfı. Bu özellik salt okunurdur.|Bu rol için rol oyuncusunun etki alanı sınıfı.|
|Notlar|Etki alanı rolüyle ilişkili resmi olmayan notlar.|\<none >|
|Kategori|Oluşturulan tasarımcının **Özellikler** penceresinde oluşturulan özelliğin altında göründüğü kategori. Bu özellik boşsa, oluşturulan özellik, **Sair** kategori altında görünür|\<none >|
|Açıklama|Kodu belgelemek için kullanılan açıklama ve oluşturulan tasarımcının Kullanıcı arabiriminde kullanılır.<br /><br /> Açıklama, rol oynatıcı sınıfında oluşturulan özelliğin IntelliSense araç ipucunda görüntülenir.|*rolün tam adını* `Description for`|
|Görünen ad|Etki alanı rolü için oluşturulan tasarımcıda görüntülenen ad.|Ad özelliğinin ayarlanmış değeri.|
|Help anahtar sözcüğü|Etki alanı rolü için F1 yardımını dizine eklemek üzere kullanılan isteğe bağlı anahtar sözcük.|\<none >|
|Özellik görünen adı|Oluşturulan rol özelliği için oluşturulan tasarımcıda görüntülenen ad.|Özellik adı özelliğinin ayarlanmış değeri.|

> [!NOTE]
> Bir görünen adının varsayılan değeri, daha önce küçük bir karakter ve ardından başka bir büyük harf karakteri tarafından izlenen her bir büyük/küçük harf öncesinde boşluk ekleyerek ilişkili özellik değerini temel alır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Etki Alanı İlişkilerinin Özellikleri](../modeling/properties-of-domain-relationships.md)
