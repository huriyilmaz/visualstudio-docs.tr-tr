---
title: Görsel Stüdyo için Kullanıcı Arabirimi Metin ve Yardım | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3247aeaa702b59722471c7d28e98957f04f3e07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698293"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Visual Studio İçin UI Metni ve Yardımı
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>UI metin ve terminoloji
 Anlaşılır metin etkili Kullanıcı Bira sı için çok önemlidir. Yazılım kullanıcıları önce etiketleri, yani eldeki görevi tamamlamakla en alakalı olanları okuma eğilimindedirler. Statik metin daha az sıklıkta okunur. Kullanıcıların çalışma oturumlarına tüm pencerenin hızlı bir tararmasını ve ardından kullanıcı aralarının bu yaklaşık sırada okunmasını planlayın:

1. Merkezdeki etkileşimli denetimler

2. Düğmeleri işleme

3. Başka bir yerde bulunan etkileşimli denetimler

4. Ana talimatlar

5. Ek açıklamalar

6. Pencere başlığı

7. Ana gövdedeki diğer statik metin

### <a name="usage-patterns-for-ui-text"></a>Kullanıcı Arabirimi metni için kullanım desenleri

#### <a name="title-bar-text"></a>Başlık çubuğu metni
 Başlık çubuğu metni, Kullanıcı Bira'yı oluşturan komutla eşleşmelidir.

#### <a name="instructional-text-helper-text"></a>Öğretim metni (yardımcı metin)
 Bazı iletişim kutularında, pencerede veya sayfada ne yapılacağını açıklamak için ünesi olan ana yürütümler sağlamak yararlılık taşır. Bu bazen "yardımcı metin" olarak adlandırılır.

##### <a name="writing-style-rules-for-helper-text"></a>Yardımcı metin için stil kuralları yazma

- Bariz olanı açıklama. Kesinlikle gerekli olmadıkça, öğretim metnini içermez.

- Öğretim metni her zaman iletişim kutusunun en üstüne yerleştirilir ve gerçekleştirilen göreve başvurulmalıdır.

- Kullanıcılara tam olarak ne yapmaları gerektiğini açıklayın. Aşırı iletişim ve artıklıktan kaçının.

- Her pencereyi gözden geçirin ve yinelenen sözcükleri ve deyimleri ortadan kaldırın.

- Öğretici metni kısa tutun. Belirli kullanıcılar veya senaryolar için daha fazla bilgi gerekiyorsa, ayrıntılı bir kavramsal çevrimiçi konuya bağlantı sağlayın.

- Her kelimenin ağırlığını ve gerekliliğini sağlayacak şekilde metninizi yazın.

- [Kullanıcı Arabirimi Metin](/windows/desktop/uxguide/text-ui) ve [Stil ve Ton](/windows/desktop/uxguide/text-style-tone)için varolan Microsoft kılavuzunu izleyin.

