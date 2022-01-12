---
title: Kullanıcı gereksinimlerini modelleme
description: Visual Studio, etkinlikleri hakkında diyagramlar çizerek kullanıcılarınızın ihtiyaçlarını anlamanıza, tartışmanıza ve iletmenize nasıl yardımcı olduğunu öğrenin.
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
ms.openlocfilehash: 23de6705c5ae0956e18ebfc60cf1939d2ec9a741
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135516523"
---
# <a name="model-user-requirements"></a>Kullanıcı gereksinimlerini modelleme

Visual Studio, etkinliklerine yönelik diyagramlar çizerek kullanıcılarınızın ihtiyaçlarını anlamanıza, tartışmanıza ve iletmenize yardımcı olur. Gereksinimler modeli, her biri kullanıcı gereksinimlerinin farklı bir yönüne odaklanan Bu diyagramların bir kümesidir.

Visual Studio sürümlerinin her bir model türünü desteklediğini görmek için bkz. [mimari ve modelleme araçları için sürüm desteği](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

Gereksinim modeli şunları yapmanıza yardımcı olur:

- İç tasarımından ayrı olarak sistemin dış davranışına odaklanın.

- Doğal dilde olduğundan, kullanıcıların ve paydaşların ihtiyaçlarını çok daha az belirsizliğe göre tanıtın.

- Kullanıcılar, geliştiriciler ve test ediciler tarafından kullanılabilecek tutarlı bir terim sözlüğü tanımlayın.

- Gereksinimlerde boşlukları ve tutarsızlıkları azaltın.

- Gereksinim değişikliklerine yanıt vermek için gereken işi azaltın.

- Özelliklerin geliştirilecek sırayı planlayın.

- Testler ve gereksinimler arasında net bir ilişki yaparak modelleri sistem testleri için temel olarak kullanın. Gereksinimler değiştiğinde, bu ilişki testleri doğru şekilde güncelleştirmenize yardımcı olur. Bu, sistemin yeni gereksinimleri karşıladığından emin olmanızı sağlar.

Bir gereksinim modeli, kullanıcıları veya temsilcileriyle tartışmalara odaklanmak için kullanıyorsanız en büyük avantaj sağlar ve her yinelemenin başlangıcında onu tekrar ziyaret edebilirsiniz. Kodu yazmadan önce ayrıntılı olarak doldurmanız gerekmez. Kısmen çalışan bir uygulama, çok fazla Basitleştirilmiş olsa bile, genellikle gereksinimlerle ilgili olarak gereksinimlerin tartışılması için en fazla bir temel oluşturur. Model, bu tartışmaların sonuçlarını özetlemek için etkili bir yoldur. Daha fazla bilgi için bkz. [geliştirme sürecinizdeki modelleri kullanma](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> Bu konularda, "sistem", geliştirmekte olduğunuz sistem veya uygulama anlamına gelir. Birçok yazılım ve donanım bileşeninin büyük bir koleksiyonu olabilir; ya da tek bir uygulama; veya daha büyük bir sistem içindeki bir yazılım bileşenidir. Her durumda, gereksinimler modeli, bir kullanıcı arabirimi veya API aracılığıyla sisteminizin dışından görülebilen davranışı açıklar.

## <a name="common-tasks"></a>Genel görevler

Kullanıcıların gereksinimlerinin birkaç farklı görünümünü oluşturabilirsiniz.  Her görünüm belirli bir bilgi türü sağlar.  Bu görünümleri oluşturduğunuzda sıklıkla bir tane diğerine taşımak en iyisidir. Herhangi bir görünümden başlayabilirsiniz.

|Diyagram veya belge|Gereksinimler modelinde neleri açıklar|Section|
|-|-|-|
|Kavramsal sınıf diyagramı|Gereksinimleri anlatmak için kullanılan türlerin sözlüğü; Sistem arabiriminde görünen türler.||
|Ek belgeler veya iş öğeleri|Performans, güvenlik, kullanılabilirlik ve güvenilirlik ölçütleri.|[Hizmet gereksinimlerinin kalitesini açıklama](#QoSRequirements)|
|Ek belgeler veya iş öğeleri|Belirli bir kullanım örneğine özgü bulunmayan kısıtlamalar ve kurallar|[İş kurallarını gösterme](#BusinessRules)|

Diyagram türlerinin çoğunun başka amaçlar için de kullanılabileceğini unutmayın. Diyagram türlerine genel bir bakış için bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).

## <a name="showing-business-rules"></a><a name="BusinessRules"></a> Iş kurallarını gösterme

İş kuralı, belirli bir kullanım örneği ile ilişkilendirilmemiş ve sistem genelinde gözlenecek bir gereksinimdir.

Birçok iş kuralı, kavramsal sınıflar arasındaki ilişkilerdeki kısıtlamalardır. Bu *statik iş kurallarını* , kavramsal sınıf diyagramında ilgili sınıflarla ilişkili açıklamalar olarak yazabilirsiniz. Örneğin:

![Açıklama, Order sınıfına iliştirilmiş kural.](../modeling/media/uml_reqmcd2.png)

*Dinamik iş kuralları* , izin verilen olay dizilerini kısıtlar. Örneğin, bir kullanıcının sisteminizde başka işlemler gerçekleştirmeden önce oturum açması gerektiğini göstermek için bir sıra veya etkinlik diyagramı kullanın.

Ancak, birçok dinamik kural, statik kurallarla değiştirilerek daha etkin ve genel olarak ifade edilebilir. Örneğin, kavramsal sınıf modelindeki bir sınıfa ' oturum açmış ' Boole özniteliği ekleyebilirsiniz. Oturum açma durumunu kullanım durumunun sonkoşulu olarak, diğer kullanım örneklerinin çoğunun bir önkoşulu olarak eklemeniz gerekir. Bu yaklaşım, olay sıralarının tüm olası birleşimlerini tanımlamaktan kaçınmanızı sağlar. Modele yeni kullanım durumları eklemeniz gerektiğinde de daha esnektir.

Buradaki seçim, gereksinimlerin nasıl tanımladığına ilişkin olduğunu ve bu seçeneğin program kodunda gereksinimlerin nasıl uygulandığını fark ettiğini unutmayın.

Aşağıdaki konularda daha fazla bilgi sağlanmaktadır:

|Hakkında bilgi edinmek için|Okuma|
|-|-|
|İş kurallarına uygun kod geliştirme|[Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)|

## <a name="describing-quality-of-service-requirements"></a><a name="QoSRequirements"></a> Hizmet gereksinimlerinin kalitesini açıklama

Hizmet gereksinimi kalitesi için çeşitli kategoriler vardır. Bunlar aşağıdakileri içerir:

- Performans

- Güvenlik

- Kullanılabilirlik

- Güvenilirlik

- Sağlamlık

Bu gereksinimlerin bazılarını, belirli kullanım durumlarının açıklamalarına dahil edebilirsiniz. Diğer gereksinimler kullanım örneklerine özgü değildir ve en etkili şekilde ayrı bir belgede yazılır. Mümkün olduğunda, gereksinim modeli tarafından tanımlanan bir sözlüğüne bağlı kalmak yararlı olur. Aşağıdaki örnekte, gereksinimde kullanılan ana sözcüklerin, önceki çizimlerdeki aktörlerin, kullanım durumlarının ve sınıfların başlıkları olduğunu fark edeceksiniz:

Bir restoran, bir müşteri bir yemek sipariş ederken bir menü öğesini silerse, bu menü öğesine başvuran herhangi bir sıralama öğesi kırmızı renkte görüntülenir.

Hizmet gereksinimlerinin kalitesine uygun kod geliştirmeyi öğrenmek için [uygulamanızın mimarisini modelleyin](../modeling/model-your-app-s-architecture.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
