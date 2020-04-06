---
title: Visual Studio için Animasyonlar | Microsoft Dokümanlar
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc11eb7bab69728be5ceaa55143f56e93cd1fca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698603"
---
# <a name="animations-for-visual-studio"></a>Visual Studio İçin Animasyonlar
## <a name="animation-fundamentals"></a>Animasyon temelleri

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio'da animasyon en iyi uygulamaları
Visual Studio IDE'de tutarlı ve kullanıcı dostu animasyon stilleri sağlamak için bu kurallara uyun.

- **Seçici ol.** Animasyonları belirli amaçlara hizmet edenlerle sınırlandırın.

- **Geçişlerin** hızlı ve doğal hissetmesini sağlamak için zamanlama ve hız önemlidir:

  - Animasyonlu geçişleri bir yarım saniye (500 milisaniye) içinde tamamlayın.

  - Sık sık oluşacak animasyonların, kullanıcının iş akışını kesintiye uğratacak kadar hızlı olması gerekir. Animasyonu bir döngü içinde izleyin ve doğru hissedene kadar zamanlamayı ayarlayın.

  - Animasyonlar anlaşılması zor olacak kadar hızlı veya sarsıcı olmamalıdır, ancak geçişin tamamlanması için sabırsızbir şey olacak kadar yavaş olmamalıdır.

  - Önemi vurgulamak için değişken zamanlama kullanın. Örneğin, sınıf diyagramındaki bir öğe dizisinde gezinirken, öğeler arasındaki geçişlerde hız verirken önemli öğelere odaklanmak için yavaşlayın.

- Sakin ve doğal bir hareket hissi vererek, bir durumdan diğerine **kademeli doğrusal olmayan kolaylaştırma kullanın.**

- Mümkün olduğunda, farenin altındaki etkileşimli öğeleri belirtmek için **havada ince bir animasyon kullanın.**

- Özelliklerinizdeki animasyonlara büyük ölçüde güveniyorsanız, **Araçlar > Seçenekleri** iletişim kutusunda seçenek olarak bunları yerel olarak (tüm özellikleriniz için) kapatmak için bir araç **sağlayın.**

- **Aynı anda yalnızca bir animasyon oluşmalı** ve yalnızca bir bilgi parçası aktarılmalıdır. Birden fazla nesne nin taşınması veya birden çok şeyi iletmeye çalışması kafa karıştırıcı olabilir.

- **Kurnazlık önemlidir.** Çoğu durumda, animasyon amacına hizmet etmek için kullanıcı nın dikkatini talep etmek zorunda değildir. Zamanlama, sıralama ve davranıştaki ince değişiklikler algıyı önemli ölçüde etkileyebilir ve etkili ve etkisiz animasyon arasındaki farkı yaratabilir.

- Bir şeye dikkat çekmek için animasyonu kullanırken, kullanıcının düşünce trenini **kesintiye uğratmaya değdiğinden emin olun.**

- Animasyon aracılığıyla **ilerleme veya durum gösterirken:**

  - Altta yatan süreç ilerleme olmadığında ilerleme hareketini göstermeyi durdurun.

  - Belirsiz süreçleri belirli işlemlerden ayırt edin.

  - Animasyonun tanımlanabilir tamamlama ve hata durumları olduğundan emin olun.

  - Durumu gösteren efekt animasyonlarının kullanımını en aza indirin ve gerçek kullanımhakkında ek bilgiler sağlayarak gerçek değere sahip olduğundan emin olun. Örnekler geçici durum değişiklikleri ve acil durumlar içerir

#### <a name="animation-donts"></a>Animasyon un yapmasi:

- Küçük hareketler (küçük bir ayak izi hareketi) kullanmayın. Hareketli nesnelere göre soluklukları ve değişiklikleri tercih edin.

- Ekran gayrimenkul geniş bir alanda yer alan animasyonlar kullanmayın. Boyutu ne olursa olsun, bu animasyon stili kullanıcının dikkatini dağıtıyor.

- Kullanıcının şu anda odaklandığı veya etkileşimde bulunduğu nesneyle ilgisi olmayan animasyonlar kullanmayın.

