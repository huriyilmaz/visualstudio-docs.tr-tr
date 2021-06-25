---
title: Visual Studio için animasyonlar | Microsoft Docs
description: Visual Studio IDE genelinde tutarlı ve Kullanıcı dostu animasyon stillerinin sağlanmasına yardımcı olan kurallar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f1e8e61e5decea326fcb7f670ed2ab58f0137530
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902793"
---
# <a name="animations-for-visual-studio"></a>Visual Studio İçin Animasyonlar
## <a name="animation-fundamentals"></a>Animasyon temelleri

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio 'daki animasyon en iyi uygulamaları
Visual Studio IDE genelinde tutarlı ve Kullanıcı dostu animasyon stilleri sağlamak için bu kuralları izleyin.

- **Seçici olun.** Animasyonları belirli amaçlara hizmet eden olanlarla sınırlayın.

- Geçişlerin hızlı ve doğal olmasını sağlamak için **zamanlama ve hız önemlidir** :

  - Tek bir yarı saniye içinde animasyonlu geçişleri (500 milisaniye) doldurun.

  - Genellikle ortaya çıkabilecek animasyonların, kullanıcının iş akışını kesintiye uğramayan yeterince hızlı olması gerekir. Animasyonu bir döngüde izleyin ve doğru olana kadar zamanlamayı ayarlayın.

  - Animasyonlar daha hızlı veya Jarring bir şekilde anlaşılmamalıdır, ancak geçişin sonlanması için bir sabırsız davranır yaptığını yavaşlatmaz.

  - Önemi vurgulamak için değişken zamanlamasını kullanın. Örneğin, bir sınıf diyagramında bir dizi öğe ile gezinirken, öğeler arasındaki geçişleri hızlandırmak ve önemli öğelere odaklanmak için bu işlemleri yavaşlatır.

- Tek bir durumdan diğerine **dereceli doğrusal olmayan hareket hızını kullanın** , sakı ve doğal bir hareket hissi verir.

- Mümkün olduğunda, fare altındaki etkileşimli öğeleri göstermek için, **üzerine gidildiğinde hafif bir animasyon kullanın** .

- Özelliklerinizde çok fazla animasyon kullanıyorsanız, **araçlar > seçenekleri** iletişim kutusunda bir seçenek olarak, bunları yerel olarak (tüm özelliklerinizde) **devre dışı bırakmak için bir yol belirtin** .

- Tek seferde **yalnızca bir animasyon gerçekleşmeli** ve tek bir bilgi parçası iletmelidir. Birden çok nesneyi taşıma veya bir şeyi almaya çalışırken birden fazla nesne kafa karıştırıcı olabilir.

- **Alt tcellik önemli.** Çoğu durumda, animasyonun amacını karşılamak için Kullanıcı dikkatini talep etmek zorunda değildir. Zamanlama, sıralama ve davranıştaki hafif değişiklikler performansı önemli ölçüde etkileyebilir ve etkili ve verimsiz bir animasyon arasında farklılık gösterebilir.

- Bir şeye dikkat çekmek için animasyon kullanırken, kullanıcının düşündüme eğmesini **kesintiye uğradığından emin olun**.

- Animasyon aracılığıyla **ilerleme durumunu veya durumu gösterirken** :

  - Temeldeki işlem ilerlemiyorsa ilerleme hareketini gösterme işlemini durdurun.

  - Belirsiz işlemlerin belirleyici işlemlerden ayırt edilmesini sağlamak.

  - Bir animasyonun, tanımlayıcı ve hata durumlarına sahip olduğundan emin olun.

  - Durumu gösteren efekt animasyonları kullanımını en aza indirin ve gerçek kullanım hakkında daha fazla bilgi sağlayarak gerçek değere sahip olduklarından emin olun. Örnekler, geçici durum değişiklikleri ve acil durumlar içerir

#### <a name="animation-donts"></a>Animasyon yapılmaması gerekenler:

- Küçük hareketler kullanmayın (küçük bir parmak izi içinde hareket edin). Hareketli nesneler üzerinde belirme ve değişiklik yapmayı tercih edin.

- Büyük bir ekran Emlak alanı üzerinde gerçekleşen animasyonları kullanmayın. Boyut ne olursa olsun, bu animasyon stili kullanıcıya dikkat dağıtıcı.

