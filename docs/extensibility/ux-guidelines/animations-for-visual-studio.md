---
title: Visual Studio | için animasyonlar Microsoft Docs
description: IDE genelinde tutarlı ve kullanıcı dostu animasyon stillerini sağlamaya yardımcı olan Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4ded908acf84f4d932c95fe70d8dab209caa2b44
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028689"
---
# <a name="animations-for-visual-studio"></a>Visual Studio İçin Animasyonlar
## <a name="animation-fundamentals"></a>Animasyonun temelleri

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio'de animasyon en iyi Visual Studio
IDE'de tutarlı ve kullanıcı dostu animasyon stillerini sağlamak için Visual Studio izleyin.

- **Seçici olun.** Animasyonları belirli amaçlara hizmet edenlerle sınırla.

- **Geçişlerin hızlı ve doğal** olmasını sağlamak için zamanlama ve hız önemlidir:

  - Bir yarım saniye (500 milisaniye) içinde animasyonlu geçişleri tamamlama.

  - Sık sık meydana gelen animasyonların, kullanıcının iş akışını kesintiye uğratmayacak kadar hızlı olması gerekir. Bir döngüde animasyonu izleyin ve doğru olana kadar zamanlamayı ayarlayın.

  - Animasyonlar, anlamanın zor olduğu kadar hızlı veya hızlı olmalı, ancak geçişin bitip bite geçilene kadar çok yavaş olmamasına neden olabilir.

  - Önemini vurgulamak için değişken zamanlama kullanın. Örneğin, bir sınıf diyagramında bir öğe dizisinde gezinirken, öğeler arasındaki geçişleri hızlandırın ve ardından önemli öğelere odaklanmak için yavaşlar.

- **Bir durumdan diğerine aşamalı doğrusal** olmayan kolaylaştırmayı kullanarak sakin ve doğal bir hareket algısı sunanın.

- Mümkün olduğunda **farenin altındaki etkileşimli öğeleri göstermek için** üzerine gelindiğinde hafif bir animasyon kullanın.

- Özelliklerinizin animasyonlarına yoğun bir şekilde güveniyorsanız, Araçlar ve Seçenekler iletişim kutusunda bir seçenek olarak bunları yerel olarak (tüm özellikleriniz için) kapatmak için **bir > belirtin.** 

- **Aynı anda yalnızca bir animasyon oluşmalı** ve yalnızca tek bir bilgi iletmeli. Birden fazla nesneyi taşıma veya birden çok şeyi iletmeye deneme kafa karıştırıcı olabilir.

- **Incelik önemlidir.** Çoğu durumda animasyonun amacına hizmet etmek için kullanıcıya dikkat çekmesi gerekmemektedir. Zamanlama, dizim ve davranışta küçük değişiklikler algıyı önemli ölçüde etkileyenin ve etkili ve etkili bir animasyon arasındaki farkı yaratabilir.

- Dikkat çekmek için animasyon kullanırken **kullanıcının** düşünce eğitimini kesintiye uğratmaya değer olduğundan emin olun.

- **Animasyon aracılığıyla ilerleme veya durum** gösteriliyorken:

  - Temel işlem ilerlemezken ilerleme hareketini göstermeyi durdurun.

  - Belirsiz işlemleri, belirleyici işlemlerden ayırt etmek.

  - Animasyonda tanımlanabilir tamamlama ve hata durumları olduğundan emin olmak.

  - Durumu gösterecek olan etki animasyonlarının kullanımını en aza indirme ve gerçek kullanım hakkında ek bilgi sağlayarak gerçek değere sahip olduğundan emin olun. Geçici durum değişiklikleri ve acil durumlar buna örnek olarak verilmiştir

#### <a name="animation-donts"></a>Animasyon şunların olmadığını gösterir:

- Küçük hareket (küçük bir ayak izinde hareket) kullanma. Nesneleri taşımaya göre soldurmayı ve değişiklikleri tercih edin.

- Büyük bir ekran alanı üzerinde geçen animasyonları kullanmayın. Boyut ne olursa olsun, bu animasyon stili kullanıcının dikkatini dağıtıyor.

