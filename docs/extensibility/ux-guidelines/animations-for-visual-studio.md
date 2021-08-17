---
title: Visual Studio | için animasyonlar Microsoft Docs
description: IDE'de tutarlı ve kullanıcı dostu animasyon stillerini sağlamaya yardımcı Visual Studio öğrenin.
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
ms.openlocfilehash: 933856cffcf7a012be7d9774b3d703aa92e335fb5d7939d804ef49043875f1a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388460"
---
# <a name="animations-for-visual-studio"></a>Visual Studio İçin Animasyonlar
## <a name="animation-fundamentals"></a>Animasyonun temelleri

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio'da animasyon en iyi Visual Studio
IDE genelinde tutarlı ve kullanıcı dostu animasyon stillerini sağlamak için Visual Studio izleyin.

- **Seçici olun.** Animasyonları belirli amaçlara hizmet edenlerle sınırla.

- **Geçişlerin hızlı ve doğal** olmasını sağlamak için zamanlama ve hız önemlidir:

  - Bir yarım saniye (500 milisaniye) içinde animasyonlu geçişleri tamamlama.

  - Sık sık meydana gelen animasyonların, kullanıcının iş akışını kesintiye uğratmayacak kadar hızlı olması gerekir. Bir döngüde animasyonu izleyin ve doğru olana kadar zamanlamayı ayarlayın.

  - Animasyonlar, anlamanın zor olduğu kadar hızlı veya jarring(jarring) olmalı, ancak bu kadar yavaş olmaması nedeniyle geçişin bitip bite geçilene kadar çok hızlı olmaması gerekiyor.

  - Önemini vurgulamak için değişken zamanlama kullanın. Örneğin, bir sınıf diyagramında bir öğe dizisinde gezinirken, öğeler arasındaki geçişleri hızlandırın ve ardından önemli öğelere odaklanmak için yavaşlar.

- **Bir durumdan diğerine aşamalı doğrusal** olmayan kolaylaştırmayı kullanarak sakin ve doğal hareket hakkında bir anlam ifade etmek.

- Mümkün olduğunda **farenin altındaki etkileşimli öğeleri göstermek için** üzerine gelindiğinde hafif bir animasyon kullanın.

- Özelliklerinizin animasyonlarına yoğun bir şekilde güveniyorsanız, Araçlar ve Seçenekler iletişim kutusunda bir seçenek olarak bunları yerel olarak (tüm özellikleriniz için) kapatmak için **bir > belirtin.** 

- **Aynı anda yalnızca bir animasyon oluşmalı** ve yalnızca tek bir bilgi iletmeli. Birden fazla nesneyi taşıma veya birden çok şeyi iletmeye deneme kafa karıştırıcı olabilir.

- **Incelik önemlidir.** Çoğu durumda animasyonun amacına hizmet etmek için kullanıcıya dikkat çekmesi gerekmemektedir. Zamanlama, dizim ve davranışta küçük değişiklikler algıyı önemli ölçüde etkileyenin ve etkili ve etkisiz animasyon arasındaki farkı yaratabilir.

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

- Sistem, kullanıcı hareketlerine 10 milisaniyeden daha kısa bir süre içinde görünür şekilde tepki vermeli.

- Animasyonlu geçişlerin tamamlanması 500 milisaniyeden uzun sürebilir.

- Daha uzun süre gerektiren geçişleri dengelemenin bir yolu, iki parçaya ayırmaktır. Örneğin, bir animasyonun ilk bölümü boş içerik kapsayıcısı (500 milisaniyeye kadar), ardından içerik kapsayıcıya sildi (500 milisaniyeye kadar) olabilir.

- Hesaplanabilir yük süreleri için belirleyici bir ilerleme göstergesi (yapılan yüzde ilerleme göstergesi) tercih edilir.

- Hesaplanmayabilecek yükleme süreleri için, imleç veya ekli dönen animasyon (yükleme veya çalışma göstergesi) gibi meşgul bir gösterge uygundur.

### <a name="animation-as-communicator"></a>İletişimci olarak animasyon
Kullanıcı Visual Studio animasyon yalnızca bir iletişim aracı olarak işlev gösterir.  Kullanıcı arabiriminde yapısal değişiklikler (örneğin, bir menü açıldığında veya kapanıyorsa) gibi çeşitli bilgileri iletişim kurmak için kullanılır. Animasyon, yükleme ilerleme durumu görselleştirmesi gibi karmaşık sistemlerin zaman bağımlı davranışını görselleştirmeye yardımcı olabilir. Animasyonlar, uyarılar ve bildirimlerle dikkat çekmek için de kullanılabilir.

 Kullanıcı arabirimi animasyonları genellikle dört şekilde çalışır: görselleştirme, dikkat çekme, benzetim ve yanıt süreleri/ilerleme göstergeleri.

