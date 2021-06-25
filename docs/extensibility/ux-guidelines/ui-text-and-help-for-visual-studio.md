---
title: Visual Studio için Kullanıcı arabirimi metni ve yardımı | Microsoft Docs
description: Visual Studio için yardım bilgilerinde kullanılan Kullanıcı arabirimi metni ve terminoloji hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b128c5e95c70457d92843e620b4aa072c409ba
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899439"
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

- **Belirli.** VAG ifadesi kullanmaktan kaçının ve ilgili nesnelerin belirli adlarını ve konumlarını verin. Örneğin, "karakter geçersiz" gibi bir hata iletisi kullanışlı değildir. Hangi karakter? "Dosya bulunamadı." Hangi dosya?

- **Nazik.** Kullanıcıya suç atmayın veya kendini kötü hissetmelerini s anmayın. Saldırgan veya rahatsız edici dillerden kaçının (sonlandırma, yürütme, sonlandırma, önemli, geçersiz). Büyük harfli metinlerden kaçının; bu genellikle çok büyük olarak görülür ve o kadar okunabilir değildir. Tirnak kullanma.

- **Doğru.** Doğru yazım ve dil bilgisi (alfalarda bile) kullanın. Yazım hataları, profesyonel olmayan ve rahatsız edicidir.

- **Bağlamsal olarak uygun.** Uygun düğme metnini kullanın. "Tamam" düğmesini kaçının ve bunun yerine "Devam" veya "Evet/Hayır" kullanın.

### <a name="error-message-examples"></a>Hata iletisi örnekleri

