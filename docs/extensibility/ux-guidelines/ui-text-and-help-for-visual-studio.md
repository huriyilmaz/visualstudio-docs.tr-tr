---
title: Kullanıcı Arabirimi Metni ve Visual Studio | Microsoft Docs
description: Yardım bilgileri'nde kullanılan kullanıcı arabirimi metni ve terminolojisi hakkında bilgi Visual Studio.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6e946715687b46f651ac301f4e95207dbde23451011e9a48d0c20ae6a200e073
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121335426"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Visual Studio İçin UI Metni ve Yardımı
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> Kullanıcı arabirimi metni ve terminolojisi
 Anlanabilir metin, etkili kullanıcı arabirimi için çok önemlidir. Yazılım kullanıcıları etiketleri ilk olarak okuma eğilimindedir; diğer bir ad da görevi tamamlamakla ilgili olanlardır. Statik metin daha az sıklıkta okunur. Kullanıcıların tüm pencereyi hızlı bir taramayla iş oturumlarını başlatmasını ve ardından bu yaklaşık sırayla kullanıcı arabirimini okumasını planla:

1. Ortalarda etkileşimli denetimler

2. Yürütme düğmeleri

3. Başka bir yerde bulunan etkileşimli denetimler

4. Ana yönergeler

5. Ek açıklamalar

6. Pencere başlığı

7. Ana gövdede diğer statik metin

### <a name="usage-patterns-for-ui-text"></a>Kullanıcı arabirimi metni için kullanım desenleri

#### <a name="title-bar-text"></a>Başlık çubuğu metni
 Başlık çubuğu metni, kullanıcı arabirimini doğuran komutla eşleşmeli.

#### <a name="instructional-text-helper-text"></a>Yönerge metni (yardımcı metin)
 Bazı iletişim kutularında, pencerede veya sayfada ne yap adımlarını açıklamak için önemli ana yönergeler sağlamak yararlı olur. Bu bazen "yardımcı metin" olarak adlandırılır.

##### <a name="writing-style-rules-for-helper-text"></a>Yardımcı metin için stil kuralları yazma

- Bariz olan şeyi açıklayacağız. Kesinlikle gerekli değilse, yönerge metni dahil değildir.

- Yönerge metni her zaman iletişim kutusunun en üstüne yerleştirilir ve gerçekleştirilen göreve başvur yapılmalıdır.

- Kullanıcılara yapmaları gerekenleri tam olarak açıklayacaklar. Aşırı iletişim ve yedeklilikten kaçının.

- Her pencereyi gözden geçirin ve yinelenen sözcükleri ve deyimleri ortadan kaldırın.

- Yönerge metnini kısa tut. Belirli kullanıcılar veya senaryolar için daha fazla bilgi gerekiyorsa, ayrıntılı bir kavramsal çevrimiçi konunun bağlantısını sağlar.

- Her sözcüğün ağırlığını ve gerekli olduğu şekilde metinlerinizi yazın.

- Metin ve Stil ve Tone [Kullanıcı Arabirimi için](/windows/desktop/uxguide/text-ui) mevcut Microsoft [yönergelerini izleyin.](/windows/desktop/uxguide/text-style-tone)

