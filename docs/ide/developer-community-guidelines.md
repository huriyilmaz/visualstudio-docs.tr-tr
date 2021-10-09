---
title: Geliştirici Topluluğu yönergeleri
description: Visual Studio Developer Community ile çalışmaya Community.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5c641b9b3fb307b262e8f594a949729c603d346d
ms.sourcegitcommit: 5f1e0171626e13bb2c5a6825e28dde48061208a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2021
ms.locfileid: "129704566"
---
# <a name="developer-community-guidelines"></a>Geliştirici Topluluğu yönergeleri

Geliştirici Community, sorun ve özellik önerileri Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Sorunları ve önerileri gönderme

Geliştirici [Visual Studio Community,](https://aka.ms/feedback/suggest?space=8) sorun ve özellik önerileri Visual Studio.

### <a name="before-submitting-an-issue"></a>Sorun göndermeden önce

Henüz mevcut Visual Studio emin olmak Community Geliştirici Hesabı'Community sorunlarınızı arama. Sorun zaten varsa, ilgili yorumlarda bulun ve oylarınızı atarak.

Sorun bir soru ise, _visual-studio Stack Overflow topluluka sorun._ [](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) Bu etiketi takip edecek ve soruları yanıtlamaya yardımcı olacak müşteri destek personelimiz var.

Hatanızı veya özelliğinizi açıklayan mevcut bir sorun bulamazsanız, aşağıdaki yönergeleri kullanarak bir sorun gönderin.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>İyi bir hata raporu veya özellik önerisi yazma

- Sorun başına yalnızca bir sorun veya özellik isteği kaydedin.

  - Birden çok sorunu veya özellik isteğini tek bir sorunda birleştirerek tanılamayı ve diğer kullanıcıların soruna oy vermelerini zorlaştırabilirsiniz.
  - Aynı giriş için değilse sorunlarınızı mevcut bir soruna yorum olarak eklemeyin. Birçok sorun birbirine benzer ancak farklı nedenleri vardır ve bu da sorunlarınızı tanılamayı zorlaştırır.

- Ne kadar fazla bilgi sağlarsa sorunlarınızı yeniden oluşturmamız ve düzeltmemiz o kadar kolay olur.
- Her soruna aşağıdaki adımları dahil edin.

  - Yenidenlanabilir adımlar (1... 2... 3...) ve neyle karşı karşıya olduğunu tahmin ettiy ve neyle karşı karşıya olduğunu.
  - Görüntüler, animasyonlar veya video bağlantısı. Görüntüler ve animasyonlar yeniden adımlarını gösterir _ancak bunları_ değiştirmez.
  - Uygun şekilde, sorunu gösteren bir kod parçacığı veya sorunu yeniden oluşturmak için makinemize kolayca çekebiliyoruz bir kod deposu bağlantısı.

- Aşağıdaki adımları gerçekleştirin:

  - Yinelenen bir var mı diye arama yapmak için arama. Öyleyse, gerektiğinde ek açıklamalar veya açıklamalar sağlayarak mevcut sorunu oylar.
  - Tüm uzantıları devre dışı bırakarak sorunu yeniden oluşturun. Sorunun, yüklü bir uzantıdan kaynak açtığını bulursanız, uzantıya sırasıyla bir sorun kaydedin.
  - Sorunu daha iyi yalıtmak için kodunuzu soruna göre basitleştirin.

Zengin ayrıntıları içeren sorunlarda bile sorunu yeniden oluşturamayabilirsiniz ve daha fazla bilgi isteyebilirsiniz!

## <a name="managing-problem-reports"></a>Sorun raporlarını yönetme

Bir sorunu triyaklama, özellik ekibi içinde işbirliğine dayalı olarak yapılan çok adımlı bir işlemdir. Triyazma genellikle bir hafta sürer, ancak daha uzun sürebilir. Bu konudaki amaç, soruna ne olacağını net bir şekilde anlamanızı sağlamaktır. Örneğin, değerlendirme sonrasında sorunlarınızı düzeltmeyi mi yoksa daha fazla topluluk geri bildirimi mi beklemeyi planlıyoruz?

Bir sorun bildirdikten sonra, eyaletler gönderimlerinizi yaşam döngüsünde nerede olduğunu gösteriyor. Ürün Visual Studio ekipler geri bildiriminizi gözden geçirsin ve uygun bir durumla ayarlayın. Sorun durumları ve SSS bölümüne başvurarak [sorun raporlarınızı takip edin.](./how-to-report-a-problem-with-visual-studio.md)

### <a name="prioritizing-which-issues-to-fix"></a>Düzeltilen sorunları önceliklendirme

Bildirilen tüm sorunları düzelte teceğiz. Bazıları düzeltilemez kadar pahalıdır, bazıları diğer özellik alanlarında regresyona neden olabilir ve bazıları çok düşük bir etkiye sahip olabilir. Bize bir sorun raporu göndermek için zaman verdiyebilirsiniz. Bu projede veya katkıda bulunan diğer projelerde hepimiz orada bulunduk. Bir sorun kapatıldı ve bize verilen nedenin yerine getirilemedi olduğunu hissedecek olursanız, kullanım örneğiniz netleştirilebilir ve sorunun başka bir geçiş için yeniden etkinleştirilmesi talep edilebilir. Bu noktada sizden daha fazla bilgi istememiz gerekir.

### <a name="missing-important-information"></a>Önemli bilgiler eksik

Bir sorunda önemli bilgiler eksik olduğunda, Daha Fazla Bilgi Gerekiyor _durumunu atarız._ Soruna ihtiyacımız olan belirli bilgilerle ilgili yorumda bulunduk ve bir e-posta bildirimi alırsınız. Yedi gün içinde bilgileri al yer yer almazsa size bir anımsatıcı göndeririz. Bundan sonra, 14 gün boyunca hiç hareketsizlik olduktan sonra bileti kapatırız.

### <a name="other-product"></a>Diğer ürün

Bazen bir sorun bildiriyor, bunun nedeni başka bir ürün olabilir ve bu durum Visual Studio. Başka bir ilgili uygulama veya uzantı olabilir. 

Böyle bir durumda sorunu kapatıp diğer ürünle birlikte açmanız gerekir. Bu sorunları dosyalanan bazı yaygın yerler:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio Abonelik Desteği](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Ek bilgiler

- [Bir performans sorunu düzeltilen olasılığı artırma](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Sorun giderme ve günlük oluşturma MSBuild oluşturma](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Özellik önerilerini yönetme

Özellik önerileri, bizimle geliştirici topluluğu üyeleri arasındaki iletişimin bir aracıdır. Teknik olarak, tüm özellik isteklerini sonsuza kadar açık tutabilirsiniz. Ancak sorunları açık tutmak, bir özelliğin gerçek durumuna ilişkin topluluk görünürlüğünü azaltır. Bu nedenle, ele almayacak özellik isteklerini kapatacak ve ele atayacak özellikleri Gözden Geçir altında _etiketine atadık._

Bir özellik öneriniz varsa isteğinizi ele alamayacaksınız. Bunu anlıyoruz. Bu projede veya katkıda bulunan diğer projelerde hepimiz orada bulunduk. Bu nedenle tüm girişlerinizi çok seviyorum. Önerinize Gözden Geçir etiketini kapatırken veya atarken _kişisel_ bir suç atmayın. Özellik önerinizin açık kalmanın uygun olduğunu hissedecek olursanız, kullanım örneklerinizi netleştirin ve bizimle iletişime geçin veya daha fazla oy toplayın.

Karar verme sürecimizde, özellik önerisiyle ilgili olarak aşağıdaki özelliklere göz atacağız:

- Genel ürün yönüyle eş mi?
- Bunu derlemeyi ve bakımını yapmak bize yetmiyor mu?
- Genel yol haritası stratejimize [uygun mu?](/visualstudio/productinfo/vs-roadmap)
- Oylar ve yorumlarla belirtilen topluluk desteğine sahip mi?
- Düşük topluluk desteğiyle bile bunu seviyor muz?

Bu sorulardan herhangi birini "evet" olarak yanıtlayamayarak kapatırız. Ancak daha fazla topluluk geri bildirimi toplamak için öneri _genellikle Gözden Geçirildi_ olarak açık kalır.

Bir öneri genel ürün yönüyle eşleşmezse kapsamı dışında olarak *kapatırız.* Örneğin, ürün ailesinin diğer üyelerine benzer yatırımlar Visual Studio olabilir. Veya önerilen özellik yalnızca birkaç kişi için uygun olabilir ve bu da uzantıyı sağlamak için daha uygun olabilir.

Öneri durumları ve SSS bölümüne başvurarak özellik [önerinizin ilerlemesini takip edin.](./report-a-problem.yml)

## <a name="discussion-etiquette"></a>Tartışma kuralları

Konuşmayı net ve şeffaf bir şekilde tutmak için, tartışmayı İngilizce ile sınırla ve soruna uygun şeyleri tut. Başkalarını göz önünde bulundurarak her zaman iyi ve profesyonel olmaya çalışma.

Daha fazla bilgi için [bkz. Microsoft Community Kuralları.](https://answers.microsoft.com/en-us/page/codeofconduct)

Tartışma kurallarına yönelik tüm ihlaller, açıklamanın kaldırılmasına ve sonunda kullanıcının yasaklanmasına neden olabilir.

## <a name="data-privacy"></a>Veri gizliliği

Açıklamalar ve yanıtlar genel olarak görünür, ancak eklenen tüm dosyalar yalnızca Microsoft ile özel olarak paylaşılır. Bu görünürlük, topluluğun tamamının diğer kullanıcıların bulduğu sorunları ve çözümleri görmesini sağlar. Verilerinizin veya kimliğinizin gizliliği konusunda endişeleriniz varsa seçenekleriniz vardır. Developer [Community veri gizliliği hakkında daha fazla bilgi edinebilirsiniz.](./developer-community-privacy.md)

## <a name="next-steps"></a>Sonraki adımlar

Sorunları rapor etmek, [Visual Studio önermek Community](https://aka.ms/feedback/suggest?space=8) mevcut biletlere göz atmak için Visual Studio Developer Community'ye gidin. Keyfini çıkarın!
