---
title: Visual Studio için Kullanıcı arabirimi metni ve yardımı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0477a0e1994e9c3b94df13ace4c1f3b4df51039
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409118"
---
# <a name="ui-text-and-help-for-visual-studio"></a>UI metni ve Visual Studio için Yardım
## <a name="BKMK_UITextAndTerminology"></a>UI metni ve terminolojisi
 Anlaşılır metin etkin kullanıcı Arabirimi için çok önemlidir. Yazılım kullanıcıları eğilimli okumak için ilk olarak, yani bu görevi tamamlamak için en uygun etiketler. Statik metin daha az sıklık ile okunur. Planı iş oturumlarını yaklaşık bu sırada kullanıcı arabiriminin bir okuma ardından pencerenin tamamını bir hızlı tarama başlatmak kullanıcılar için:

1. Merkezi'ndeki etkileşimli denetimleri

2. Yürütme düğmeleri

3. Etkileşimli denetimleri başka bir yerde

4. Ana yönergeleri

5. Ek açıklamaları

6. Pencere Başlığı

7. Ana gövdesi içinde başka bir statik metin

### <a name="usage-patterns-for-ui-text"></a>UI metni için kullanım desenleri

#### <a name="title-bar-text"></a>Başlık çubuğu metni
 Başlık çubuğu metni UI kökenli komut eşleşmesi gerekir.

#### <a name="instructional-text-helper-text"></a>Açıklayıcı metni (Yardımcısı metin)
 Bazı iletişim kutularında, pencere veya sayfa yapmanız gerekenler açıklamak için belirgin ana yönergeler sağlamak yararlıdır. Bu bazen "Yardımcısı text." adlandırılır

##### <a name="writing-style-rules-for-helper-text"></a>Stil kuralları Yardımcısı metin yazma

- Belirgin açıklamak değildir. Kesinlikle gerekli olmadıkça, eğitici metin içermez.

- Eğitici metin her zaman iletişim kutusunun en üstünde yer alır ve gerçekleştirilen görev başvurmanız gerekir.

- Tam olarak kullanıcılara yapmak için ihtiyaçları açıklayın. Aşırı iletişim ve yedeklilik kaçının.

- Her pencere gözden geçirin ve yinelenen sözcükleri ve ifadeleri ortadan kaldırın.

- Eğitici metin kısa tutun. Daha fazla bilgi gerekli belirli kullanıcılar veya senaryoları ise, daha sonra ayrıntılı kavramsal çevrimiçi konusuna bağlantı sağlamak.

- Metninizi yazın, böylece her sözcük ağırlık tutar ve gereklidir.

- [Kullanıcı arabirimi metni](/windows/desktop/uxguide/text-ui) ve [stili ve tonu](/windows/desktop/uxguide/text-style-tone)için mevcut Microsoft kılavuzunu izleyin.