#### <a name="visualize"></a>Görselleştirme
Animasyon nesnelerin üç boyutlu yapısını vurgular ve kullanıcıların uzamsal yapılarını görselleştirmesini kolaylaştırır. Bunu başarmak için animasyonun nesneyi tam bir daire içinde döndürmesi, yavaş bir şekilde ileri ve geri döndürmesi ya da nesneyi daha yakına getirmesi ve boyutunu biraz artırarak rollover veya focus vurgusunu vurgulaması gerekir.

Üç boyutlu nesneler kullanıcı denetimiyle taşınsa da, tasarımcı nesnenin en iyi şekilde anlaşılmasını sağlayan bir harekete en iyi animasyonu nasıl ekleyeceklerini önceden (program aracılığıyla veya el ile) belirlemeli. Bu programlanmış animasyon daha sonra imleci nesnenin üzerine getirerek kullanıcı tarafından etkinleştirilebilirken, kullanıcı denetimli taşımalar kullanıcının nesneyi nasıl işleycesini an izlemesini gerektirir. Hareketi tek bir eksenle veya aynı anda yönlendirmeyle sınırlama; ölçeklendirin, döndürün veya çevirin, ancak aynı anda birden fazla şey yapma.

Görselleştir kategorisi verilerin, ilişkilerin, durumların, yapının, sıranın ve zamanların yönlerini içerir.

##### <a name="data"></a>Veriler
Karmaşık ve değişken bilgileri göster:

- Grafikler ve grafikler gibi bilgi görselleştirmeleri arasında ilerleme

- Dizi, kılavuzlu tur ve disk belleği adımlama

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

- Çevrimiçi olarak daha fazla bilgi bulmak veya geçerli görev hakkında bilgi almak gibi görev sırasında kullanıcılara sorun

##### <a name="notifications"></a>Bildirimler

- Bir hata koşulu hakkında kullanıcıya uyarı

- Kullanıcının başka bir şeye katılmayı ister misiniz?

- Bir indirme işlemi tamamlandığında, kullanıcıyı bir işlemin tamamlandığını veya değiştiğini bir şekilde bilgilendirir.

#### <a name="simulate"></a>Simüle
Bu kategori, doktor ve boyutlılık içerir.

- Nesnelerin nereden geldiği veya nereden gideceni gösterir

- Genişlet ve daralt veya aç ve Kapat

- Kaydırma, kaydırma ve sayfa dönüşler

- Yığınlama ve z-sıralama

- Carusel ve Accordion

- Kullanıcı arabirimini çevirme ve döndürme

#### <a name="response-and-progress-indicators"></a>Yanıt ve ilerleme göstergeleri
İlerleme göstergeleri birkaç önemli avantaj sağlar:

- Hem kesin hem de belirsiz ilerleme göstergeleri, sistemin kilitlenmediğinden ve sorun üzerinde çalışmamasına neden olan kullanıcıyı yeniden alır.

- Kesin göstergeler, kullanıcıya eylemin ne kadar ilerlediğini ve sonuna kadar yaklaşmayı çok daha yakından elde etme konusunda fikir verir.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Animasyon desenleri

### <a name="overview"></a>Genel Bakış
Visual Studio animasyonlar, hindering kullanıcı üretkenliği olmadan belirli bir işlevi sunmaktır. genellikle, Visual Studio animasyonların olması gerekir:

- Küçük ve unobive

- Doğal ve gerçekçi

- Hafif ve alt

- Hızlı ve verimli

- Gevşek, acelebilir değil

Bu çizimde Visual Studio için önerdiğimiz animasyon stilleri gösterilmektedir. Belirme/soluklaştırma gibi bir animasyon veya hafif animasyon yoktur en sık kullanılan. Genişletme ve sözleşme, X ve Y konumu değişikliği ve döndürme gibi hareket animasyonlarının sınırlı bir uygulaması vardır.

