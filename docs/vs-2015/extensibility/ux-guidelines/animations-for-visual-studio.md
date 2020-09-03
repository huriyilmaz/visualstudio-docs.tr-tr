---
title: Animasyonlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c07fb0887ae01ec917b39f5d7537d5a78fb5a4c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825353"
---
# <a name="animations-for-visual-studio"></a>Visual Studio İçin Animasyonlar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="animation-fundamentals"></a>Animasyon temelleri

### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio 'daki animasyon en iyi uygulamaları
 Visual Studio IDE 'de tutarlı ve Kullanıcı dostu animasyon stilleri sağlamak için bu kuralları izleyin.

- **Seçici olun.** Animasyonları belirli amaçlara hizmet eden olanlarla sınırlayın.

- Geçişlerin hızlı ve doğal olmasını sağlamak için **zamanlama ve hız önemlidir** :

  - Tek bir yarı saniye içinde animasyonlu geçişleri (500 milisaniye) doldurun.

  - Genellikle ortaya çıkabilecek animasyonların, kullanıcının iş akışını kesintiye uğramayan yeterince hızlı olması gerekir.

  - Animasyonlar daha hızlı veya Jarring bir şekilde anlaşılmamalıdır, ancak geçiş işleminin bitmesini zorlaştırmamak için bir sabırsız davranır.

  - Önemi vurgulamak için değişken zamanlamasını kullanın. Örneğin, bir sınıf diyagramında bir dizi öğe ile gezinirken, öğeler arasındaki geçişleri hızlandırmak ve önemli öğelere odaklanmak için bu işlemleri yavaşlatır.

- Tek bir durumdan diğerine **dereceli doğrusal olmayan hareket hızını kullanın** , sakın ve doğal hareket hakkında fikir verir

- Mümkün olduğunda, fare altındaki etkileşimli öğeleri göstermek için, **üzerine gidildiğinde hafif bir animasyon kullanın** .

- Özelliklerinizde çok fazla animasyon kullanıyorsanız, **araçlar > seçenekleri** iletişim kutusunda bir seçenek olarak, bunları yerel olarak (tüm özelliklerinizde) **devre dışı bırakmak için bir yol belirtin** .

- Tek seferde **yalnızca bir animasyon gerçekleşmeli** ve tek bir bilgi parçası iletmelidir.

- **Alt tcellik önemli.** Çoğu durumda, animasyonun amacını karşılamak için Kullanıcı dikkatini talep etmesi gerekmez. Zamanlama, sıralama ve davranıştaki hafif değişiklikler performansı önemli ölçüde etkileyebilir ve etkili ve verimsiz bir animasyon arasında farklılık gösterebilir.

- Bir şeye dikkat çekmek için animasyon kullanırken, kullanıcının düşünce eğmesini **kesintiye uğradığından emin olun**.

- Animasyon aracılığıyla **ilerleme durumunu veya durumu gösterirken** :

  - Temeldeki işlem ilerlemiyorsa ilerleme hareketini gösterme işlemini durdurun.

  - Belirsiz işlemlerin belirleyici işlemlerden ayırt edilmesini sağlamak.

  - Bir animasyonun, tanımlayıcı ve hata durumlarına sahip olduğundan emin olun.

  - Durumu gösteren efekt animasyonları kullanımını en aza indirin ve gerçek kullanım hakkında daha fazla bilgi sağlayarak gerçek değere sahip olduklarından emin olun. Örnekler, geçici durum değişiklikleri ve acil durumlar içerir

#### <a name="do-not"></a>Yapma:

- Küçük taşımaları (küçük bir ayak izi hareket ettirmek), hareket ettirilmesi ve hareketli nesneler üzerindeki değişiklikleri tercih edin.

- Büyük bir ekran Emlak alanı üzerinde gerçekleşen animasyonları kullanın. Boyut ne olursa olsun, bu animasyon stili kullanıcıya dikkat dağıtıcı.

- Kullanıcının şu anda odaklanmış veya ile etkileşimde bulunduğu nesneyle ilgisi olmayan animasyonları kullanın.