- Kullanıcının durumu sıfırlamasını gerektiren animasyonlar kullanmayın, örneğin kullanıcıyı yanıp sönen bildirimi durdurmak için yanıt vermeye zorlamak gibi. Onlarla herhangi bir şekilde etkileşim onları reddetmek için yeterli olmalıdır.

Bu en iyi uygulamalar için uygulamalar hakkında daha fazla bilgi için [Animasyon desenleri](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)bakın.

### <a name="animation-metrics"></a>Animasyon ölçümleri

- Sistem, kullanıcı hareketlerine 10 milisaniyeden daha kısa bir sürede gözle görülür bir şekilde tepki vermelidir.

- Animasyonlu geçişlerin tamamlanması 500 milisaniyeden uzun sürmemelidir.

- Daha uzun süre gerektiren geçişleri telafi etmenin bir yolu, geçişi iki parçaya ayırmaktır. Örneğin, bir animasyonun ilk bölümü boş içerik kapsayıcısı (500 milisaniyeye kadar) ve ardından içeriğin kapsayıcıya solması (500 milisaniyeye kadar) olabilir.

- Hesaplanabilen yükleme süreleri için bir belirleyici ilerleme göstergesi (yüzde-yapılan ilerleme göstergesi) tercih edilir.

- Hesaplanamaz yükleme süreleri için imleç veya gömülü eğirme animasyonu (yükleme veya çalışma göstergesi) gibi meşgul bir gösterge uygundur.

### <a name="animation-as-communicator"></a>İletişimci olarak animasyon
Visual Studio UI'de animasyon yalnızca bir iletişim aracı olarak işlev görür.  Kullanıcı Arabirimi'ndeki yapısal değişiklikler gibi çeşitli bilgileri iletmek için kullanılır (örneğin, bir menü açıldığında veya kapandığında). Animasyon, yükleme ilerleme görselleştirmesi gibi karmaşık sistemlerin zamana bağlı davranışını görselleştirmeye yardımcı olabilir. Animasyonlar uyarılar ve bildirimler ile dikkat çekmek için de kullanılabilir.

 Kullanıcı Arabirimi animasyonları genellikle dört şekilde çalışır: görselleştirme, dikkat çekme, simüle etme ve yanıt süreleri/ilerleme göstergeleri.

#### <a name="visualize"></a>Görselleştirme
Animasyon, nesnelerin üç boyutlu doğasını vurgulayabilir ve kullanıcıların uzamsal yapılarını görselleştirmelerini kolaylaştırabilir. Bunu başarmak için animasyonun nesneyi tam bir daire içinde döndürmesi, yavaşça ileri geri çevirmesi veya nesneyi yakınlaştırması ve rollover veya odaklamayı vurgulamak için boyutunu biraz artırması gerekebilir.

Üç boyutlu nesneler kullanıcı denetimi ile taşınmış olsa da, tasarımcı nesnenin en iyi anlaşılmasını sağlayan bir hareketi en iyi şekilde nasıl canlandırabileceğini önceden (programlı veya el ile) belirlemelidir. Bu programlanmış animasyon daha sonra imleci nesnenin üzerine yerleştirerek kullanıcı tarafından etkinleştirilebilir, oysa kullanıcı tarafından denetitilen hareketler kullanıcının nesneyi nasıl manipüle edeceğini anlamasını gerektirir. Hareketi bir defada tek bir eksen veya yönlendirmeyle sınırlandırın; ölçeklendirin, döndürün veya çevirin, ancak aynı anda birden fazla yapmayın.

Görselleştir kategorisi veri, ilişkiler, durum, yapı, diziliş ve zaman yönlerini içerir.

##### <a name="data"></a>Veriler
Karmaşık ve değişken bilgileri göster:

- Grafikler ve grafikler gibi bilgi görselleştirmeleri arasında gezinme

- Bir sıra, rehberli tur ve sayfalama ile step

- Ayrıntıları çağırma, işaret etme ve belirli bilgileri vurgulama

