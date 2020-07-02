---
title: Bölme Şekillerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51b652adcc482d6e326c0b64eda3a9d32efab309
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532295"
---
# <a name="properties-of-compartment-shapes"></a>Bölme Şekillerinin Özellikleri
Bölme şekilleri, etki alanına özgü bir dilde bir etki alanı sınıfını göstermek için kullanabileceğiniz şekillerden biridir. Bölmeleri genişletebilir ve daraltabilirsiniz.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Bölme şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Varsayılan genişletme daraltma durumu|İse `Expanded` , bölmeleri oluşturma sırasında gösterilir. Aksi takdirde `Collapsed` , bunlar değildir.|Genişletildi|
|Dolgu Rengi|Bu şeklin dolgusu rengi.|Beyaz|
|Doldur gradyanı modu|Bu şeklin doldur gradyanı modu.|Yatay|
|Geometrisi|Bu şeklin geometrisi (dikdörtgen veya yuvarlak dikdörtgen).|Dikdörtgen|
|Varsayılan bağlantı noktalarına sahiptir|İse `True` , şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|False|
|Tek bölme üst bilgisi görünür|`False`Ve şeklin tek bir bölmesi varsa, bölmenin üst bilgisi görünmez.|True|
|Ana hat rengi|Bu şeklin ana hat rengi.|Siyah|
|Ana hat kesik çizgi stili|Bu şeklin ana hat kesik çizgi stili (düz, kesik çizgi, nokta, çizgi nokta, çizgi Noktanoktası, özel).|Düz|
|Ana hat kalınlığı|Bu şeklin ana hat kalınlığı.|0,03125|
|Metin rengi|Bu şekille ilişkilendirilen metin Dekoratörleri için kullanılan renk.|Siyah|
|Erişim değiştiricisi|Bölme şeklinin ( `public` veya) erişim düzeyi `internal` .|Ortak|
|Özel Öznitelikler|Bu bölme şeklinden oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır|\<none>|
|Double türevi üretir|Eğer `True` bir temel sınıf ve kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel Oluşturucusu vardır|İse `True` , kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Devralma değiştiricisi|Bölme şeklinden oluşturulan kaynak kodu sınıfının devralım türünü açıklar ( `none` `abstract` veya `sealed` ).|Hiçbiri|
|Temel bölme şekli|Bu şeklin temel sınıfı.|(yok)|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekille ilişkili ad alanı.|Geçerli ad alanı|
|Araç ipucu türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya yok). Düzeltildiğinde, `Fixed Tooltip Text` özelliğin değeri araç ipucu olarak kullanılır; değişken ise, araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkili resmi olmayan notlar.|\<none>|
|Başlangıç yüksekliği|Bu şeklin inç cinsinden başlangıç yüksekliği. Bölme şekilleri için bu, yalnızca üst bilgi bölümünün yüksekliğidir ve yeniden boyutlandırılmaz.|1|
|Başlangıç genişliği|Bu şeklin inç cinsinden başlangıç genişliği.|1,5|
|Özellik olarak gösterilen Fill Color<br /><br /> Sunulma dolgusu gradyan modu<br /><br /> Özellik olarak gösterilen ana hat rengi<br /><br /> Özellik olarak sunulan ana hat kesik çizgi stili<br /><br /> Sunulan ana hat kalınlığı özellik olarak<br /><br /> Metin rengini gösterir|Eğer `True` Kullanıcı, bir şeklin belirtilen özelliğini ayarlayabilir. Bunu ayarlamak için, şekil tanımına sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|False|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none>|
|Görünen Ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Düzeltilen araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help anahtar sözcüğü|Bu şekle yönelik F1 yardımını indekslemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)