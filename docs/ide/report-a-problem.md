---
title: 'Sorun bildirin: durumlar ve SSS'
description: Sorun bildir aracına genel bir bakış sağlar ve sorun durumları ve tanımlar içerir
ms.date: 11/15/2018
ms.custom: seodec18
ms.topic: conceptual
author: seaniyer
ms.author: seiyer
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d024e28d696a60a9fc77c290283382dcd0e0ede8
ms.sourcegitcommit: 2148f3fd69569d8ec54fd21a66370932ce610ce4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74853509"
---
# <a name="report-a-problem-states-and-faq"></a>Sorun bildirin: durumlar ve SSS

Sorun bildir Aracı, Visual Studio geliştirici topluluğunun sorunları göndermesini sağlar. Sorun raporlarınızdan her biri, temel mühendislik sistemimizde bir iş öğesi haline gelir ve bu sorunları belirlememize ve çözmenize yardımcı olmak için doğrudan ürün ekiplerimiz ile birlikte çalışmanıza olanak sağlar. Zengin tanılama bilgileriyle gönderilen geri bildiriminiz, Visual Studio ürün ailesini geliştirmek için kritik öneme sahiptir. Sorunları bildirmek için zaman ayırdığınız için teşekkür ederiz.

Buna ek olarak, bir soruna daha fazla dikkat çekici ve sorunu daha hızlı gidermeye yardımcı olması için diğer topluluk üyelerinden geri bildirimde oy verebilirsiniz.

## <a name="problem-status"></a>Sorun durumu

Bir sorunu bildirdikten sonra, durumlar, Gönderimlerinizin yaşam döngüsünün nerede olduğunu gösterir. Microsoft ekipleri geri bildiriminizi gözden geçirdikten sonra uygun bir durumla ayarlanırlar.  Aşağıda listelenen durumlara ve renk göstergeleriyle birlikte, sorun raporlarınızı ilerleme durumunu izleyin.