- Odaklanmış bir öğenin üstüne bilgi ve ek bilgi üst üste koyma

- Bir yapısal veya örgütsel temsilden diğerine dönüşme

- Zaman kaydırıcıları, koşu ve mekik tekerlekleri ve taşıma kontrolleri (oynatma, durdurma ve duraklatma) kullanarak zaman içinde değişiklikleri temsil etme

##### <a name="relationships"></a>İlişkiler

- Öğelerin birbiriyle nasıl ilişkili olduğunu veya hangi öğelerin belirli bir öğeyle ilişkisini göster

- Hiyerarşileri ve üst-alt veya kardeş ilişkilerini göster

- Bir element başka bir elementi yumurtlar

- Bir öğe başka bir öğeye en aza indirir

- Bir eleman diğerine bağlı

##### <a name="state"></a>Durum

- İçerik güncellemeleri

- Kullanıcı odaklılık ve seçim

- İlerleme durumu

- Hatalar

##### <a name="structure"></a>Yapı

- Yapıyı tek bir düğüm üzerinde döndürme

- Yeniden Yönlendirme

- En aza indirin ve en üst düzeye çıkarın veya genişletin ve daraltın

##### <a name="sequence"></a>Sequence

- Slayt gösterisi sırası

- Resimler arasında gezinme

##### <a name="time"></a>Zaman

- Zaman içinde değişimi, zaman atlamasını ve ekran yayınlarını göster

- Çöp kutusuna taşıyın, geri alamayın ve yeniden yapın

- Geçmiş durumu geri yükleme

#### <a name="attract-attention"></a>Dikkat çekin
Amaç, kullanıcının dikkatini birden çok öğeden tek bir öğeye çekmek veya kullanıcıyı güncelleştirilmiş bilgiler konusunda uyarmaksa, animasyon uygun olabilir. Örneğin, uygulama başlangıç sayfanız, sayfa yüklendikten sonra yerine kayan bir Başlangıç düğmesi kullanarak başlayabilir.

Kural olarak, ekrandaki son hareketli öğe kullanıcının dikkatini çeker.  Animasyonlu öğeler serisinde, kullanıcının dikkati son hareket eden nesneyi takip eder.

##### <a name="alert"></a>Uyarı

- Kullanıcıyı uyar, dikkat çek, ilerlemeyi göster

- Bir şeyin doğru veya yanlış yapıldığını gösterme veya ilerleme veya ilerleme değişiklikleri gösterme

- Çevrimiçi daha fazla bilgi bulma veya geçerli görev hakkında bilgi edinme gibi bir görev sırasında kullanıcıları harekete edinme

##### <a name="notifications"></a>Bildirimler

- Kullanıcıyı bir hata durumu hakkında uyar

- Başka bir şeyle ilgilenmek ister misin görmek için kullanıcıyı bölme

- Kullanıcıya, indirme işleminin tamamlandığı gibi bir işlemin tamamlandığını veya değiştiğini yavaşça bildirin.

#### <a name="simulate"></a>Benzet -imini
Bu kategori fiziksellik ve boyutsallık kapsar.

- Nesnelerin nereden geldiğini veya nereye gittiklerini göster

- Genişletin ve daraltın veya açıp kapa

- Kaydırma, kaydırma ve sayfa dönüşleri

- İstifleme ve z-sıralama

- Atlıkarınca ve akordeon

- Çevirme ve dönen UI

#### <a name="response-and-progress-indicators"></a>Yanıt ve ilerleme göstergeleri
İlerleme göstergelerinin birkaç önemli avantajı vardır:

- Hem belirsiz hem de belirsiz ilerleme göstergeleri, kullanıcıya sistemin çökmediğini ve sorun üzerinde çalıştığı konusunda güvence sağlar.

- Belirli göstergeler, kullanıcıya eylemin ne kadar ilerlediğini ve bitişe daha da yaklaştığını hissettirir.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a>Animasyon desenleri

### <a name="overview"></a>Genel Bakış
Visual Studio'daki animasyonlar, kullanıcı üretkenliğini engellemeden belirli bir işleve hizmet etmek içindir. Genellikle Visual Studio'daki animasyonlar şöyle olmalıdır:

