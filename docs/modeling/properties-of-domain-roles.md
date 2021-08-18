---
title: Etki Alanı Rollerinin Özellikleri
description: Koleksiyon Türü, Özel Öznitelikler ve Özellik Gözatılabilir gibi bir etki alanı rolüyle ilişkili özellikler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: f542faecf3ba1ac64076f145cc1e280cf255aad6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085578"
---
# <a name="properties-of-domain-roles"></a>Etki Alanı Rollerinin Özellikleri
Aşağıdaki tablodaki özellikler bir etki alanı rolüyle ilişkilendirildi. Etki alanı rolleri hakkında bilgi için [bkz. Modelleri, Sınıfları ve İlişkileri Anlama.](../modeling/understanding-models-classes-and-relationships.md) Bu özellikleri kullanma hakkında daha fazla bilgi için, bkz. Domain-Specific Dili [Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Koleksiyon Türü|Bu rol 0..* veya 1.. çokluğuna sahipse, bu özellik bağlantı koleksiyonunu depolamak için kullanılan \* genel türü özeller.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> kullanılır|
|Özel Öznitelikler|Burada belirttiğiniz öznitelikler, oluşturulan kod sınıfına öznitelik olarak eklenir.|<yok\>|
|Özellik Gözatılabilir mi?|`True`İlişkinin çokluğu 0...1 veya 1..1 ise, rol özelliği Özellikler penceresinde kullanıcı tarafından **göz atabilir.** özelliği, ilişki bağlantısının diğer ucunda öğenin adını görüntüler.|`True`|
|Özellik Oluşturucu|ise, bu rol için program kodunda ilişkiyi çapraz geçiş yapmak `True` için kullanabileceğiniz bir rol özelliği oluşturulur. Bu false'i ayarsanız, etki alanı ilişkisinin statik yöntemlerini kullanarak ilişkiyi daha az verimli bir şekilde geçirebilirsiniz.|`True`|
|Özellik Değiştiricisi Erişim Değiştiricisi|Oluşturulan özelliğin ( , , , veya ) değiştiricisi için `public` `internal` erişim `private` `protected` `protected internal` değiştiricisi.|`public`|
|Özellik Ayarlayıcısı Erişim Değiştiricisi|Oluşturulan özellik ( , , , veya ) için ayarlayıcı `public` `internal` için erişim `private` `protected` `protected internal` değiştiricisi.|`public`|
|Çokluk|Karşıt rolü ( , , veya ) oynatacak `0..1` `1..1` model `0..*` öğelerinin `1..*` sayısı. Çokluğun veya ise, oluşturulan özellik bir koleksiyonu temsil eder; aksi takdirde, oluşturulan özellik `0..*` tek bir model öğesini temsil `1..*` eder.|İlişki türüne ve bunun ilişkide kaynak veya hedef rol olup olmadığına bağlıdır.|
|Name|Etki alanı rolünün adı. Bu özellik boşluk içerenin.|Bu rol için rol oynatıcının etki alanı sınıfının adı.|
|Kopya yayma|`DoNotPropagateCopy` - Kopyalanan rol oynatıcıda bu bağlantının hiçbir kopyası olmaz.<br /><br /> `PropagateCopyToLinkOnly` - Kopyalanan bağlantı, mevcut karşıt rol oynatıcısını ifade ediyor.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` - Kopyalanan bağlantı, karşıt rol oynatıcının bir kopyasının olduğunu ifade ediyor.|`PropagateCopyToLinkAndOppositeRolePlayer` eklemelerin kaynak rolleri için.<br /><br /> `DoNotPropagateCopy` diğer roller için.<br /><br /> Daha fazla bilgi için [bkz. Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)|
|Yayın Silme|`True` ilişkili bağlantı silindiğinde bu rolü üsten öğeyi silmek için.|`True` ekleme rolünün hedefi için.<br /><br /> `False` diğer roller için.|
|Özellik Adı|Rol oynatıcının kodunda oluşturulan özelliğin adı. Bu ad boşluk içeramaz.|Bu rol sıfırdan bire veya bire bir çokluğuna sahipse, karşıt rolün adı; aksi takdirde, karşıt rolün çoğullaştırılmış adı.|
|Rol Oynatıcısı|İlişkide bu rolü oynatacak öğenin etki alanı sınıfı. Bu özellik salt okunur durumdadır.|Bu rolün rol oynatıcısı etki alanı sınıfı.|
|Notlar|Etki alanı rolüyle ilişkili resmi olmayan notlar.|<yok\>|
|Kategori|Oluşturulan özelliğin, oluşturulan tasarımcının **Özellikler penceresinde** göründüğü kategori. Bu özellik boşsa, oluşturulan özellik **Misc** kategorisi altında görünür|<yok\>|
|Açıklama|Kodu belgeley için kullanılan ve oluşturulan tasarımcının kullanıcı arabiriminde kullanılan açıklama.<br /><br /> Açıklama, rol oynatıcısı sınıfında oluşturulan özelliğin IntelliSense araç ipucunda görünür.|`Description for`*rolün tam adı*|
|Görünen Ad|Etki alanı rolü için oluşturulan tasarımcıda görüntülenen ad.|Name özelliğinin ayarlanmış değeri.|
|Help Anahtar Sözcüğü|Etki alanı rolü için F1 yardım dizinini dizine eklemek için kullanılan isteğe bağlı anahtar sözcük.|\<none>|
|Özellik Görünen Adı|Oluşturulan rol özelliği için oluşturulan tasarımcıda görüntülenen ad.|Özellik Adı özelliğinin ayarlanmış değeri.|

> [!NOTE]
> Görünen adın varsayılan değeri, önüne küçük harf karakteri gelen ve ardından başka bir büyük harf karakteri gelen her büyük harf karakterden önce boşluklar ekerek ilişkili özellik değerini temel almaktadır.

## <a name="see-also"></a>Ayrıca bkz.

- [Etki Alanı İlişkilerinin Özellikleri](../modeling/properties-of-domain-relationships.md)