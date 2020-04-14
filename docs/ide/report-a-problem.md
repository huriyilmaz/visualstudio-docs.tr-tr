---
title: 'Sorun bildirin: Durumlar ve SSS'
description: Sorun Bildir aracına genel bir bakış sağlar ve sorun durumları ve tanımları içerir
ms.date: 11/15/2018
ms.custom: seodec18
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6172be3995596807562c1dc7956a1ca8952e5ad4
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276481"
---
# <a name="report-a-problem-states-and-faq"></a>Sorun bildirin: Durumlar ve SSS

Sorun Bildir aracı, Visual Studio geliştirici topluluğunun sorunları göndermesini sağlar. Sorun raporlarınızın her biri, temel mühendislik sistemimizde bir iş öğesi haline gelir ve etkili sorunları belirlememize ve çözmemize yardımcı olmak için ürün ekiplerimizle doğrudan iletişim kurmanızı güçlendirir. Zengin tanısal bilgilerle gönderilen geri bildiriminiz Visual Studio ürün ailesini geliştirmek için çok önemlidir. Sorunları bildirmek için zaman ayırdığınız için gerçekten teşekkür ederiz.

Buna ek olarak, bir soruna daha fazla dikkat çekmek ve sorunu daha hızlı çözmeye yardımcı olmak için diğer topluluk üyelerinden gelen geri bildirimleri oylayabilirsiniz.

## <a name="problem-status"></a>Sorun durumu

Bir sorunu bildirdikten sonra, durumlar gönderimlerinizin yaşam döngülerinde nerede olduğunu gösterir. Microsoft ekipleri geri bildiriminizi gözden geçirdikçe, uygun bir durumla ayarlarlar.  Aşağıda listelenen durumlara, anlamve renk göstergeleriyle birlikte başvurarak sorun raporlarınızın ilerlemesini izleyin.

