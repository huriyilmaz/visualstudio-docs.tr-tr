---
title: Visual Studio için Kullanıcı arabirimi metni ve yardımı | Microsoft Docs
description: Visual Studio için yardım bilgilerinde kullanılan Kullanıcı arabirimi metni ve terminoloji hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8635907b5c0190165855378fa692fb9abca4b0ec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052664"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Visual Studio İçin UI Metni ve Yardımı
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> UI metni ve terminolojisi
 Uygun olmayan metin, etkili Kullanıcı arabirimi için önemlidir. Yazılım kullanıcıları ilk olarak etiketleri okumaya eğilimlidir. Bu, en alakalı olan görevi tamamladıktan sonra. Statik metin daha az sıklıkta okundu. Kullanıcıların tüm pencerede hızlı bir şekilde taranması ve ardından Kullanıcı arabirimini bu yaklaşık sırada okumak için iş oturumlarını başlatmasını planlayın:

1. Merkezden etkileşimli denetimler

2. Kayıt düğmeleri

3. Etkileşimli denetimler başka bir yerde bulundu

4. Ana yönergeler

5. Ek açıklamalar

6. Pencere başlığı

7. Ana gövdedeki diğer statik metin

### <a name="usage-patterns-for-ui-text"></a>UI metni için kullanım desenleri

#### <a name="title-bar-text"></a>Başlık çubuğu metni
 Başlık çubuğu metninin Kullanıcı arabirimini oluşturan komutla eşleşmesi gerekir.

#### <a name="instructional-text-helper-text"></a>Yönerge metni (yardımcı metin)
 Bazı iletişim kutularında, pencerede veya sayfada ne yapılacağını açıklamak için belirgin ana yönergeler sağlamak yararlı olur. Bu bazen "yardımcı metin" olarak adlandırılır.

##### <a name="writing-style-rules-for-helper-text"></a>Yardımcı metin için stil kuralları yazma

- Belirgin bir şekilde açıklanmayın. Kesinlikle gerekmiyorsa, eğitici metin eklemeyin.

- Yönerge metni her zaman iletişim kutusunun üstüne yerleştirilir ve gerçekleştirilen göreve başvurmalıdır.

- Kullanıcılara yapması gerekenleri kesin olarak açıklayın. Aşırı iletişim ve artıklık kullanmaktan kaçının.

- Her pencereyi gözden geçirin ve yinelenen sözcükleri ve deyimleri kaldırın.

- Eğitici metin kısa tutun. Belirli kullanıcılar veya senaryolar için daha fazla bilgi gerekiyorsa, ayrıntılı bir kavramsal çevrimiçi konuya bir bağlantı sağlayın.

- Her sözcüğün ağırlığı ve gerekli olmasını sağlamak için metninizi yazın.

- [Kullanıcı arabirimi metni](/windows/desktop/uxguide/text-ui) ve [stili ve tonu](/windows/desktop/uxguide/text-style-tone)için mevcut Microsoft kılavuzunu izleyin.