|İyi|Kötü|
|----------|---------|
|"Çeviren numara artık hizmette değil. Lütfen numarayı kontrol edin ve tekrar çevirin veya işleci için 0'a tıklayın."|- "Hata (449): Geçersiz sayı"<br />- "Bu iş alınemeyen özel durum hatası, işlemi başarıyla tamamlamış olduğunu gösterir."<br /><br /> ![Hata iletisinde hatalı Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Yardıma Erişme

### <a name="overview"></a>Genel Bakış
 MSDN'de belgelere ek olarak, Visual Studio kullanıcı arabirimindeyken kullanıcıya yardımcı olmak için birkaç erişim noktası vardır. Bu erişim noktalarının tutarlı bir şekilde kullanılabilir olduğundan emin olmak için özellik ekiplerinin ortam tarafından sunulan Yardım sisteminden yararlanması gerekir. Bu erişim noktaları:

- **İletişim kutularında yönerge ve ek metin.** Kullanıcı arabirimi yüzeyinde yön veya açıklama veren ya da üzerine gelindiğinde InfoTip simgesinin üzerine gelindiğinde kullanılabilen statik metin.

- **F1 Yardımı** (yalnızca düzenleyici). Kullanıcı, Visual Studio F1 tuşuna basılarak geçerli seçime özgü bir Yardım konusu getirebilirsiniz. F1 ile ilişkili konuların uygun ve bilgilendirici olduğundan emin olmak.

- **Yardım konularına köprüler.** Bir iletişim kutusu, araç penceresi veya tasarım yüzeyi içinde bulunan ve kullanıcıya teknoloji, özellik veya görevi gerçekleştirme hakkında daha fazla bilgi edindiren bir konu başlığı başlatan köprü.

- **Akıllı etiketler ve iletişim kutuları gibi yardımcı kullanıcı arabirimi mekanizmaları.** Bu mekanizmalar kullanıcıya kullanıcı arabirimi öğesini anlama veya akıllı etiketler veya oluşturucu iletişim kutuları gibi bir görevi kolaylaştırma konusunda yardımcı olur.

- **Kullanıcı Arabirimi Yardım** düğmeleri (kullanım dışı). Başlık çubuğunda, ilgili F1 Yardım konu başlığına erişim veren görünür bir gösterge.

### <a name="text"></a>Metin

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>İletişim kutularında yönerge ve ek metin
 Karmaşık görevleri destekleyen iletişim kutularında, genellikle iletişim kutusunun en üstünde veya karmaşık denetimlere yakın olarak kullanıcı arabirimi içinde yönerge metni verme ihtiyacı olabilir. Stil [yazma hakkında ayrıntılı bilgi için kullanıcı arabirimi](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) metni ve terminolojisi'ne bakın.

#### <a name="infotips"></a>InfoTips
 Genellikle, yönerge metni kullanıcı arabiriminde yer alan konum için fazla uzun olabilir veya yalnızca yeni kullanıcılar için yararlı olabilir ve deneyimli kullanıcılar için dağınık gibi olabilir. Bu durumda, yönerge/bilgilendirme metni bir InfoTip'in altına araç ipucu olarak yerleştirilmli.

 InfoTips, ilişkili olduğu denetimlerin yanına yerleştiril olmalı ve dikkatisiz ancak fark edilebilir olan belirli InfoTip simgesini kullan seçmelidir.

 ![Visual Studio'de InfoTip](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio'de InfoTip örneği**

### <a name="interactive-help-mechanisms"></a>Etkileşimli Yardım mekanizmaları

#### <a name="f1-help"></a>F1 Yardımı
 F1 Yardım bir düzenleyici veya tasarım yüzeyi içinde gereklidir, ancak ortam ortamının başka Visual Studio gerekmez.

#### <a name="hyperlinks-to-help-topics"></a>Yardım konularına köprüler
 Köprüler bir eylem gerçekleştirmek, IDE içinde gezinmek veya tarayıcıda Yardım başlatmak için kullanılabilir. Dil ve 07.10.01 Düğmeleri ve görsel ve düzen yönergeleri için köprüler hakkında ayrıntılı bilgi için bkz. Kullanıcı arabirimi metni ve [terminolojisi.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>İletişim kutusu başlık çubuklarında Yardım [?] düğmeleri (kullanım dışı)
 Çoğu bölümde, iletişim kutularının başlık çubuğundaki Yardım [?] düğmeleri kullanım dışıdır. Kullanıcı arabirimi konuları artık belge modelimizin bir parçası değildir ve bu nedenle bağlantı verilecek ilgili bir konu olabilir. Temelde, başlık çubuğu düğmesi F1 Yardımı ile aynı şeydir ve bu artık iletişim kutusunda gerekli değildir. Bazı durumlarda, köprüler daha yeni kullanıcı arabiriminde daha yaygın olarak kullanılmaktadır ancak bu, daha fazla kavramsal veya yordamsal bilgi olduğunu göstergesi olarak kullanılabilir.

##### <a name="dialogs-created-through-the-environment"></a>Ortam aracılığıyla oluşturulan iletişim kutuları
 Birçok kabuk iletişim kutusu **VBDialogBoxParam işlevi aracılığıyla** oluşturulur. Bu paylaşılan işlev, yardım düğmesini iletişim **kutusundan** **?** düğmesiyle çalışırken geriye dönük uyumlu ve genişletilebilir bir mimariyi korur.

 **Özellikle, VBDialogBoxParam** işlevi **IDHELP** (9) veya etiketi Yardım veya Yardım  olan bir düğmenin iletişim **&bakıyor.** Bir Yardım düğmesi bulunursa gizlidir ve **WS_EX_CONTEXTHELP** stili iletişim kutusuna eklenir ve  bu da ? düğmesini seçin.

 İletişim kutusu oluşturulduğunda, iletişim kutusu işlemini bir yığına iletir ve **DialogPreProc** adlı bir ön işleme iletişim kutusu temini ile iletişim kutusunu çağırır. Ne **zaman?** düğmesine tıklar, iletişim kutusuna **WM_SYSCOMMAND** **SC_CONTEXTHELP** bir dosya gönderir. **DialogPreProc bu** komutu yakalar ve özgün **iletişim WM_HELP** ileti olarak değiştirir.

 Ortam tarafından oluşturulan iletişim kutularının çoğunda iletişim kutusunda Bir Yardım düğmesi vardır. İletişim kutusu görüntülendiğinde Yardım düğmesi otomatik olarak gizlenir ve yalnızca **?** düğmesi çalışır. ?  düğmesi Windows'da kaldırılır veya değiştirilirse, bu çözüm hızlı bir şekilde özgün Yardım düğmelerine geri dönmenize olanak sağlar.

 Bu çözüm, hatalara neden olacak dört varsayımda bulunarak:

- İletişim kutusunun yardım düğmesi **IDHELP** (9) düğmesidir.

- Yardım düğmesi gizli olduğunda iletişim kutusu doğru görünür.

- İletişim kutusu winproc öğesinin yerini alamaz.

- İletişim kutusu başka bir iletişim kutusunun içine ekli değildir.

  İletişim kutusu msenv içinde yer alıyorsa ve **VBDialogBoxParam** kullanmayacaksa, kendi işleyicinizi uygulamadan **önce VBDialogBoxParam'dan** yararlanarak araştırma gerçekleştirin.

##### <a name="dialogs-created-through-other-packages"></a>Diğer paketler aracılığıyla oluşturulan iletişim kutuları
 msenv dışında bulunan iletişim kutuları için kendi çözümlerinizi kullanabilirsiniz. VSPackage dosyanıza paylaşılan bir iletişim kutusu sınıfı için düğmeyi başlık çubuğuna taşımayı veya her iletişim kutusunda bir işleyici uygulamayı göz önünde bulundurabilirsiniz. Aşağıdaki kod, başlamanıza yardımcı olacak bir uygulamanın iskeletidir:

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