- Kullanıcıyı yanıp sönmesini durdurmak için bir yanıp sönen bildirime yanıt vermeye zorlamak gibi kullanıcı etkileşimi gerektiren animasyonları kullanın. Bunlarla herhangi bir şekilde etkileşimde bulunmak, bunları kapatmak için yeterli olmalıdır.

  Bu en iyi yöntemlere yönelik uygulamalar hakkında daha fazla bilgi için bkz. [animasyon desenleri](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns).

### <a name="animation-metrics"></a>Animasyon ölçümleri

- Sistem, 10 milisaniyeden kısa bir süre içinde Kullanıcı hareketlerine uygun şekilde tepki sağlamalıdır.

- Hareketli geçişlerin tamamlanması 500 milisaniyeden uzun sürmemelidir.

- Daha uzun süre gerektiren geçişleri dengeetmenin bir yolu, bunu iki bölümden ayıramaktır; Örneğin, bir animasyonun ilk bölümü boş içerik kapsayıcısı (en fazla 500 milisaniye) ve ardından kapsayıcıya (en fazla 500 milisaniyeye kadar) içerik geçişi olabilir.

- Hesaplanabilecek yükleme süreleri için, bir determinyarı ilerleme göstergesi (Tamamlanma yüzdesi ilerleme göstergesi) tercih edilir.

- Hesaplanamayacak yükleme süreleri için, imleç veya katıştırılmış dönen animasyon (yükleme veya çalışma göstergesi) gibi bir meşgul göstergesi uygundur.

### <a name="animation-as-communicator"></a>Communicator olarak animasyon
 Visual Studio 'nun Kullanıcı arabiriminde animasyon yalnızca bir iletişim aracı olarak çalışır.  Kullanıcı arabirimindeki yapısal değişiklikler gibi çeşitli bilgileri iletmek için kullanılır; Örneğin, bir menü açıldığında veya kapandığında. Animasyon, yükleme ilerleme durumu görselleştirmesi gibi karmaşık sistemlerin zamana bağlı davranışını görselleştirmenize yardımcı olabilir veya uyarılar ve bildirimler hakkında dikkat çekmek için kullanılır.

 UI animasyonları genellikle dört şekilde çalışır: görselleştirin, dikkat çekici, benzetim yapın ve yanıt sürelerini/ilerlemesini belirtin.

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

- Zaman sürgüleri, jog-ve-shuttle tekerlekleri ve taşıma denetimleri (Oynat, durdur ve Duraklat) kullanarak zaman içindeki değişiklikleri temsil etme.

##### <a name="relationships"></a>İlişkiler

- Öğelerin birbiriyle ilişkisini veya hangi öğelerin belirli bir öğeyle bağlantılı olduğunu gösterir.

- Hiyerarşileri ve üst-alt veya Eşdüzey ilişkileri göster

- Bir öğe başka bir şekilde çoğaltılır

- Bir öğe başka bir öğe için en aza indirilir

- Bir öğe tethered

##### <a name="state"></a>Durum

- İçerik güncelleştirmeleri.

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

##### <a name="time"></a>Süre

- Zaman içindeki değişikliği, zaman atlama ve ekran kaydı 'nı göster

- Çöp kutusuna taşı, geri al ve Yinele

- Geçmiş durumunu geri yükle

#### <a name="attract-attention"></a>Dikkat çekici
 Hedef, kullanıcının dikkatini birkaç farklı bir öğeye çizmektir veya kullanıcıyı güncelleştirilmiş bilgilere uyarlıyorsanız, bir animasyon uygun olabilir. Örneğin, uygulamalarınızın Başlangıç sayfası, sayfa yüklendikten sonra slaytların yer aldığı bir başlangıç düğmesi kullanabilir.

 Bir kural olarak, ekranda geçen en son öğe, kullanıcının dikkatini çekmesini sağlar.  Bir dizi animasyonlu öğe içinde, kullanıcının ilgilenilmesi son hareketli nesneyi takip edecektir.

##### <a name="alert"></a>Uyarı