#### <a name="supplemental-instructions"></a>Ek yönergeler
 Ek yönergeler, kullanıcının denetimleri veya denetim gruplamalarını anlamasına yardımcı olan ek bilgiler sağlar. Bu, giriş denetiminin hangi biçimin beklenmekte olduğunu anlamak için gereken ipucu metnini de içerebilir. Ek yönergeleri gelişigüzel bir şekilde kullanın. Kullanıcının yaptıkları seçimin kollarını tam olarak anlayamayabileceği durumlar için onları ayırın.

 ![Seçenek ayarlarının değiştirilmesinin etkisini açıklayan, aşağıdaki ek metinle Internet Explorer Seçenekler düğmesini gösteren ekran görüntüsü.](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Visual Studio 'da ek metin**

 ![Kaynak denetim sistemi seçeneklerinin her birini açıklayan ek metni gösteren Visual Studio 'da kaynak denetimi seçme iletişim kutusunun ekran görüntüsü.](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Visual Studio 'da ek metin**

#### <a name="infotips"></a>Bilgi Ipuçları
 Genellikle, yönerge metni Kullanıcı arabiriminde yerinde konumlandırılamayacak kadar uzun olabilir veya yalnızca yeni kullanıcılar için yararlı olabilir ve bu da deneyimli kullanıcılar için dağınıklığı gibi çok daha kullanışlı olabilir. Bu durumda, yönerge/bilgilendirici metnin bir bilgi Ipucu altına bir araç ipucu olarak yerleştirilmesi gerekir.

 InfoTips, ilişkili oldukları denetimlerin yanına yerleştirilmelidir ve kesin bir şekilde fark edilebilir olan belirli bilgi Ipucu simgesini kullanmalıdır.

 ![Visual Studio 'da InfoTip Ipucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio 'da bilgi Ipucu örneği**

##### <a name="writing-style-rules-for-infotips"></a>InfoTips için stil kuralları yazma

- Bilgi Ipuçlarını tüm cümleler olarak yazın. Belirli fiiller, tümce ve bitiş noktalamaları gerekir.

- Ana yönergeyi veya bilgilerinizi tamamlamak için InfoTips kullanın. Ana fikri yeniden kullanmak için yalnızca farklı sözcükler kullanıyorsanız, bilgi Ipucu gerekmez.

- Bilgi Ipuçlarını kısa ve swekoruyun. Kullanıcıyı destekleyen ve etkileyen, küçük sözcükler ve düz, günlük dil kullanın.

- [Kullanıcı arabirimi metni](/windows/desktop/uxguide/text-ui) ve [stili ve tonu](/windows/desktop/uxguide/text-style-tone)için mevcut Microsoft kılavuzunu izleyin.

#### <a name="control-labels"></a>Denetim etiketleri
 Denetim etiketleri kısa, kısa olmalı ve [denetimler Için Windows Masaüstü Kılavuzu](/windows/desktop/uxguide/controls)' nu izlemelidir.

 Kullanıcı arabiriminde Denetim etiketi biçimi ve yerleştirme hakkında daha fazla bilgi için, [Visual Studio 'Nun düzenine](../../extensibility/ux-guidelines/layout-for-visual-studio.md)bakın.

#### <a name="help-links"></a>Yardım bağlantıları
 Yardım bağlantıları, eğitici metin içine veya Kullanıcı arabiriminin gövdesine yerleştirilebilir. Bunlara yardım veya iç iletişim kutularını başlatma bağlantıları bulunabilir.

##### <a name="visual-style-rules-for-help-links"></a>Yardım bağlantıları için görsel stil kuralları

- Köprüler için doğru ortam renklerini kullanın. Doğru stillendirilmiş bir köprü tıklandığında kısa bir süre sonra kırmızı yanıp sönmez. Bunu görürseniz, ortam renklerinin kullanılmadığını gösteren bir göstergesidir.

- Alt çizgiler yalnızca, üzerine gelindiğinde veya bağlantı bir paragrafa katıştırıldığında kullanılmalıdır.

- Köprüler için görsel ve etkileşim stilleri hakkında daha ayrıntılı bilgi için bkz. düğmeler ve köprüler.

##### <a name="writing-style-rules-for-help-links"></a>Yardım bağlantıları için stil kuralları yazma

- İletişim kutuları başlatırken, üç nokta için standartları koruyun: gezinme için üç nokta yok, görev ek kullanıcı arabirimi gerektiriyorsa üç nokta.

     ![Visual Studio 'da yardım bağlantısı](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Yardım bağlantısındaki üç nokta (...), görevin ek kullanıcı arabirimi gerektirdiğini gösterir.**

- Bağlantılar, kullanıcının amacı olmadığı için "öğreneni" ile başlamamalıdır. Kullanıcı, genel bir eğitim almamanız için belirli bir soruyu yanıtlamak istiyor.

- Tümcecik, konunun yanıt verecek soruyu sormasını sağlamak için Yardım bağlantılarına yardımcı olur.

     Yanlış: "Windows Azure Mobile Services fiyatlandırması hakkında daha fazla bilgi edinin"

     Doğru: "Windows Azure Mobile Services için hangi fiyatlandırma seçenekleri mevcuttur?"

- Bağlantı metninde hiçbir şekilde *tıklama... seçeneğini* kullanmayın.

- "Burada" sözcüğünü hiçbir şekilde bağlamayın. Bu, bazı ekran okuyucular için sorunlu olan ve yalnızca köprü uygulanmış kelimeyi seslendirilecektir.

     Yanlış **: "Windows** Azure hakkında bilgi edinin Mobile Services

     Doğru: "Windows Azure Mobile Services için hangi fiyatlandırma seçenekleri mevcuttur?"

- Yardım bağlantıları için doğru yazma stili hakkında daha fazla bilgi için bkz. [Yardım Için Windows Masaüstü Kılavuzu](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>İpucu metni
 İpucu metni bir denetim içinde veya denetimin altında bir filigran olarak görüntülenir. Doğru biçimlendirme uygun VSColors belirteci kullanılarak uygulanır `Environment.GrayText` .

 Bu, bir dizi formda görünebilir.

- Denetim etiketinin yerine:

     !["Arama Çözüm Gezgini (Ctrl +;)" okuyan denetim etiketinin yerine ipucu metniyle birlikte açılan bir denetimin ekran görüntüsü.](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Bir fiil ile yönergeler vererek:

     !["Adınızı gir" i okuyan denetimdeki ipucu metniyle bir metin kutusunun ekran görüntüsü.](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Gerekli bir girişi belirten metinle:

     ![Denetimde "gerekli" okuyan ipucu metni içeren bir metin kutusunun ekran görüntüsü \< \> .](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Filigran metni
 Boş bir tasarım yüzeyinde metin, ne yapılacağını göstermelidir ve uygunsa diğer ilgili pencereleri açmak için bağlantılar sağlar:

 ![Visual Studio 'da filigran metni](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Visual Studio 'da filigran metni örneği**

### <a name="common-terminology"></a>Ortak terminoloji

|Süre|Açıklama|Yorum|
|----------|-----------------|-------------|
|Oturum Aç/Oturumu Kapat|Fiiller, bir Web özelliğinde kimlik doğrulamayı temsil etmek için Web ile terimler kullandı. İstemciler içinde, bu, diğer tüm bağlantılarda bulunmayan dolaşım ve lisanslama gibi daha yüksek düzey yetenekler sağlayan üst düzey bir kimliği temsil eden, IDE Kullanıcı bağlantısı açmak ve kapatmak için en üst düzey bir kavram olarak bir kez kullanılır.|IDE kullanıcısı, en üst düzey IDE kullanıcısını temsil ettiğinden, oturum açma/kapatma fiilini temsil eden tek özelliktir.|
|Bağlan/Bağlantıyı kes|Bir özelliğin çevrimiçi bir hizmetle tek bir bağlantı tuttuğu yerlerde kullanın.|Sunucu Gezgini, tek seferde yalnızca bir etkin Azure bağlantınız olabilir, Connect/Disconnect örneğidir.|
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

 Visual Studio kullanıcıları, derleme hatalarını çözmede çok sayıda geliştirme saati harcayabilir. Bu çözüm süresi, hatalar bağımlılıklar olduğunda veya hata iletileri hatalı yazıldığında artar ve bu da hatanın kaynağını açığa çıkarmak güç çıkarabilir.

 En iyi derleme hataları, Visual Studio 'Nun otomatik tamamlama ve IntelliSense dalgalı çizgiler sağladığı ilk yerde gerçekleşmeyecek olanlardır. Şema Doğrulayıcıları ve benzer araçlar aynı türde geri bildirim sağlar. Bu mekanizmalar, kullanıcıya düzgün biçimlendirilmiş kod oluşturmayı ve derleme hatası olasılığını azaltır.

 Visual Studio, kullanıcıların belge pencereleri içinde oluşan hataları okuyabilecekleri ve bunlara gidebileceği bir araç penceresi sağlar. Klavye kısayolları, kullanıcının büyük miktarlarda koda hızla gidebilmesi ve doğrudan sorunun konumuna gidebilmesi için sağlanır. Visual Studio Ayrıca, kullanıcının hata hakkında daha ayrıntılı bilgi veren bir yardım konusuna gidebilmesi için her derleme hatasının belirli bir Yardım anahtar sözcüğüne/bağlam KIMLIğINE bağlı olmasına izin verir.

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

- **Belirli.** VAG ifadesi kullanmaktan kaçının ve ilgili nesnelerin belirli adlarını ve konumlarını verin. Örneğin, "karakter geçersiz" gibi bir hata mesajı yararlı değildir. Hangi karakter? "Dosya bulunamadı". Hangi dosya?

- **Korkusuz.** Kullanıcı yapmayın veya onları STUPID hissetmeyin. Saldırgan veya kötü amaçlı dil kullanmaktan kaçının (KILL, Execute, Terminate, önemli, geçersiz). Genellikle, görünen ve okunabilir olmayan büyük harfli metinden kaçının. Humor kullanmayın.

- **Doğru.** Doğru yazım ve dilbilgisi (Alpin içinde bile) kullanın. Yazım hataları, profesyonel olmayan ve embaranet.

- **Bağlamsal olarak uygun.** Uygun düğme metnini kullanın. "Tamam" düğmesini kullanmaktan kaçının ve bunun yerine "Continue" veya "Yes/No" kullanın.

### <a name="error-message-examples"></a>Hata iletisi örnekleri

|İyi|Kötü|
|----------|---------|
|"Çevirdiğiniz sayı artık hizmette değil. Lütfen numarayı denetleyin ve operatör için bir kez daha çevirin veya 0 çevirin. "|-"Hata (449): Geçersiz sayı"<br />-"İşlenmemiş özel durum hatası işlemin başarıyla tamamlandığını gösteriyor."<br /><br /> ![Visual Studio 'da hatalı hata iletisi](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Yardım 'A erişme

### <a name="overview"></a>Genel Bakış
 MSDN 'deki belgelere ek olarak, bir Visual Studio kullanıcısının Kullanıcı ARABIRIMINDEN çalışırken yardım almak için çeşitli erişim noktalarına sahip olması gerekir. Bu erişim noktalarının sürekli olarak kullanılabilir olduğundan emin olmak için, özellik ekiplerinin ortam tarafından sunulan yardım sisteminden faydalanması gerekir. Bu erişim noktaları şunlardır:

- **İletişim kutularında yönerge ve ek metin.** UI yüzeyinde veya bir bilgi Ipucu simgesinin üzerine gelindiğinde, yön veya açıklama sağlayan statik metin.

- **F1 yardımı** (yalnızca Düzenleyici). Visual Studio Düzenleyicisi 'nde, bir Kullanıcı herhangi bir zamanda bu şekilde güvenebileceği gibi, F1 tuşuna basıldığında geçerli seçime özgü bir yardım konusu sunulacaktır. F1 ile ilişkili konuların uygun ve bilgilendirici olduğundan emin olun.

- **Yardım konularına yönelik köprüler.** Bir iletişim kutusu, araç penceresi veya tasarım yüzeyi içindeki bir köprü, kullanıcının bir teknoloji, yetenek veya bir görevi nasıl gerçekleştireceğinizi hakkında daha fazla bilgi edinmeye yardımcı olacak bir konu başlatır.

- **Akıllı Etiketler ve yapı iletişimleri gibi yardımcı UI mekanizmaları.** Bu mekanizmalar, kullanıcının bir kullanıcı ARABIRIMI öğesini anlamasına veya akıllı etiketler ya da Oluşturucu iletişim kutuları gibi bir görevi kolaylaştırmasına yardımcı olur.

- **UI yardım düğmeleri** (kullanım dışı). Başlık çubuğunda ilgili F1 Yardım konusuna erişim sağlayan görünür bir gösterge.

### <a name="text"></a>Metin

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>İletişim kutularında yönerge ve ek metin
 Karmaşık görevleri destekleyen iletişim kutularında, genellikle iletişim kutusunun üstünde ya da karmaşık denetimlerin yakınında, Kullanıcı arabirimi içinde açıklayıcı metin verme gereksinimi olabilir. Stil yazma hakkında daha fazla bilgi için bkz. [Kullanıcı arabirimi metni ve terminolojisi](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="infotips"></a>Bilgi Ipuçları
 Genellikle, eğitici metin Kullanıcı arabiriminde yerinde konumlandırılamayacak kadar uzun olabilir veya yalnızca yeni kullanıcılar için yararlı olabilir. Bu durumda, yönerge/bilgilendirici metnin bir bilgi Ipucu altına bir araç ipucu olarak yerleştirilmesi gerekir.

 InfoTips, ilişkili oldukları denetimlerin yanına yerleştirilmelidir ve kesin bir şekilde fark edilebilir olan belirli bilgi Ipucu simgesini kullanmalıdır.

 ![Visual Studio 'da InfoTip Ipucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio 'da bilgi Ipucu örneği**

### <a name="interactive-help-mechanisms"></a>Etkileşimli yardım mekanizmaları

#### <a name="f1-help"></a>F1 Yardımı
 Visual Studio ortamında başka bir yerde değil, bir düzenleyici veya tasarım yüzeyi içinde F1 yardımı gereklidir.

#### <a name="hyperlinks-to-help-topics"></a>Yardım konularına yönelik köprüler
 Köprüler bir eylem gerçekleştirmek, IDE içinde gezinmek veya yardımı bir tarayıcıda başlatmak için kullanılabilir. Görsel ve düzen yönergeleri için dil ve 07.10.01 düğmeleri ve köprüleriyle ilgili ayrıntılar için bkz. [Kullanıcı arabirimi metni ve terimleri](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>İletişim kutusu başlık çubuklarındaki yardım [?] düğmeleri (kullanım dışı)
 Çoğu bölüm için, iletişim kutularının başlık çubuğundaki Help [?] düğmeleri kullanım dışıdır. Kullanıcı arabirimi konuları artık belge modelimizin bir parçası değildir ve bu nedenle bağlantı için ilgili bir konu bulunmayabilir. Temelde, başlık çubuğu düğmesi F1 yardımı ile aynı şeydir ve iletişim kutularında artık gerekli değildir. Bazı örneklerde bu, daha fazla kavramsal veya yordamsal bilgiler olduğunu gösteren bir gösterge olarak kullanılabilir, ancak köprüler daha yaygın olarak daha fazla Kullanıcı arabiriminde kullanılıyor olabilir.

##### <a name="dialogs-created-through-the-environment"></a>Ortam üzerinden oluşturulan iletişim kutuları
 Birçok kabuk iletişim kutusu, **Vbdialogboxparam** işlevi aracılığıyla oluşturulur. Bu paylaşılan işlev **Yardım** düğmesini iletişim kutusu 'ndan öğesine taşımaya yardımcı olacak şekilde **güncelleştirildi.** düğmesini basılı tutarak, geriye dönük olarak uyumlu ve genişletilebilir bir mimari tutarken.

 Özellikle, **Vbdialogboxparam** IşLEVI, kimliği **IDHELP** (9) veya etiket **Yardım** veya **&yardım** olan bir düğmenin iletişim şablonuna bakar. Bir Yardım düğmesi bulunursa, gizlenir ve **ws_ex_contexthelp** stili iletişim kutusuna eklenir ve **Bu, öğesini yerleştiriyor.** düğmesine basın.

 İletişim kutusu oluşturulduğunda iletişim kutusu proc öğesini bir yığına gönderir ve iletişim kutusunu, **Iletişimpreproc** adlı bir işlem öncesi iletişim kutusu proc ile çağırır. Ne zaman **?** düğmesine tıklandığında, iletişim kutusuna **SC_CONTEXTHELP** **WM_SYSCOMMAND** gönderir. **Dialogpreproc** bu komutu yakalar ve özgün iletişim kutusu proc öğesine geçirilen bir **wm_help** iletisiyle değiştirir.

 Ortam tarafından oluşturulan birçok iletişim kutusu, iletişim kutusunda bir Yardım düğmesi vardır. İletişim kutusu görüntülendiğinde, Yardım düğmesi otomatik olarak gizlenir ve yalnızca **?** düğme işe yarar. **Mi?** düğme Windows 'ta kaldırılır veya değiştirildiğinde, bu çözüm özgün yardım düğmelerine hızlıca geri taşımanızı sağlar.

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
