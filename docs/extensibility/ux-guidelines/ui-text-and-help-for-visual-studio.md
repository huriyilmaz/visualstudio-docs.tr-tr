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
ms.openlocfilehash: 4ca987c3f4b311b75b6a6070f8340c179c2ea6e0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078719"
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

- Yönerge metni her zaman iletişim kutusunun en üstüne yerleştirilir ve gerçekleştirilen göreve başvurur.

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

 **Visual Studio'de InfoTip örneği**

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

- Hiçbir zaman *bağlantı metnine tıklayın...* seçeneğini kullanın.

- Hiçbir zaman yalnızca "here" sözcüğüne bağlamayın. Bu, bazı ekran okuyucular için soruna neden olur ve bu durum yalnızca köprüdeki sözcüğü ifade etmektedir.

     Yanlış: "Azure Windows bilgileri burada Mobile Services **bulabilirsiniz"**

     Doğru: "Azure Windows için Mobile Services?"

- Yardım bağlantıları için doğru yazma stili hakkında daha fazla bilgi için yardım [için Windows Masaüstü kılavuzuna bakın.](/windows/desktop/uxguide/winenv-help)

#### <a name="hint-text"></a>İpucu metni
 İpucu metni, denetim içinde veya denetimin altında filigran olarak görünür. Doğru biçimlendirme, uygun VSColors belirteci kullanılarak `Environment.GrayText` uygulanır.

 Çeşitli biçimlerde görünebilir.

