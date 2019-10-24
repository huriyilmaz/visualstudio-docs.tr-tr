---
title: Bölme Şekillerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ad53866c1930edb01ccd163131ce5e23644929c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747505"
---
# <a name="properties-of-compartment-shapes"></a>Bölme Şekillerinin Özellikleri
Bölme şekilleri, etki alanına özgü bir dilde bir etki alanı sınıfını göstermek için kullanabileceğiniz şekillerden biridir. Bölmeleri genişletebilir ve daraltabilirsiniz.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Bölme şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Varsayılan genişletme daraltma durumu|@No__t_0, bölmeleri oluşturma sırasında gösterilir. @No__t_0, bunlar değildir.|Genişletileceğini|
|Rengi doldur|Bu şeklin dolgusu rengi.|be|
|Doldur gradyanı modu|Bu şeklin doldur gradyanı modu.|Yatay|
|Geometrisi|Bu şeklin geometrisi (dikdörtgen veya yuvarlak dikdörtgen).|Dikdörtgen|
|Varsayılan bağlantı noktalarına sahiptir|@No__t_0, şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|False|
|Tek bölme üst bilgisi görünür|@No__t_0 ve şeklin tek bir bölmesi varsa, bölmenin üst bilgisi görünmez.|Doğru|
|Ana hat rengi|Bu şeklin ana hat rengi.|siyah|
|Ana hat kesik çizgi stili|Bu şeklin ana hat kesik çizgi stili (düz, kesik çizgi, nokta, çizgi nokta, çizgi Noktanoktası, özel).|Sağlam|
|Ana hat kalınlığı|Bu şeklin ana hat kalınlığı.|0,03125|
|Metin rengi|Bu şekille ilişkilendirilen metin Dekoratörleri için kullanılan renk.|siyah|
|Erişim değiştiricisi|Bölme şeklinin erişim düzeyi (`public` veya `internal`).|Ortak|
|Özel Öznitelikler|Bu bölme şeklinden oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır|\<none >|
|Double türevi üretir|@No__t_0, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları kullanarak özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel Oluşturucusu vardır|@No__t_0, kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Bölme şeklinden oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract` veya `sealed`).|Yok.|
|Temel bölme şekli|Bu şeklin temel sınıfı.|seçim|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekille ilişkili ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya yok). Düzeltildiğinde, `Fixed Tooltip Text` özelliğinin değeri araç ipucu olarak kullanılır; değişken ise, araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkili resmi olmayan notlar.|\<none >|
|Başlangıç yüksekliği|Bu şeklin inç cinsinden başlangıç yüksekliği. Bölme şekilleri için bu, yalnızca üst bilgi bölümünün yüksekliğidir ve yeniden boyutlandırılmaz.|1\.|
|Başlangıç genişliği|Bu şeklin inç cinsinden başlangıç genişliği.|1,5|
|Özellik olarak gösterilen Fill Color<br /><br /> Sunulma dolgusu gradyan modu<br /><br /> Özellik olarak gösterilen ana hat rengi<br /><br /> Özellik olarak sunulan ana hat kesik çizgi stili<br /><br /> Sunulan ana hat kalınlığı özellik olarak<br /><br /> Metin rengini gösterir|@No__t_0, Kullanıcı bir şeklin belirtilen özelliğini ayarlayabilir. Bunu ayarlamak için, şekil tanımına sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|False|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none >|
|Görünen ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none >|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none >|
|Help anahtar sözcüğü|Bu şekle yönelik F1 yardımını indekslemek için kullanılan anahtar sözcük.|\<none >|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)