- Küçük ve göze batmaz

- Doğal ve gerçekçi

- İnce ve bastırılmış

- Hızlı ve verimli

- Rahat, acele değil

Bu resimde Visual Studio için önerdiğimiz animasyon stilleri gösterilmektedir. En sık kullanılan animasyon veya solukla/soluksa gibi ince animasyonlar kullanılmaz. Genişletme ve sözleşme, X ve Y konum değişikliği ve döndürme gibi hareket animasyonlarının sınırlı uygulaması vardır.

![Visual Studio için önerilen animasyon stilleri](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Visual Studio için önerilen animasyon stilleri

#### <a name="appear-and-disappear"></a>Görün ve kaybolur
Bu desenle, bir öğe görünürden görünüm dışına ve geçiş animasyonu olmadan geri geçer.

![Animasyonu görün ve yok edin](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animasyonu görün ve yok edin

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcının dikkatinin dağılamayacağı veya engellenmeyeceği için anında görünmesi veya kaybolması gereken yeni Kullanıcı Arabirimi öğeleri. Buna ek olarak, yavaş hareket eden animasyonlar, görünüm ve kaybolma stiliyle oluşmayan bir performans sürüklemesi olarak algılanabilir.

##### <a name="incorrect-usage"></a>Yanlış kullanım
Kullanıcı Kullanıcının ne olduğu hakkında hiçbir fikri olmadığı ve animasyon eklemenin bağlamsal anlayışa yardımcı olacağı durumlarda uyrular.

##### <a name="animation-properties"></a>Animasyon özellikleri
Zaman gecikmesi genellikle sıfır saniyedir.

##### <a name="examples"></a>Örnekler
- Araç pencerelerini otomatik gizleme

- IntelliSense ve Parametre Yardım gibi klavye ile etkinleştirilen editör UI

- Kodu genişletme ve daraltma bölgeleri

#### <a name="fade-in-and-fade-out"></a>Solma ve solma
Bu desenle, bir UI öğesi görünür değil (0% opaklık) görünür (100% opaklık) veya tam tersi geçişler.

![Solukve solma animasyonu](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Solukve solma animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Bu, en sık önerilen UI animasyonudur. Akışı kesintiye uğratmadan faiz katan ince bir etkidir. Bazı durumlarda, kullanıcı düzgün ve akıcı bir kullanıcı arabirimi sistemi algılayan bir animasyon olduğunu bile fark etmeyebilir.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç opaklığı: solma için %0, solma için %100

- Bitiş opaklığı: solma için %100, solma için %0

- Süre: 200 milisaniye tek başına, 100 milisaniye bir kombinasyon animasyon dizisinin bir parçası olarak kullanıldığında

- Kolaylaştırma stili: Sine InOut

##### <a name="examples"></a>Örnekler

- Araç pencerelerini otomatik gizleme

- Menü açılıp kapan

- Arka plan ve ön plan sekmesi geçişleri

#### <a name="color-blend-from-a-to-b"></a>A'dan B'ye renk karışımı
Bu desenle, bir UI öğesi A renginden B rengine değişir.

![Renk karışımı animasyon](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Renk karışımı animasyon

##### <a name="correct-usage"></a>Doğru kullanım
Bir UI öğesi bir bağlam veya durum diğerine renk değiştirdiğinde animasyonlu geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç rengi: UI'ye özgü

- Bitiş rengi: UI'ye özgü

- Süre: 200 milisaniye tek başına, 100 milisaniye bir kombinasyon animasyon dizisinin bir parçası olarak kullanıldığında

- Kolaylaştırma stili: Sine InOut

##### <a name="examples"></a>Örnekler

- Belge penceresi durumu geçişleri (etkin, son etkin ve etkin olmayan)

- Araç penceresi durumu geçişleri (odaklanmış ve odaklanmamış)

#### <a name="expand-and-contract"></a>Genişletme ve sözleşme
Bu desenle, bir UI öğesi X, Y veya her iki yönde genişler.

![Animasyonu genişletme ve sözleşme](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Animasyonu genişletme ve sözleşme

##### <a name="correct-usage"></a>Doğru kullanım
Bir UI öğesi boyutu bir bağlamdan diğerine değiştirdiğinde animasyonlu geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- X ölçeği: % veya belirli boyut (piksel olarak)

- Y ölçeği: % veya belirli boyut (piksel olarak)

- Çapa pozisyonu: genellikle sol üstte (soldan sağa diller için) veya sağ üst (sağdan sola diller için)

- Süre: 200 milisaniye tek başına, 100 milisaniye bir kombinasyon animasyon dizisinin bir parçası olarak kullanıldığında

##### <a name="examples"></a>Örnekler

- Mimari Explorer paneli genişletin ve daraltın

- Visual Studio 2017 Başlangıç Sayfası öğesi genişletin ve daraltın

#### <a name="x-y-position-change"></a>X-Y pozisyon değişikliği
Bu desenle, bir UI öğesi X veya Y konumunu veya her ikisini de değiştirir.

![X-Y pozisyon değişikliği animasyonu](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X-Y pozisyon değişikliği animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Bir UI öğesi konumunu bir bağlamdan diğerine değiştirdiğinde animasyonlu geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç X ve Y konumu: UI'ye özgü

- Bitiş X ve Y konumu: UI'ye özgü

- Hareket yolu: yok

- Süre: 200 milisaniye tek başına, 100 milisaniye bir kombinasyon animasyon dizisinin bir parçası olarak kullanıldığında

- Kolaylaştırma stili: Sine InOut

##### <a name="example"></a>Örnek
Sekme yeniden sıralama

#### <a name="rotate"></a>Döndür
Bu desenle, UI öğesi döndürür.

![UI öğesi döndürme animasyonu](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />UI öğesi döndürme animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Sadece belirsiz dönen ilerleme göstergesi için.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Dönüş derecesi: 360

- Döndürme merkezi: nesnenin ortası

- Süre: sürekli

##### <a name="example"></a>Örnek
Belirsiz ilerleme göstergesi (iplik)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ortak kabuk UI eylemleri ve önerilen animasyonlar

#### <a name="tab-open"></a>Sekme açık
![Sekme açık animasyon](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Sekme açık animasyon

- Stil: görünür

- Süre: sıfır saniye

#### <a name="tab-close"></a>Sekme kapat
![Sekme kapatma animasyonu](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Sekme kapatma animasyonu

- Stil: X pozisyon değişikliği

- Süre: 200 milisaniye

#### <a name="tab-reorder"></a>Sekme yeniden sipariş
![Visual Studio'da sekme yeniden sipariş animasyonu](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Sekme yeniden sipariş animasyonu

- Stil: X pozisyon değişikliği

- Süre: 200 milisaniye

#### <a name="close-floating-document"></a>Kayan belgeyi kapatma
![Kayan belge animasyonuna kapatma](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Kayan belge animasyonuna kapatma

- Stil: görünür

- Süre: 200 milisaniye

#### <a name="window-state-transition"></a>Pencere durumu geçişi
![Pencere durumu geçiş animasyonu](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Pencere durumu geçiş animasyonu

- Stil: Diğer pencerelerle tutarlı olması için, geçerli işletim sisteminin belgeyi kapatma animasyonu tanımlamasına izin verin.

- Süre: 200 milisaniye

#### <a name="menu-open"></a>Menü açık
![Menü açık animasyon](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Menü açık animasyon

- Stil: solma-in

- Süre: 200 milisaniye

#### <a name="menu-close"></a>Menü kapat
![Menü kapatma animasyonu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Menü kapatma animasyonu

- Stil: solma-out

- Süre: 200 milisaniye

#### <a name="auto-hide-tool-window-reveal"></a>Otomatik gizleme aracı penceresi ortaya
![Otomatik gizleme aracı penceresi animasyonu ortaya çıkarır](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Otomatik gizleme aracı penceresi animasyonu ortaya çıkarır

- Stil: görünür

- Süre: sıfır saniye