![Visual Studio için önerilen animasyon stilleri](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Visual Studio için önerilen animasyon stilleri

#### <a name="appear-and-disappear"></a>Görünür ve kaybolur
Bu Düzenle bir öğe, bir geçiş animasyonu olmadan görünür ve geri dön durumuna geçer.

![Görünür ve kaybolur animasyonu](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Görünür ve kaybolur animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcının hiç bir şekilde veya daha fazla görünmemesi veya kaldırılması için anında görünmesi veya kaybolması gereken yeni kullanıcı arabirimi öğeleri. Ayrıca, yavaş hareketli animasyonlar, görünür ve kaybolur stili ile gerçekleşmeyecek bir performans sürükleme olarak algılanır.

##### <a name="incorrect-usage"></a>Yanlış kullanım
Kullanıcının ne olduğu konusunda hiçbir fikir olmaması ve bir animasyon eklemek bağlamsal anlama konusunda yardımcı olur.

##### <a name="animation-properties"></a>Animasyon özellikleri
Gecikme süresi genellikle sıfır saniyedir.

##### <a name="examples"></a>Örnekler
- Araç pencerelerini otomatik gizle

- IntelliSense ve parametre yardımı gibi klavye özellikli düzenleyici Kullanıcı arabirimi

- Kod bölgelerini Genişlet ve Daralt

#### <a name="fade-in-and-fade-out"></a>Soldur ve Soldur
Bu Düzenle, bir kullanıcı arabirimi öğesi, görünür değil (%0 opaklık) görünür değil (%100 opaklık) veya tam tersi.

![Belirme ve soluklaştırma animasyonu](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Belirme ve soluklaştırma animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Bu en yaygın olarak önerilen UI animasyondur. Akışı kesintiye uğramadan ilgi ekleyen hafif bir etkiye sahiptir. Bazı durumlarda, Kullanıcı bir animasyon, perceiving, sorunsuz ve akan bir kullanıcı arabirimi sistemi olduğunu bile fark etmeyebilir.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Opaklık başlatılıyor: belirme için %0, Soldur için %100

- Son opaklık: %100, silinme için %0, silinme için %0

- Süre: bir karma animasyon sırasının bir parçası olarak kullanıldığında, 200 milisaniye tek başına, 100 milisaniyesi

- Kolaylaştırıcı stil: sinüs giriş

##### <a name="examples"></a>Örnekler

- Araç pencerelerini otomatik gizle

- Menü aç ve Kapat

- Arka plan ve ön plan sekme geçişleri

#### <a name="color-blend-from-a-to-b"></a>A 'dan B 'ye renk karışımı
Bu düzende, bir UI öğesi Color A 'dan rengine B 'ye değişir.

![Renk karışımı animasyonu](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />Renk karışımı animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Bir kullanıcı arabirimi öğesi bir içerikten veya durumdan diğerine renk değiştirdiğinde animasyonlu geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç rengi: UI 'ye özgü

- Bitiş rengi: Kullanıcı arabirimine özgü

- Süre: bir karma animasyon sırasının bir parçası olarak kullanıldığında, 200 milisaniye tek başına, 100 milisaniyesi

- Kolaylaştırıcı stil: sinüs giriş

##### <a name="examples"></a>Örnekler

- Belge penceresi durum geçişleri (etkin, son etkin ve etkin değil)

- Araç penceresi durum geçişleri (odaklanmış ve odaklanmış değil)

#### <a name="expand-and-contract"></a>Genişlet ve Daralt
Bu düzende, bir kullanıcı arabirimi öğesi X, Y veya her iki yönde de genişletilir.

![Genişlet ve sözleşme animasyonu](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Genişlet ve sözleşme animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Bir kullanıcı arabirimi öğesi, bir bağlamdan diğerine boyut değiştirdiğinde animasyonlu geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- X Ölçeği:% veya belirli bir boyut (piksel cinsinden)

- Y Ölçeği:% veya belirli bir boyut (piksel cinsinden)

- Yer işareti konumu: genellikle sol üst (soldan sağa diller için) veya sağ üst (sağdan sola diller için)

- Süre: bir karma animasyon sırasının bir parçası olarak kullanıldığında, 200 milisaniye tek başına, 100 milisaniyesi

##### <a name="examples"></a>Örnekler

- Mimari Gezgini paneli Genişlet ve Daralt

- Visual Studio 2017 başlangıç sayfası öğesi genişlet ve daralt

#### <a name="x-y-position-change"></a>X-Y konum değişikliği
Bu düzende, bir kullanıcı arabirimi öğesi X veya Y konumunu veya her ikisini de değiştirir.

![X-Y konum değişikliği animasyonu](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X-Y konum değişikliği animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Bir kullanıcı arabirimi öğesi bir bağlamdan diğerine konum değiştirdiğinde animasyonlu geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç X ve Y konumu: UI-özel

- Bitiş X ve Y konumu: UI-özel

- Hareket yolu: yok

- Süre: bir karma animasyon sırasının bir parçası olarak kullanıldığında, 200 milisaniye tek başına, 100 milisaniyesi

- Kolaylaştırıcı stil: sinüs giriş

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
![Araç penceresini otomatik gizleme animasyonu gösterme](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />Araç penceresini otomatik gizleme animasyonu gösterme

- Stil: görünür

- Süre: sıfır saniye
