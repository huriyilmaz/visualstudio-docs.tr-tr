---
title: Geometri Şekillerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1088dafea1c43e624d029de6b890c9b597b061
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658173"
---
# <a name="properties-of-geometry-shapes"></a>Geometri Şekillerinin Özellikleri
Etki alanı sınıflarının örneklerinin, etki alanına özgü bir dilde nasıl görüntülendiğini belirtmek için geometri şekillerini kullanabilirsiniz. Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Geometri şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Rengi doldur|Bu şeklin dolgusu rengi.|be|
|Doldur gradyanı modu|Bu şeklin (yatay, dikey, Ileri köşegen, geriye doğru köşegen veya yok) dolguyu gradyanı modu.|Yatay|
|Geometrisi|Bu şeklin geometrisi (dikdörtgen, yuvarlatılmış dikdörtgen, elips veya daire).|Dikdörtgen|
|Varsayılan bağlantı noktalarına sahiptir|@No__t_0, şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|False|
|Ana hat rengi|Bu şeklin ana hat rengi.|siyah|
|Ana hat kesik çizgi stili|Bu şeklin ana hat kesik çizgi stili (düz, kesik çizgi, nokta, çizgi nokta, çizgi dotdot veya özel).|Sağlam|
|Ana hat kalınlığı|Bu şeklin ana hat kalınlığı.|0,03125|
|Metin rengi|Bu şekille ilişkilendirilen metin Dekoratörleri için kullanılan renk.|siyah|
|Erişim değiştiricisi|Sınıfın erişim değiştiricisi (genel veya iç).|Ortak|
|Özel Öznitelikler|Bu şekil için oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none >|
|Double türevi üretir|@No__t_0, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları kullanarak özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel Oluşturucusu vardır|@No__t_0, kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Şekilden oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract` veya `sealed`).|yok|
|Taban geometri şekli|Bu şeklin temel sınıfı.|seçim|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekille ilişkili ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya yok). Düzeltildiğinde, `Fixed Tooltip Text` özelliğinin değeri araç ipucu olarak kullanılır; değişken ise, araç ipucu özel kodda tanımlanır.|Yok.|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar.|\<none >|
|Başlangıç yüksekliği|Bu şeklin inç cinsinden başlangıç yüksekliği.|1\.|
|Başlangıç genişliği|Bu şeklin inç cinsinden başlangıç genişliği.|1,5|
|Özellik olarak gösterilen Fill Color<br /><br /> Sunulma dolgusu gradyan modu<br /><br /> Özellik olarak gösterilen ana hat rengi<br /><br /> Özellik olarak sunulan ana hat kesik çizgi stili<br /><br /> Sunulan ana hat kalınlığı özellik olarak<br /><br /> Metin rengini gösterir|@No__t_0, Kullanıcı bir şeklin belirtilen özelliğini ayarlayabilir. Bunu ayarlamak için, şekil tanımına sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|False|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılan açıklama.|\<none >|
|Görünen ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none >|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none >|
|Help anahtar sözcüğü|Bu şekle yönelik F1 yardımını indekslemek için kullanılan anahtar sözcük.|\<none >|

## <a name="see-also"></a>Ayrıca Bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)