- Kullanıcıyı uyarma, dikkat edin, ilerlemeyi göster

- Bir şeyin doğru veya yanlış bir şekilde yapıldığını ya da ilerleme durumunu veya ilerleme değişikliklerini gösterir

- Çevrimiçi olarak daha fazla bilgi bulma veya geçerli görev hakkında öğrenme gibi bir görev sırasında kullanıcılara sor

##### <a name="notifications"></a>Bildirimler

- Bir hata durumu hakkında kullanıcıyı uyarır

- Kullanıcının başka bir şeye katılmayı ister misiniz?

- Kullanıcının bir işlemin tamamlandığını veya değiştiğini (örneğin, bir indirme işlemi tamamlandığında) yavaşça bilgilendirmesini ister.

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
 Visual Studio 'daki animasyonlar, hudra Kullanıcı üretkenliğini değil, belirli bir işlevi sunmaktır. Dahil edilecek genel animasyon özellikleri:

- Küçük ve unobive

- Doğal ve gerçekçi

- Hafif ve alt

- Hızlı ve verimli

- Gevşek, acelebilir değil

  Aşağıdaki çizimde, Visual Studio 'da kullanılması önerilen animasyon stilleri gösterilmektedir. Soluklaştırma/soluklaştırma gibi animasyon ve hafif animasyonlar, en sık kullanılan bir şekilde kullanılır. Genişletme ve sözleşme, X ve Y konumu değişikliği ve döndürme gibi hareket animasyonlarının sınırlı bir uygulaması vardır.

  ![Visual Studio için önerilen animasyon stilleri](../../extensibility/ux-guidelines/media/1202-a-vsanimstyles.png "1202-a_VSAnimStyles")

  **Visual Studio için önerilen animasyon stilleri**