- Kullanıcının şu anda odaklanmış olduğu veya etkileşim kurduğu nesneyle ilgili olmayan animasyonları kullanma.

- Durumu sıfırlamak için kullanıcı etkileşimi gerektiren animasyonlar kullanmayın; örneğin, kullanıcıya yanıp sönmeyi durdurmak için yanıp sönen bir bildirime yanıt vermeye zorlayın. Onlarla herhangi bir şekilde etkileşim kurmak, bunları yok etmek için yeterli olmalıdır.

Bu en iyi yöntemlere yönelik uygulamalar hakkında daha fazla bilgi için [bkz. Animasyon desenleri.](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)

### <a name="animation-metrics"></a>Animasyon ölçümleri

- Sistem, kullanıcı hareketlerine 10 milisaniyeden daha kısa bir süre içinde görünür şekilde tepki gösterse de.

- Animasyonlu geçişlerin tamamlanması 500 milisaniyeden uzun sürebilir.

- Daha uzun süre gerektiren geçişleri dengelemenin bir yolu, iki parçaya ayırmaktır. Örneğin, bir animasyonun ilk bölümü boş içerik kapsayıcısı (500 milisaniyeye kadar), ardından içerik kapsayıcıya sildi (500 milisaniyeye kadar) olabilir.

- Hesaplanabilir yük süreleri için belirleyici bir ilerleme göstergesi (yapılan yüzde ilerleme göstergesi) tercih edilir.

- Hesaplanmayabilecek yükleme süreleri için, imleç veya ekli dönen animasyon (yükleme veya çalışma göstergesi) gibi meşgul bir gösterge uygundur.

### <a name="animation-as-communicator"></a>İletişimci olarak animasyon
Kullanıcı Visual Studio animasyon yalnızca bir iletişim aracı olarak işlev gösterir.  Kullanıcı arabiriminde yapısal değişiklikler (örneğin, bir menü açıldığında veya kapanıyorsa) gibi çeşitli bilgileri iletişim kurmak için kullanılır. Animasyon, yükleme ilerleme durumu görselleştirmesi gibi karmaşık sistemlerin zaman bağımlı davranışını görselleştirmeye yardımcı olabilir. Animasyonlar, uyarılar ve bildirimlerle dikkat çekmek için de kullanılabilir.

 Kullanıcı arabirimi animasyonları genellikle dört şekilde çalışır: görselleştirme, dikkat çekme, benzetim ve yanıt süreleri/ilerleme göstergeleri.

#### <a name="visualize"></a>Görselleştirme
Animasyon nesnelerin üç boyutlu yapısını vurgular ve kullanıcıların uzamsal yapılarını görselleştirmesini kolaylaştırır. Bunu başarmak için animasyonun nesneyi tam bir daire içinde döndürmesi, yavaş bir şekilde ileri ve geri döndürmesi ya da nesneyi daha yakına getirmesi ve boyutunu biraz artırarak döngü veya odağı vurgulaması gerekir.

Üç boyutlu nesneler kullanıcı denetimiyle taşınsa da, tasarımcı nesnenin en iyi şekilde anlaşılmasını sağlayan bir harekete en iyi animasyonu nasıl ekleyeceklerini önceden (program aracılığıyla veya el ile) belirlemeli. Bu programlanmış animasyon daha sonra imleci nesnenin üzerine getirerek kullanıcı tarafından etkinleştirilebilirken, kullanıcı tarafından denetlenen taşımalar kullanıcının nesneyi nasıl işleycesini anlayacaktır. Hareketi tek bir eksenle veya aynı anda yönlendirmeyle sınırlama; ölçeklendirin, döndürün veya çevirin, ancak aynı anda birden fazla şey yapma.

Görselleştir kategorisi verilerin, ilişkilerin, durumların, yapının, sıranın ve zamanların yönlerini içerir.

##### <a name="data"></a>Veriler
Karmaşık ve değişken bilgileri göster:

- Grafikler ve grafikler gibi bilgi görselleştirmeleri arasında ilerleme

- Bir dizide adım adım, kılavuzlu tur ve disk belleği

- Ayrıntıları çağırma, belirli bilgileri işaret edin ve vurgulayın