- Denetim etiketinin yerine:

     ![Denetim etiketi yerine "Arama çubuğu (Ctrl ;)+Çözüm Gezgini" ifadesinin yer alan ipucu metninin yer Çözüm Gezgini ekran görüntüsü.](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

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
|Oturum Aç/Oturumu Kapat|Fiiller, bir Web özelliğinde kimlik doğrulamayı temsil etmek için Web ile terimler kullandı. İstemciler içinde, bu, diğer tüm bağlantılarda bulunmayan dolaşım ve lisanslama gibi daha yüksek düzey yetenekler sağlayan üst düzey bir kimliği temsil eden, IDE Kullanıcı bağlantısı açmak ve kapatmak için en üst düzey bir kavram olarak bir kez kullanılır.|IDE kullanıcısı, en üst düzey IDE kullanıcısını temsil ettiğinden, oturum açma/kapatma fiilini temsil eden tek özelliktir.|
|Bağlan/bağlantıyı kes|Bir özelliğin çevrimiçi bir hizmetle tek bir bağlantı tuttuğu yerlerde kullanın.|tek seferde yalnızca bir etkin Azure bağlantınız olabilir Sunucu Gezgini, Bağlan/disconnectörneğidir.|
|Ekle/Kaldır|Bozucu olmayan. Bir listeden bir öğe eklerken veya kaldırırken kullanın.|TFS bağlantı Yöneticisi sunucu listesi iletişim kutusu, Ekle/Kaldır ' a bir örnektir.|
|Sil|Siparişin. Yalnızca kaldırılmakta olan öğe kalıcı olarak atıldığı veya diskten silindiği zaman kullanın.|"Sil" işlemi genellikle sonuç diskten bir dosyayı silmeseniz bir istem gerektirir.|

## <a name="error-messages"></a>Hata iletileri

### <a name="overview"></a>Genel Bakış
 Hatalar meydana gelir. Kullanıcının yapabilecekleri kısıtlamaların ayarlanması, kaçınılmaz hata iletilerini engellemeye yönelik bir ilk adımdır. Ancak bir hata oluştuğunda, iyi yazılmış bir hata iletisi sorunu gidermek için uzun bir süre sürebilir. Hata iletileri, zaman uyumlu olduklarından ve çözülmesi gereken bir sorunu belirttiğinden, kullanıcının gördüğü en önemli bildirim türlerinden biridir. Hatalı yazılmış hata iletileri, hataların ve olası çözümlerin nedenine karar vermek için kullanıcıları kendi kendilerine bırakır.

 Kullanıcılar aşırı kullanılan veya kafa karıştırıcı hata iletilerine dikkat ederek durmayabilir, bu nedenle yalnızca kullanıcı deneyimine değer ekleyen gerekli iletileri yazın. İleti yalnızca bir bildirimidir, alternatif bir sunum kullanın.

### <a name="rules-for-creating-an-error-message"></a>Hata iletisi oluşturma kuralları

- Hata iletileri oluştururken, hedef kitle için uygun hata düzeyini seçin. Varsa, kullanıcının uygulayabileceğiniz bir eylem sağlayan basit özetler için hedefleyin. Kullanıcının bilmeleri gerekmeyen her şeyi değil.

- Oluşturulabilir yardım sağlayın. Yönerge içeren bir hata iletisini okumak ve üzerinde işlem yapmak daha kolay.

- Çift negatifler kullanmayın.

- Yazdığınız herhangi bir hata iletisinde otomatik ve el ile dilbilgisi ve yazım denetimi gerçekleştirin.

- Karmaşık hata iletileri için sıralı iletişimlerden kaçının. Hata iletisi için hiçbir şekilde F1 kancası kullanmayın. İletinin kendisi yeterli olmalıdır.

- Doğru simgeyi kullanın.

- "Sil" ve "Iptal" gibi açık seçeneklere sahip düğmeleri daha kolay anlaşılır hale getirin ve kullanın.

- Uyarılar için, devam eden nesnelerin ne olacağı hakkında net bir onay olun. Düğmeler, sonucu göstermelidir.

- Hatalar için kullanıcının sorunu çözmek için neler yapabileceğini betimleyen. Düğmeler eylem olmalıdır veya "Kapat" deyin. Bir hata iletisi için "Tamam" düğmesini kullanmayın.

- Bir hata iletisi oluştururken kendinize sorabileceğiniz bazı sorular:

  - Kullanıcı bu hatayla ilgili sorunu tek başına nasıl çözebileceğinizi anlayabilir mi?

  - Kullanıcı bu hata ile aynı sözlüğü kullanıyor mu?

  - Bu hata belirsiz veya birden çok durumda paylaşılıyor mu? Öyleyse, kullanıcılara gereken çözüme nasıl kılavuzluk edersiniz?

#### <a name="build-errors"></a>Derleme hataları
 Visual Studio bir yazılım geliştirme aracı olduğundan, bileşenlerinin çoğunda geliştirici işini ikili biçime dönüştürmek için bir derleme, dönüştürme veya kodlama adımı vardır. Derleyici yanlış yazılmış dosyaları işleyemezlerse veya derleyici seçenekleri doğru şekilde ayarlanmayacaksa, bu dönüşümler hatalara neden olabilir.

 Visual Studio kullanıcılar, derleme hatalarını çözmede çok sayıda geliştirme saati harcayabilir. Bu çözüm süresi, hatalar bağımlılıklar olduğunda veya hata iletileri hatalı yazıldığında artar ve bu da hatanın kaynağını açığa çıkarmak güç çıkarabilir.

 en iyi derleme hataları ilk yerde gerçekleşmeyecek olanlardır ve bu neden Visual Studio otomatik tamamlama ve ıntellisense dalgalı çizgiler sağlar. Şema Doğrulayıcıları ve benzer araçlar aynı türde geri bildirim sağlar. Bu mekanizmalar, kullanıcıya düzgün biçimlendirilmiş kod oluşturmayı ve derleme hatası olasılığını azaltır.

 Visual Studio, kullanıcıların belge pencereleri içinde oluşan hataları okuyabilecekleri ve bunlara gidebileceği bir araç penceresi sağlar. Klavye kısayolları, kullanıcının büyük miktarlarda koda hızla gidebilmesi ve doğrudan sorunun konumuna gidebilmesi için sağlanır. Visual Studio ayrıca, kullanıcının hata hakkında daha ayrıntılı bilgi veren bir yardım konusuna doğrudan gidebilmesi için, her derleme hatasının belirli bir yardım anahtar sözcüğüne/bağlam kimliğine bağlı olmasına izin verir.

 Write net, kısa derleme hataları:

- Çok az sayıda derleyici jargon ile ilgili sorunu açıklayan **düz dil kullanın** . Derleme hatasının metni aşırı teknik olmamalıdır.

- **Olası nedenler ana hattı.** Örneğin, "(özellik): (değer) ' bildiriminde özellik ve değer arasında iki nokta eksik."

- Olası düzeltmeler hakkında ayrıntılı bilgi verin. Yeterli yer yoksa, ilgili yardım konusuna ek ayrıntılar eklenebilir.

### <a name="components-of-a-well-written-error-message"></a>İyi yazılmış bir hata iletisinin bileşenleri

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Hata iletileri için kabuk iletişim kutusu hizmetini kullanın.
 Kabuk iletişim hizmetinin kullanılması, tek tek öğelerde büyük değişiklikler yapmadan iletinin görünüşünü, özellikle de yazı tiplerini denetlemenize olanak tanır. **IErrorInfo** mekanizmalarını kullanın ve **ısuishell:: SetErrorInfo/ReportErrorInfo** kullanarak bunları raporlayın.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Etkili ve uygun bir bildirim sunumu seçin.
 Veri kaybını önlemek için acil eylem gerekliyse, kritik bir uyarı ile kalıcı iletişim kutusu kullanın (zaman uyumlu bildirim). Kritik simgeler, iletiyi okumadan kapatmak, olumsuz sonuçlara yol açabilecek durumlar için ayrılmıştır. Veri kaybı, alarm düzeyinde bir yanıt gerektiren kritik bir durumdur. Kritik simgenin desensitizes kullanıcıları önem derecesine göre aşırı kullanımı. Hata iletisi doğası halinde bilgi alıyorsa, kalıcı iletişim kutusu (zaman uyumsuz bildirim) için alternatifleri göz önünde bulundurun.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Neden sorun oluştuğunu teknik bir açıklama yerine bir temiz, kısa açıklaması sağlayın.
 Açıklamada teknik ayrıntıları olan kullanıcılar, hata iletilerini yoksaymaya daha büyük hale getirir. İyi mesajlaşma örnekleri:

- "İstenen dosya açılamıyor."

- "Internet bağlantısı kurulamıyor."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Sorunu nasıl gidereceğiniz hakkında bilgi sağlayın.
 Sorunun nasıl çözüleceğini gösteren kullanıcı önerilerini sunun. Öneriniz yoksa kullanıcıyla birlikte kavun. Teknik destek veya topluluk desteği gibi alternatif çevrimiçi kaynaklara doğrudan bağlantılar sağlar. Kullanıcıları sorunla ilgili belirli çevrimiçi bilgileri gösterecek şekilde deneyin. Bir hata KIMLIĞI için, kullanıcıları ilgili belirli bir hata hakkında bir tartışma iş parçacığına bağlamayı göz önünde bulundurun. İyi mesajlaşma örnekleri:

- "Internet 'e bağlı olduğunuzdan emin olun ve bu işlemi yeniden deneyin."

- "Dosyanın var olduğundan ve dosyayı açma izniniz olduğundan emin olun."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Kısa ve noktaya bir ileti yazın.
 Bir hata iletisi bir çözüme bildirimde bulunabilir, açıklayabilir ve sunabilir, ancak yine de çok fazla sözcük olduğunda yok sayılır. Bir çözüm, bir ayrıntılar düğmesi ile aşamalı bir açıklama kullanmaktır. Örneğin, kısa bir açıklama/çözüm verin ve daha sonra Ayrıntılar düğmesi altına daha fazla ayrıntı koyun. Kullanıcılar hata hakkında daha fazla bilgi okumayı tercih ediyorsanız, bunu yapabilir.

 İletideki dil şu şekilde olmalıdır:

- **Etki alanı uygun.** Kullanıcının anlayabilmesi için dil kullanın. Müşterilerimiz geliştiriciler olsa da, sahip olduğumuz bağlam ve terminoloji genellikle bu değildir.

- **Belirli.** VAG ifadesi kullanmaktan kaçının ve ilgili nesnelerin belirli adlarını ve konumlarını verin. Örneğin, "karakter geçersiz" gibi bir hata iletisi kullanışlı değildir. Hangi karakter? "Dosya bulunamadı." Hangi dosya?

- **Nazik.** Kullanıcıya suç atmayın veya kendini kötü hissetmelerini smayın. Saldırgan veya rahatsız edici dillerden kaçının (sonlandırma, yürütme, sonlandırma, önemli, geçersiz). Büyük harfli metinlerden kaçının. Bu metin genellikle çok büyük olarak görülür ve okunabilir değildir. Tirnak kullanma.

- **Doğru.** Doğru yazım ve dil bilgisi (alfalarda bile) kullanın. Yazım hataları, profesyonel olmayan ve rahatsız edicidir.

- **Bağlamsal olarak uygun.** Uygun düğme metnini kullanın. "Tamam" düğmesini kaçının ve bunun yerine "Devam" veya "Evet/Hayır" kullanın.

### <a name="error-message-examples"></a>Hata iletisi örnekleri

|İyi|Kötü|
|----------|---------|
|"Çeviren numara artık hizmette değil. Lütfen numarayı kontrol edin ve tekrar çevirin veya işleci için 0'a tıklayın."|- "Hata (449): Geçersiz sayı"<br />- "Bu iş alınemeyen özel durum hatası, işlem başarıyla tamamlanır."<br /><br /> ![Hata iletisinde hatalı Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Yardıma Erişme

### <a name="overview"></a>Genel Bakış
 MSDN'de belgelere ek olarak, Visual Studio kullanıcı arabirimindeyken kullanıcıya yardımcı olmak için birkaç erişim noktası vardır. Bu erişim noktalarının tutarlı bir şekilde kullanılabilir olduğundan emin olmak için özellik ekiplerinin ortam tarafından sunulan Yardım sisteminden yararlanması gerekir. Bu erişim noktaları:

- **İletişim kutularında yönerge ve ek metin.** Kullanıcı arabirimi yüzeyinde yön veya açıklama veren ya da üzerine gelindiğinde InfoTip simgesinin üzerine gelindiğinde kullanılabilen statik metin.

- **F1 Yardımı** (yalnızca düzenleyici). Kullanıcı Visual Studio F1 tuşuna basılarak geçerli seçime özgü bir Yardım konusu getirebilirsiniz. F1 ile ilişkili konuların uygun ve bilgilendirici olduğundan emin olmak.

- **Yardım konularına köprüler.** Bir iletişim kutusu, araç penceresi veya tasarım yüzeyi içinde bulunan ve kullanıcıya teknoloji, özellik veya görevi gerçekleştirme hakkında daha fazla bilgi edindiren bir konu başlığı başlatan köprü.

- **Akıllı etiketler ve iletişim kutuları gibi yardımcı kullanıcı arabirimi mekanizmaları.** Bu mekanizmalar kullanıcıya kullanıcı arabirimi öğesini anlama veya akıllı etiketler veya oluşturucu iletişim kutuları gibi bir görevi kolaylaştırma konusunda yardımcı olur.

- **UI Yardım düğmeleri** (kullanım dışı). Başlık çubuğunda, ilgili F1 Yardım konu başlığına erişim veren görünür bir gösterge.

### <a name="text"></a>Metin

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>İletişim kutularında yönerge ve ek metin
 Karmaşık görevleri destekleyen iletişim kutularında, genellikle iletişim kutusunun en üstünde veya karmaşık denetimlere yakın olarak kullanıcı arabirimi içinde yönerge metni verme ihtiyacı olabilir. Yazma [stili hakkında ayrıntılı bilgi için bkz.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) Kullanıcı arabirimi metni ve terminolojisi.

#### <a name="infotips"></a>InfoTips
 Genellikle, kullanıcı arabiriminde yer alan yönerge metni çok uzun olabilir veya yalnızca yeni kullanıcılar için yararlı olabilir ve deneyimli kullanıcılar için dağınık gibi olabilir. Bu durumda, yönerge/bilgilendirme metni bir InfoTip'in altına araç ipucu olarak yerleştiril should.

 InfoTips, ilişkili olduğu denetimlerin yanına yerleştiril olmalı ve dikkatisiz ancak fark edilebilir olan belirli InfoTip simgesini kullan seçmelidir.

 ![Visual Studio'de InfoTip](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio'da InfoTip örneği**

### <a name="interactive-help-mechanisms"></a>Etkileşimli Yardım mekanizmaları

#### <a name="f1-help"></a>F1 Yardımı
 F1 Yardım bir düzenleyici veya tasarım yüzeyi içinde gereklidir, ancak ortam ortamının başka Visual Studio gerekmez.

#### <a name="hyperlinks-to-help-topics"></a>Yardım konularına köprüler
 Köprüler bir eylem gerçekleştirmek, IDE içinde gezinmek veya tarayıcıda Yardım başlatmak için kullanılabilir. Dil ve 07.10.01 Düğmeleri ve görsel ve düzen yönergeleri için köprüler hakkında ayrıntılı bilgi için bkz. Kullanıcı arabirimi metni ve [terminolojisi.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>İletişim kutusu başlık çubuklarında Yardım [?] düğmeleri (kullanım dışı)
 Çoğu bölümde, iletişim kutularının başlık çubuğundaki Yardım [?] düğmeleri kullanım dışıdır. Kullanıcı arabirimi konuları artık belge modelimizin bir parçası değildir ve bu nedenle bağlantı verilecek ilgili bir konu yoktur. Temelde, başlık çubuğu düğmesi F1 Yardımı ile aynı şeydir ve bu artık iletişim kutusunda gerekli değildir. Bazı durumlarda, köprüler daha yeni kullanıcı arabiriminde daha yaygın olarak kullanılmaktadır ancak bu, daha fazla kavramsal veya yordamsal bilgi olduğunu göstergesi olarak kullanılabilir.

##### <a name="dialogs-created-through-the-environment"></a>Ortam aracılığıyla oluşturulan iletişim kutuları
 Birçok kabuk iletişim kutusu **VBDialogBoxParam işlevi aracılığıyla** oluşturulur. Bu paylaşılan işlev, yardım düğmesini iletişim **kutusundan** **?** düğmesiyle çalışırken geriye dönük uyumlu ve genişletilebilir bir mimariyi korur.

 **Özellikle, VBDialogBoxParam** işlevi **IDHELP** (9) veya etiketi Yardım veya Yardım  olan bir düğmenin **iletişim&bakıyor.** Bir Yardım düğmesi bulunursa gizlidir ve **WS_EX_CONTEXTHELP** stili iletişim kutusuna eklenir.  düğmesini seçin.

 İletişim kutusu oluşturulduğunda, iletişim kutusu işlemini bir yığına iletir ve **DialogPreProc** adlı bir ön işleme iletişim kutusu temini ile iletişim kutusunu çağırır. Ne **zaman?** düğmesine tıklar, iletişim kutusuna **WM_SYSCOMMAND** **SC_CONTEXTHELP** bir dosya gönderir. **DialogPreProc bu** komutu yakalar ve özgün **iletişim WM_HELP** iletisinde ileti olarak değiştirir.

 Ortam tarafından oluşturulan iletişim kutularının çoğunda iletişim kutusunda Bir Yardım düğmesi vardır. İletişim kutusu görüntülendiğinde Yardım düğmesi otomatik olarak gizlenir ve yalnızca **?** düğmesi çalışır. ?  düğmesi kaldırıldığında veya Windows, bu çözüm hızlı bir şekilde özgün Yardım düğmelerine geri dönmene olanak sağlar.

 Bu çözüm, hatalara neden olacak dört varsayımda bulunarak:

- İletişim kutusunun yardım düğmesi **IDHELP** (9) düğmesidir.

- Yardım düğmesi gizli olduğunda iletişim kutusu doğru görünür.

- İletişim kutusu winproc öğesinin yerini alamaz.

- İletişim kutusu başka bir iletişim kutusunun içine ekli değildir.

  İletişim kutusu msenv içinde yer alıyorsa ve **VBDialogBoxParam** kullanmayacaksa, kendi işleyicinizi uygulamadan **önce VBDialogBoxParam'dan** yararlanarak araştırma gerçekleştirin.

##### <a name="dialogs-created-through-other-packages"></a>Diğer paketler aracılığıyla oluşturulan iletişim kutuları
 msenv dışında bulunan iletişim kutuları için kendi çözümlerinizi uygulayabilirsiniz. VSPackage dosyanıza paylaşılan bir iletişim kutusu sınıfı için düğmeyi başlık çubuğuna taşımayı veya her iletişim kutusunda bir işleyici uygulamayı göz önünde bulundurabilirsiniz. Aşağıdaki kod, başlamanıza yardımcı olacak bir uygulamanın iskeletidir:

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

##### <a name="help-buttons-in-managed-code"></a>Yönetilen kodda yardım düğmeleri
 Yönetilen kodda pencere başlık çubuğunun Yardım düğmesinin varsayılan davranışını geçersiz kılma kolaydır. Aşağıda bu davranışı gösteren eksiksiz bir tanıtım uygulaması verilmiştir. Özünde, formun **WndProc** yöntemini geçersiz kılmanız ve ardından bir hata  iletisi kes SC_CONTEXTHELP F1 yardım isteklerini kapatmanız gerekir.

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