#### <a name="appear-and-disappear"></a>Görünür ve kaybolur
 Bu Düzenle, bir öğe, bir geçiş animasyonu olmadan görünür ve geri dön durumuna geçer:

 ![Visual Studio 'da&#47;görünmez animasyon](../../extensibility/ux-guidelines/media/1202-b-appearanddisappear.png "1202-b_AppearAndDisappear")

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
 Bu düzende, bir kullanıcı arabirimi öğesi, görünür değil (%0 opaklık) görünmez (%100 opaklık) veya bunun tersini yapar:

 ![&#45;belirme&#45;Visual Studio 'da&#47;belirme animasyonu](../../extensibility/ux-guidelines/media/1202-c-fadeinfadeout.png "1202-c_FadeInFadeOut")

##### <a name="correct-usage"></a>Doğru kullanım
 Bu en yaygın olarak önerilen UI animasyondur. Akışı kesintiye uğramadan ilgi ekleyen hafif bir etkiye sahiptir. Bazı durumlarda, Kullanıcı bir animasyon olduğunu bile ve sorunsuz, akan bir kullanıcı arabirimi sistemini beyin.

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
 Bu düzende, bir UI öğesi Color A 'dan rengine B 'ye değişir:

 ![Visual Studio 'da renk karışımı animasyonu](../../extensibility/ux-guidelines/media/1202-d-colorblend.png "1202-d_ColorBlend")

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
 Bu Düzenle, bir kullanıcı arabirimi öğesi X, Y veya her iki yönde de genişletilir:

 ![Visual Studio 'da&#47;sözleşmesi animasyonunu Genişlet](../../extensibility/ux-guidelines/media/1202-e-expandcontract.png "1202-e_ExpandContract")

##### <a name="correct-usage"></a>Doğru kullanım
 Bir kullanıcı arabirimi öğesi, bir bağlamdan diğerine boyut değiştirdiğinde animasyonlu geçiş olarak.

##### <a name="animation-properties"></a>Animasyon özellikleri

- X Ölçeği:% veya belirli bir boyut (piksel cinsinden)

- Y Ölçeği:% veya belirli bir boyut (piksel cinsinden)

- Yer işareti konumu: genellikle sol üst (soldan sağa diller için) veya sağ üst (sağdan sola diller için)

- Süre: bir karma animasyon sırasının bir parçası olarak kullanıldığında, 200 milisaniye tek başına, 100 milisaniyesi

##### <a name="examples"></a>Örnekler

- Mimari Gezgini paneli Genişlet ve Daralt

- Başlangıç sayfası öğesi Genişlet ve Daralt

#### <a name="x-y-position-change"></a>X-Y konum değişikliği
 Bu düzende, bir kullanıcı arabirimi öğesi X veya Y konumunu veya her ikisini de değiştirir:

 ![Visual Studio 'da X&#47;Y konumu değişikliği animasyonu](../../extensibility/ux-guidelines/media/1202-f-xypositionchange.png "1202-f_XYPositionChange")

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
 Bu Düzenle, UI öğesi şunu döndürür:

 ![Visual Studio 'da animasyonu döndürme](../../extensibility/ux-guidelines/media/1202-g-rotate.png "1202-g_Rotate")

##### <a name="correct-usage"></a>Doğru kullanım
 Yalnızca belirsiz dönen ilerleme durumu göstergesi için.

##### <a name="animation-properties"></a>Animasyon özellikleri

- Döndürme derecesi: 360

- Döndürme Merkezi: nesnenin ortası

- Süre: sürekli

##### <a name="example"></a>Örnek
 Belirsiz ilerleme göstergesi (dönen)

### <a name="common-shell-ui-actions-and-recommended-animations"></a>Ortak kabuk UI eylemleri ve önerilen animasyonlar

#### <a name="tab-open"></a>Sekme açık

- Stil: görünür

- Süre: sıfır saniye

  ![Visual Studio 'da sekme açık animasyonu](../../extensibility/ux-guidelines/media/1202-h-tabopen.png "1202-h_TabOpen")

#### <a name="tab-close"></a>Sekme Kapat

- Stil: X konum değişikliği

- Süre: 200 milisaniye

  ![Visual Studio 'da sekme kapatma animasyonu](../../extensibility/ux-guidelines/media/1202-i-tabclose.png "1202-i_TabClose")

#### <a name="tab-reorder"></a>Sekme yeniden düzenleme

- Stil: X konum değişikliği

- Süre: 200 milisaniye

  ![Visual Studio 'da sekme yeniden sıralama animasyonu](../../extensibility/ux-guidelines/media/1202-j-tabreorder.png "1202-j_TabReorder")

#### <a name="close-floating-document"></a>Kayan belgeyi kapat

- Stil: görünür

- Süre: 200 milisaniye

  ![Visual Studio 'da kayan belge animasyonunu kapat](../../extensibility/ux-guidelines/media/1202-k-closefloatingdocument.png "1202-k_CloseFloatingDocument")

#### <a name="window-state-transition"></a>Pencere durum geçişi

- Stil: diğer pencereler ile tutarlı olması Için, geçerli işletim sisteminin, belgeyi kapatma animasyonunu tanımlamasına izin verin.

- Süre: 200 milisaniye

  ![Visual Studio 'da pencere durumu geçiş animasyonu](../../extensibility/ux-guidelines/media/1202-l-windowstatetransition.png "1202-l_WindowStateTransition")

#### <a name="menu-open"></a>Menüyü aç

- Stil: belirme

- Süre: 200 milisaniye

  ![Visual Studio 'da menü açma animasyonu](../../extensibility/ux-guidelines/media/1202-m-menuopen.png "1202-m_MenuOpen")

#### <a name="menu-close"></a>Menü kapat

- Stil: Soldur

- Süre: 200 milisaniye

  ![Visual Studio 'da menü kapatma animasyonu](../../extensibility/ux-guidelines/media/1202-n-menuclose.png "1202-n_MenuClose")

#### <a name="auto-hide-tool-window-reveal"></a>Araç penceresini otomatik gizle açığa çıkar

- Stil: görünür

- Süre: sıfır saniye

  ![Visual Studio 'da araç pencere animasyonunu otomatik&#45;gizle](../../extensibility/ux-guidelines/media/1202-o-autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")