![Geliştirici topluluğu 'nda sorun raporlama için yeni durum](../ide/media/ProblemStates/New.jpg)

**Yeni** , hata veya sorunun yeni rapor alındığını ve henüz bir işlem yapıldığını gösterir.

- - -

![Geliştirici topluluğu 'nda sorun raporlama için değerlendirilmemiş durum](../ide/media/ProblemStates/Triaged.jpg)

**Değerlendirildi** , yineleme için denetleme, çeviri ve ilk denetim gibi ön adımların tamamlandığını gösterir. Bilet, uygun mühendislik ekibine göz önüne yönlendirildi.

- - -

![Geliştirici topluluğu 'nda sorun raporlama için dikkate alınması gereken durum](../ide/media/ProblemStates/UnderConsideration.jpg)

Bu konu **başlığı altında** , Microsoft 'un topluluk üzerindeki sorunu gözden geçirdiğini ve buna göre önceliklendirilecağını belirtir. Topluluk etkisi henüz net değildir veya önemli değilse, bu durumda sorunu izlemeye devam edeceğiz.

- - -

![Geliştirici topluluğu 'nda sorun raporlama için araştırma durumu altında](../ide/media/ProblemStates/UnderInvestigation.jpg)

**Araştırma bölümünde** mühendislerin çözüm bulmak için sorununuzu etkin bir şekilde araştırdığını gösterir.

- - -

![Geliştirici topluluğu 'nda sorun raporlama için daha fazla bilgi gerekiyor](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**Daha fazla bilgi gerekiyor** , araştırmaya gidebilmemiz için daha fazla tanılama bilgisine ihtiyacımız olduğunu gösterir.  [Daha fazla bilgi isteği Ihtiyacını nasıl yanıtlayacağınızı öğrenin.](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed-need-more-info)

- - -

![Geliştirici topluluğu 'nda sorun raporlama için sabit bekleyen yayın durumu](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**Sabitlenmiş yayın** , sorun için bir düzeltireceğiz olduğunu ve yakında bir önizleme veya sürümde mevcut olacağını gösterir.  Düzeltme bir önizlemede kullanılabilir hale geldiğinde, sorun önizleme sürümünü belirten ' sabitlenmiş ' etiketi ile etiketlenir.

- - -

![Geliştirici topluluğu 'nda sorun raporlama için kapalı durum düzeltildi](../ide/media/ProblemStates/ClosedFixed.jpg)

**Closed-fixed** , sorun için bir düzeltme yayımladığımızda olduğunu gösterir. Bu sorun artık yayın sürümünü belirten bir "sabitlenmiş:" etiketiyle etiketlenir.

- - -

![Kapatılmış-geliştirici topluluğu 'nda sorun raporlama için yinelenen durum](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**Kapalı-yinelenen** , sorununuzun başka bir geri bildirimde zaten rapor edilmiş olduğunu gösterir. Size özgün sorun raporunu izleyebileceğiniz bağlantıyı sağlıyoruz.

- - -

![Geliştirici topluluğu 'nda sorun raporlama için kapalı-düşük öncelik durumu](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Kapalı-düşük öncelik** Geliştirici topluluğumuza her birini en iyi şekilde getirecek şekilde odaklanmak için, en yüksek müşteri etkisi ile ilgili sorunları önceliklendirtik. Bu sorunu şu anda ele alabiliriz, ancak tüm geri bildirimlerinizin değerli olduğundan emin olun ve Visual Studio 'Yu iyileştirmenize yardımcı olun.

- - -

![Closed-geliştirici topluluğundaki sorun raporlaması için hata durumu değil](../ide/media/ProblemStates/ClosedNotABug.jpg)

**Kapalı-hata değil** , bildirilen işlevin geçerli tasarıma göre olduğunu belirlediğimize işaret etti.

- - -

![Kapalı-geliştirici topluluğu 'nda sorun raporlama için yeterli bilgi durumu yok](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**Kapalı-yeterli bilgi yok** , bunu sizin için araştırmak için yeterli bilgiye sahip olmadığını gösterir. Gerekli bilgiler kullanılabilir olduktan sonra geri bildirimin yeniden dikkate alınması mutlu olacaktır.

- - -

![Kapalı-geliştirici topluluğu 'nda sorun raporlama için diğer ürün durumu](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**Kapalı-diğer ürün** , sorununuzun başka bir ürün için geçerli olduğunu belirledik. Dış ürün ve ilgili tüm bağlantılar için Microsoft 'un açıklamasına bakın.

- - -

![Kapalı-geliştirici topluluğu 'nda sorun raporlama için durum düzeltilmeyecek](../ide/media/ProblemStates/ClosedWontFix.jpg)

**Kapalı, düzeltilmeyecek** , ürün yönü hizalaması veya topluluk etkisi gibi faktörlerden dolayı bu sorunu giderdiğimiz anlamına gelir. Ek açıklık için Microsoft 'un açıklamasına bakın.  Bu sorunu ele vermemiz mümkün olsa da, tüm geri bildirimlerinizin değerli olduğundan emin olun ve Visual Studio 'Yu iyileştirmenize yardımcı olun.

- - -

## <a name="faq"></a>SSS

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>Sorunum hızlı bir şekilde çözümlenme olasılığını nasıl artırabilirim?

Raporlamak üzere olduğunuz sorunun zaten bildirilmediğinden emin olmak için aramayı kullanmanızı öneririz. Sorununuz ile eşleşen bir öğe bulursanız, bu sorun biletini izleyin ve oylayın.

Ekiplerimizin karşılaştığınız şeyi yeniden üretmesi için kullanabileceğiniz tüm bilgileri sağlayın.  Bu bilgiler, gerekli yeniden üretme adımları, kod parçaları, ekran görüntüleri, yeniden oluşturma kayıtları, günlük dosyaları ve diğer yapıtları içerir.  [Visual Studio 'da sorun bildirme yöntemi](./how-to-report-a-problem-with-visual-studio.md)aşağıda verilmiştir.

### <a name="how-is-my-feedback-prioritized"></a>Geri Bildirimlerim nasıl önceliklendirilir?

Müşterilerimizden çok sayıda değerli sorun alırız. Geliştirici topluluğumuzdaki her birine en iyi değeri getirdiğimiz için, en yüksek topluluk etkisi olan geri bildirimde gerçekleştirilecek eylemi önceliklendirtik.

Geri bildiriminiz için kişisel olarak yanıt veremesek, girişinizi tam anlamıyla beğentik. Tüm geri bildirimlerinizi doğru ekibe aldığından emin olun.

Visual Studio 'Yu daha iyi hale getirmek için yatırım yaptığınız zamana gerçekten değer veriyoruz.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>Çözünürlükten memnun kalmazsam hangi eylemleri yapabilirim?

Takımlarımız, karşılaşabileceğiniz sorunları tanılamak ve çözmek için en iyi seçenektir, ancak önerimizde tam olarak memnun olmadığınız zamanlar olabilir. Geri bildirimde bulunun ve tam olarak memnun kalmadıklarınızı bize iletin ve gereksinimlerinizi karşıladığımızdan emin olmak için en iyi şekilde deneyeceğiz.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>Geri bildirimimde ilerleme durumunu nasıl alabilirim?

Microsoft mühendislik ekipleri, geri bildirim bileti hakkında yorum yaparak ve iş süreci sırasında bilet durumunu değiştirerek sizinle iletişim kurar. Bilet durumu değiştiğinde veya bir yorum gönderildiğinde gönderilen e-posta bildirimlerini izleyin.  Geliştirici topluluğu sitesinde profil ve Tercihler ayarlarındaki bildirimlerin sıklığını yönetebilirsiniz.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>Geliştirici topluluğu Web sitesinde Visual Studio IDE için neden sorun ekleyemiyorum?

Visual Studio ile ilgili bir sorun bildirmek, tanılama bilgilerinin rapora otomatik olarak eklenmesini sağlar. Mühendislerimizi, sorununuzu tamamen anlamak ve çözmeye çalışmak için ihtiyaç duydukları bağlamı sunan önemli bilgiler.

Visual Studio aracılığıyla rapor ettiğinizde, büyük günlük dosyaları, kilitlenme bilgileri, ekran görüntüleri, yeniden üretme kaydı ve daha yüksek kaliteli çözümler sunmamıza yardımcı olan diğer yapıtlar gibi bizimle zengin tanılama bilgilerini kolayca paylaşabilirsiniz.