- Kullanıcının şu anda odaklanmış veya ile etkileşimde bulunduğu nesneyle ilgisi olmayan animasyonları kullanmayın.

- Kullanıcı etkileşimi gerektiren animasyonları kullanmayın. bu durum, kullanıcının yanıp sönmesini durdurmak için yanıp sönen bir bildirime yanıt vermesini zorluyor. Bunlarla herhangi bir şekilde etkileşimde bulunmak, bunları kapatmak için yeterli olmalıdır.

Bu en iyi yöntemlere yönelik uygulamalar hakkında daha fazla bilgi için bkz. [animasyon desenleri](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Animasyon ölçümleri

- Sistem, 10 milisaniyeden kısa bir süre içinde Kullanıcı hareketlerine uygun şekilde tepki sağlamalıdır.

- Animasyonlu geçişlerin tamamlanması 500 milisaniyeden uzun sürmemelidir.

- Daha uzun süre gerektiren geçişler için telafi etmenin bir yolu, bunu iki bölümden ayıramaktır. Örneğin, bir animasyonun ilk bölümü boş içerik kapsayıcısı (en fazla 500 milisaniye), ardından kapsayıcıya içerik geçişi (500 milisaniyeye kadar) olabilir.

- Hesaplanabilecek yükleme süreleri için, bir determinyarı ilerleme göstergesi (Tamamlanma yüzdesi ilerleme göstergesi) tercih edilir.

- Hesaplanamayacak yükleme süreleri için, imleç veya katıştırılmış dönen animasyon (yükleme veya çalışma göstergesi) gibi meşgul bir gösterge uygundur.

### <a name="animation-as-communicator"></a>Communicator olarak animasyon
Visual Studio Kullanıcı arabiriminde animasyon yalnızca bir iletişim aracı olarak çalışır.  Kullanıcı arabirimindeki yapısal değişiklikler (örneğin, bir menü açıldığında veya kapandığında) gibi çeşitli bilgilerle iletişim kurmak için kullanılır. Animasyon, yükleme ilerleme durumu görselleştirmesi gibi karmaşık sistemlerin zamana bağlı davranışını görselleştirmenize yardımcı olabilir. Animasyonlar, uyarılar ve bildirimlerle ilgili dikkat çekmek için de kullanılabilir.

 UI animasyonları genellikle dört şekilde çalışır: görselleştirme, dikkat çekici, benzetim yapma ve yanıt süreleri/ilerleme göstergeleri.

#### <a name="visualize"></a>Görselleştirme
Animasyon, nesnelerin üç boyutlu yapısını vurgularken kullanıcıların uzamsal yapısını görselleştirmelerini kolaylaştırır. Bunu başarmak için, animasyonun nesneyi tam bir daire içinde dönmesi, yavaş açıp geri dönmesi veya nesneyi daha yakınına getirip, rollover veya odağı vurgulamak için boyutunu biraz daha büyütmek gerekebilir.

Üç boyutlu nesneler kullanıcı denetimiyle taşınabilir, ancak nesnenin en iyi şekilde öğrenilmesine olanak tanıyan bir taşımanın en iyi şekilde nasıl hareketlendirileceğini, tasarımcı önceden (programlı veya el ile) belirlemelidir. Bu programlanmış animasyon daha sonra imleç nesnenin üzerine yerleştirilerek Kullanıcı tarafından etkinleştirilebilir, ancak kullanıcı denetimli hareketler kullanıcının nesneyi nasıl işleyebileceğini anlaması gerekir. Hareketi tek bir eksenli veya yönlendirmeye göre sınırlayın; ölçeklendirin, döndürün ya da çevirin, ancak aynı anda birden fazla yapmayın.

Görselleştirilecek kategori, verilerin, ilişkilerin, durumun, yapının, sıranın ve zamanın yönlerini içerir.

##### <a name="data"></a>Veriler
Karmaşık ve değişken bilgilerini gösterir:

- Grafikler ve grafikler gibi bilgi görselleştirmeleri arasında dolaşma

- Bir dizi, Kılavuzlu Tur ve disk belleği aracılığıyla adımla

- Ayrıntıları çağırma, belirli bilgileri gösterme ve vurgulama

- Odaklanmış bir öğenin üzerine ayrıntıları ve ek bilgileri yerleştirme

- Bir yapısal veya kuruluş gösteriminden diğerine morphing

- Zaman sürgüleri, jog-ve-shuttle tekerlekleri ve taşıma denetimleri (Oynat, durdur ve Duraklat) kullanarak zaman içindeki değişiklikleri temsil etme

##### <a name="relationships"></a>İlişkiler

- Öğelerin birbirleriyle veya hangi öğelerin belirli bir öğeyle bağlantılı olduğunu gösterir

- Hiyerarşileri ve üst-alt veya Eşdüzey ilişkileri göster

- Bir öğe başka bir şekilde çoğaltılır

- Bir öğe başka bir öğe için en aza indirilir

- Bir öğe tethered

##### <a name="state"></a>Durum

- İçerik güncelleştirmeleri

- Kullanıcı odağı ve seçimi

- İlerleme Durumu

- Hatalar

##### <a name="structure"></a>Yapı

- Bir düğümdeki yapıyı özetleme

- Reorienting

- Simge durumuna küçült ve büyüt veya Genişlet ve Daralt

##### <a name="sequence"></a>Sequence

- Slayt gösterisi sırası

- Resimleri arasında dolaşma

##### <a name="time"></a>Saat

- Zaman içindeki değişikliği, zaman atlama ve ekran kaydı 'nı göster

- Çöp kutusuna taşı, geri al ve Yinele

- Geçmiş durumunu geri yükle

#### <a name="attract-attention"></a>Dikkat çekici
Hedef, kullanıcının dikkatini birkaç farklı bir öğeye çizmektir veya kullanıcıyı güncelleştirilmiş bilgilere uyarlıyorsanız, bir animasyon uygun olabilir. Örneğin, uygulama başlangıç sayfası, sayfa yüklendikten sonra slaytların yer aldığı bir başlangıç düğmesi kullanabilir.

Bir kural olarak, ekranda geçen en son öğe, kullanıcının dikkatini çekmesini sağlar.  Bir dizi animasyonlu öğe içinde, kullanıcının ilgilenilmesi son hareketli nesneyi takip edecektir.

##### <a name="alert"></a>Uyarı

- Kullanıcıyı uyarma, dikkat edin, ilerlemeyi göster

- Bir şeyin doğru veya yanlış bir şekilde yapıldığını ya da ilerleme durumunu veya ilerleme değişikliklerini gösterir

- Çevrimiçi olarak daha fazla bilgi bulma veya geçerli görev hakkında öğrenme gibi bir görev sırasında kullanıcılara sor

##### <a name="notifications"></a>Bildirimler

- Bir hata durumu hakkında kullanıcıyı uyarır

- Başka bir şeye katılmak ister mi diye görmek için kullanıcının kesintiye uğratması

- İndirme işlemi tamamlandığında olduğu gibi kullanıcıya bir işlemi tamamlamış veya değiştirdiğini bildirmiş olur.

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

- Hem belirleyici hem de belirsiz ilerleme göstergeleri, kullanıcıya sistemin kilitlenmeyerek sorun üzerinde çalıştığı konusunda güvence sağlar.

- Belirleyici göstergeler, kullanıcıya eylemin ne kadar ilerler, ne kadar ilerler ve bitişe daha yakın olduğunu hissetmesini sağlar.

## <a name="animation-patterns"></a><a name="BKMK_AnimationPatterns"></a> Animasyon desenleri

### <a name="overview"></a>Genel Bakış
Çalışma Visual Studio, kullanıcı üretkenliğini engellemeden belirli bir işleve hizmet etmek için hazırlar. Genel olarak, Visual Studio şu şekildedir:

- Küçük ve dikkatsiz

- Doğal ve gerçekçi

- Küçük ve alt

- Hızlı ve verimli

- Gevşek, kolay değil

Bu çizimde, uygulama için önerilen animasyon Visual Studio. En sık kullanılan animasyon veya soldurma/soldurma gibi hafif animasyonlar yoktur. Genişletme ve daraltma, X ve Y konum değişikliği ve döndürme gibi hareket animasyonlarının sınırlı bir uygulaması vardır.

![Visual Studio için önerilen animasyon stilleri](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Visual Studio için önerilen animasyon stilleri

#### <a name="appear-and-disappear"></a>Görünür ve kaybolur
Bu desenle, bir öğe görünürden görünüm dışındana ve geçiş animasyonu olmadan geri döner.

![Animasyonu görüntüden çıkar ve gözden çıkar](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />Animasyonu görüntüden çıkar ve gözden çıkar

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcının dikkatinin dağılmış veya rahatsız edici görünmesi için anında görünmesi veya kaybolması gereken yeni kullanıcı arabirimi öğeleri. Buna ek olarak, yavaş hareket eden animasyonlar, görünen ve kaybolan stilde oluşmayacak bir performans sürüklemesi olarak algılanabiliyor.

##### <a name="incorrect-usage"></a>Yanlış kullanım
Kullanıcı arabiriminin aniden ne olduğunu anlamadan göründüğü durumlar ve animasyon eklemek bağlamsal anlama konusunda yardımcı olabilir.

##### <a name="animation-properties"></a>Animasyon özellikleri
Gecikme süresi genellikle sıfır saniyedir.

##### <a name="examples"></a>Örnekler
- Araç pencerelerini otomatik gizleme

- IntelliSense ve Parametre Yardımı gibi klavyeyle etkinleştirilmiş düzenleyici kullanıcı arabirimi

- Kod bölgelerini genişletme ve daraltma

#### <a name="fade-in-and-fade-out"></a>Soldurma ve soldurma
Bu düzende, bir kullanıcı arabirimi öğesi görünür değil (%0 opaklık) öğesinden görünür (%100 opaklık) veya tam tersi olarak geçişler.

![Soldurma ve soldurma animasyonu](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />Soldurma ve soldurma animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Bu, en sık önerilen kullanıcı arabirimi animasyonu. Bu, akışı kesintiye uğratmadan ilgiyi artıran hafif bir etkidir. Bazı durumlarda kullanıcı, sorunsuz ve akışlı bir kullanıcı arabirimi sistemi benimseen bir animasyon olduğunu fark bile ede bile olabilir.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç opaklığı: soldurma için %0, soldurma için %100

- Bitiş opaklığı: Soldurma için %100, soldurma için %0

- Süre: Tek başına 200 milisaniye, bir birleşim animasyon dizisinin parçası olarak kullanılan 100 milisaniye

- Kolaylama stili: Sine InOut

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

- Kolaylama stili: Sine InOut

##### <a name="examples"></a>Örnekler

- Belge penceresi durum geçişleri (etkin, son etkin ve etkin değil)

- Araç penceresi durum geçişleri (odaklanmış ve odaklanmamış)

#### <a name="expand-and-contract"></a>Genişletme ve sözleşme
Bu düzende bir kullanıcı arabirimi öğesi X, Y veya her iki yönde genişler.

![Genişletme ve daraltma animasyonu](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />Genişletme ve daraltma animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcı arabirimi öğesinin boyutu bir bağlamdan diğerine değişirken animasyonlu bir geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- X ölçeği: % veya belirli boyut (piksel cinsinden)

- Y ölçeği: % veya belirli boyut (piksel cinsinden)

- Yer konumu: genellikle sol üst (soldan sağa diller için) veya sağ üst (sağdan sola diller için)

- Süre: Tek başına 200 milisaniye, bir birleşim animasyon dizisinin parçası olarak kullanılan 100 milisaniye

##### <a name="examples"></a>Örnekler

- Mimari Gezgini paneli genişletme ve daraltma

- Visual Studio 2017 Başlangıç Sayfası öğesini genişletme ve daraltma

#### <a name="x-y-position-change"></a>X-Y konum değişikliği
Bu desenle, kullanıcı arabirimi öğesi X veya Y konumunu veya her ikisini de değiştirir.

![X-Y konumu değiştirme animasyonu](../../extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X-Y konumu değiştirme animasyonu

##### <a name="correct-usage"></a>Doğru kullanım
Kullanıcı arabirimi öğesi bir bağlamdan diğerine geçişte animasyonlu geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Başlangıç X ve Y konumu: Kullanıcı arabirimine özgü

- Bitiş X ve Y konumu: Kullanıcı arabirimine özgü

- Hareket yolu: yok

- Süre: Tek başına 200 milisaniye, bir birleşim animasyon dizisinin parçası olarak kullanılan 100 milisaniye

- Kolaylama stili: Sine InOut

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

- Stil: Diğer pencerelerle tutarlı olması için geçerli işletim sisteminin belgeyi kapatma animasyonunu tanımlamasına izin ver.

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