#### <a name="supplemental-instructions"></a>Ek talimatlar
 Ek yönergeler, kullanıcının denetimleri veya denetim gruplandırmalarını anlamasına yardımcı olan ek bilgiler sağlar. Bu, giriş denetiminin hangi biçimde beklediğini anlamak için gerekli ipucu metnini de içerebilir. Ek talimatları dikkatli kullanın. Kullanıcının yaptıkları seçimin sonuçlarını tam olarak anlayamayacağı durumlar için ayırın.

 ![Visual Studio'da ek metin](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Visual Studio'da ek metin**

 ![Visual Studio'da ek metin](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Visual Studio'da ek metin**

#### <a name="infotips"></a>Bilgi İpuçları
 Genellikle, öğretim metni Kullanıcı Bir Arada'nda yerinde konumlandırmak için çok uzun olabilir veya yalnızca yeni kullanıcılar için yararlı olabilir, deneyimli kullanıcılara dağınıklık hissi. Bu durumda, öğretim/bilgilendirme metni Bilgi İpucu altında araç ucu olarak yerleştirilmelidir.

 InfoTips, ilişkili oldukları denetimlerin yakınına yerleştirilmeli ve göze batan henüz fark edilebilen belirli InfoTip simgesini kullanmalıdır.

 ![Visual Studio'da Bilgi İpucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio'da Bilgi İpucu Örneği**

##### <a name="writing-style-rules-for-infotips"></a>InfoTips için stil kuralları yazma

- InfoTips'i tam cümleler olarak yazın. Belirli fiiller, tümce durumu ve noktalama işaretleri nin bitmesi gerekir.

- Ana talimatınızı veya bilgilerinizi tamamlamak için InfoTips'i kullanın. Ana fikri yeniden ifade etmek için farklı sözcükler kullanıyorsanız, Bilgi İpucu'na ihtiyacınız yoktur.

- InfoTips kısa ve tatlı tutun. Kullanıcıyı destekleyen ve teşvik eden küçük kelimeler ve sade, günlük dil kullanın.

- [Kullanıcı Arabirimi Metin](/windows/desktop/uxguide/text-ui) ve [Stil ve Ton](/windows/desktop/uxguide/text-style-tone)için varolan Microsoft kılavuzunu izleyin.

#### <a name="control-labels"></a>Kontrol etiketleri
 Denetim etiketleri kısa, kısa olmalı ve [Denetimler için Windows Masaüstü kılavuzunu](/windows/desktop/uxguide/controls)izlemeli.

 Kullanıcı arabirimi içindeki denetim etiketi biçimi ve yerleşimi hakkında daha fazla bilgi için [Visual Studio için Düzen'e](../../extensibility/ux-guidelines/layout-for-visual-studio.md)bakın.

#### <a name="help-links"></a>Yardım bağlantıları
 Yardım bağlantıları, öğretim metniiçinde veya Kullanıcı Arabirimi'nin gövdesine yerleştirilebilir. Bunlar Yardım'a bağlantılar olabilir veya dahili iletişim kurabilir.

##### <a name="visual-style-rules-for-help-links"></a>Yardım bağlantıları için görsel stil kuralları

- Köprüler için doğru ortam renklerini kullanın. Düzgün bir şekilde şekillendirilmiş bir köprü tıklatıldığında kısa bir süre kırmızı yanıp sönmez. Bunu görürseniz, ortam renklerinin kullanılmadığının bir göstergesidir.

- Altı çizili altı çizili her yerde veya bağlantı bir paragrafa katıştırıldığında kullanılmalıdır.

- Köprüler için görsel ve etkileşim stilleri hakkında daha ayrıntılı bilgi için Düğmeler ve köprülere bakın.

##### <a name="writing-style-rules-for-help-links"></a>Yardım bağlantıları için stil kuralları yazma

- İletişim kurarak, elipsler için standartları koruyun: gezinme için elips yok, görev ek ui gerektiriyorsa elipsler.

     ![Visual Studio'da Yardım bağlantısı](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Yardım bağlantısındaki bir elips (...) görevin ek web-posta aracı gerektireceğini gösterir.**

- Bağlantılar kullanıcının amacı olmadığı için "Öğren" ile başlamamalıdır. Kullanıcı belirli bir soruyu yanıtlamak, genel bir eğitim almak değil istiyor.

- Sorunun yanıtlayacakları soruyu sorabilmeleri için yardım bağlantılarını ifade edin.

     Yanlış: "Windows Azure Mobil Hizmetler fiyatlandırması hakkında daha fazla bilgi edinin"

     Doğru: "Windows Azure Mobil Hizmetleri için hangi fiyatlandırma seçenekleri kullanılabilir?"

- Bağlantı metnine *Click...* seçeneğini asla kullanmayın.

- Asla sadece "burada" kelimesini bağlamayın. Bu, yalnızca köprübağlantılı sözcüğü seslendirecek bazı ekran okuyucular için sorunludur.

     Yanlış: "Windows Azure Mobil Hizmetleri hakkında bilgi **bulabilirsiniz "**

     Doğru: "Windows Azure Mobil Hizmetleri için hangi fiyatlandırma seçenekleri kullanılabilir?"

- Yardım bağlantıları için doğru yazma stili hakkında daha fazla bilgi için [Yardım için Windows Masaüstü kılavuzuna](/windows/desktop/uxguide/winenv-help)bakın.

#### <a name="hint-text"></a>İpucu metni
 İpucu metin, denetim içinde veya denetimin altında filigran olarak görünür. Uygun VSColors belirteci kullanılarak doğru biçimlendirme `Environment.GrayText`uygulanacaktır.

 Çeşitli şekillerde görünebilir.

- Kontrol etiketi yerine:

     ![Visual Studio'da ipucu metni](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Bir fiille, talimatlar vererek:

     ![Visual Studio'da ipucu metni](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Gerekli girişi gösteren metinle:

     ![Visual Studio'da ipucu metni](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Filigran metni
 Boş bir tasarım yüzeyinde, metin ne yapacağını belirtmeli ve uygunsa diğer ilgili pencereleri açmak için bağlantılar sağlamalıdır:

 ![Visual Studio'da filigran metni](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Visual Studio filigran metin örneği**

### <a name="common-terminology"></a>Yaygın terminoloji

|Sözleşme Dönemi|Açıklama|Açıklama|
|----------|-----------------|-------------|
|Oturum Aç / Oturum Aç|Fiiller, kimlik doğrulamayı bir web özelliğinde temsil etmek için web ile eş anlamlı olarak kullanılır. İstemciler içinde, bunu, diğer tüm bağlantılarda bulunmayan dolaşım ve lisanslama gibi üst düzey özellikler sağlayan üst düzey bir kimliği temsil eden IDE kullanıcı bağlantısına oturum açma ve devre dışı oturum açma için üst düzey bir kavram olarak kullanırız.|IDE Kullanıcısı, üst düzey IDE kullanıcısını temsil ettiği için bir oturum açma / imzalama fiilini temsil etmesi gereken tek özelliktir.|
|Bağlan / Kes|Bir özelliğin çevrimiçi bir hizmete tek bir bağlantı nın bulunduğu yerlerde kullanın.|Aynı anda yalnızca bir etkin Azure bağlantınız olabileceği Sunucu Gezgini, Bağlan/Bağlantıyı Kesme'ye bir örnektir.|
|Ekle / Kaldır|Zarar vermeyen. Bir şeyi listeden eklerken veya kaldırırken kullanın.|TFS Connection Manager sunucu listesi iletişim kutusu Ekle/Kaldır'A bir örnektir.|
|Sil|Yıkıcı. Yalnızca kaldırılan öğe diskten kalıcı olarak atıldığında veya silindiğinde kullanın.|Sonuç bir dosyayı diskten siliyorsa, genellikle "Sil" bir istem gerektirir.|

## <a name="error-messages"></a>Hata iletileri

### <a name="overview"></a>Genel Bakış
 Hatalar olur. Kullanıcının yapabileceklerine ilişkin sınırlamalar ayarlamak, önlenebilir hata iletilerini önlemede mantıklı bir ilk adımdır. Ancak, bir hata oluştuğunda, iyi yazılmış bir hata iletisi sorunu azaltma yönünde uzun bir yol kat edebilir. Hata iletileri, eşzamanlı oldukları ve çözülmesi gereken bir sorunu gösterdiğinden, kullanıcının gördüğü en önemli bildirim türlerinden biridir. Kötü yazılmış hata iletileri, kullanıcıların hataların ve olası çözümlerin nedenini belirlemelerini sağlar.

 Kullanıcılar aşırı kullanılan veya kafa karıştırıcı hata iletilerine dikkat etmeyi bırakabilir, bu nedenle yalnızca kullanıcı deneyimine değer katan gerekli iletileri yazın. İleti yalnızca bir bildirimse, alternatif bir sunu kullanın.

### <a name="rules-for-creating-an-error-message"></a>Hata iletisi oluşturma kuralları

- Hata iletileri oluşturmakta, hedef kitle için uygun hata düzeyini seçin. Varsa, kullanıcının uygulayabileceği bir eylemi sağlayan basit özetleri hedefleyin. Kullanıcının bilmesi gerekmeyen hiçbir şeyi belirtmeyin.

- Yapıcı yardım sağlayın. Yönerge içeren bir hata iletisini okumak ve hareket etmek daha kolaydır.

- Çift negatif kullanmayın.

- Yazdığınız herhangi bir hata iletisi üzerinde hem otomatik hem de el ile dilbilgisi ve yazım denetimi gerçekleştirin.

- Karmaşık hata iletileri için sıralı iletişimlerden kaçının. Hata iletisi için asla F1 bağlantısı kullanmayın. İletinin kendisi yeterli olmalıdır.

- Doğru simgeyi kullanın.

- "Sil" ve "İptal Et" gibi net seçenekleri olan soruların anlaşılmasını ve kullanılmasını kolaylaştırın.

- Uyarılar için, işlemin sonucunun ne olacağı konusunda açık olun. Düğmeler sonucu göstermelidir.

- Hatalar için, kullanıcının sorunu gidermek için neler yapabileceğini açıklayın. Düğmeler eylem olmalı veya "Kapat" demelidir. Hata iletisi için "Tamam" düğmesi kullanmayın.

- Bir hata iletisi kurarken kendinize sormanız gereken bazı sorular:

  - Kullanıcı bu hatayla sorunu tek başına nasıl çözeceğini bulabilir mi?

  - Kullanıcı bu hatayla aynı kelime dağarcığı kullanıyor mu?

  - Bu hata ambigious veya birden çok durumda paylaşılan mı? Eğer öyleyse, kullanıcıları ihtiyaç duydukları çözüme nasıl yönlendirirsiniz?

#### <a name="build-errors"></a>Yapı hataları
 Visual Studio bir yazılım geliştirme aracı olduğundan, bileşenlerinin çoğu geliştiricinin çalışmasını ikili forma dönüştürmek için bir derleme, dönüştürme veya kodlama adımına sahiptir. Derleyici yanlış yazılmış dosyaları işleyemediğinde veya derleyici seçenekleri doğru ayarlanamadığında bu dönüşümler hatalara neden olabilir.

 Visual Studio kullanıcıları yapı hatalarını çözmek için çok sayıda geliştirme saati harcayabilirler. Bu çözümleme süresi, hatalar bağımlılıkları olduğunda veya hata iletileri kötü yazıldığında artar ve bu da hatanın kaynağını ortaya çıkarmakta zorlanabilir.

 En iyi yapı hataları ilk etapta meydana gelmez olanlar, Visual Studio AutoComplete ve IntelliSense squiggles sağlar neden olmasıdır. Şema doğrulayıcıları ve benzeri araçlar aynı tür geri bildirim sağlar. Bu mekanizmalar, kullanıcıyı iyi biçimlendirilmiş kod lar oluşturması için proaktif olarak yönlendirerek yapı hataları olasılığını azaltıyor.

 Visual Studio, kullanıcıların belge pencerelerinde oluşan hataları okuyup gezinebilecekleri bir araç penceresi sağlar. Klavye kısayolları, kullanıcının büyük miktarda kodda hızla gezinmesi ve doğrudan sorunun konumuna gideabilmesi için sağlanır. Visual Studio ayrıca, kullanıcının hata hakkında daha ayrıntılı bilgi veren bir Yardım konusuna doğrudan gidebilmeleri için her yapı hatasının belirli bir Yardım anahtar kelime/bağlam kimliğine bağlanmasını sağlar.

 Açık, kısa yapı hataları yazın:

- Çok az veya hiç derleyici jargon ile sorunu açıklayan **düz dil kullanın.** Yapı hatası metni aşırı teknik olmamalıdır.

- **Olası nedenleri anahat.** Örneğin, "'(özellik) : (değer)' bildirimindeki özellik ve değer arasında bir iki nokta üst üste eksik."

- Olası düzeltmeler hakkında ayrıntılı bilgi verin. Yeterli alan yoksa, ilgili Yardım konusuna ek ayrıntılar eklenebilir.

### <a name="components-of-a-well-written-error-message"></a>İyi yazılmış bir hata iletisinin bileşenleri

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Hata iletileri için kabuk iletişim hizmetini kullanın.
 Kabuk iletişim hizmetini kullanmak, tek tek öğelerde önemli değişiklikler olmadan iletinin görünümünü, özellikle de yazı tiplerini denetlemenize olanak tanır. **IErrorInfo** mekanizmalarını kullanın ve **IVsUIShell kullanarak bildirin::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Etkili ve uygun bir bildirim sunumu seçin.
 Veri kaybını önlemek için acil eylem gerekiyorsa, kritik bir uyarı içeren bir modal iletişim kutusu kullanın (senkron bildirim). Kritik simgeler, iletinin okumadan kapatılmasının olumsuz sonuçlara yol açabileceği durumlar için ayrılmıştır. Veri kaybı, alarm düzeyinde yanıt gerektiren kritik bir durumdur. Kritik simgenin aşırı kullanımı, kullanıcıları önemine karşı duyarsızlaştırıyor. Hata iletisi bilgi amaçlıysa, modal iletişim kutusuna (asynchronous bildirimi) alternatifleri göz önünde bulundurun.

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Sorunun teknik bir açıklama yerine neden oluştuğuna ilişkin temiz ve kısa bir açıklama sağlayın.
 Kullanıcılara açıklamadaki teknik ayrıntıları aşırı yüklemek, hata iletilerini yok sayma olasılığını artıracaktır. İyi mesajlaşma örnekleri:

- "İstenen dosya açılmıyor."

- "Internet'e bağlanamıyor."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Sorunun nasıl giderilen hakkında bilgi sağlayın.
 Sorunu nasıl çözeceğime ilgili kullanıcıönerileri sunun. Herhangi bir öneri niz varsa kullanıcıya karşı dürüst olun. Teknik destek veya topluluk desteği gibi alternatif çevrimiçi kaynaklara doğrudan bağlantılar sağlayın. Kullanıcıları sorunla ilgili belirli çevrimiçi bilgilere yönlendirmeye çalışın. Bir hata kimliği için, kullanıcıları bu belirli hatayla ilgili bir tartışma iş parçacığına bağlamayı düşünün. İyi mesajlaşma örnekleri:

- "Internet'e bağlı olduğundan emin olun ve bu işlemi yeniden deneyin."

- "Dosyanın var olduğundan ve dosyayı açma izniniz olduğundan emin olun."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Kısa ve noktaya kadar bir ileti yazın.
 Bir hata iletisi bir çözümü bildirebilir, açıklayabilir ve sunabilir, ancak çok sözcüklüyse yine de yoksayılabilir. Bir çözüm ayrıntılar düğmesi ile aşamalı açıklama kullanmaktır. Örneğin, kısa bir açıklama/çözüm verin ve ardından ayrıntılar düğmesinin altına daha fazla ayrıntı koyun. Kullanıcılar hata hakkında daha fazla bilgi okumayı seçerse, bunu yapabilirler.

 İletideki dil şöyle olmalıdır:

- **Etki alanına uygun.** Kullanıcının anlayacağı dili kullanın. Müşterilerimiz geliştiriciler olsa da, genellikle sahip olduğumuz bağlam ve terminolojiye sahip değildirler.

- **Belirli.** Belirsiz ifadelerden kaçının ve ilgili nesnelerin belirli adlarını ve konumlarını verin. Örneğin, "karakter geçersizdir" gibi bir hata iletisi yararlı değildir. Hangi karakter? "Dosya bulunamadı." Hangi dosya?

- **Nazik.** Kullanıcıyı suçlamayın ya da aptal hissetmelerini etmeyin. Düşmanca veya saldırgan dillerden kaçının (öldürmek, yürütmek, sonlandırmak, ölümcül, yasadışı). Genellikle bağırma olarak görülen ve okunabilen olmayan büyük harfli metinden kaçının. Mizah kullanma.

- **Doğru.** Doğru yazım ve dilbilgisi (alfalarda bile) kullanın. Yazım hataları profesyonellik dışı ve utanç verici.

- **Bağlamsal olarak uygun.** Uygun düğme metnini kullanın. "Tamam" düğmesinden kaçının ve bunun yerine "Continue" veya "Yes/No" düğmesini kullanın.

### <a name="error-message-examples"></a>Hata iletisi örnekleri

|İyi|Kötü|
|----------|---------|
|"Aradığınız numara artık kullanımda değil. Lütfen numarayı kontrol edin ve tekrar arayın veya operatör için 0'ı arayın."|- "Hata (449): Yasadışı numara"<br />- "Bu işlenmemiş özel durum hatası, işlemin başarıyla tamamlandığını gösterir."<br /><br /> ![Visual Studio'da hatalı hata iletisi](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Yardıma Erişim

### <a name="overview"></a>Genel Bakış
 MSDN'deki belgelere ek olarak, Visual Studio kullanıcısı kullanıcıya UI'de yken yardımcı olmak için çeşitli erişim noktalarına sahiptir. Bu erişim noktalarının sürekli olarak kullanılabildiğinden emin olmak için özellik ekiplerinin ortam tarafından sunulan Yardım sisteminden yararlanması gerekir. Bu erişim noktaları şunlardır:

- **Diyaloglarda öğretici ve tamamlayıcı metin.** Kullanıcı Arabirimi yüzeyinde veya bir InfoTip simgesinin üzerinde gezinmede bulunan yön veya açıklama veren statik metin.

- **F1 Yardım** (yalnızca düzenleyici). Visual Studio düzenleyicisi içinde, bir kullanıcı f1 tuşuna basarak geçerli seçime özgü bir Yardım konusunu gündeme getireceğine güvenebilir. F1 ile ilişkili konuların uygun ve bilgilendirici olduğundan emin olun.

- **Yardım konularına köprüler.** Bir iletişim kutusu, araç penceresi veya tasarım yüzeyi içindeki bir köprü, kullanıcıya bir görevi nasıl tamamlayacakları hakkında daha fazla bilgi edinmesinde yardımcı olmak için bir konu başlatır.

- **Akıllı etiketler ve oluşturma iletişim leri gibi Yardımcı UI mekanizmaları.** Bu mekanizmalar kullanıcıya kullanıcıya kullanıcının kullanıcıyı bir Kullanıcı Aracı öğesini anlamasında yardımcı olur veya akıllı etiketler veya oluşturucu iletişim kutuları gibi bir görevi kolaylaştırır.

- **UI Yardım düğmeleri** (amortismana uğradı). Başlık çubuğunda, ilgili F1 Yardım konusuna erişim sağlayan görünür bir gösterge.

### <a name="text"></a>Metin

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Diyaloglarda öğretici ve tamamlayıcı metin
 Karmaşık görevleri destekleyen iletişim kutularında, kullanıcı arabirimi içinde genellikle iletişim kutusunun üst kısmında veya karmaşık denetimlerin yakınında öğretim metni verilmesi gerekebilir. Yazma stili yle ilgili ayrıntılar için [Kullanıcı Arabirimi metni ve terminolojisi](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) için bkz.

#### <a name="infotips"></a>Bilgi İpuçları
 Genellikle, öğretim metni Kullanıcı BirA'da yerini yerleştirmek için çok uzun olabilir veya yalnızca yeni kullanıcılar için yararlı olabilir, deneyimli kullanıcılara yığılmayı hisseder. Bu durumda, öğretim/bilgilendirme metni Bilgi İpucu altında araç ucu olarak yerleştirilmelidir.

 InfoTips, ilişkili oldukları denetimlerin yakınına yerleştirilmeli ve göze batan henüz fark edilebilen belirli InfoTip simgesini kullanmalıdır.

 ![Visual Studio'da Bilgi İpucu](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Visual Studio'da Bilgi İpucu Örneği**

### <a name="interactive-help-mechanisms"></a>Etkileşimli Yardım mekanizmaları

#### <a name="f1-help"></a>F1 Yardımı
 F1 Yardım bir editör veya tasarım yüzeyi içinde gereklidir, ancak Visual Studio ortamında başka bir yerde değil.

#### <a name="hyperlinks-to-help-topics"></a>Yardım konularına köprüler
 Köprüler bir eylem gerçekleştirmek, IDE içinde gezinmek veya bir tarayıcıda Yardım başlatmak için kullanılabilir. Dil ve 07.10.01 Düğmeleri ve görsel ve düzen yönergeleri için köprüler hakkında ayrıntılı bilgi için Kullanıcı Arabirimi metni ve [terminolojisi](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) için bkz.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>İletişim kutusu çubuklarındaki Yardım [?] düğmeleri (amortismana uğradı)
 Çoğunlukla, iletişim lerin başlık çubuğundaki Yardım [?] düğmeleri küçümsenen. UI konuları artık doküman modelimizin bir parçası değildir ve bu nedenle bağlantı için ilgili bir konu olmayabilir. Esasen, başlık çubuğu düğmesi F1 Yardım ile aynı şey, ve artık diyaloglar gerekli değildir. Bazı durumlarda, köprüler daha yaygın olarak yeni kullanıcı arabirimi'nde kullanılmasına rağmen, bu hala daha fazla kavramsal veya yordamsal bilgi nin mevcut olduğunun bir göstergesi olarak kullanılabilir.

##### <a name="dialogs-created-through-the-environment"></a>Çevre üzerinden oluşturulan iletişim kutuları
 **VBDialogBoxParam** işlevi aracılığıyla birçok kabuk iletişim kutusu oluşturulur. Bu paylaşılan işlev, **Yardım** düğmesini iletişim kutusundan **?** geriye dönük uyumlu ve genişletilebilir bir mimari korurken düğmesini.

 Özellikle, **VBDialogBoxParam** işlevi, kimliği **IDHELP** (9) veya etiketi Yardım veya **&** **Yardım** olan bir düğmenin iletişim şablonuna bakar. Yardım düğmesi bulunursa, gizlenir ve iletişim kutusuna **WS_EX_CONTEXTHELP** stili eklenir, aşağıdakileri **yerleştirir?** iletişim kutusunun başlık çubuğundaki düğme.

 İletişim oluşturulduğunda, iletişim proc'unu bir yığın üzerine iter ve **dialogPreProc**adlı bir ön işlem iletişim proc'u ile iletişim kutusunu çağırır. Ne **zaman?** düğmesine tıklanırsa, **WM_SYSCOMMAND** iletişim kutusuna **WM_SYSCOMMAND SC_CONTEXTHELP** gönderir. **DialogPreProc** bu komutu yakalar ve özgün iletişim proc geçirilir **WM_HELP** bir ileti, değiştirir.

 Ortam tarafından oluşturulan iletişim kutularının çoğunda iletişim kutusunda Yardım düğmesi vardır. İletişim kutusu görüntülendiğinde, Yardım düğmesi otomatik olarak gizlenir ve **yalnızca?** düğmesi çalışır. Eğer? **?** düğmesi Windows'da hiç kaldırılır veya değiştirilirse, bu çözüm hızlı bir şekilde orijinal Yardım düğmelerine geri dönmenizi sağlar.

 Bu çözüm, hatalara neden olabilecek dört varsayım yapar:

- İletişim kutusunun yardım düğmesi **IDHELP** 'dir (9).

- Yardım düğmesi gizlendiğinde iletişim kutusu doğru görünür.

- İletişim, winproc'un yerini almaz.

- İletişim, başka bir iletişim kutusunun içine katıştırılmış değil.

  İletişiminiz msenv içinde bulunuyorsa ve **VBDialogBoxParam**kullanmıyorsa, kendi işleyicinizi uygulamadan önce **VBDialogBoxParam'dan** yararlanmayı araştırın.

##### <a name="dialogs-created-through-other-packages"></a>Diğer paketler aracılığıyla oluşturulan iletişim kutuları
 Msenv dışında ikamet eden iletişim için kendi çözümünüzü uygulayabilirsiniz. VSPackage'ınızdaki paylaşılan bir iletişim sınıfı için düğmeyi başlık çubuğuna taşımayı veya her iletişim kutusunda bir işleyici uygulamayı düşünün. Aşağıdaki kod, başlamanıza yardımcı olacak bir uygulamaiskeletidir:

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
 Pencere başlığı çubuğunu geçersiz kılmak Yardım düğmesinin varsayılan davranışını yönetilen kodda kolayca alır. Aşağıda bu davranışı gösteren tam bir demo uygulamasıdır. Özünde, formunuzun **WndProc** yöntemini geçersiz kılmanız ve **SC_CONTEXTHELP** bir ileti ele geçirildiğinde F1 yardım isteklerini kapatmanız gerekir.

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