![Geliştirici Topluluğu'nda sorun raporlaması için yeni durum](../ide/media/ProblemStates/New.jpg)

**Yeni,** hatanın veya sorunun yeni bildirildiğini ve henüz bu konuda herhangi bir işlem yapılmadığını gösterir.

- - -

![Geliştirici Topluluğu'nda sorun raporlaması için triaged durumu](../ide/media/ProblemStates/Triaged.jpg)

**Triaged,** denetleme, çeviri ve yinelemeler için ilk denetim gibi ön adımların tamamladığını gösterir. Biletiniz değerlendirilmek üzere uygun mühendislik ekibine yönlendirildi.

- - -

![Geliştirici Topluluğu'nda sorun raporlaması için Göz Altında Durum](../ide/media/ProblemStates/UnderConsideration.jpg)

**Göz Altında,** Microsoft'un sorununuzu topluluk etkisi için gözden geçirdiğini ve buna göre öncelik vereceğini belirtir. Eğer toplumun etkisi henüz net ya da önemli değilse, bu eyaletteki sorunu izlemeye devam edeceğiz.

- - -

![Geliştirici Topluluğu'nda sorun raporlaması için Araştırma altında durum](../ide/media/ProblemStates/UnderInvestigation.jpg)

**Under Investigation,** mühendislerin bir çözüm bulmak için sorununuzu etkin bir şekilde araştırdıklarını gösterir.

- - -

![Geliştirici Topluluğu'nda sorun raporlaması için Daha Fazla Bilgi durumuna ihtiyacınız Var](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**Need More Info,** soruşturmaya devam edebilmemiz için sizden daha fazla tanısal bilgiye ihtiyacımız olduğunu gösterir.  [Daha Fazla Bilgi Gereksinimi isteklerine nasıl yanıt verilebildiğini öğrenin.](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed-need-more-info)

- - -

![Geliştirici Topluluğu'nda sorun raporlaması için Sabit - Bekleyen Sürüm durumu](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**Sabit - Bekleyen Sürüm,** sorun için bir düzeltmemiz olduğunu ve yaklaşan bir önizleme veya sürümde kullanıma sunulacağını gösterir.  Düzeltme bir önizlemede kullanılabilir olduğunda, sorun önizleme sürümünü belirten bir 'sabit' etiketiyle etiketlenir.

- - -

![Kapalı - Geliştirici Topluluğu'nda sorun raporlaması için sabit durum](../ide/media/ProblemStates/ClosedFixed.jpg)

**Kapalı - Sabit,** sorun için bir düzeltme yayımladiğimizı gösterir. Sorun da şimdi sürüm sürümünü belirten bir "sabit:" etiketi ile etiketlenir.

- - -

![Kapalı - Geliştirici Topluluğu'nda sorun raporlaması için yinelenen durum](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**Kapalı - Yinelenen,** sorunuzun başka bir geri bildirim le zaten raporlandığını gösterir. Orijinal sorun raporunu izleyebileceğiniz bağlantıyı size sağlarız.

- - -

![Kapalı - Geliştirici Topluluğu'nda sorun raporlaması için Daha Düşük Öncelik durumu](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Kapalı - Düşük Öncelik** Geliştirici topluluğumuzdaki her birinizi en iyi değeri sunmaya odaklanmak için, en yüksek müşteri etkisine sahip konulara öncelik veririz. Şu anda bu sorunu çözemesek de, tüm geri bildirimlerinizin değerli olduğundan ve Visual Studio'nun geliştirilmesine yardımcı olduğundan emin olun.

- - -

![Kapalı - Geliştirici Topluluğu'nda sorun raporlaması için bir Hata durumu değil](../ide/media/ProblemStates/ClosedNotABug.jpg)

**Kapalı - Not a Bug,** bildirilen işlevselliğin geçerli tasarıma göre olduğunu belirlediğimizi gösterir.

- - -

![Kapalı - Geliştirici Topluluğu'nda sorun raporlama için Yeterli Bilgi durumu](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**Kapalı - Yeterli Bilgi Yok,** bunu sizin için araştırmak için yeterli bilgiye sahip olmadığımızı gösterir. Gerekli bilgiler kullanılabilir hale gelen geri bildirimleri yeniden gözden geçirmekten mutluluk dulacağız.

- - -

![Kapalı - Geliştirici Topluluğu'nda sorun raporlaması için diğer Ürün durumu](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**Kapalı - Diğer Ürün,** sorununuzun başka bir ürün için geçerli olduğunu belirlediğimizi belirtir. Microsoft'un hangi harici ürün ve ilgili bağlantılar için yapılan yorumuna bakın.

- - -

![Kapalı - Geliştirici Topluluğu'nda sorun raporlama sı için durumu düzeltmez](../ide/media/ProblemStates/ClosedWontFix.jpg)

**Kapalı - Düzeltme olmaz,** ürün yönü hizalaması veya topluluk etkisi gibi etkenler nedeniyle bu sorunu takip etmediğimizi gösterir. Ek netlik için Microsoft'un yorumuna bakın.  Bu sorunu çözemesek de, tüm geri bildirimlerinizin değerli olduğundan ve Visual Studio'nun geliştirilmesine yardımcı olduğundan emin olun.

- - -

## <a name="faq"></a>SSS

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>Sorunumun bir an önce çözülme olasılığını nasıl artırabilirim?

Bildirmek üzere olduğunuz sorunun önceden bildirilmemiş olduğundan emin olmak için aramayı kullanmanızı öneririz. Sorununuzu eşleşen varolan bir öğe bulursanız, bu sorun bilet izleyin ve oy.

Ekiplerimizin yaşadıklarınızı yeniden oluşturmalarına yardımcı olmak için tüm bilgileri sağlayın.  Bu bilgiler gerekli repro adımları, kod parçaları, ekran görüntüleri, repro kayıtları, günlük dosyaları ve diğer yapıları içerir.  Visual [Studio'da bir sorunu şu şekilde bildirebilirsiniz.](./how-to-report-a-problem-with-visual-studio.md)

### <a name="how-is-my-feedback-prioritized"></a>Geri bildirimime nasıl öncelik verilir?

Müşterilerimizden çok sayıda değerli sorun alıyoruz. Geliştirici topluluğumuzdaki her biriniz için en iyi değeri sunduğumuzdan emin olmak için, topluluk etkisi en yüksek olan geri bildirimlere öncelik veriyoruz.

Geri bildiriminize kişisel olarak yanıt veremezsek, girişiniz için tam olarak minnettar olduğumuzu bilin. Tüm geri bildirimlerinizin doğru ekibe ulaştığından emin olun.

Visual Studio'yu daha iyi hale getirmek için yatırım yaptığınız zamana gerçekten değer biçiyoruz.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>Karardan memnun değilsem hangi eylemleri yapabilirim?

Ekiplerimiz, karşılaştığınız sorunları teşhis etmek ve düzeltmek için ellerinden geleni yaparlar, ancak tavsiyemizden tam olarak memnun olmadığınız zamanlar olabilir. Geri bildirimlerhakkında yorum yapın ve tam olarak nelerden memnun olmadığınızı bize bildirin ve ihtiyaçlarınızı karşılamak için elimizden geleni yapalım.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>Geri bildirimlerimde ilerleme den nasıl haberdar edilirim?

Microsoft mühendislik ekipleri, geri bildirim bileti hakkında yorum yaparak ve ilerleme kaydederken biletinizin durumunu değiştirerek sizinle iletişim kurar. Bilet durumu değiştiğinde veya bir yorum yayınlandığında gönderilen e-posta bildirimlerini izleyin.  Geliştirici Topluluğu sitesindeki Profil ve Tercihler ayarlarında bildirim sıklığını yönetebilirsiniz.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>Geliştirici Topluluğu web sitesinde Visual Studio IDE için neden bir sorun ekleyemiyorum?

Visual Studio aracılığıyla bir sorunu bildirmek, tanılama bilgilerinin rapora otomatik olarak eklenmesini sağlar. Mühendislerimize sorununuzu tam olarak anlamaları ve çözmek için çalışmaları için gereken bağlamı sağlayan temel bilgilerdir.

Visual Studio aracılığıyla rapor yaptığınızda, büyük günlük dosyaları, kilitlenme bilgileri, ekran görüntüleri, repro kayıt ve size daha hızlı daha yüksek kaliteli çözümler sunmamıza yardımcı olan diğer yapılar gibi zengin tanıbilgilerini bizimle kolayca paylaşabilirsiniz.
