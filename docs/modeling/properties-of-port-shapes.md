---
title: Bağlantı Noktası Şekillerinin Özellikleri
description: Bağlantı noktası şekilleri ve oluşturulan tasarımcıda etki alanı sınıflarını göstermek için bağlantı noktası şekillerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5994d2629a49757980695ca99a6d12ae21160a6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386533"
---
# <a name="properties-of-port-shapes"></a>Bağlantı Noktası Şekillerinin Özellikleri
Oluşturulan tasarımcıda etki alanı sınıflarını göstermek için bağlantı noktası şekillerini kullanabilirsiniz.

 Daha fazla bilgi için bkz. [Domain-Specific dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Bağlantı noktası şekilleri aşağıdaki tabloda listelenen özelliklere sahiptir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu Rengi|Bu şeklin dolgusu rengi.|Beyaz|
|Doldur gradyanı modu|Bu şeklin doldur gradyanı modu.|Yatay|
|Geometri|Bu şeklin geometrisi (dikdörtgen, yuvarlatılmış dikdörtgen, elips veya daire).|Dikdörtgen|
|Varsayılan bağlantı noktalarına sahiptir|İse `True` , şekil oluşturulan tasarımcıda üst, alt, sol ve sağ bağlantı noktalarını kullanır.|Yanlış|
|Ana hat rengi|Bu şeklin ana hat rengi.|Siyahi|
|Ana hat kesik çizgi stili|Bu şeklin ana hat kesik çizgi stili (düz, kesik çizgi, nokta, çizgi nokta, çizgi dotdot veya özel).|Düz|
|Ana hat kalınlığı|Bu şeklin ana hat kalınlığı.|0,03125|
|Metin rengi|Bu şekille ilişkilendirilen metin Dekoratörleri için kullanılan renk.|Siyahi|
|Erişim değiştiricisi|Sınıfın erişim düzeyi ( `public` veya `internal` ).|Genel|
|Özel Öznitelikler|Bu şekilden oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Double türevi üretir|Eğer `True` bir temel sınıf ve kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz [. oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Özel Oluşturucusu vardır|İse `True` , kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|Yanlış|
|Devralma değiştiricisi|Bağlantı noktasından (veya) oluşturulan kaynak kodu sınıfının devralım türünü açıklar `none` `abstract` `sealed` .|yok|
|Temel bağlantı noktası|Bu şeklin temel sınıfı.|(yok)|
|Name|Bu şeklin adı.|Geçerli ad|
|Ad Alanı|Bu şekille ilişkili ad alanı.|Geçerli ad alanı|
|Araç Ipucu türü|Araç ipucu nasıl tanımlanır (sabit, değişken veya yok). Düzeltildiğinde, `Fixed Tooltip Text` özelliğin değeri araç ipucu olarak kullanılır; değişken ise, araç ipucu özel kodda tanımlanır.|yok|
|Notlar|Bu şekille ilişkili resmi olmayan notlar.|\<none>|
|Başlangıç yüksekliği|Bu şeklin inç cinsinden başlangıç yüksekliği.|1|
|Başlangıç genişliği|Bu şeklin inç cinsinden başlangıç genişliği.|1,5|
|Özellik olarak gösterilen Fill Color<br /><br /> Sunulma dolgusu gradyan modu<br /><br /> Özellik olarak gösterilen ana hat rengi<br /><br /> Özellik olarak sunulan ana hat kesik çizgi stili<br /><br /> Sunulan ana hat kalınlığı özellik olarak<br /><br /> Metin rengini gösterir|Eğer `True` Kullanıcı, bir şeklin belirtilen özelliğini ayarlayabilir. Bunu ayarlamak için, şekil tanımına sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|Yanlış|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılır.|\<none>|
|Görünen Ad|Bu şekil için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Sabit araç Ipucu metni|Sabit bir araç ipucu için kullanılan metin.|\<none>|
|Help anahtar sözcüğü|Bu şekle yönelik F1 yardımını indekslemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))