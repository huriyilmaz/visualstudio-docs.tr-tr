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
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 29970ff3c50a0e28e35751e1c9807f201f48f51f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047874"
---
# <a name="model-user-requirements"></a>Kullanıcı gereksinimlerini modelleme

Visual Studio etkinlikleri ve sisteminizin hedeflerine ulaşmalarına yardımcı olmak için oynadığı parça hakkında diyagramlar çizerek kullanıcı ihtiyaçlarını anlamanıza, tartışmanıza ve iletişim kurmanıza yardımcı olur. Gereksinimler modeli, her biri kullanıcıların ihtiyaçlarının farklı bir yönüne odaklanan bu diyagramlardan bir kümedir. Bir video gösterimi için bkz. [İş Etki Alanını Modelleme.](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-3-modeling-the-business-domain)

Her model türünü destekleyen Visual Studio sürümlerini görmek için [bkz. Mimari ve](../modeling/analyze-and-model-your-architecture.md#VersionSupport)modelleme araçları için sürüm desteği.

Gereksinimler modeli şunları sağlar:

- Sistemin iç tasarımından ayrı olarak dış davranışına odaklanın.

- Kullanıcıların ve proje katılımcılarının ihtiyaçlarını doğal dilden çok daha az belirsizlikle açıkla.

- Kullanıcılar, geliştiriciler ve testçiler tarafından kullanılmaktadır tutarlı bir terim sözlüğü tanımlayın.

- Gereksinimlerde boşlukları ve tutarsızlıkları azaltma.

- Gereksinimler değişikliklerine yanıt vermek için gereken işi azaltma.

- Özelliklerin hangi sırayla geliştirileceklerini planla.

- Modelleri sistem testleri için temel olarak kullanarak testler ile gereksinimler arasında net bir ilişki sağlar. Gereksinimler değiştiklerinde bu ilişki testleri doğru güncelleştirmenizi sağlar. Bu, sistemin yeni gereksinimleri karşılamalarını sağlar.

Gereksinimler modeli, kullanıcılarla veya temsilcileriyle tartışmalara odaklanmak ve her yinelemenin başında bu modeli yeniden ziyaret etmek için kullanırsanız en büyük avantajı sağlar. Kod yazmadan önce ayrıntılı olarak tamamlamanız gerek değildir. Çok basitleştirilmiş olsa bile kısmen çalışan bir uygulama, gereksinimleri kullanıcılarla tartışmanın en etkili temelini oluşturur. Model, bu tartışmaların sonuçlarını özetlemek için etkili bir yol sağlar. Daha fazla bilgi için [bkz. Geliştirme sürecinize modelleri kullanma.](../modeling/use-models-in-your-development-process.md)

> [!NOTE]
> Bu konu başlıkları boyunca "sistem", geliştirmekte olduğunuz sistem veya uygulama anlamına gelir. Birçok yazılım ve donanım bileşeninden büyük bir koleksiyon olabilir; veya tek bir uygulama; veya daha büyük bir sistem içindeki bir yazılım bileşeni. Her durumda gereksinimler modeli, ister kullanıcı arabirimi ister API olsun, sistemin dışından görünen davranışı açıklar.

## <a name="common-tasks"></a>Genel görevler

Kullanıcıların gereksinimlerinin birkaç farklı görünümlerini oluşturabilirsiniz.  Her görünüm belirli bir bilgi türünü sağlar.  Bu görünümleri oluşturmanın en iyi uygulamalarından biri, sık sık bir görünümden diğerine taşımaktır. Herhangi bir görünümden başlayabilirsiniz.

|Diyagram veya belge|Gereksinimler modelinde ne anlatmaktadır?|Section|
|-|-|-|
|Kavramsal sınıf diyagramı|Gereksinimleri tanımlamak için kullanılan türler sözlüğü; sistemin arabiriminde görünen türler.||
|Ek belgeler veya iş öğeleri|Performans, güvenlik, kullanılabilirlik ve güvenilirlik ölçütleri.|[Hizmet kalitesi gereksinimlerini açıklama](#QoSRequirements)|
|Ek belgeler veya iş öğeleri|Belirli bir kullanım durumuna özgü değil kısıtlamalar ve kurallar|[İş kurallarını gösterme](#BusinessRules)|

Diyagram türlerinin çoğunun başka amaçlar için kullanıla değiştirilebilir. Diyagram türlerine genel bakış için [bkz. Uygulamanıza model oluşturma.](../modeling/create-models-for-your-app.md)

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Showing Business Rules

İş kuralı, belirli bir kullanım durumuyla ilişkilendirilen bir gereksinimdir ve sistem genelinde gözlemlenmeli.

Birçok iş kuralı, kavramsal sınıflar arasındaki ilişkiler üzerinde kısıtlamalardır. Bu statik iş *kurallarını kavramsal bir* sınıf diyagramında ilgili sınıflarla ilişkili açıklamalar olarak yazabilirsiniz. Örnek:

![Order sınıfına eklenen Açıklama'daki kural.](../modeling/media/uml_reqmcd2.png)

*Dinamik iş kuralları,* izin verilebilecek olay dizilerini kısıtlar. Örneğin, bir kullanıcının sisteminiz üzerinde başka işlemler gerçekleştirmeden önce oturum açması gerektiğini göstermek için bir sıra veya etkinlik diyagramı kullanabilirsiniz.

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