- Ayrıntıları ve ek bilgileri odaklanmış bir öğenin üzerine katmanlama

- Bir yapısal veya kuruluş temsilinden diğerine geçiş

- Zaman kaydırıcıları, tekerlekler ve taşıma denetimleri (oynatma, durdurma ve duraklatma) kullanarak zaman içinde yapılan değişiklikleri temsil eder

##### <a name="relationships"></a>İlişkiler

- Öğelerin bir diğer öğeyle nasıl ilişkili olduğunu veya hangi öğelerin bir öğeyle ilişkili olduğunu göster

- Hiyerarşileri ve üst-alt veya alt öğe ilişkilerini gösterme

- Bir öğe başka bir öğe doğurur

- Bir öğe, başka bir öğeyi simge durumuna küçülter

- Bir öğe başka bir öğeye

##### <a name="state"></a>Durum

- İçerik güncelleştirmeleri

- Kullanıcı odağı ve seçimi

- İlerleme Durumu

- Hatalar

##### <a name="structure"></a>Yapı

- Bir düğümde yapıyı özetle

- Yeniden Yön

- Simge durumuna küçült ve ekranı kapla veya genişlet ve daralt

##### <a name="sequence"></a>Sequence

- Slayt gösterisi dizisi

- Resimleri çevirme

##### <a name="time"></a>Saat

- Zaman içinde değişikliği, zaman atlamalarını ve ekran yayınını gösterme

- Çöp kutusuna taşıma, geri alma ve tekrar etme

- Geçmiş durumu geri yükleme

#### <a name="attract-attention"></a>Dikkat çek
Amaç kullanıcının dikkatini birden fazla öğeden tek bir öğeye çekmek veya kullanıcıya güncelleştirilmiş bilgilerle ilgili uyarı oluşturmaksa, bir animasyon uygun olabilir. Örneğin, uygulama başlangıç sayfanız, sayfa Başlarken kayan bir uygulama düğmesi çalıştırabiliyor.

Kural olarak, ekranda son hareket eden öğe kullanıcının dikkatini çeker.  Bir dizi animasyonlu öğede, kullanıcının dikkati son hareket eden nesneyi takip eder.

##### <a name="alert"></a>Uyarı

- Kullanıcıya uyarı, dikkat çekme, ilerlemeyi gösterme

- Bir şeyin doğru veya yanlış bir şekilde tamamlanmış olduğunu ya da ilerleme veya ilerleme değişikliklerinin gösterilmiş olduğunu gösterme

- Çevrimiçi olarak daha fazla bilgi bulmak veya geçerli görev hakkında bilgi almak gibi bir görev sırasında kullanıcılara sorun

##### <a name="notifications"></a>Bildirimler

- Bir hata koşulu hakkında kullanıcıya uyarı

- Başka bir şeye katılmak ister mi diye görmek için kullanıcının kesintiye uğratması

- İndirme işlemi tamamlandığında olduğu gibi, kullanıcıya bir işlemi tamamlamış veya değiştirdiğini bildirmiş olur.

#### <a name="simulate"></a>Benzet -imini
Bu kategori fizikselliği ve boyutsallığı kapsar.

- Nesnelerin nereden veya nereye gittiğini göster

- Genişletme, daraltma veya açma ve kapatma

- Kaydırma, kaydırma ve sayfa dönüşleri

- Yığınlama ve z sıralama

- Carousel ve accordion

- Kullanıcı arabirimini çevirme ve döndürme

#### <a name="response-and-progress-indicators"></a>Yanıt ve ilerleme göstergeleri
İlerleme göstergelerinin birkaç önemli avantajı vardır:

- Hem kararlı hem de belirsiz ilerleme göstergeleri, kullanıcıya sistemin kilitlenmeyerek sorun üzerinde çalıştığı konusunda güvence sağlar.

- Belirleyici göstergeler, kullanıcıya eylemin ne kadar ilerler, ne kadar ilerler ve bitişe daha yakın olduğunu hissetmesini sağlar.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Animasyon desenleri

### <a name="overview"></a>Genel Bakış
Veri Visual Studio, kullanıcı üretkenliğini engellemeden belirli bir işleve hizmet etmek için hazırlar. Genel olarak, Visual Studio şu şekildedir:

- Küçük ve dikkatsiz

- Doğal ve gerçekçi

- Küçük ve alt

- Hızlı ve verimli

- Gevşek, kolay değil

Bu çizimde, uygulama için önerilen animasyon Visual Studio. En sık kullanılan animasyon veya soldurma/soldurma gibi hafif animasyonlar yoktur. Genişletme ve daraltma, X ve Y konum değişikliği ve döndürme gibi hareket animasyonlarının sınırlı bir uygulaması vardır.

![Visual Studio için önerilen animasyon Visual Studio](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Visual Studio için önerilen animasyon Visual Studio

#### <a name="appear-and-disappear"></a>Görünür ve kaybolur
Bu düzende bir öğe, geçiş animasyonu olmadan görünürden görünümden görünüm dışındana ve geri döner.

![Animasyonu görüntüden çıkar ve gözden çıkar](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animasyonu görüntüden çıkar ve gözden çıkar

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcının dikkatinin dağılmış veya rahatsız edici görünmesi için anında görünmesi veya kaybolması gereken yeni kullanıcı arabirimi öğeleri. Ayrıca yavaş hareket eden animasyonlar, görünen ve kaybolan stilde oluşmayacak bir performans sürüklemesi olarak algılanabiliyor.

##### <a name="incorrect-usage"></a>Yanlış kullanım
Kullanıcı arabiriminin aniden ne olduğunu anlamadan göründüğü durumlar ve animasyon eklemek bağlamsal anlama konusunda yardımcı olabilir.

##### <a name="animation-properties"></a>Animasyon özellikleri
Gecikme süresi genellikle sıfır saniyedir.

##### <a name="examples"></a>Örnekler
- Araç pencerelerini otomatik gizleme

- IntelliSense ve Parametre Yardımı gibi klavyeyle etkinleştirilmiş düzenleyici kullanıcı arabirimi

- Kod bölgelerini genişletme ve daraltma

#### <a name="fade-in-and-fade-out"></a>Soldurma ve soldurma
Bu düzende, kullanıcı arabirimi öğesi görünür değil (%0 opaklık) yerine görünür (%100 opaklık) veya tam tersi olarak geçiş yapılır.

![Soldurma ve soldurma animasyonu](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Soldurma ve soldurma animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Bu, en sık önerilen kullanıcı arabirimi animasyonu. Akışı kesintiye uğratmadan ilgiyi artıran hafif bir etkidir. Bazı durumlarda kullanıcı, sorunsuz ve akışlı bir kullanıcı arabirimi sistemiyle ilgili bir animasyon olduğunu fark bile edeyem bile olabilir.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç opaklığı: Soldurma için %0, soldurma için %100

- Bitiş opaklığı: Soldurma için %100, soldurma için %0

- Süre: Tek başına 200 milisaniye, bir birleşim animasyon dizisinin parçası olarak kullanılan 100 milisaniye

- Kolaylık stili: Sine InOut

##### <a name="examples"></a>Örnekler

- Araç pencerelerini otomatik gizleme

- Menü aç ve kapat

- Arka plan ve ön plan sekmesi geçişleri

#### <a name="color-blend-from-a-to-b"></a>A'dan B'ye renk karışımı
Bu desenle, kullanıcı arabirimi öğesi A renginden B rengine değişir.

![Renk karışımı animasyonu](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Renk karışımı animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcı arabirimi öğesi bir bağlamdan veya durumdan diğerine renk değiştirirken animasyonlu bir geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç rengi: Kullanıcı arabirimine özgü

- Bitiş rengi: Kullanıcı arabirimine özgü

- Süre: Tek başına 200 milisaniye, bir birleşim animasyon dizisinin parçası olarak kullanılan 100 milisaniye

- Kolaylık stili: Sine InOut

##### <a name="examples"></a>Örnekler

- Belge penceresi durum geçişleri (etkin, son etkin ve etkin değil)

- Araç penceresi durum geçişleri (odaklanmış ve odaklanmamış)

#### <a name="expand-and-contract"></a>Genişletme ve sözleşme
Bu düzende bir kullanıcı arabirimi öğesi X, Y veya her iki yönde genişler.

![Genişletme ve anlaşma animasyonu](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Genişletme ve anlaşma animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcı arabirimi öğesinin boyutu bir bağlamdan diğerine değişirken animasyonlu bir geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- X ölçeği: % veya belirli boyut (piksel cinsinden)

- Y ölçeği: % veya belirli boyut (piksel cinsinden)

- Yer noktası konumu: genellikle sol üst (soldan sağa diller için) veya sağ üst (sağdan sola diller için)

- Süre: Tek başına 200 milisaniye, bir birleşim animasyon dizisinin parçası olarak kullanılan 100 milisaniye

##### <a name="examples"></a>Örnekler

- Mimari Gezgini paneli genişletme ve daraltma

- Visual Studio 2017 Başlangıç Sayfası öğesini genişletme ve daraltma

#### <a name="x-y-position-change"></a>X-Y konum değişikliği
Bu desenle, kullanıcı arabirimi öğesi X veya Y konumunu veya her ikisini de değiştirir.

![X-Y konumu değiştirme animasyonu](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X-Y konumu değiştirme animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcı arabirimi öğesinin konumu bir bağlamdan diğerine değişirken animasyonlu bir geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç X ve Y konumu: Kullanıcı arabirimine özgü

- Bitiş X ve Y konumu: Kullanıcı arabirimine özgü

- Hareket yolu: yok

- Süre: Tek başına 200 milisaniye, bir birleşim animasyon dizisinin parçası olarak kullanılan 100 milisaniye

- Kolaylık stili: Sine InOut

##### <a name="example"></a>Örnek
Sekme yeniden sıralama

#### <a name="rotate"></a>Döndür
Bu düzende kullanıcı arabirimi öğesi döndürülür.

![Kullanıcı arabirimi öğe döndürme animasyonu](../../extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />Kullanıcı arabirimi öğe döndürme animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Yalnızca belirsiz dönen ilerleme göstergesi için.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Döndürme derecesi: 360

- Döndürme merkezi: nesnenin ortası

- Süre: sürekli

##### <a name="example"></a>Örnek
Belirsiz ilerleme göstergesi (dönen)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ortak kabuk kullanıcı arabirimi eylemleri ve önerilen animasyonlar

#### <a name="tab-open"></a>Sekme aç
![Sekmeyle aç animasyonu](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />Sekmeyle aç animasyonu

- Stil: görünür

- Süre: sıfır saniye

#### <a name="tab-close"></a>Sekme kapatma
![Sekmeyle animasyonu kapatma](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />Sekmeyle animasyonu kapatma

- Stil: X konum değişikliği

- Süre: 200 milisaniye

#### <a name="tab-reorder"></a>Sekme yeniden sıralama
![Sekmeyle animasyonu yeniden Visual Studio](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />Sekme yeniden sıralama animasyonu

- Stil: X konum değişikliği

- Süre: 200 milisaniye

#### <a name="close-floating-document"></a>Kayan belgeyi kapatma
![Kayan belge animasyonunu kapatma](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />Kayan belge animasyonunu kapatma

- Stil: görünür

- Süre: 200 milisaniye

#### <a name="window-state-transition"></a>Pencere durumu geçişi
![Pencere durumu geçişi animasyonu](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />Pencere durumu geçişi animasyonu

- Stil: Diğer pencerelerle tutarlı olması için geçerli işletim sisteminin belge kapatma animasyonunu tanımlamasına izin ver.

- Süre: 200 milisaniye

#### <a name="menu-open"></a>Menü açık
![Menü açık animasyon](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />Menü açık animasyon

- Stil: soldurma

- Süre: 200 milisaniye

#### <a name="menu-close"></a>Menü kapat
![Menü kapatma animasyonu](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />Menü kapatma animasyonu

- Stil: soldurma

- Süre: 200 milisaniye

#### <a name="auto-hide-tool-window-reveal"></a>Araç penceresini otomatik gizleme
![Araç penceresini otomatik gizle animasyonu gösterme](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Araç penceresini otomatik gizle animasyonu gösterme

- Stil: görünür

- Süre: sıfır saniye