#### <a name="supplemental-instructions"></a>Ek yönergeler
 Ek yönergeler, kullanıcının denetimleri veya denetim gruplamalarını anlamanıza yardımcı olacak ek bilgiler sağlar. Bu, giriş denetimi için hangi biçimin beklediğini anlamak için gerekli ipucu metnini de içerebilir. Ek yönergeleri çok fazla kullanın. Bunları, kullanıcının tercihle ilgili sonuçları tam olarak anlamayacakları durumlar için yedekler.

 ![Seçenekler düğmesini Internet Explorer ayarlarını değiştirmenin etkisini açıklayan ek metinle birlikte gösteren ekran görüntüsü.](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Metinde ek Visual Studio**

 ![Kaynak denetimi sistemi seçeneklerinin her birini Visual Studio ek metni gösteren Kaynak Denetimi Seç iletişim kutusunun ekran görüntüsü.](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Metinde ek Visual Studio**

#### <a name="infotips"></a>InfoTips
 Genellikle, yönerge metni kullanıcı arabiriminde yerinde konumlandırmak için fazla uzun olabilir veya yalnızca yeni kullanıcılar için yararlı olabilir ve deneyimli kullanıcılar için dağınık gibi olabilir. Bu durumda, yönerge/bilgilendirme metni bir InfoTip'in altına araç ipucu olarak yerleştiril should.

 InfoTips, ilişkili olduğu denetimlerin yanına yerleştiril olmalı ve dikkatisiz ancak fark edilebilir olan belirli InfoTip simgesini kullan seçmelidir.

 ![Visual Studio'de InfoTip](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio'da InfoTip örneği**

##### <a name="writing-style-rules-for-infotips"></a>InfoTips için stil kuralları yazma

- Tam cümleler olarak InfoTips yazın. Belirli fiiller, cümle büyük/küçük harf ve bitiş noktalama işaretleri gerektirir.

- Ana yönergenizi veya bilgilerinizi tamamlarken InfoTips'i kullanın. Ana fikri yeniden ifade etmek için yalnızca farklı sözcükler kullanıyorsanız InfoTip'e ihtiyacınız yok.

- InfoTips'i kısa ve tatlı olarak tut. Küçük sözcükleri ve kullanıcıya destek olan ve teşvik eden düz, günlük dil kullanın.

- Metin ve Stil ve Tone [Kullanıcı Arabirimi için](/windows/desktop/uxguide/text-ui) mevcut Microsoft [yönergelerini izleyin.](/windows/desktop/uxguide/text-style-tone)

#### <a name="control-labels"></a>Denetim etiketleri
 Denetim etiketleri kısa, kısa olmalı ve Denetimler için [Windows Desktop yönergelerini izlemeli.](/windows/desktop/uxguide/controls)

 Denetim etiketi biçimi ve kullanıcı arabiriminde yerleştirme hakkında daha fazla bilgi için bkz. [Visual Studio.](../../extensibility/ux-guidelines/layout-for-visual-studio.md)

#### <a name="help-links"></a>Yardım bağlantıları
 Yardım bağlantıları, yönerge metni içine veya kullanıcı arabiriminin gövdesine yer verilmiştir. Bunlar Yardım'a bağlantı olabilir veya iç iletişim kutularını başlatabilirsiniz.

##### <a name="visual-style-rules-for-help-links"></a>Yardım bağlantıları için görsel stil kuralları

- Köprüler için doğru ortam renklerini kullanın. Düzgün bir şekilde stile sahip köprüler tıklarken kısa süre kırmızı renkle yanıp sönmez. Bunu görüyorsanız bu, ortam renklerinin kullanılmama göstergesidir.

- Alt çizgiler yalnızca üzerine gelindiğinde veya bağlantı bir paragrafa ekli olduğunda kullanılmalıdır.

- Köprüler için görsel ve etkileşim stilleri hakkında daha ayrıntılı bilgi için bkz. Düğmeler ve köprüler.

##### <a name="writing-style-rules-for-help-links"></a>Yardım bağlantıları için stil kuralları yazma

- İletişim kutularını başlatıyorsanız üç nokta standartlarını sürdürün: gezinti için üç nokta yok, görev ek kullanıcı arabirimi gerektiriyorsa üç nokta.

     ![Visual Studio'de yardım bağlantısı](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Yardım bağlantısında üç nokta (...) olması, görevin ek kullanıcı arabirimi gerektireceklerini gösterir.**

- Bağlantılar "Learn" ile başlamaz çünkü bu kullanıcının amacı değildir. Kullanıcı, genel eğitim almak değil belirli bir soruyu yanıtlamak istiyor.

- Tümcecik yardımı bağlantıları, konunun yanıtını soracakları bir soru sorar.

     Yanlış: "Azure Mobile Services fiyatlandırması hakkında Windows bilgi edinin"

     Doğru: "Azure Windows için Mobile Services?"

- Bağlantı metni *için hiçbir zaman Tıklama...* seçeneğini kullanma.

- Hiçbir zaman yalnızca "here" sözcüğüne bağlamayın. Bu, bazı ekran okuyucular için soruna neden olur ve bu durum yalnızca köprüdeki sözcüğü ifade etmektedir.

     Yanlış: "Azure Windows bilgileri burada Mobile Services **bulabilirsiniz"**

     Doğru: "Azure Windows için Mobile Services?"

- Yardım bağlantıları için doğru yazma stili hakkında daha fazla bilgi için Yardım için [Windows Masaüstü kılavuzuna bakın.](/windows/desktop/uxguide/winenv-help)

#### <a name="hint-text"></a>İpucu metni
 İpucu metni, denetim içinde veya denetimin altında filigran olarak görünür. Doğru biçimlendirme, uygun VSColors belirteci kullanılarak `Environment.GrayText` uygulanır.

 Çeşitli biçimlerde görünebilir.

- Denetim etiketinin yerine:

     ![Denetim etiketi yerine "Arama çubuğu (Ctrl+Çözüm Gezgini) " ifadesinin yer Çözüm Gezgini açılan denetimin ;).](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Bir fiil ile yönergeler verme:

     ![Denetimde "Adını girin" ifadesinin yer alan ipucu metninin yer alan metin kutusunun ekran görüntüsü.](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Gerekli girişi gösteren metin:

     ![Denetimde " Gerekli " ifadesinin yer alan ipucu metninin yer alan metin \< kutusunun ekran \> görüntüsü.](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Filigran metni
 Boş bir tasarım yüzeyinde, metin ne yapacaklarını belirt olmalı ve uygunsa diğer ilgili pencerelerin bağlantılarını sağlamış olmalı:

 ![Visual Studio'de filigran metni](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Visual Studio'de filigran metni örneği**

### <a name="common-terminology"></a>Ortak terminoloji

|Süre|Açıklama|Yorum|
|----------|-----------------|-------------|
|Oturum açma / Oturum açma|Fiiller, bir web özelliğine kimlik doğrulamasını temsil eden web ile eş anlamlı olarak kullanılır. İstemciler içinde bunu, IDE kullanıcı bağlantısında oturum açma ve bağlantıdan çıkma için en üst düzey bir durum olarak kullanıriz. Bu, dolaşım ve diğer tüm bağlantılarda mevcut olmayan lisanslama gibi daha üst düzey özellikler sağlayan üst düzey bir kimliği temsil eder.|IDE Kullanıcısı, üst düzey IDE kullanıcısını temsil ettiği için oturum açma/oturum açma fiilini temsil eden tek özelliktir.|
|Bağlan / Bağlantıyı Kes|Bir özelliğin çevrimiçi bir hizmete tek bir bağlantının olduğu yerlerde kullanın.|Sunucu Gezgini tek bir etkin Azure bağlantısına sahip olmak, bağlantının kesilmesi/bağlantısının kesilmesine Bağlan örnektir.|
|Ekle/ Kaldır|Yıkıcı olmayan. Listeden bir şey eklerken veya listeden bir şeyi çıkarırken kullanın.|TFS Bağlantı Yöneticisi listesi iletişim kutusu, Ekle/Kaldır'a bir örnektir.|
|Sil|Yıkıcı. Yalnızca kaldırılan öğe kalıcı olarak atılacak veya diskten silinecekse kullanın.|Sonuçta diskten bir dosya silindiğinde "Sil" genellikle bir istem gerektirir.|

## <a name="error-messages"></a>Hata iletileri

### <a name="overview"></a>Genel Bakış
 Hatalar olur. Kullanıcının neler yapa bir sınırlama ayarlaması, önlenebilir hata iletilerini önlemenin mantıklı bir ilk adımıdır. Ancak, bir hata oluştuğunda, iyi yazılmış bir hata iletisi sorunu azaltmaya yönelik uzun bir yol olabilir. Hata iletileri muhtemelen kullanıcının gördüğü en önemli bildirim türlerinden biri olabilir çünkü bunlar zaman uyumludur ve çözülmesi gereken bir sorunu gösterir. Hatalı yazılmış hata iletileri kullanıcıların kendi başına hataların nedenini ve olası çözümleri karar vermelerini sağlar.

 Kullanıcılar fazla veya kafa karıştırıcı hata iletilerine dikkat etmeyi durdurabilir, bu nedenle yalnızca kullanıcı deneyimine değer katacak gerekli iletileri yazın. İleti yalnızca bir bildirimse alternatif bir sunu kullanın.

### <a name="rules-for-creating-an-error-message"></a>Hata iletisi oluşturma kuralları

- Hata iletileri oluşturma sırasında hedef kitle için uygun hata düzeyini seçin. Kullanıcının uygunsa, bir eylemde esnes geçe basit özetler sağlamayı hedefle. Kullanıcının bilmek zorunda olmadığını bir şey söyleme.

- Yapıcı yardım sağlama. Yönerge içeren bir hata iletisini okumak ve üzerinde eylem yapmak daha kolaydır.

- Çift negatif kullanma.

- Yazmanız gereken hata iletisinde hem otomatik hem de el ile dil bilgisi ve yazım denetimi gerçekleştirin.

- Karmaşık hata iletileri için sıralı iletişimlerden kaçının. Hata iletisi için hiçbir zaman F1 kancası kullanma. İletinin kendisi yeterli olmalıdır.

- Doğru simgeyi kullanın.

- "Sil" ve "İptal" gibi net seçeneklere sahip olan, kolay anlaşılır ve kullanımı kolay sorular sorun.

- Uyarılarda, devam etmeden sonra ne olacağını net bir şekilde açık olun. Düğmelerin sonucu belirt olması gerekir.

- Hatalar için, kullanıcının sorunu çözmek için neler yapalarını açık olun. Düğmeler eylem olmalı veya "Kapat" desin. Hata iletisi için "Tamam" düğmesini kullanma.

- Hata iletisi oluşturma sırasında kendinize sormanız gereken bazı sorular:

  - Kullanıcı yalnızca bu hatayla ilgili sorunu nasıl çözeceğini çözebilir mi?

  - Kullanıcı bu hatayla aynı sözlüğü kullanıyor mu?

  - Bu hata belirsiz mi yoksa birden çok durumda mı paylaşılıyor? Öyleyse, kullanıcılara ihtiyaçları olan çözüm için nasıl yol sunarsınız?

#### <a name="build-errors"></a>Derleme hataları
 Bu Visual Studio bir yazılım geliştirme aracı olduğu için, bileşenlerinin çoğu geliştiricinin çalışmalarını ikili biçime dönüştürmek için derleme, dönüştürme veya kodlama adımına sahiptir. Bu dönüştürmeler, derleyici yanlış şekilde yazmalı dosyaları işleyemey olduğunda veya derleyici seçenekleri doğru ayarlanmasa hatalara neden olabilir.

 Visual Studio kullanıcılar derleme hatalarını çözmek için çok fazla sayıda geliştirme saati harcayabiliyor. Hataların bağımlılıkları olduğunda veya hata iletileri kötü yazıldığı zaman bu çözümleme süresi artar ve bu da hatanın kaynağını ortaya çıkarmayı zorlaştırabilirsiniz.

 En iyi derleme hataları, en başta oluşmaz. Bu nedenle Visual Studio Ve IntelliSense geçişleri sağlar. Şema doğrulayıcıları ve benzer araçlar aynı tür geri bildirim sağlar. Bu mekanizmalar, kullanıcıya proaktif olarak iyi oluşturulmuş kod oluşturması için yol gösterir ve derleme hatalarının ihtimalini azaltır.

 Visual Studio kullanıcıların belge pencerelerinde oluşan hataları okuyabilen ve gezinen bir araç penceresi sağlar. Klavye kısayolları, kullanıcının büyük miktarda kodda hızla gezinmesini ve doğrudan sorunun bulunduğu konuma gitmesini sağlar. Visual Studio ayrıca her derleme hatasının belirli bir Yardım anahtar sözcüğüne/bağlam kimliğine bağlanarak kullanıcının hata hakkında daha ayrıntılı bilgi veren bir Yardım konu başlığına doğrudan gidebilir.

 Net ve kısa derleme hataları yazın:

- **Sorunu çok az** derleyici jargonu ile açıklayan düz dil kullanın. Derleme hatasının metni fazla teknik olmayacaktır.

- **Olası nedenleri özetle.** Örneğin, "'(property) : (value)' bildiriminde özellik ve değer arasında iki nokta üst üste eksik."

- Olası düzeltmeler hakkında ayrıntılı bilgi verme. Yeterli alan yoksa, ilgili Yardım konu başlığına ek ayrıntılar girebilirsiniz.

### <a name="components-of-a-well-written-error-message"></a>İyi yazılmış hata iletisinin bileşenleri

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Hata iletileri için kabuk iletişim kutusunu kullanın.
 Kabuk iletişim kutusunu kullanmak, tek tek öğelerde büyük değişiklikler yapmadan iletinin, yazı tiplerinin görünümünü denetlemenizi sağlar. **IErrorInfo** mekanizmalarını kullanın ve **IVsUIShell::SetErrorInfo/ReportErrorInfo kullanarak bunları rapor edin.**

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Etkili ve uygun bir bildirim sunusu seçin.
 Veri kaybını (zaman uyumlu bildirim) önlemek için hemen eylem gerekirse kritik uyarı ile kalıcı bir iletişim kutusu kullanın. Kritik simgeler, iletiyi okumadan kapatmanın olumsuz sonuçlara neden olduğu durumlar için ayrılmıştır. Veri kaybı, alarm düzeyinde yanıt gerektiren kritik bir durumdur. Kritik simgenin aşırı aşırı kullanılabilirlik durumu, kullanıcıları önemine karşı duyarsız hale taşır. Hata iletisi doğası gereği bilgilendirmeye ilişkinse kalıcı iletişim kutusunun (zaman uyumsuz bildirim) alternatiflerini göz önünde bulundurabilirsiniz.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Sorunun teknik bir açıklama yerine neden meydana geldiğine ilişkin temiz ve kısa bir açıklama sağlar.
 Açıklamanın teknik ayrıntılarıyla kullanıcıların aşırı yüklü olması, hata iletilerini yoksaymalarının daha olası hale gelmelerini sağlar. İyi mesajlaşma örnekleri:

- "İstenen dosya açamıyor."

- "İnternet'e bağlanamıyor."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Sorunun nasıl çözülecekleri hakkında bilgi sağlama.
 Sorunu çözmek için kullanıcıya önerilerde bulundurabilirsiniz. Öneri yoksa kullanıcıya karşı dürüst olun. Teknik destek veya topluluk desteği gibi alternatif çevrimiçi kaynaklara doğrudan bağlantılar sağlama. Kullanıcıları sorunla ilgili belirli çevrimiçi bilgilere işaret etmeye çalışma. Hata kimliği için kullanıcıları bu hatayla ilgili bir tartışma iş parçacığına bağlamayı göz önünde bulundurabilirsiniz. İyi mesajlaşma örnekleri:

- "İnternet'e bağlı olduğunuzdan emin olun ve bu işlemi yeniden deneyin."

- "Dosyanın mevcut olduğundan ve dosyayı açma izniniz olduğundan emin olun."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Kısa ve noktaya kadar olan bir ileti yazın.
 Hata iletisi bir çözümü bildirerek, açıklayabilir ve sunsa da çok fazla sözcük varsa yine de yoksayılabilir. Çözümlerden biri, bir ayrıntılar düğmesiyle aşamalı açıklama kullanmaktır. Örneğin, kısa bir açıklama/çözüm girin ve ayrıntılar düğmesinin altına daha fazla ayrıntı girin. Kullanıcılar hata hakkında daha fazla bilgi okumayı seçerse, bunu yapar.

 İletide yer alan dil şu şekildedir:

- **Etki alanına uygun.** Kullanıcının anlayacaktır dili kullanın. Müşterilerimiz geliştirici olsa da çoğu zaman sahip olduğu bağlam ve terminolojiye sahip değil.

- **Belirli.** Belirsiz ifadelerden kaçının ve söz konusu nesnelerin belirli adlarını ve konumlarını verir. Örneğin, "karakter geçersiz" gibi bir hata mesajı yararlı değildir. Hangi karakter? "Dosya bulunamadı". Hangi dosya?

- **Korkusuz.** Kullanıcı yapmayın veya onları STUPID hissetmeyin. Saldırgan veya kötü amaçlı dil kullanmaktan kaçının (KILL, Execute, Terminate, önemli, geçersiz). Genellikle, görünen ve okunabilir olmayan büyük harfli metinden kaçının. Humor kullanmayın.

- **Doğru.** Doğru yazım ve dilbilgisi (Alpin içinde bile) kullanın. Yazım hataları, profesyonel olmayan ve embaranet.

- **Bağlamsal olarak uygun.** Uygun düğme metnini kullanın. "Tamam" düğmesini kullanmaktan kaçının ve bunun yerine "Continue" veya "Yes/No" kullanın.

### <a name="error-message-examples"></a>Hata iletisi örnekleri

|İyi|Kötü|
|----------|---------|
|"Çevirdiğiniz sayı artık hizmette değil. Lütfen numarayı denetleyin ve operatör için bir kez daha çevirin veya 0 çevirin. "|-"Hata (449): Geçersiz sayı"<br />-"İşlenmemiş özel durum hatası işlemin başarıyla tamamlandığını gösteriyor."<br /><br /> ![Visual Studio hatalı hata iletisi](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Yardım 'A erişme

### <a name="overview"></a>Genel Bakış
 MSDN 'deki belgelere ek olarak, bir Visual Studio kullanıcının kullanıcı arabiriminden çalışırken yardım almak için çeşitli erişim noktalarına sahip olması gerekir. Bu erişim noktalarının sürekli olarak kullanılabilir olduğundan emin olmak için, özellik ekiplerinin ortam tarafından sunulan yardım sisteminden faydalanması gerekir. Bu erişim noktaları şunlardır:

- **İletişim kutularında yönerge ve ek metin.** UI yüzeyinde veya bir bilgi Ipucu simgesinin üzerine gelindiğinde, yön veya açıklama sağlayan statik metin.

- **F1 yardımı** (yalnızca Düzenleyici). Visual Studio düzenleyicisinde, bir kullanıcı herhangi bir zamanda güvenebilir, F1 tuşuna basıldığında geçerli seçime özgü bir yardım konusu görüntülenir. F1 ile ilişkili konuların uygun ve bilgilendirici olduğundan emin olun.

- **Yardım konularına yönelik köprüler.** Bir iletişim kutusu, araç penceresi veya tasarım yüzeyi içindeki bir köprü, kullanıcının bir teknoloji, yetenek veya bir görevi nasıl gerçekleştireceğinizi hakkında daha fazla bilgi edinmeye yardımcı olacak bir konu başlatır.

- **Akıllı Etiketler ve yapı iletişimleri gibi yardımcı UI mekanizmaları.** Bu mekanizmalar, kullanıcının bir kullanıcı ARABIRIMI öğesini anlamasına veya akıllı etiketler ya da Oluşturucu iletişim kutuları gibi bir görevi kolaylaştırmasına yardımcı olur.

- **UI yardım düğmeleri** (kullanım dışı). Başlık çubuğunda ilgili F1 Yardım konusuna erişim sağlayan görünür bir gösterge.

### <a name="text"></a>Metin

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>İletişim kutularında yönerge ve ek metin
 Karmaşık görevleri destekleyen iletişim kutularında, genellikle iletişim kutusunun üstünde ya da karmaşık denetimlerin yakınında, Kullanıcı arabirimi içinde açıklayıcı metin verme gereksinimi olabilir. Stil yazma hakkında daha fazla bilgi için bkz. [Kullanıcı arabirimi metni ve terminolojisi](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="infotips"></a>Bilgi Ipuçları
 Genellikle, eğitici metin Kullanıcı arabiriminde yerinde konumlandırılamayacak kadar uzun olabilir veya yalnızca yeni kullanıcılar için yararlı olabilir. Bu durumda, yönerge/bilgilendirici metnin bir bilgi Ipucu altına bir araç ipucu olarak yerleştirilmesi gerekir.

 InfoTips, ilişkili oldukları denetimlerin yanına yerleştirilmelidir ve kesin bir şekilde fark edilebilir olan belirli bilgi Ipucu simgesini kullanmalıdır.

 ![Visual Studio bilgi Ipucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio bilgi Ipucu örneği**

### <a name="interactive-help-mechanisms"></a>Etkileşimli yardım mekanizmaları

#### <a name="f1-help"></a>F1 Yardımı
 bir düzenleyici veya tasarım yüzeyi içinde F1 yardımı gereklidir, ancak Visual Studio ortamında başka bir yerde değildir.

#### <a name="hyperlinks-to-help-topics"></a>Yardım konularına yönelik köprüler
 Köprüler bir eylem gerçekleştirmek, IDE içinde gezinmek veya yardımı bir tarayıcıda başlatmak için kullanılabilir. Görsel ve düzen yönergeleri için dil ve 07.10.01 düğmeleri ve köprüleriyle ilgili ayrıntılar için bkz. [Kullanıcı arabirimi metni ve terimleri](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>İletişim kutusu başlık çubuklarındaki yardım [?] düğmeleri (kullanım dışı)
 Çoğu bölüm için, iletişim kutularının başlık çubuğundaki Help [?] düğmeleri kullanım dışıdır. Kullanıcı arabirimi konuları artık belge modelimizin bir parçası değildir ve bu nedenle bağlantı için ilgili bir konu bulunmayabilir. Temelde, başlık çubuğu düğmesi F1 yardımı ile aynı şeydir ve iletişim kutularında artık gerekli değildir. Bazı örneklerde bu, daha fazla kavramsal veya yordamsal bilgiler olduğunu gösteren bir gösterge olarak kullanılabilir, ancak köprüler daha yaygın olarak daha fazla Kullanıcı arabiriminde kullanılıyor olabilir.

##### <a name="dialogs-created-through-the-environment"></a>Ortam üzerinden oluşturulan iletişim kutuları
 Birçok kabuk iletişim kutusu, **Vbdialogboxparam** işlevi aracılığıyla oluşturulur. Bu paylaşılan işlev **Yardım** düğmesini iletişim kutusu 'ndan öğesine taşımaya yardımcı olacak şekilde **güncelleştirildi.** düğmesini basılı tutarak, geriye dönük olarak uyumlu ve genişletilebilir bir mimari tutarken.

 Özellikle, **Vbdialogboxparam** IşLEVI, kimliği **IDHELP** (9) veya etiket **Yardım** veya **&yardım** olan bir düğmenin iletişim şablonuna bakar. Bir Yardım düğmesi bulunursa, gizlenir ve **ws_ex_contexthelp** stili iletişim kutusuna eklenir ve **Bu, öğesini yerleştiriyor.** düğmesine basın.

 İletişim kutusu oluşturulduğunda iletişim kutusu proc öğesini bir yığına gönderir ve iletişim kutusunu, **Iletişimpreproc** adlı bir işlem öncesi iletişim kutusu proc ile çağırır. Ne zaman **?** düğmesine tıklandığında, iletişim kutusuna **SC_CONTEXTHELP** **WM_SYSCOMMAND** gönderir. **Dialogpreproc** bu komutu yakalar ve özgün iletişim kutusu proc öğesine geçirilen bir **wm_help** iletisiyle değiştirir.

 Ortam tarafından oluşturulan birçok iletişim kutusu, iletişim kutusunda bir Yardım düğmesi vardır. İletişim kutusu görüntülendiğinde, Yardım düğmesi otomatik olarak gizlenir ve yalnızca **?** düğme işe yarar. **Mi?** düğme, Windows bir süre önce kaldırılır veya değiştirildiğinde, bu çözüm özgün yardım düğmelerine hızlıca geri taşımanızı sağlar.

 Bu çözüm, hatalara neden olabilecek dört varsayımlar yapar:

- İletişim kutusunun Yardım düğmesi **IDHELP** (9) ' dir.

- Yardım düğmesi gizliyse iletişim kutusu doğru görünür.

- İletişim kutusu WinProc 'u değiştirmez.

- İletişim kutusu başka bir iletişim kutusunun içine katıştırılmamış.

  İletişim kutusu Msenv içinde bulunuyorsa ve **Vbdialogboxparam** kullanmıyorsa, kendi işleyicinizi uygulamadan önce **vbdialogboxparam** ' ı araştırın.

##### <a name="dialogs-created-through-other-packages"></a>Diğer paketlerle oluşturulan iletişim kutuları
 Msenv dışında bulunan iletişim kutuları için kendi çözümünüzü uygulayabilirsiniz. VSPackage içindeki paylaşılan bir iletişim kutusu sınıfı için, düğmeyi başlık çubuğuna taşımayı veya her iletişim kutusunda bir işleyici uygulamayı düşünün. Aşağıdaki kod, başlamanıza yardımcı olması için bir uygulamanın iskelet 'udır:

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

##### <a name="help-buttons-in-managed-code"></a>Yönetilen koddaki yardım düğmeleri
 Pencere başlık çubuğunun Yardım düğmesinin varsayılan davranışını geçersiz kılmak, yönetilen kodda kolaydır. Aşağıda, bu davranışı gösteren kapsamlı bir tanıtım uygulaması verilmiştir. Esas olarak, formunuzun **WndProc** metodunu geçersiz kılmanız ve ardından **SC_CONTEXTHELP** bir Ileti yakalandığı zaman F1 Yardım isteklerini tetiketmeniz gerekir.

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
