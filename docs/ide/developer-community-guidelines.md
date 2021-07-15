---
title: Geliştirici Topluluğu yönergeleri
description: Visual Studio geliştirici Community ile çalışmaya yönelik yönergeleri açıklar.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 21cf3bd6a0c208a78cd391f93702865e905482e0
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756881"
---
# <a name="developer-community-guidelines"></a>Geliştirici Topluluğu yönergeleri

geliştirici Community Visual Studio ilgili sorunları ve özellik önerilerini izler.

## <a name="submitting-problems-and-suggestions"></a>Sorunları ve önerileri gönderme

[Visual Studio geliştirici](https://aka.ms/feedback/suggest?space=8) , Visual Studio yönelik sorunları ve özellik önerilerini Community izler.

### <a name="before-submitting-an-issue"></a>Bir sorunu göndermeden önce

Visual Studio geliştirici Community, zaten mevcut olmadığından emin olmak için sorun için arama yapın. Sorununuzu zaten var buldıysanız, ilgili yorumlarınızı yapın ve oyunuzu atayın.

Sorununuz bir sorunuz ise, topluluktan _Visual-Studio_ etiketini kullanarak [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) isteyin. Müşteri desteği personeli bu etiketi izliyor ve soruları yanıtlamaya yardımcı olacak.

Hata veya özelliğinizi açıklayan mevcut bir sorunu bulamazsanız, aşağıdaki yönergeleri kullanarak bir sorun gönderin.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>İyi bir hata raporu veya özellik önerisi yazma

- Sorun başına yalnızca bir sorun veya özellik isteği dosyası.

  - Birden çok sorunu veya özellik isteğini tek bir sorunla birleştirmek, diğer kullanıcıların sorununuzu oylamasını ve diğer kullanıcıların daha zor olmasını sağlar.
  - Sorunu, aynı girişe ait olmadığı sürece mevcut bir soruna açıklama olarak eklemeyin. Birçok sorun benzerdir, ancak farklı nedenlerine sahiptir ve bu da sorununuzu tanılamanıza daha zor hale getirir.

- Daha fazla bilgi sağlayabilmeniz için daha kolay olan bilgiler, sorununuzu yeniden oluşturmak ve çözmemizi sağlamaktır.
- Her bir sorunla birlikte aşağıdaki adımları ekleyin.

  - Tekrarlanabilir adımlar (1... 2... 3...) ve neleri öğrendiklerinizle karşılaştırıldığında.
  - Görüntüler, animasyonlar veya bir videonun bağlantısı. Görüntüler ve animasyonlar yeniden üretme adımlarını _gösterir ancak bunları_ değiştirmez.
  - Sorunu veya bir kod deposunun bağlantısını gösteren bir kod parçacığı, uygun şekilde, sorunu yeniden oluşturmak için makinemizi kolayca çekebilir.

- Aşağıdaki adımları belirtmeyi unutmayın:

  - Yinelenen bir öğe olup olmadığını görmek için arama yapın. Varsa, var olan sorunu oylayın ve gerektiğinde ek yorumlar veya açıklamalar sağlayın.
  - Tüm uzantıları devre dışı bıraktıktan sonra sorunu yeniden oluşturun. Sorunu, yüklediğiniz bir uzantının neden olduğunu fark ederseniz, sırasıyla uzantıya bir sorun verin.
  - Sorunu daha iyi ayırabilmemiz için sorunu çözmek için kodunuzu kolaylaştırın.

Zengin ayrıntılar içeren sorunlar da dahil olmak üzere sorunu yeniden oluşturamayız ve daha fazla bilgi istenebilir!

## <a name="managing-problem-reports"></a>Sorun raporlarını yönetme

Bir sorunu önceliklendirme, özellik ekibi içinde işbirliği yapılan çok adımlı bir işlemdir. Üçlü yaşlandırma genellikle bir hafta sürer, ancak daha uzun sürebilir. Üç aylık dönemin amacı, sorununuzun ne olduğunu net bir şekilde anlamanızı sağlar. Örneğin, önceliklendirme sonrasında sorununuzu gidermeyi planlıyoruz veya daha fazla topluluk geri bildirimi bekleyebilirsiniz.

Bir sorunu bildirdikten sonra, durumlar, Gönderimlerinizin yaşam döngüsünün nerede olduğunu gösterir. Visual Studio ürün ekipleri geri bildiriminizi gözden geçirdikten sonra uygun bir durumla ayarlanırlar. Sorun [durumlarına ve SSS](./report-a-problem.yml)'ye başvurarak sorun raporlarınız ilerlemesini izleyin.

### <a name="prioritizing-which-issues-to-fix"></a>Hangi sorunların düzeltilmesine öncelik verme

Bildirilen tüm sorunu düzeltemedi. Bazılarının düzeltilmesi çok pahalıdır, bazıları diğer özellik alanlarında bulunabilir ve bazıları çok düşük bir etkiye sahip olabilir. Bize bir sorun raporu göndermek için zaman ayırdıysanız bunu anladık. Bu projede veya başkaları tarafından katkıda bulunulmuş olsun, hepsi vardı. Bir sorun kapalıysa ve verdiğimiz nedeni karşılamadıysa, kullanım örneğini açıklığa kavuşturmanıza ve sorunu başka bir geçiş için yeniden etkinleştirilecek şekilde istemeniz gerekir. Bu noktada sizden daha fazla bilgi isteyeceğiz.

### <a name="missing-important-information"></a>Eksik önemli bilgiler

Bir sorun için önemli bilgiler eksik olduğunda, _Ihtiyaçları daha fazla bilgi_ durumuna atacağız. İhtiyaç duyduğumuz belirli bilgilerle ilgili sorun hakkında yorum yaptık ve bir e-posta bildirimi alacaksınız. Bilgileri yedi gün içinde almadığımızda size bir anımsatıcı göndereceğiz. Bundan sonra, 14 gün etkin olmama sonrasında bilet kapattık.

### <a name="other-product"></a>Diğer ürün

Bazen bir sorun bildirilmediğinde, başka bir ürünün neden olmadığı ve Visual Studio değil. Başka bir ilgili uygulama veya uzantı olabilir. 

Bu durumda, sorunu kapatacaktır ve diğer ürünle açmanız istenir. Bu sorunları gidermek için bazı yaygın konumlar aşağıda verilmiştir:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Visual Studio Abonelik desteği](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Ek bilgiler

- [Bir performans sorununun düzeltilme olasılığını artırma](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [MSBuild sorunları için sorun giderme ve günlük oluşturma](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Özellik önerilerini yönetme

Özellik önerileri, bizim ve geliştirici topluluğunun üyeleri arasındaki iletişimin bir yöntemidir. Teknik olarak tüm özellik isteklerini sonsuza kadar açık tutabiliriz. Ancak sorunların açık tutulması, topluluk görünürlüğünü bir özelliğin gerçek durumuna düşürür. Bu nedenle, özellik isteklerini kapatmayacağız ve ' _ın gözden geçirme_ etiketi ' ne adresettiğimiz özellikleri atayamayacağız.

Bir özellik önermeniz durumunda isteğinizi ele almak için planlamadığımız bir durum olabilir. Bunu anladık. Tüm ABD bu proje veya katkıda bulunan kişiler üzerinde vardı. Bu nedenle, geri kalan tüm girişinizi sevtik. Önerdiğimiz bir _İnceleme_ etiketini kapatdığımızda veya bir daha atarken kişisel OFFENSE kullanmayın. Özellik önerinizin açık kalmaya devam etmesini düşünüyorsanız, kullanım durumunu açıklığa kavuşturun ve bizimle iletişim kurun veya daha fazla oy toplayın.

Karar verme sürecimizde, özellik önerisi hakkında aşağıdaki özelliklere göz atalım:

- Genel ürün yönümüzle eşleşiyor mu?
- Derleyip bakımını yapabilir mi?
- Genel [yol haritası](/visualstudio/productinfo/vs-roadmap) stratejimize göre hizalansın mı?
- Oylarda ve açıklamalarda gösterildiği gibi topluluk desteği mi var?
- Düşük topluluk desteğiyle bile bu dosyayı sevtik mı?

Bu sorulardan herhangi birine "Evet" Yanıt vermiyoruz. Ancak genellikle öneri, daha fazla topluluk geri bildirimi toplamak için _Gözden geçirme bölümünde_ açık kalır.

Bir öneri genel ürün yönümüzle eşleşmezse, bunu *kapsam dışı* olarak kapalarız. örneğin, Visual Studio ürün ailesinin diğer üyelerinde benzer yatırımları olabilir. Ya da önerilen özellik yalnızca birkaç kişiyle ilgili olabilir, bu da uzantının sağlanması daha uygun hale gelir.

[Öneri durumlarına ve SSS](./report-a-problem.yml)'ye başvurarak Özellik önerinizin ilerlemesini izleyin.

## <a name="discussion-etiquette"></a>Tartışma etiği

Konuşmayı açık ve şeffaf tutmak için tartışmayı Ingilizce ile sınırlayın ve sorunla ilgili şeyleri koruyun. Considerate ve her zaman korkusuz ve profesyonel olacak şekilde çalışın.

daha fazla bilgi için [Microsoft Community kullanım kuralları](https://answers.microsoft.com/en-us/page/codeofconduct)' na bakın.

Tartışmaya yönelik herhangi bir ihlal, açıklamanın kaldırılmasına ve sonunda kullanıcıyı yönlendirebilir.

## <a name="data-privacy"></a>Veri gizliliği

Açıklamalar ve yanıtlar herkese açık bir şekilde görünür, ancak ekli dosyalar yalnızca Microsoft ile özel olarak paylaşılır. Bu görünürlük, tüm topluluğun diğer kullanıcılar tarafından bulunan sorunları ve çözümleri görmesini sağladığından faydalıdır. Verilerinizin veya kimliğinizin gizliliğiyle ilgileniyorsanız, seçenekleriniz vardır. [veri gizliliği Community geliştirici](./developer-community-privacy.md)hakkında daha fazla bilgi edinin.

## <a name="next-steps"></a>Sonraki adımlar

sorunları bildirmek, özellikler önermek veya mevcut biletlere gözatmak için [Visual Studio Community geliştiricisi](https://aka.ms/feedback/suggest?space=8) üzerine gelin. Keyfini çıkarın!