#### <a name="supplemental-instructions"></a>Ek yönergeler
 Ek yönergeler kullanıcı denetimleri anlamak veya gruplandırmaları denetim yardımcı olacak ek bilgileri sağlayın. Bu, İpucu metin girişi denetimi bekleniyor hangi biçimde anlamak için gerekli de içerebilir. Ek yönergeler tedbirli şekilde kullanın. Kullanıcının yaptıkları seçimin kollarını tam olarak anlayamayabileceği durumlar için onları ayırın.

 ![Visual Studio 'da ek metin](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Visual Studio 'da ek metin**

 ![Visual Studio 'da ek metin](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Visual Studio 'da ek metin**

#### <a name="infotips"></a>InfoTips
 Genellikle, açıklayıcı metni kullanıcı Arabiriminde yerleşik yerleştirmek için çok uzun olabilir veya deneyimli kullanıcılar için dağınıklık gibi HİSSEDİYORSUNUZ yalnızca yeni kullanıcılar için yararlı olabilir. Bu durumda, bir bilgi ipucu altında bir araç ipucu olarak eğitici/bilgilendirici metin yerleştirilmelidir.

 InfoTips belirgin olarak ilgili ve henüz örtük belirli bilgi ipucu simgesi kullanması gereken denetimleri yerleştirilmelidir.

 ![Visual Studio 'da InfoTip Ipucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio 'da bilgi Ipucu örneği**

##### <a name="writing-style-rules-for-infotips"></a>InfoTips için yazma stil kuralları

- InfoTips tam cümle yazın. Bunlar, belirli fiillere, cümle ve bitiş için noktalama işaretleri gerektirir.

- Ana yönerge veya bilgi desteklemek üzere InfoTips kullanın. Buradaki ana fikir yazmayı yalnızca farklı sözcük kullanıyorsanız, bir bilgi ipucu gerekmez.

- InfoTips ve tatlı kısa tutun. Küçük kelimeleri ve düz, gündelik dil destekler ve kullanıcı teşvik eder.

- [Kullanıcı arabirimi metni](/windows/desktop/uxguide/text-ui) ve [stili ve tonu](/windows/desktop/uxguide/text-style-tone)için mevcut Microsoft kılavuzunu izleyin.

#### <a name="control-labels"></a>Denetim etiketleri
 Denetim etiketleri kısa, kısa olmalı ve [denetimler Için Windows Masaüstü Kılavuzu](/windows/desktop/uxguide/controls)' nu izlemelidir.

 Kullanıcı arabiriminde Denetim etiketi biçimi ve yerleştirme hakkında daha fazla bilgi için, [Visual Studio 'Nun düzenine](../../extensibility/ux-guidelines/layout-for-visual-studio.md)bakın.

#### <a name="help-links"></a>Yardım bağlantıları
 Yardım bağlantıları ya da eğitici metin veya gövdesini kullanıcı arabiriminin yerleştirilebilir. Yardım bağlantılarını olması veya iç iletişim kutuları başlatın.

##### <a name="visual-style-rules-for-help-links"></a>Yardım bağlantıları için görsel stil kuralları

- Doğru ortamı renkleri için köprüler kullanın. Düzgün stil uygulanmış bir köprü kısaca tıklandığında kırmızı yanar değil. Bunu görürseniz, ardından bu ortam renkleri kullanılmayan göstergesidir.

- Alt çizgi, üzerine gelindiğinde veya bağlantı bir paragraf içinde ne zaman katıştırılmış yalnızca kullanılmalıdır.

- Köprüler için görsel ve etkileşim stilleri hakkında ayrıntılı bilgi için düğmeler ve köprüler bakın.

##### <a name="writing-style-rules-for-help-links"></a>Yardım bağlantıları için yazma stil kuralları

- İletişim kutularını başlatma sırasında üç nokta standartları korumak: gezinme, görev ek kullanıcı Arabirimi gerektiriyorsa, üç nokta için hiçbir üç nokta.

     ![Visual Studio 'da yardım bağlantısı](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Yardım bağlantısındaki üç nokta (...), görevin ek kullanıcı arabirimi gerektirdiğini gösterir.**

- Bağlantılar, kullanıcının amacı olmadığı için "öğreneni" ile başlamamalıdır. Kullanıcının istediği belirli bir soruya yanıt, genel bir eğitim alma.

- Böylece bunlar konu yanıtlayacak soru sorun, tümcecik Yardım bağlar.

     Yanlış: "Windows Azure Mobile Services fiyatlandırması hakkında daha fazla bilgi edinin"

     Doğru: "Windows Azure Mobile Services için hangi fiyatlandırma seçenekleri mevcuttur?"

- Bağlantı metninde hiçbir şekilde *tıklama... seçeneğini* kullanmayın.

- "Burada" sözcüğünü hiçbir şekilde bağlamayın. Yalnızca köprülü word sesli bazı ekran okuyucular için sorunlu budur.

     Yanlış **: "Windows**Azure hakkında bilgi edinin Mobile Services

     Doğru: "Windows Azure Mobile Services için hangi fiyatlandırma seçenekleri mevcuttur?"

- Yardım bağlantıları için doğru yazma stili hakkında daha fazla bilgi için bkz. [Yardım Için Windows Masaüstü Kılavuzu](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>İpucu metni
 İpucu metni, bir denetimi veya denetim altına filigran olarak görüntülenir. Doğru biçimlendirme uygun VSColors belirteci kullanılarak uygulanacak `Environment.GrayText`.

 Bu, çok sayıda formu görünebilir.

- Denetim etiketinin yerine:

     ![Visual Studio 'da ipucu metni](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Bir eylem ile yönergeler verir:

     ![Visual Studio 'da ipucu metni](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Gerekli bir giriş gösteren metin ile:

     ![Visual Studio 'da ipucu metni](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Filigran metni
 Boş bir tasarım yüzeyine bir metin ne yapmak yanı sıra diğer ilgili pencerelerde uygunsa açmak için bağlantılar sağlar belirtmeniz gerekir:

 ![Visual Studio 'da filigran metni](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Visual Studio 'da filigran metni örneği**

### <a name="common-terminology"></a>Sık kullanılan terimler

|Süre|Açıklama|Açıklama|
|----------|-----------------|-------------|
|Oturum açma / Oturumu Kapat|Fiilleri maliyetle aynı anlamda ile web kimlik doğrulaması web özelliği içinde temsil etmek için kullanılır. İstemcileri, bu kez en üst düzey bir kavram IDE kullanıcı bağlantısı, lisanslama ve dolaşım gibi daha üst düzey özellikleri ile tüm diğer bağlantılar kullanılamaz sağlayan bir üst düzey kimliğini temsil eder ve imzalama için kullanırız.|Üst düzey IDE kullanıcı temsil ettiğinden IDE kullanıcı temsil eden bir oturum açma / oturum fiili yalnızca özelliğidir.|
|Connect / bağlantısını kes|Burada bir özellik bir çevrimiçi hizmet tek bir bağlantı tutar yerlerde kullanın.|Sunucu Gezgini, burada yalnızca bir etkin Azure bağlantı bir zaman olabilir, Bağlan/bağlantısını kes örneğidir.|
|Ekle / Kaldır|Olmayan yıkıcı. Ekleme veya bir listeden kaldırma işlevini kullanın.|TFS Bağlantı Yöneticisi sunucu listesi iletişim kutusu Ekle/Kaldır örneğidir.|
|Sil|Yıkıcı. Yalnızca kaldırılan öğe kalıcı olarak atılacak veya diskten silindikçe kullanın.|Sonuç diskten bir dosya silindiğinde "Sil" genellikle bir istemi gerektirir.|

## <a name="error-messages"></a>Hata iletileri

### <a name="overview"></a>Genel Bakış
 Hataları gerçekleşir. Kullanıcı neler yapabileceğinizi kısıtlamaları ayarlama kaçınılabilir hata iletileri engelleyen bir mantıklı ilk adımıdır. Ancak, bir hata oluştuğunda, bu iyi-yazılan hata iletisi sorunu azaltmaya yönelik uzun yol gidebilirsiniz. Hata iletileri tartışmaya zaman uyumlu ve çözülmesi gereken bir sorunu gösterir çünkü kullanıcı, görür bildirim en önemli türlerinden biridir. Kullanıcılar, kötü yazılmış hata iletileri hatalarının nedenini karar vermek için kendi ve tüm olası çözümleri bırakın.

 Kullanıcılar için aşırı kullanılmasına dikkat veya değer kullanıcıyı eklemek yalnızca gerekli iletileri yazma deneyimi için hata iletileri kafa karıştırıcı durabilir. Yalnızca bir bildirim iletisi ise alternatif bir sunu'ni kullanın.

### <a name="rules-for-creating-an-error-message"></a>Bir hata iletisi oluşturmak için kurallar

- Hata iletileri oluştururken, izleyici için uygun hata düzeyini seçin. Kullanıcı alabilir, bir eylem varsa sağlamak için basit özetlerini hedeflenir. Durumu kullanıcı bilmeniz gerekmez. herhangi bir şey yoktur.

- Yapıcı Yardımı sağlarız. Okuma ve yönerge içeren bir hata iletisi üzerinde işlem yapma daha kolaydır.

- Çift negatif kullanmayın.

- Her iki otomatikleştirilmiş gerçekleştirmek ve el ile dil bilgisi ve yazım denetimi, yazdığınız herhangi bir hata iletisi denetleyin.

- Karmaşık hata iletileri için sıralı iletişimleri kaçının. Hiçbir zaman F1 birleştirme için hata iletisini kullanın. İleti yeterli olur.

- Doğru simgesini kullanın.

- "Sil" ve "Iptal" gibi açık seçeneklere sahip düğmeleri daha kolay anlaşılır hale getirin ve kullanın.

- Uyarılar için ne devam etmeden adımlamayla olacağı hakkında açık olun. Düğmeleri adımlamayla belirtmeniz gerekir.

- Hatalar için kullanıcı sorunu gidermek için neler yapabileceğini açıklayın. Düğmeler eylem olmalıdır veya "Kapat" deyin. Bir hata iletisi için "Tamam" düğmesini kullanmayın.

- Kendinize bir hata iletisi oluşturulurken sorun gereken bazı sorular:

  - Kullanıcı başına bu hata sorunu çözmek nasıl ekleyeceğimi?

  - Kullanıcı, bu hata olarak aynı sözlük kullanıyor mu?

  - Bu hata belirsiz veya birden çok durumlarda paylaşılan? Nasıl bu durumda, kullanıcıların ihtiyacı olan çözümü kılavuzu?

#### <a name="build-errors"></a>Derleme hataları
 Visual Studio bir yazılım geliştirme aracı olduğundan, bileşenlerinin çoğunda geliştirici işini ikili biçime dönüştürmek için bir derleme, dönüştürme veya kodlama adımı vardır. Derleyici yanlış yazılmış dosyaları işleyemezlerse veya derleyici seçenekleri doğru şekilde ayarlanmayacaksa, bu dönüşümler hatalara neden olabilir.

 Visual Studio kullanıcılarına devasa bir derleme hatalarını çözme geliştirme saat sayısı ayırabilirsiniz. Hataları bağımlılıkları veya ne zaman hata iletileri kötü, hangi, hatanın kaynağını ortaya çıkarmak zorlaştırabilir yazılır olduğunda bu çözümleme süresini artırır.

 Bu nedenle ilk yerinde Visual Studio oluşmaz otomatik tamamlama sağlar en iyi derleme hataları olan ve IntelliSense dalgalı çizgiler. Şema doğrulayıcılar ve benzer araçları aynı türde bir geri bildirim sağlayın. Bu mekanizmalar proaktif olarak biçimlendirilmiş kod, derleme hataları olasılığını lessening oluşturmak için Kullanıcı Kılavuzu.

 Visual Studio araç penceresi burada kullanıcılar okuyabilir ve belge pencerelerini meydana gelen hatalara gezinmek sağlar. Böylece kullanıcı, hızla kod büyük miktarlarda gidin ve doğrudan sorun konuma gidin, klavye kısayollarını sağlanır. Visual Studio, her yapı hatası kullanıcıya hata hakkında daha ayrıntılı bilgi sağlayan bir Yardım konusu için doğrudan çalışabilmeniz için belirli bir Yardım anahtar sözcüğü/bağlam Kimliğine bağlanması de sağlar.

 Yazma NET, kısa ve öz derleme hataları:

- Çok az sayıda derleyici jargon ile ilgili sorunu açıklayan **düz dil kullanın** . Bir yapı hatası metnini aşırı teknik olmamalıdır.

- **Olası nedenler ana hattı.** Örneğin, "(özellik): (değer) ' bildiriminde özellik ve değer arasında iki nokta eksik."

- Olası düzeltmeleri hakkında ayrıntılar verir. Yeterli alan yoksa, ek ayrıntılar karşılık gelen Yardım konusunu yerleştirilebilir.

### <a name="components-of-a-well-written-error-message"></a>İyi yazılmış hata iletisinin bileşenleri

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Hata iletileri Kabuk iletişim hizmeti kullanın.
 Kabuk iletişim hizmetinin kullanılması, tek tek öğelerde büyük değişiklikler yapmadan iletinin görünüşünü, özellikle de yazı tiplerini denetlemenize olanak tanır. **IErrorInfo** mekanizmalarını kullanın ve **ısuishell:: SetErrorInfo/ReportErrorInfo**kullanarak bunları raporlayın.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Etkili ve uygun bildirim sunu seçin.
 Kalıcı bir iletişim kutusu (zaman uyumlu bildirim) veri kaybını önlemek için Acil eylem gerekli kritik bir uyarı ile kullanın. Kritik simgelerini hangi ileti okuma olmadan kapatma, olumsuz sonuçlara yol açabilir durumlar için ayrılmıştır. Veri kaybı Uyarısı Düzeyi yanıt gerektiren kritik bir durumdur. Kritik simgesi aşırı kullanımını önem derecesini kullanıcılara desensitizes. Hata iletisi bilgilendirme ise, kalıcı bir iletişim kutusu (zaman uyumsuz bildirim) alternatifleri düşünün.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Neden bir teknik açıklama yerine sorun oluştu, temiz, birleştiren bir açıklama sağlayın.
 Teknik Ayrıntılar açıklama kullanıcılarla overburdening bunları hata iletileri yok saymak büyük olasılıkla yapar. İyi Mesajlaşma örnekleri:

- "İstenen dosya açılamıyor."

- "Internet bağlantısı kurulamıyor."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Sorunun çözümü hakkında bilgi sağlar.
 Sorunu gidermek nasıl kullanıcı öneriler sunar. Öneri yok ise kullanıcıyla dürüst olun. Teknik destek veya topluluk desteği gibi diğer çevrimiçi kaynakları doğrudan bağlantıları verilmektedir. Kullanıcılar, sorunla ilgili belirli çevrimiçi bilgi işaret edecek şekilde deneyin. Hata kimliği için kullanıcıların belirli bir hata hakkında bir tartışma iş parçacığına bağlama göz önünde bulundurun. İyi Mesajlaşma örnekleri:

- "Internet'e bağlı ve bu işlemi yeniden deneyin emin olun."

- "Dosyasının varolduğunu ve ürünü açma izniniz olduğundan emin olun."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Kısa ve noktasına olduğunu belirten bir ileti yazın.
 Bir hata iletisi bir çözüme bildirimde bulunabilir, açıklayabilir ve sunabilir, ancak yine de çok fazla sözcük olduğunda yok sayılır. Tek bir çözüm ayrıntıları düğmeyle aşamalı açığa kullanmaktır. Örneğin, kısa bir açıklama/çözüm verin ve ardından ayrıntılar düğmesine altında daha fazla ayrıntı yerleştirin. Hata hakkında daha fazla bilgi okumak kullanıcılar'ı seçerseniz, bunlar bunu yapabilirsiniz.

 İleti dilde olmalıdır:

- **Etki alanı uygun.** Kullanıcı anlayacaksınız dil kullanın. Müşterilerimizin geliştiriciler olsa da, bunlar genellikle sahibiz terminoloji ve bağlam yok.

- **Belirli.** Belirsiz ifadesi önlemek ve belirli adları ve konumları katılan nesnelerin verin. Örneğin, "karakteri geçersiz gibi" bir hata iletisi yararlı değildir. Hangi karakter? "Dosya bulunamadı." Hangi dosya?

- **Korkusuz.** Kullanıcı sorumlu veya onları stupid düşünüyorsanız kullanmayın. Tehlikeli ya da rahatsız edici dil kaçının (KILL, yürütün, önemli, geçersiz sonlandırma). Çok shouting olarak görülür ve olarak okunabilir değil tüm harfleri büyük metin kaçının. Anıları kullanmayın.

- **Düzeltmeye.** Yazım ve dil bilgisi (hatta alfalar içinde) kullanın. Yazım hatası okuyucunuz ve marifetiyle.

- **Bağlamsal olarak uygun.** Uygun düğme metni kullanın. "Tamam" düğmesini kullanmaktan kaçının ve bunun yerine "Continue" veya "Yes/No" kullanın.

### <a name="error-message-examples"></a>Hata iletisi örnekleri

|İyi|hatalı|
|----------|---------|
|"Çevirdiğiniz sayı artık hizmette değil. Lütfen numarayı denetleyin ve operatör için bir kez daha çevirin veya 0 çevirin. "|-"Hata (449): Geçersiz sayı"<br />-"İşlenmemiş özel durum hatası işlemin başarıyla tamamlandığını gösteriyor."<br /><br /> ![Visual Studio 'da hatalı hata iletisi](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Yardımı'na erişme

### <a name="overview"></a>Genel Bakış
 MSDN belgelerinde yanı sıra, Visual Studio kullanıcı, kullanıcı arabiriminde yardımcı olmak üzere çeşitli erişim noktaları vardır. Bu erişim noktaları sürekli kullanılabilir olmasını sağlamak için ortamı tarafından sunulan Yardım sistemi yararlanmak özellik takımı gerekir. Bu erişim noktaları şunlardır:

- **İletişim kutularında yönerge ve ek metin.** Yön veya açıklaması, üzerinde yüzey veya üzerine bilgi ipucu simgesinin üzerine gelindiğinde kullanılabilen kullanıcı Arabirimi sağlayan statik metin.

- **F1 yardımı** (yalnızca Düzenleyici). Visual Studio düzenleyicisi içinde bir kullanıcı herhangi bir zamanda F1 tuşuna bastığınızda geçerli seçime belirli bir Yardım konusu çıkarır, güvenebilir. F1 ile ilgili konuları ilgili ve bilgilendirici olduğundan emin olun.

- **Yardım konularına yönelik köprüler.** Bir iletişim kutusu, araç penceresi ya da kullanıcı bir teknoloji, özellik veya bir görevi gerçekleştirmek nasıl bilgi hakkında daha fazla yardımcı olmak için bir konu başlatan tasarım yüzeyine içinde köprü.

- **Akıllı Etiketler ve yapı iletişimleri gibi yardımcı UI mekanizmaları.** Bu mekanizmalar kullanıcı UI öğesi anlaşılmasına yardımcı veya akıllı etiketler veya Oluşturucu iletişim kutuları gibi bir görev.

- **UI yardım düğmeleri** (kullanım dışı). F1 Yardımı ilgili konuya erişmenizi başlık çubuğunda görünür bir göstergesi.

### <a name="text"></a>Metin

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Yönerge ve ek metin kutularındaki
 Karmaşık görevleri desteklemek iletişim kutularında, iletişim kutusunun veya karmaşık denetimlerde yakın üst genellikle kullanıcı Arabirimi içinde eğitici metin vermek için bir gereksinim olabilir. Stil yazma hakkında daha fazla bilgi için bkz. [Kullanıcı arabirimi metni ve terminolojisi](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="infotips"></a>InfoTips
 Genellikle, eğitici metin kullanıcı arabiriminde bir yerde konumlandırmak için çok uzun olabilir veya deneyimli kullanıcılar için dağınıklık gibi HİSSEDİYORSUNUZ yalnızca yeni kullanıcılar için yararlı olabilir. Bu durumda, bir bilgi ipucu altında bir araç ipucu olarak eğitici/bilgilendirici metin yerleştirilmelidir.

 InfoTips belirgin olarak ilgili ve henüz örtük belirli bilgi ipucu simgesi kullanması gereken denetimleri yerleştirilmelidir.

 ![Visual Studio 'da InfoTip Ipucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio 'da bilgi Ipucu örneği**

### <a name="interactive-help-mechanisms"></a>Etkileşimli yardım mekanizmaları

#### <a name="f1-help"></a>F1 Yardımı
 F1 Yardımı gerekiyor, içinde bir düzenleyici veya tasarım yüzeyine ancak Visual Studio ortamında değil başka bir yerde.

#### <a name="hyperlinks-to-help-topics"></a>Köprüler Yardım konuları
 Köprüler, bir eylemi gerçekleştirmek, IDE içinde gidin veya Yardım bir tarayıcıda başlatmak için kullanılabilir. Görsel ve düzen yönergeleri için dil ve 07.10.01 düğmeleri ve köprüleriyle ilgili ayrıntılar için bkz. [Kullanıcı arabirimi metni ve terimleri](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>(Kullanım dışı) iletişim başlık çubuğu düğmeleri [?] Yardım
 Çoğunlukla, iletişim kutuları, başlık çubuğunda Yardımı [?] düğmeleri kullanım dışı bırakılmıştır. Kullanıcı Arabirimi konuları artık doc modelimizi parçasıdır ve bu nedenle olmayabilir bağlamak için uygun bir konu. Aslında başlık çubuğu düğme F1 Yardımı ile aynı şeyi edildi ve artık iletişim kutularında gereklidir. Köprüler yeni kullanıcı Arabiriminde daha yaygın olarak kullanılan karşın bazı durumlarda, bu hala daha fazla kavramsal ya da yordam bilgisi kullanılabilir olduğunu bir gösterge kullanılabilir.

##### <a name="dialogs-created-through-the-environment"></a>Ortamı üzerinden oluşturulan iletişim kutuları
 Birçok kabuk iletişim kutusu, **Vbdialogboxparam** işlevi aracılığıyla oluşturulur. Bu paylaşılan işlev **Yardım** düğmesini iletişim kutusu 'ndan öğesine taşımaya yardımcı olacak şekilde **güncelleştirildi.** Geriye dönük bir mimari korurken düğmesi uyumlu ve genişletilebilir.

 Özellikle, **Vbdialogboxparam** IşLEVI, kimliği **IDHELP** (9) veya etiket **Yardım** veya **& yardım**olan bir düğmenin iletişim şablonuna bakar. Bir Yardım düğmesi bulunursa, gizlenir ve **ws_ex_contexthelp** stili iletişim kutusuna eklenir ve **Bu, öğesini yerleştiriyor.** iletişim kutusunun başlık çubuğunda düğme.

 İletişim kutusu oluşturulduğunda iletişim kutusu proc öğesini bir yığına gönderir ve iletişim kutusunu, **Iletişimpreproc**adlı bir işlem öncesi iletişim kutusu proc ile çağırır. Ne zaman **?** düğmesine tıklandığında, iletişim kutusuna **SC_CONTEXTHELP** **WM_SYSCOMMAND** gönderir. **Dialogpreproc** bu komutu yakalar ve özgün iletişim kutusu proc öğesine geçirilen bir **wm_help** iletisiyle değiştirir.

 Çoğu ortam oluşturulan iletişim kutuları, iletişim kutusunda Yardım düğmesine sahip. İletişim kutusu görüntülendiğinde, Yardım düğmesi otomatik olarak gizlenir ve yalnızca **?** Düğme çalışır. **Mi?** Düğme hiç olmadığı kadar kaldırıldı veya değiştirildi Windows, bu çözümü hızlı bir şekilde geri özgün Yardım düğmelere taşımanızı sağlar.

 Bu çözüm, hatalara neden olabilecek dört varsayımlarda bulunur:

- İletişim kutusunun Yardım düğmesi **IDHELP** (9) ' dir.

- Yardım düğmesi gizlenir doğru iletişim kutusu görünür.

- İletişim kutusu, kendi winproc yerine değil.

- İletişim kutusu içinde başka bir iletişim kutusu ekli değil.

  İletişim kutusu Msenv içinde bulunuyorsa ve **Vbdialogboxparam**kullanmıyorsa, kendi işleyicinizi uygulamadan önce **vbdialogboxparam** ' ı araştırın.

##### <a name="dialogs-created-through-other-packages"></a>Diğer paketler aracılığıyla oluşturulan iletişim kutuları
 Msenv dışında bulunan iletişim kutuları için kendi çözümünüzü uygulayabilirsiniz. İçinde VSPackage paylaşılan iletişim kutusu sınıfı için için başlık çubuğu düğmesini taşıma veya bir işleyici her iletişim kutusunda uygulama göz önünde bulundurun. Aşağıdaki kod, başlamanıza yardımcı olmak için bir uygulama bir skeleton şöyledir:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Yönetilen kodda Yardım düğmeleri
 Pencere başlık çubuğu Yardım düğmesinin varsayılan davranışı geçersiz kılma, yönetilen kodda kolaydır. Aşağıda bu davranışını gösteren bir tam bir tanıtım uygulamasıdır. Esas olarak, formunuzun **WndProc** metodunu geçersiz kılmanız ve ardından **SC_CONTEXTHELP** bir Ileti yakalandığı zaman F1 Yardım isteklerini tetiketmeniz gerekir.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio İçin Yazı Tipleri ve Biçimlendirme](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Visual Studio İçin Düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Visual Studio İçin Bildirimler ve İlerleme Durumu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
