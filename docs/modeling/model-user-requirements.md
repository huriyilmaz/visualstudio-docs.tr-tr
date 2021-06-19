---
title: Kullanıcı gereksinimlerini modelleme
description: Kullanıcı Visual Studio etkinlikleriyle ilgili diyagramlar çizerek kullanıcı ihtiyaçlarını anlamanıza, tartışmanıza ve iletişim kurmanıza nasıl yardımcı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 381395eb0b9dabde0e94c479cb43033bc8443c8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390157"
---
# <a name="model-user-requirements"></a>Kullanıcı gereksinimlerini modelleme

Visual Studio etkinlikleri ve sisteminizin hedeflerine ulaşmalarına yardımcı olmak için oynadığı parça hakkında diyagramlar çizerek kullanıcı ihtiyaçlarını anlamanıza, tartışmanıza ve iletişim kurmanıza yardımcı olur. Gereksinimler modeli, her biri kullanıcıların ihtiyaçlarının farklı bir yönüne odaklanan bu diyagramlardan bir kümedir. Bir video gösterimi için bkz. [İş Etki Alanını Modelleme.](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)

Her model türünü destekleyen Visual Studio sürümlerini görmek için [bkz. Mimari ve modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

Gereksinimler modeli şunları sağlar:

- Sistemin iç tasarımından ayrı olarak dış davranışına odaklanın.

- Kullanıcıların ve proje katılımcılarının ihtiyaçlarını doğal dilden çok daha az belirsizlikle açıkla.

- Kullanıcılar, geliştiriciler ve testçiler tarafından kullanılan tutarlı bir terim sözlüğü tanımlayın.

- Gereksinimlerde boşlukları ve tutarsızlıkları azaltma.

- Gereksinimler değişikliklerine yanıt vermek için gereken işi azaltma.

- Özelliklerin hangi sırayla geliştirileceklerini planla.

- Modelleri sistem testleri için temel olarak kullanarak testler ile gereksinimler arasında net bir ilişki sağlar. Gereksinimler değiştiklerinde bu ilişki testleri doğru güncelleştirmenizi sağlar. Bu, sistemin yeni gereksinimleri karşılamalarını sağlar.

Gereksinimler modeli, kullanıcılarla veya temsilcileriyle tartışmalara odaklanmak ve her yinelemenin başında yeniden ziyaret etmek için bunu kullanırsanız en büyük avantajı sağlar. Kod yazmadan önce ayrıntılı bir şekilde tamamlamanız gerek değildir. Çok basitleştirilmiş olsa bile kısmen çalışan bir uygulama, gereksinimleri kullanıcılarla tartışmanın en etkili temelini oluşturur. Model, bu tartışmaların sonuçlarını özetlemek için etkili bir yol sağlar. Daha fazla bilgi için [bkz. Geliştirme sürecinize modelleri kullanma.](../modeling/use-models-in-your-development-process.md)

> [!NOTE]
> Bu konu başlıkları boyunca "sistem", geliştirmekte olduğunuz sistem veya uygulama anlamına gelir. Birçok yazılım ve donanım bileşeninden büyük bir koleksiyon olabilir; veya tek bir uygulama; veya daha büyük bir sistem içindeki bir yazılım bileşeni. Her durumda gereksinimler modeli, ister kullanıcı arabirimi ister API olsun, sistemin dışından görünen davranışı açıklar.

## <a name="common-tasks"></a>Genel görevler

Kullanıcıların gereksinimlerinin birkaç farklı görünümlerini oluşturabilirsiniz.  Her görünüm belirli bir bilgi türünü sağlar.  Bu görünümleri oluşturmanın en iyisi, sık sık bir görünümden diğerine taşınmaktır. Herhangi bir görünümden başlayabilirsiniz.

|Diyagram veya belge|Gereksinimler modelinde ne anlatmaktadır?|Section|
|-|-|-|
|Kavramsal sınıf diyagramı|Gereksinimleri açıklamak için kullanılan türler sözlüğü; sistemin arabiriminde görünen türler.||
|Ek belgeler veya iş öğeleri|Performans, güvenlik, kullanılabilirlik ve güvenilirlik ölçütleri.|[Hizmet kalitesi gereksinimlerini açıklama](#QoSRequirements)|
|Ek belgeler veya iş öğeleri|Belirli bir kullanım durumuna özgü değil kısıtlamalar ve kurallar|[İş kurallarını gösterme](#BusinessRules)|

Diyagram türlerinin çoğunun başka amaçlar için kullanılaca dikkat kullanılmaktadır. Diyagram türlerine genel bakış için [bkz. Uygulamanıza model oluşturma.](../modeling/create-models-for-your-app.md)

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Showing Business Rules

İş kuralı, belirli bir kullanım durumuyla ilişkilendirilen bir gereksinimdir ve sistem genelinde gözlemlenmeli.

Birçok iş kuralı, kavramsal sınıflar arasındaki ilişkiler üzerinde kısıtlamalardır. Bu statik iş *kurallarını kavramsal bir* sınıf diyagramında ilgili sınıflarla ilişkili açıklamalar olarak yazabilirsiniz. Örneğin:

![Order sınıfına eklenen Açıklama'daki kural.](../modeling/media/uml_reqmcd2.png)

*Dinamik iş kuralları,* izin verilebilecek olay dizilerini kısıtlar. Örneğin, bir kullanıcının sisteminiz üzerinde başka işlemler gerçekleştirmeden önce oturum açması gerektiğini göstermek için bir sıra veya etkinlik diyagramı kullanırsiniz.

Ancak birçok dinamik kural, statik kurallarla değiştirerek daha etkili ve genel olarak belirtiliyor olabilir. Örneğin, kavramsal sınıf modelinde bir sınıfa 'Logged In' Boole özniteliği ekleme. Oturum Açma'ya kullanım durumundaki günlüğün sonkoşulları olarak ve diğer kullanım örneklerinden çoğunun önkoşulları olarak eklemeniz gerekir. Bu yaklaşım, olay dizilerinin olası tüm birleşimlerini tanımlamayı önlemenizi sağlar. Ayrıca modele yeni kullanım örnekleri eklemeniz gereken durumlarda da daha esnektir.

Buradaki seçimin gereksinimleri nasıl tanımladığınızla ilgili olduğunu ve bunun program kodundaki gereksinimleri nasıl uygulayasınızdan bağımsız olduğunu fark edin.

Aşağıdaki konular daha fazla bilgi sağlar:

|Hakkında bilgi edinmek için|Okuma|
|-|-|
|İş kurallarına uygun kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Hizmet Kalitesi Gereksinimlerini Açıklama

Hizmet kalitesi gereksiniminin çeşitli kategorileri vardır. Bunlar aşağıdakileri içerir:

- Performans

- Güvenlik

- Kullanılabilirlik

- Güvenilirlik

- Sağlamlık

Belirli kullanım örnekleri açıklamalarında bu gereksinimlerin bazılarını dahil edin. Diğer gereksinimler kullanım örneklerine özgü değildir ve en etkili şekilde ayrı bir belgede yazılır. Bunu yapmak için gereksinimler modeli tarafından tanımlanan sözlüğüne bağlı kalmanızı sağlar. Aşağıdaki örnekte, gereksinimde kullanılan ana sözcüklerin, önceki çizimlerde aktörlerin, kullanım örneklerinin ve sınıfların başlıkları olduğunu fark edeceğiz:

Bir Restoran, Müşteri Yemek Sipariş Ederken Menü Öğesini silerse, bu Menü Öğesine başvuran tüm Sipariş Öğeleri kırmızı renkle görüntülenir.

Hizmet [kalitesi gereksinimlerine uygun kod geliştirmeyi](../modeling/model-your-app-s-architecture.md) öğrenmek için bkz. Uygulama mimarinizi modelleme.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
