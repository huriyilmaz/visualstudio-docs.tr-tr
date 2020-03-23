---
title: Visual Studio için Uygulama Kalıpları | Microsoft Dokümanlar
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55044df3898b452e87ec877f9ae10dd12a2b1110
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303192"
---
# <a name="application-patterns-for-visual-studio"></a>Visual Studio İçin Uygulama Desenleri
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Pencere etkileşimleri

### <a name="overview"></a>Genel Bakış
Visual Studio'da kullanılan iki ana pencere türü belge düzenleyicileri ve araç pencereleridir. Nadir, ancak mümkün, büyük modsuz iletişim vardır. Bunların hepsi kabukta modeless olmasına rağmen, desenleri temelde farklıdır. Bu bölüm, belge pencereleri, araç pencereleri ve modeless iletişim kutuları arasındaki farkı kapsar. Modal iletişim desenleri [Dialogs](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)kaplıdır.

### <a name="comparing-window-usage-patterns"></a>Pencere kullanım desenlerini karşılaştırma
**Belge pencereleri** hemen hemen her zaman belge içinde iyi görüntülenir. Bu, belge düzenleyicisine ek araç pencerelerini düzenlemek için bir "orta sahne" sağlar.

Bir **araç penceresi** genellikle IDE kenarına çökmüş ayrı, daha küçük bir pencere olarak görüntülenir. Bu görünür, gizli veya otomatik olarak gizlenmiş olabilir. Ancak, bazen araç pencereleri penceredeki **Pencere/Yerleştirme** özelliğini uncheck by, iyi belge içinde sunulur. Bu, daha fazla gayrimenkulle sonuçlanır, aynı zamanda yaygın bir tasarım kararı: Visual Studio'ya entegre etmeye çalışırken, özelliğinizin bir araç penceresi mi yoksa belge penceresi mi görüntülemesi gerektiğine karar vermelisiniz.

Visual Studio'da **modeless diyalogları** önerilmez. Modsuz iletişim lerin çoğu, tanım gereği kayan araç pencereleridir ve bu şekilde uygulanmalıdır. Kabuğun yan tarafına sabitlenmiş normal bir araç penceresinin boyutunun çok sınırlayıcı olacağı durumlarda modeless iletişim kutularına izin verilir. Ayrıca, kullanıcının iletişim kutusunu ikincil bir monitöre taşıma olasılığının yüksek olduğu durumlarda da izin verilir.

Hangi konteyner türüne ihtiyacınız olduğunu dikkatlice düşünün. UI tasarımı için yaygın kullanım deseni hususlaraşağıdaki tabloda yer alıyor.

||Belge penceresi|Araç penceresi|Modeless iletişim kutusu|
|-|---------------------|-----------------|---------------------|
| **Konum** | Belgenin içinde her zaman iyi konumlandırılır ve IDE'nin kenarlarına yanaşmaz. Ana kabuktan ayrı olarak yüzecek şekilde "çekilebilir". | Genellikle IDE'nin kenarlarına sekmeli, ancak kayan, otomatik olarak gizlenecek (sabitlenmemiş) veya belgenin içine iyi sabitlenecek şekilde özelleştirilebilir.|Büyük kayan pencere IDE'den ayrıdır. |
| **Model işleme** | *Gecikmiş taahhüt*<br /><br /> Bir belgedeki verileri kaydetmek için, kullanıcının **Dosya &gt; Kaydet**, Kaydet , **Farklı Kaydet**veya **Tümlerini Kaydet** komutunu vermesi gerekir. Belge penceresi, içindeki verilerin "kirlenmiş" ve sonra kaydet komutlarından birine adadığı kavramına sahiptir. Belge penceresini kapatırken, tüm içerikler diske kaydedilir veya kaybolur. | *Hemen taahhüt*<br /><br /> Kaydet modeli yok. Bir dosyayı düzenlemeye yardımcı olan denetçi araç pencereleri için, dosyanın etkin düzenleyici veya tasarımcıda açık olması gerekir ve kaydedine düzenleyici veya tasarımcı sahiptir. | *Gecikmiş veya hemen taahhüt*<br /><br /> Çoğu zaman, büyük bir modeless iletişim kutusu değişiklikleri işlemek için bir eylem gerektirir ve iletişim oturumu içinde yapılan değişiklikleri geri rulo bir "İptal" işlemi için izin verir.  Bu, bu araç pencerelerinde her zaman hemen işleme modeli olan bir araç penceresinden modsuz bir iletişim aracı ayırt eder. |
| **Görünürlük** | *Aç/Oluştur (dosya) ve Kapat*<br /><br /> Belge pencerelerini açma, varolan bir belgeyi açmak veya yeni bir belge oluşturmak için şablon kullanmak la yapılır. "Özel düzenleyiciyi \<aç>" komutu yoktur. | *Gizle ve göster*<br /><br /> Tek örnekli araç pencereleri gizlenebilir veya gösterilebilir. Araç penceresi içindeki içerikler ve durumlar görünümde veya gizli olarak devam eder. Çok örnekli araç pencereleri kapatılabilir ve gizlenebilir. Çok örnekli araç penceresi kapatıldığında, araç penceresiiçindeki içerik ve durum atılır. | *Bir komuttan başlatılan*<br /><br /> İletişim kutuları görev tabanlı bir komuttan başlatılır. |
| **Örnekler** | *Multi*<br /><br /> Bazı editörler aynı anda açık ve farklı dosyaları düzenleyebilir, bazı editörler de aynı dosyanın birden fazla düzenleyicide **(Pencere &gt; Yeni Pencere** komutunu kullanarak) açılmasına izin verir.<br /><br /> Tek bir düzenleyici aynı anda bir veya birden çok dosyayı düzenliyor olabilir (Project Designer). | *Tek veya çok örnekli*<br /><br /> İçerikler bağlamı yansıtacak şekilde değişir (Özellik Tarayıcısında olduğu gibi) veya odak/bağlamı diğer pencerelere (Görev Listesi, Çözüm Gezgini) itin.<br /><br /> Zorlayıcı bir neden olmadığı sürece, hem tek örnekli hem de çok örnekli araç pencereleri etkin belge penceresiile ilişkilendirilmelidir. | *Tek örnekli* |
| **Örnekler** | **Metin editörleri**, kod düzenleyicisi gibi<br /><br /> **Tasarım yüzeyleri,** form tasarımcısı veya modelleme yüzeyi gibi<br /><br /> Bildirim düzenleri, Manifest Designer gibi **iletişim kutularına benzer denetim düzenleri** | **Çözüm Gezgini** bir çözüm ve çözüm içinde yer alan projeler sağlar<br /><br /> **Sunucu Gezgini,** kullanıcının pencerede açmayı seçtiği sunucuların ve veri bağlantılarının hiyerarşik görünümünü sağlar. Sorgu gibi veritabanı hiyerarşisinden bir nesneyi açma, belge penceresini açar ve kullanıcının sorguyu düzenleyicisine olanak tanır.<br /><br /> **Özellik Tarayıcısı,** belge penceresinde veya başka bir araç penceresinde seçilen nesnenin özelliklerini görüntüler. Özellikler hiyerarşik kılavuz görünümünde veya karmaşık iletişim kutusu benzeri denetimlerde sunulur ve kullanıcının bu özelliklerin değerlerini ayarlamasına izin verir. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Araç pencereleri

### <a name="overview"></a>Genel Bakış
Araç pencereleri, kullanıcının belge pencerelerinde gerçekleşen çalışmasını destekler. Bunlar, Visual Studio'nun sağladığı ve işleyebilir temel bir kök nesneyi temsil eden bir hiyerarşi görüntülemek için kullanılabilir.

IDE'de yeni bir araç penceresi düşünüldüğünde, yazarlar şunları yapmalıdır:

- Göreve uygun varolan araç pencerelerini kullanın ve benzer işlevsellik te yenilerini oluşturmayın. Yeni araç pencereleri yalnızca benzer bir pencereye entegre edilemeyecek önemli ölçüde farklı bir "araç" veya işlevsellik sunarsa veya varolan bir pencereyi döner hub'a dönüştürerek oluşturulmalıdır.

- Gerekirse araç penceresinin üst kısmında standart bir komut çubuğu kullanın.

- Denetim sunumu ve klavye gezintisi için diğer araç pencerelerinde zaten mevcut olan desenlerle tutarlı olun.

- Diğer araç pencerelerinde denetim sunumu yla tutarlı olun.

- Belgeye özgü araç pencerelerini mümkün olduğunda otomatik olarak görünür hale getirin, böylece yalnızca üst belge etkinleştirildiğinde görünürler.

- Pencere içeriğinin klavye (destek ok tuşları) tarafından gezinilebilir olduğundan emin olun.

#### <a name="tool-window-states"></a>Araç penceresi durumları
Visual Studio araç pencerelerinin, bazıları kullanıcı tarafından etkinleştirilen (otomatik gizleme özelliği gibi) farklı durumları vardır. Otomatik görünür gibi diğer durumlar, araç pencerelerinin doğru bağlamda görünmesine ve gerekmediğinde gizlemesine izin verir. Toplamda beş araç penceresi durumları vardır.

- **Sabitlenmiş/sabitlenmiş** araç pencereleri belge alanının dört tarafından herhangi bir ine takılabilir. Araç penceresi başlık çubuğunda toka simgesi görüntülenir. Araç penceresi, kabuğun ve diğer araç pencerelerinin kenarı boyunca yatay veya dikey olarak sabitlenebilir ve sekmeyle de bağlanabilir.

- **Otomatik gizli** araç pencereleri sabitlenmemiş. Pencere, belge alanının kenarında bir sekme (araç penceresinin adı ve simgesiyle) bırakarak gözden uzak kayar. Bir kullanıcı sekme üzerinde gezinirken araç penceresi dışarı kayar.

- **Otomatik görünür** araç pencereleri, bir düzenleyici gibi başka bir uI parçası başlatıldığında veya odak landığında otomatik olarak görünür.

- **Kayan** takım pencereleri IDE'nin dışında gezinir. Bu, çok monitörlü yapılandırmalar için yararlıdır.

- **Sekmeli belge** aracı pencereleri belgenin içine iyi sabitlenebilir. Bu, Nesne Tarayıcısı gibi çerçevenin kenarlarına yerleştirmeden daha fazla gayrimenkule ihtiyaç duyan büyük araç pencereleri için yararlıdır.

![Visual Studio'da araç penceresi durumları](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Visual Studio'da araç penceresi durumları

#### <a name="single-instance-and-multi-instance"></a>Tek örnekli ve çok örnekli
Araç pencereleri tek örnekli veya çok örneklidir. Bazı tek örnekli araç pencereleri etkin belge penceresiyle ilişkilendirilebilir, ancak çok örnekli araç pencereleri ilişkilendirilmeyebilir. Çok örnekli araç pencereleri, pencerenin yeni bir örneğini oluşturarak **Yeni &gt; Pencere Penceresi** komutunu yanıtlar. Aşağıdaki resimde, pencerenin bir örneği etkin olduğunda Yeni Pencere komutunu etkinleştiren bir araç penceresi gösteriş yapılır:

![Pencerenin bir örneği etkin olduğunda 'Yeni Pencere' komutunu etkinleştiren araç penceresi](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Pencerenin bir örneği etkin olduğunda 'Yeni Pencere' komutunu etkinleştiren araç penceresi

Tek örnekli araç pencereleri gizlenebilir veya gösterilebilirken, çok örnekli araç pencereleri kapatılabilir ve gizlenebilir. Tüm araç pencereleri sabitlenebilir, sekmeye bağlı, kayan veya Çoklu Belge Arabirimi (MDI) alt penceresi olarak ayarlanabilir (belge penceresine benzer). Tüm araç pencereleri Pencere menüsündeki uygun pencere yönetimi komutlarına yanıt vermelidir:

![Visual Studio Window menüsünde pencere yönetimi komutları](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Visual Studio Window menüsünde pencere yönetimi komutları

#### <a name="document-specific-tool-windows"></a>Belgeye özel araç pencereleri
Bazı araç pencereleri, belirli bir belge türüne göre değişecek şekilde tasarlanmıştır. Bu pencereler, IDE'deki etkin belge penceresine uygulanan işlevselliği yansıtacak şekilde sürekli olarak güncellenir.

İçeriği seçili düzenleyiciyi yansıtacak şekilde değişen araç pencerelerine örnek olarak Araç Kutusu ve Belge Anahattı verilebilir. Bu pencereler, bir düzenleyicinin pencereye bağlam sunmayan odağı olduğunda bir filigran gösterir.

#### <a name="navigable-list-tool-windows"></a>Gezilebilir liste araç pencereleri
Bazı araç pencereleri, kullanıcının etkileşimde bulunabilir öğelerin listesini görüntüler. Bu tür bir pencerede, pencere etkin olmasa bile listedeki geçerli öğe için her zaman geri bildirim olmalıdır. Liste, pencerede şu anda seçili öğeyi de değiştirerek **GoToNextLocation** ve **GoToPrevLocation** komutlarına yanıt vermelidir

Gezilebilir liste araç pencerelerinin örnekleri Çözüm Gezgini ve Sonuçları Bul penceresidir.

### <a name="tool-window-types"></a>Araç penceresi türleri

#### <a name="common-tool-windows-and-their-functions"></a>Ortak araç pencereleri ve işlevleri

**Hiyerarşik araç pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Çözüm Gezgini | Projelerde, çeşitli dosyalarda ve çözüm öğelerinde bulunan belgelerin listesini görüntüleyen hiyerarşik bir ağaç. Projelerdeki öğelerin görüntülenmesi, proje türüne (örneğin, başvuru tabanlı, dizin tabanlı veya karma mod türleri) sahip olan paket tarafından tanımlanır. |
| Sınıf Görünümü | Dosyaların kendisinden bağımsız olarak, çalışma belgeleri kümesindeki sınıfların hiyerarşik ağacı ve çeşitli öğeler. |
| Sunucu Gezgini | Çözümdeki tüm sunucuları ve veri bağlantılarını görüntüleyen hiyerarşik bir ağaç. |
| Belge Anahattı | Etkin belgenin hiyerarşik yapısı. |

**Izgara aracı pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Özellikler | Seçili nesnenin özelliklerinin listesini ve bu özellikleri ni örecek değer seçicileri görüntüleyen bir ızgara. |
| Görev Listesi | Kullanıcının görevleri ve açıklamaları oluşturmasına/düzenlemesine/silmesine olanak tanıyan bir ızgara. |

**İçerik aracı pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Yardım | Kullanıcıların "Nasıl Yardım Yaparım?" adlı yöntemden çeşitli yardım alma yöntemlerine erişmelerini sağlayan bir pencere MSDN forumlarına videolar. |
| Dinamik Yardım | Geçerli seçimiçin geçerli konulara yardımcı olmak için bağlantıları görüntüleyen bir araç penceresi. |
| Nesne Tarayıcısı | Sol bölmede hiyerarşik nesne bileşenlerinin ve sağ sütundaki nesnenin özellikleri ve yöntemlerinin bir listesini içeren iki sütunlu çerçeve kümesi. |

**İletişim aracı pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Bul | Kullanıcının çözüm içindeki çeşitli dosyaları bulmasına veya bulmasına ve değiştirmesine olanak tanıyan bir iletişim kutusu. |
| Gelişmiş Bul | Kullanıcının çözüm içindeki çeşitli dosyaları bulmasına veya bulmasına ve değiştirmesine olanak tanıyan bir iletişim kutusu. |

**Diğer araç pencereleri**

::: moniker range="vs-2017"

| Araç penceresi | İşlev |
| --- | --- |
| Araç Kutusu | Tasarım yüzeylerine bırakılacak öğeleri depolamak için kullanılan araç penceresi, tüm tasarımcılar için tutarlı bir sürükleme kaynağı sağlar. |
| Başlangıç Sayfası | Geliştirici haber, Visual Studio yardım ve son projelerin beslemeleri erişimi ile Visual Studio kullanıcı portalı. Kullanıcılar ayrıca StartPage.xaml dosyasını "Common7\IDE\StartPages\" Visual Studio program dosyaları dizininden Visual Studio doküman dizinindeki StartPages klasörüne kopyalayarak ve xaml'ı elle veya Visual Studio'da veya başka bir kod düzenleyicisinde açarak özel başlangıç sayfaları oluşturabilirler. |

::: moniker-end

::: moniker range=">=vs-2019"

| Araç penceresi | İşlev |
| --- | --- |
| Araç Kutusu | Tasarım yüzeylerine bırakılacak öğeleri depolamak için kullanılan araç penceresi, tüm tasarımcılar için tutarlı bir sürükleme kaynağı sağlar. |

::: moniker-end

**Hata ayıklama aracı pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Otomobil ||
| Hemen ||
| Çıktı | Çıktı penceresi, bildirilecek metinsel olaylar veya durum olduğunda kullanılabilir. |
| Bellek ||
| Kesme Noktaları ||
| Çalışıyor ||
| Belgeler ||
| Çağrı Yığını ||
| Yerli ||
| Saatler ||
| Demontaj ||
| Kayd -eder ||
| İş Parçacıkları ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Belge düzenleyicisi kuralları

### <a name="document-interactions"></a>Belge etkileşimleri
"Belge iyi" IDE içinde en büyük alandır ve kullanıcı genellikle ek araç pencereleri tarafından desteklenen görevlerini tamamlamak için dikkatlerini odaklanmıştır. Belge düzenleyicileri, kullanıcının Visual Studio'da açıp kaydettiği temel çalışma birimlerini temsil eder. Çözüm Gezgini'ne veya diğer etkin hiyerarşi pencerelerine bağlı güçlü bir seçim duygusunu korurlar. Kullanıcı bu hiyerarşi pencerelerinden birini gösterebilmeli ve belgenin nerede bulunduğunu ve çözüm, proje veya Visual Studio paketi tarafından sağlanan başka bir kök nesneyle ilişkisini bilmelidir.

Belge düzenleme tutarlı bir kullanıcı deneyimi gerektirir. Kullanıcının pencere yönetimi ve bulma komutları yerine eldeki göreve odaklanmasına izin vermek için, bu belge türünü düzenlemek için kullanıcı görevlerine en uygun belge görünümü stratejisini seçin.

#### <a name="common-interactions-for-the-document-well"></a>Belge için ortak etkileşimler iyi

- Ortak **Yeni Dosya** ve Açık **Dosya** deneyimlerinde tutarlı bir etkileşim modeli koruyun.

- Belge penceresi açıldığında ilgili pencerelerde ve menülerde ilgili işlevselliği güncelleştirin.

- Menü komutları, **Edit,** **Biçimlendirme**ve **Görünüm** menüleri gibi ortak menülere uygun şekilde entegre edilmiştir. Önemli miktarda özel komut varsa, yeni bir menü oluşturulabilir. Bu yeni menü yalnızca belge nin odak noktası olduğunda görünür olmalıdır.

- Editörün en üstüne katıştırılmış bir araç çubuğu yerleştirilebilir. Bu, düzenleyicinin dışında görünen ayrı bir araç çubuğuna sahip olmaktan tercih edilir.

- Çözüm Gezgini veya benzer etkin hiyerarşi penceresinde her zaman bir seçim koruyun.

- Çözüm Gezgini'ndeki bir belgeyi çift tıklatma, **Açık**ile aynı eylemi gerçekleştirmelidir.

- Belge türünde birden fazla düzenleyici kullanılabiliyorsa, kullanıcı dosyaya sağ tıklayarak ve kısayol menüsünden **Ile** Aç'ı **seçerek,** belirli bir belge türündeki varsayılan eylemi geçersiz kılabilir veya sıfırlayabilmelidir.

- Belgede sihirbazı iyi oluşturmayın.

### <a name="user-expectations-for-specific-document-types"></a>Belirli belge türleri için kullanıcı beklentileri
Belge düzenleyicilerinin birkaç farklı temel türü vardır ve her birinin aynı türden diğer kişilerle tutarlı bir etkileşim kümesi vardır.

- **Metin tabanlı düzenleyici:** kod düzenleyicisi, günlük dosyaları

- **Tasarım yüzeyi:** WPF formları tasarımcısı, Windows formları

- **İletişim stili düzenleyici:** Manifest Designer, proje özellikleri

- **Model tasarımcısı:** iş akışı tasarımcısı, kod haritası, mimari diyagramı, ilerleme

Belgeyi iyi kullanan birkaç düzenleyici olmayan türü de vardır. Belgeleri kendileri de düzenlilmese ler de, belge pencereleri için standart etkileşimleri izlemeleri gerekir.

- **Raporlar:** IntelliTrace raporu, Hyper-V raporu, profilci raporu

- **Pano:** Tanılama Merkezi

#### <a name="text-based-editors"></a>Metin tabanlı editörler

- Belge önizleme sekmesi modeline katılarak belgeyi açmadan önizlemeye olanak sağlar.

- Belgenin yapısı, belge anahattı gibi bir yardımcı araç penceresinde gösterilebilir.

- IntelliSense (uygunsa) diğer kod editörleri ile tutarlı bir şekilde davranacaktır.

- Pop-up'lar veya yardımcı UI, CodeLens gibi mevcut benzer ui için benzer stilleri ve desenleri izler.

- Belge durumuyla ilgili iletiler, belgenin üst kısmındaki veya durum çubuğundaki bilgi çubuğu denetiminde sunulur.

- Kullanıcı, paylaşılan Yazı Tipleri ve Renkler sayfası veya düzenleyiciye özgü bir Araçlar **> Seçenekleri** sayfasını kullanarak yazı tiplerinin ve renklerin görünümünü özelleştirebilmelidir.

#### <a name="design-surfaces"></a>Tasarım yüzeyleri

- Boş bir tasarımcının yüzeyinde nasıl başlanınacaklarını gösteren bir filigran olmalıdır.

- Görünüm anahtarlama mekanizmaları, kod düzenleyicisini açmak için çift tıklatma veya belge penceresindeki sekmeler ve her iki bölmeyle etkileşime izin verme gibi varolan desenleri izler.

- Son derece özel bir araç penceresi gerekmediği sürece, tasarım yüzeyine öğeler ekleme Araç Kutusu üzerinden yapılmalıdır.

- Yüzeydeki öğeler tutarlı bir seçim modeli izler.

- Katıştırılmış araç çubukları yalnızca belgeye özgü komutlar içerir, **Kaydet**gibi yaygın komutlar içermez.

#### <a name="dialog-style-editors"></a>İletişim stili düzenleyiciler

- Denetim düzeni normal iletişim düzeni kuralları izlemelidir.

- Düzenleyiciiçindeki sekmeler belge sekmelerinin görünümüyle eşleşmemeli, izin verilen iki iç sekme stilinden biriyle eşleşmelidir.

- Kullanıcılar yalnızca klavyeyi kullanarak denetimlerle etkileşim kurabilmeli; ya düzenleyiciyi etkinleştirerek ve denetimler yoluyla sekme yaparak ya da standart mnemonikler kullanarak.

- Tasarımcı ortak Kaydet modelini kullanmalıdır. Diğer düğmeler uygun olsa da, yüzeye genel kaydet veya işleme düğmeleri yerleştirilmemelidir.

#### <a name="model-designers"></a>Model tasarımcıları

- Boş bir tasarımcının yüzeyinde nasıl başlanınacaklarını gösteren bir filigran olmalıdır.

- Tasarım yüzeyine öğeler ekleme Araç Kutusu üzerinden yapılmalıdır.

- Yüzeydeki öğeler tutarlı bir seçim modeli izler.

- Katıştırılmış araç çubukları yalnızca belgeye özgü komutlar içerir, **Kaydet**gibi yaygın komutlar içermez.

- Bir gösterge yüzeyde görünebilir, ya gösterge veya filigran.

- Kullanıcı, paylaşılan Yazı Tipleri ve Renkler sayfası veya düzenleyiciye özgü bir Araçlar **> Seçenekleri** sayfasını kullanarak yazı tiplerinin/renklerin görünümünü özelleştirebilmelidir.

#### <a name="reports"></a>Reports

- Raporlar genellikle yalnızca bilgi dir ve Kaydet modeline katılmaz. Ancak, diğer ilgili bilgilere bağlantılar veya genişleyen ve daraltılmış bölümler gibi etkileşimiçerebilirler.

- Yüzeydeki komutların çoğu düğme değil köprüler olmalıdır.

- Düzen bir üstbilgi içermeli ve standart rapor düzeni yönergelerine uymalıdır.

#### <a name="dashboards"></a>Panolar

- Panoların kendileri bir etkileşim modeli yoktur, ancak çeşitli diğer araçlar sunmak için bir araç olarak hizmet verir.

- Kaydet modeline katılmaz.

- Kullanıcılar, düzenleyiciyi etkinleştirerek ve denetimleri sekmeleyerek veya standart mnemonikler kullanarak yalnızca klavye yi kullanarak denetimlerle etkileşim kurabilmeli.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Diyalog

### <a name="introduction"></a>Giriş
Visual Studio'daki iletişim kutuları genellikle kullanıcının çalışmasının ayrı bir birimini desteklemeli ve ardından görevden alınmalıdır.

Bir iletişim kutusuna ihtiyacınız olduğunu belirlediyseniz, tercih sırasına göre üç seçeneğiniz vardır:

1. Özelliklerinizi Visual Studio'daki paylaşılan iletişim dillerinden birine entegre edin.

2. Varolan benzer bir iletişim kutusunda bulunan bir deseni kullanarak kendi iletişim inizi oluşturun.

3. Etkileşim ve düzen yönergelerini izleyerek yeni bir iletişim kutusu oluşturun.

Bu bölümde, Visual Studio iş akışları içinde doğru iletişim deseni ve iletişim tasarımı için ortak kurallar nasıl seçilebileceği açıklanmaktadır.

### <a name="themes"></a>Temalar
Visual Studio'daki diyaloglar iki temel stilden birini izler:

#### <a name="standard-unthemed"></a>Standart (temalı olmayan)
İletişim kutularının çoğu standart yardımcı program iletişim leridir ve temalı olmalıdır. Ortak denetimleri yeniden şablona alma veya stilize edilmiş "modern" düğmeler veya denetimler oluşturmaya çalışmayın. Denetimler ve krom görünümü [iletişim kutuları için standart Windows Masaüstü etkileşim yönergeleriizleyin.](/windows/desktop/uxguide/win-dialog-box)

#### <a name="themed"></a>Temalı
Özel "imza" iletişim kutuları temalı olabilir. Temalı iletişim kutuları, stille ilişkili bazı özel etkileşim desenleri de içeren farklı bir görünüme sahiptir. İletişiminizin yalnızca bu gereksinimleri karşılıyorsa tema:

- İletişim, sık sık veya birçok kullanıcı (örneğin, **Yeni Proje** iletişim kutusu) tarafından görülecek ve kullanılacak yaygın bir deneyimdir.

- İletişim, önemli ürün markası öğeleri (örneğin, **Hesap Ayarları** iletişim kutusu) içerir.

- İletişim kutusu, diğer temalı iletişim iletişim lerini (örneğin, **Bağlı Hizmet Ekle** iletişim kutusu) içeren daha büyük bir akışın ayrılmaz bir parçası olarak görünür.

- İletişim, bir ürün sürümünün tanıtımında veya farklılaştırılmasında stratejik rol oynayan bir deneyimin önemli bir parçasıdır.

Temalı bir iletişim kutusu oluştururken, uygun ortam renklerini kullanın ve doğru düzeni ve etkileşim desenlerini izleyin. [(Bkz. Visual Studio için Düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>İletişim tasarımı
İyi tasarlanmış iletişim kutuları aşağıdaki öğeleri dikkate alır:

- Desteklenen kullanıcı görevi

- İletişim metni stili, dili ve terminolojisi

- Kontrol seçimi ve UI kuralları

- Görsel düzen belirtimi ve kontrol hizalaması

- Klavye erişimi

#### <a name="content-organization"></a>İçerik organizasyonu
Bu temel iletişim türleri arasındaki farkları göz önünde bulundurun:

- [Basit iletişim bilgileri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) tek bir modal pencerede denetimler sunar. Sunu, alan seçici veya simge çubuğu da dahil olmak üzere karmaşık denetim desenlerinin varyasyonlarını içerebilir.

- [Katmanlı iletişim kutuları,](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) tek bir deneme de birden çok denetim grubundan oluştuğunda ekran lı gayrimenkulden en iyi şekilde yararlanmak için kullanılır. İletişim kutusunun gruplandırmaları sekme denetimleri, gezinti listesi denetimleri veya düğmeler aracılığıyla "katmanlı" dır, böylece kullanıcı herhangi bir anda hangi grubu göreceğini seçebilir.

- [Sihirbazlar,](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) kullanıcıyı görevin tamamlanmasına yönelik mantıksal bir adım dizisi aracılığıyla yönlendirmek için yararlıdır. Bir dizi seçenek sıralı panellerde sunulur ve bazen önceki panelde yapılan bir seçime bağlı olarak farklı iş akışları ("dallar") sunulur.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Basit iletişim kutuları
Basit bir iletişim, tek bir modal penceredeki denetimlerin sunumudur. Bu sunu, alan seçici gibi karmaşık denetim desenlerinin varyasyonlarını içerebilir. Basit iletişim kutuları için, karmaşık denetim gruplandırmaları için gereken belirli düzeni ve standart genel düzeni izleyin.

![>Güçlü Ad Tuşu Oluştur, Visual Studio'daki basit bir iletişim ekidir.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Güçlü Ad Anahtarı Oluştur, Visual Studio'daki basit bir iletişim ekidir.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Katmanlı iletişim kutuları
Katmanlı iletişim kutularısek, panolar ve katıştılı ağaçlar içerir. Kullanıcı ui tek bir parça sunulan denetimlerin birden fazla grup olduğunda gayrimenkul maksimize etmek için kullanılır. Gruplandırmalar, kullanıcının aynı anda hangi gruplandırmayı göreceğini seçebilmeleri için katmanlıdır.

En basit durumda, gruplandırmalar arasında geçiş yapma mekanizması bir sekme denetimidir. Çeşitli alternatifler mevcuttur. En uygun stilin nasıl seçilebildiğini görmek için öncelik lendirme ve katmanlama ya da öncelik lendirmeye bakın.

**Araç &gt; Seçenekleri** iletişim kutusu, katıştırılmış bir ağaç kullanarak katmanlı bir iletişim kutusunun bir örneğidir:

![Araçlar > Seçenekleri, Visual Studio'daki katmanlı bir iletişim ekidir.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Araçlar > Seçenekleri, Visual Studio'daki katmanlı bir iletişim ekidir.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Sihirbaz
Sihirbazlar, bir görevin tamamlanmasında kullanıcıyı mantıksal bir adım dizisi ne yönlendiren için yararlıdır. Sıralı panellerde bir dizi seçenek sunulur ve kullanıcı nın bir sonraki adıma geçmeden önce her adımda devam etmesi gerekir. Yeterli varsayılan kullanılabilir olduğunda, **Bitiş** düğmesi etkinleştirilir.

 Modal sihirbazları görevleri için kullanılır:

- Kullanıcı seçimlerine bağlı olarak farklı yolların sunulduğu dallanma yı içerme

- Sonraki adımların önceki adım(lar)tan kullanıcı girişine bağlı olduğu adımlar arasındaki bağımlılıkları içerir

- UI'nin sunulan seçenekleri ve her adımdaki olası sonuçları açıklamak için kullanılması gerektiği yeterince karmaşıktır

- Herhangi bir değişiklik taahhüt edilmeden önce tümünün tamamlanması için bir dizi adım gerektiren işlemsel

### <a name="common-conventions"></a>Ortak sözleşmeler
İletişim kur'an-ı eriştilerinizle en iyi tasarım ve işlevselliği elde etmek için, iletişim boyutu, konum, standartlar, denetim yapılandırması ve hizalama, Kullanıcı Arama Ekibi metni, başlık çubukları, denetim düğmeleri ve erişim tuşları ile ilgili bu kuralları izleyin.

Düzene özgü yönergeler [için Visual Studio için Düzen'e](../../extensibility/ux-guidelines/layout-for-visual-studio.md)bakın.

#### <a name="size"></a>Boyut
Diyaloglar en az 1024x768 ekran çözünürlüğüne sığmalı ve ilk iletişim boyutu 900x700 pikseli geçmemelidir. İletişim iletişimleri yeniden boyutlandırılabilir, ancak bir gereklilik değildir.

Yeniden boyutlandırılabilir iletişim için iki öneri vardır:

1. Minimum boyut, kırpma olmadan denetim kümesi için optimize edecek ve makul yerelleştirme büyümesini karşılayacak şekilde ayarlanacak iletişim kutusu için tanımlanmıştır.

2. Kullanıcı ölçeğinde boyutun oturumdan oturuma devam etmesi. Örneğin, kullanıcı bir iletişim kutusunu %150'ye ölçeklendirmişse, iletişim kutusunun sonraki bir lansmanı %150 olarak görüntülenir.

#### <a name="position"></a>Konum
İlk başlatmada IDE içinde ortalanmış diyaloglar görünmelidir. Yeniden boyutlandırılamayan iletişim lerin son konumunun kalıcı olması gerekmez, bu nedenle sonraki başlatışlarda ortalanmış olarak görünürler.

Yeniden boyutlandırılabilir iletişim için boyut sonraki başlatışlarda kalıcı olmalıdır. Yeniden boyutlandırılabilir modal iletişim için pozisyonun kalıcı olması gerekmez. Bunları IDE içinde ortalanmış olarak görüntülemek, kullanıcının görüntü yapılandırması değiştiğinde iletişim kutusunun öngörülemeyen veya kullanılamaz bir konumda görüntülenme olasılığını önler.

Yeniden konumlandırılabilen modeless iletişim kutuları için, iletişim kutusu daha büyük bir iş akışının ayrılmaz bir parçası olarak sık sık kullanılabilebileceğinden, kullanıcının konumu sonraki başlatışlarda tutulmalıdır.

İletişim iletişimlerinin diğer iletişim leri üretmesi gerektiğinde, en üstteki iletişim kutusu üstten sağa ve aşağıya doğru basamaklanmalıdır, böylece kullanıcıya yeni bir yere yön ettikleri açık olur.

#### <a name="modality"></a>Modalite
Modal olmak, kullanıcıların devam etmeden önce iletişimi tamamlamaları veya iptal etmesi gerektiği anlamına gelir. Modal iletişim kutuları kullanıcının ortamın diğer bölümleriyle etkileşimkurmasını engellediklerinden, özelliğinizin görev akışı bunları mümkün olduğunca dikkatli kullanmalıdır. Bir modal işlemi gerektiğinde, Visual Studio özelliklerinizi entegre edebilirsiniz paylaşılan iletişim bir dizi vardır. Yeni bir iletişim kutusu oluşturmanız gerekiyorsa, benzer işlevselliği olan varolan bir iletişim kutusunun etkileşim deseni izleyin.

Kullanıcıların yeni kod yazarken **Bul** ve **Değiştir** gibi aynı anda iki etkinlik gerçekleştirmesi gerektiğinde, iletişim kutusu modsuz olmalıdır, böylece kullanıcı aralarında kolayca geçiş yapabilir. Visual Studio genellikle bu tür düzenleyici destekli bağlantılı görev için araç pencerelerini kullanır.

#### <a name="control-configuration"></a>Yapılandırmayı denetleme
Visual Studio'da aynı şeyi gerçekleştiren varolan denetim yapılandırmalarıyla tutarlı olun.

#### <a name="title-bars"></a>Başlık çubukları

- Başlık çubuğundaki metin, onu başlatan komutun adını yansıtmalıdır.

- İletişim başlık çubuklarında simge kullanılmamalıdır. Sistemin gerektirdiği durumlarda Visual Studio logosunu kullanın.

- İletişim düğmeleri en aza indirmek veya en üst düzeye çıkarmamalıdır.

- Başlık çubuğundaki yardım düğmeleri küçümsülmüş. Bunları yeni iletişim kutularına eklemeyin. Var olduklarında, görevle kavramsal olarak alakalı bir Yardım konusunu başlatmaları gerekir.

  ![Visual Studio iletişim kutularındaki başlık çubukları için kılavuz özellikleri](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Visual Studio iletişim kutularındaki başlık çubukları için kılavuz özellikleri

#### <a name="control-buttons"></a>Kontrol düğmeleri
Genel olarak, **Tamam**, **İptal**ve **Yardım** düğmeleri iletişimin sağ alt köşesinde yatay olarak düzenlenmelidir. Bir iletişim kutusunun alt kısmında denetim düğmeleriyle görsel karışıklık oluşturan birkaç başka düğme varsa, alternatif dikey yığına izin verilir.

![Visual Studio iletişim kutularında denetim düğmeleri için kabul edilebilir yapılandırmalar](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Visual Studio iletişim kutularında denetim düğmeleri için kabul edilebilir yapılandırmalar

İletişim kutusu varsayılan denetim düğmesi içermelidir. Varsayılan olarak kullanılacak en iyi komutu belirlemek için aşağıdaki seçeneklerden birini seçin (öncelik sırasına göre listelenmiştir):

- Varsayılan olarak en güvenli ve en güvenli komutu seçin. Bu, veri kaybını önlemek ve istenmeyen sistem erişimini önlemek için büyük olasılıkla komutu seçmek anlamına gelir.

- Veri kaybı ve güvenlik etkendeğilse, kolaylık temel inanılarak varsayılan komutu seçin. İletişim sık veya yinelenen görevleri desteklediğinde, varsayılan olarak en olası komutun kullanıcının iş akışını iyileştireceği gibi.

Varsayılan komut için kalıcı olarak yıkıcı bir eylem seçmekten kaçının. Böyle bir komut varsa, varsayılan olarak daha güvenli bir komut seçin.

#### <a name="access-keys"></a>Erişim tuşları
**Ok**, **İptal**veya **Yardım** düğmeleri için erişim tuşlarını kullanmayın. Bu düğmeler varsayılan olarak kısayol tuşlarına eşlenir:

| Düğme adı | Klavye kısayolu |
| --- | --- |
| Tamam | Enter |
| İptal | Esc |
| Yardım | F1 |

#### <a name="imagery"></a>Görüntü
Görüntüleri iletişim kutularında dikkatli kullanın. Yalnızca alanı kullanmak için iletişim kutularında büyük simgeler kullanmayın. Görüntüleri yalnızca uyarı simgeleri veya durum animasyonları gibi iletiyi kullanıcıya iletmenin önemli bir parçasıysa kullanın.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Öncelik lendirme ve katmanlama

#### <a name="prioritizing-your-ui"></a>UI'nize öncelik
Belirli u-u-u u ie öğelerini ön plana çıkarmak ve daha gelişmiş davranış ve seçenekleri (belirsiz komutlar dahil) iletişim kutularına yerleştirmek gerekebilir. İletişim kutusu gösterildiğinde kullanıcı aranızda bir metin etiketiyle kullanıcı arabirimi'nde varsayılan olarak görünür hale getirerek, yaygın olarak kullanılan işlevleri ön plana çıkar.

#### <a name="layering-your-ui"></a>UI'nizi katmanlama
Bir iletişim kutusunun gerekli olduğunu belirlediyseniz, ancak kullanıcıya sunmak istediğiniz ilgili işlevsellik basit bir iletişim kutusunda görüntülenebileceklerin ötesine geçiyorsa, kullanıcı ia'nızı katmanlamanız gerekir. Visual Studio'nun kullandığı en yaygın katmanlama yöntemleri sekmeler ve koridorlar veya panolardır. Bazı durumlarda, genişletilebilen ve daraltlanabilen bölgeler uygun olabilir. Uyarlanabilir UI genellikle Visual Studio'da önerilmez.

Sekme benzeri denetimler aracılığıyla Farklı UI katmanlama yöntemlerinin avantajları ve dezavantajları vardır. Durumunuza uygun bir katmanlama tekniği seçtiğinizden emin olmak için aşağıdaki listeyi gözden geçirin.

##### <a name="tabbing"></a>Sekme

| Anahtarlama mekanizması | Avantajları ve uygun kullanımı | Dezavantajları ve uygunsuz kullanım |
| --- | --- | --- |
| Sekme denetimi | İletişim sayfalarını mantıksal olarak ilgili kümelere gruplandırma<br /><br />İletişim kutusundaki ilgili denetimlerin beşten az (veya iletişim günlüğüne bir satıra sığan sekme sayısı) sayfaları için yararlıdır<br /><br />Sekme etiketleri kısa olmalıdır: içeriği kolayca tanımlayabilen bir veya iki sözcük<br /><br />Ortak bir sistem iletişim stili<br /><br />Örnek: **Dosya &gt; Gezgini Öğe Özellikleri** | Açıklayıcı kısa etiketler yapmak zor olabilir<br /><br />Genellikle bir iletişim kutusunda beş sekmeyi aşmaz<br /><br />Bir satır için çok fazla sekmeniz varsa uygunsuz (alternatif katmanlama tekniği kullanın)<br /><br />Genişletilebilir değil |
| Kenar çubuğu gezintisi | Sekmelerden daha fazla kategoribarındırabilen basit anahtarlama aygıtı<br /><br />Düz kategori listesi (hiyerarşi yok)<br /><br />Genişletilebilir<br /><br />Örnek: **Özelleştir... Komut &gt; Ekle** | Üçten az grup varsa yatay alanın iyi kullanılmaması<br /><br />Görev açılır bir şekilde daha uygun olabilir |
| Ağaç denetimi | Sınırsız kategorilere izin verir<br /><br />Kategorilerin gruplandırmave/veya hiyerarşisine izin verir<br /><br />Genişletilebilir<br /><br />Örnek: ** &gt; Araç Seçenekleri** | Ağır iç içe olan hiyerarşiler aşırı yatay kaydırmaya neden olabilir<br /><br />Visual Studio ağaç görünümleri bir bolluk vardır |
| Sihirbazı | Görev tabanlı, sıralı adımlarda kullanıcıya rehberlik ederek görev tamamlamaya yardımcı olur: sihirbaz üst düzey bir görevi temsil eder ve tek tek paneller genel görevi gerçekleştirmek için gereken alt görevleri temsil eder<br /><br />Görev Ui sınırlarını aştığında yararlıdır, kullanıcı görevi tamamlamak için birden çok düzenleyici ve araç penceresi kullanmak zorunda kaldığında<br /><br />Görev dallanma gerektirdiğinde yararlı<br /><br />Görev adımlar arasındaki bağımlılıkları içerdiğinde yararlı<br /><br />Farklı benzer iletişim kutularının sayısını azaltmak için tek bir iletişim kutusunda bir karar çatalı olan birkaç benzer görev sunulabilirse yararlıdır | Sıralı iş akışı gerektirmeyen herhangi bir görev için uygun olmayan<br /><br />Kullanıcılar çok fazla adımla bir sihirbaz tarafından bunalmış ve kafası karışabilir<br /><br />Sihirbazlar doğal olarak sınırlı ekran gayrimenkul var |

##### <a name="hallways-or-dashboards"></a>Koridorlar veya panolar
Koridorlar ve panolar, diğer iletişim ve pencerelere başlatma noktası görevi veren iletişim veya panellerdir. İyi tasarlanmış "koridor" hemen yalnızca en yaygın seçenekleri, komutları ve ayarları ortaya çıkararak kullanıcının ortak görevleri kolayca yerine getirmesini sağlar. Gerçek bir koridor arkalarındaki odalara erişmek için kapı sağlar gibi, burada daha az yaygın UI ayrı "odalar" (genellikle diğer diyaloglar) ana koridordan erişilebilir ilgili işlevsellik içine toplanır.

Alternatif olarak, daha az yaygın olan işlevleri ayrı konumlara yeniden düzenlemek yerine tek bir koleksiyonda kullanılabilen tüm kullanılabilir işlevleri sunan bir ui yalnızca bir panodur.

![Outlook'ta ek ui açığa çıkarmak için koridor kavramı](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Outlook'ta ek ui açığa çıkarmak için koridor kavramı

##### <a name="adaptive-ui"></a>Uyarlanabilir UI
Kullanıcı Arabirimi'ni kullanıma veya kullanıcının kendi kendine bildirilen deneyimine göre gösterme veya gizleme, diğer bölümleri gizlerken gerekli Kullanıcı Arabirimi'ni sunmanın başka bir yoludur. Bu Visual Studio'da önerilmez, çünkü Kullanıcı Arabirimi'ni ne zaman göstereceğine veya gizleyeceğine karar vermek için algoritmalar zor olabilir ve kurallar bazı servis talepleri için her zaman yanlış olacaktır.

## <a name="projects"></a><a name="BKMK_Projects"></a>Proje

### <a name="projects-in-the-solution-explorer"></a>Çözüm Gezgini'ndeki Projeler
Çoğu proje referans tabanlı, dizin tabanlı veya karışık olarak sınıflandırılır. Çözüm Gezgini'nde üç proje türü de aynı anda desteklenir. Projelerle çalışmada kullanıcı deneyiminin kökü bu pencereiçinde yer alır. Farklı proje düğümleri referans, dizin veya karma mod türü projeler olsa da, projeye özgü kullanıcı desenlerine ayrılmadan önce başlangıç noktası olarak uygulanması gereken ortak bir etkileşim deseni vardır.

Projeler her zaman:

- Proje içeriğini düzenlemek için proje klasörleri ekleme özelliğini destekleme

- Proje kalıcılığı için tutarlı bir model koruma

Projeler ayrıca, şular için tutarlı etkileşim modellerini de korumalıdır:

- Proje öğelerini kaldırma

- Belgeleri kaydetme

- Proje özelliği düzenleme

- Projeyi alternatif görünümde düzenleme

- Sürükle ve bırak işlemleri

### <a name="drag-and-drop-interaction-model"></a>Sürükle ve bırak etkileşim modeli
Projeler genellikle kendilerini referans tabanlı (yalnızca depolamadaki proje öğelerine yapılan başvuruları devam ettirebilen), dizin tabanlı (yalnızca proje hiyerarşisi içinde fiziksel olarak depolanan proje öğelerini devam ettirebilen) veya karışık (başvuruları devam ettirebilen) olarak sınıflandırın veya fiziksel öğeler). IDE, **Çözüm Gezgini**içinde aynı anda üç proje türünü de barındırır.

Sürükle ve bırak perspektifinden, **Çözüm Gezgini'ndeki**her proje türü için aşağıdaki özellikler uygulanmalıdır:

- **Referans tabanlı proje:** Önemli nokta, projenin depolama daki bir öğeye başvuruda bulunduğudur. Başvuru tabanlı bir proje bir taşıma işlemi için kaynak görevi gördüğünde, yalnızca maddeye yapılan başvuruyu projeden kaldırması gerekir. Öğe aslında sabit diskten silinmemelidir. Başvuru tabanlı bir proje bir taşıma (veya kopyalama) işlemi için hedef görevi gördüğünde, öğenin özel bir kopyasını oluşturmadan özgün kaynak öğeye bir başvuru eklemesi gerekir.

- **Dizin tabanlı proje:** Sürükle ve bırak açısından, proje bir başvuru yerine fiziksel öğenin etrafında sürüklüyor. Dizin tabanlı bir proje bir taşıma işlemi için kaynak görevi gördüğünde, fiziksel öğeyi sabit diskten silmenin yanı sıra projeden kaldırması gerekir. Dizin tabanlı bir proje bir taşıma (veya kopyalama) işlemi için hedef görevi gördüğünde, hedef konumundaki kaynak öğenin bir kopyasını yapmalıdır.

- **Karma hedef projesi:** Sürükle ve bırak açısından bakıldığında, bu tür bir projenin davranışı sürüklenen öğenin doğasına (depolamadaki bir maddeye veya maddenin kendisine bir başvuru) dayanır. Başvurular ve fiziksel öğeler için doğru davranış yukarıda açıklanmıştır.

**Çözüm Gezgini'nde**yalnızca bir proje türü olsaydı, sürükle ve bırak işlemleri basit olurdu. Her proje sistemi kendi sürükle ve bırak davranışını tanımlama yeteneğine sahip olduğundan, öngörülebilir bir kullanıcı deneyimi sağlamak için belirli yönergeler (Windows Gezgini sürükle ve bırak davranışına dayalı olarak) izlenmelidir:

- **Çözüm Gezgini'nde** değiştirilmemiş bir sürükleme işlemi (Ctrl veya Shift tuşları aşağıda tutulduğunda) bir taşıma işlemiyle sonuçlanmalıdır.

- Shift-drag işlemi de bir hareket işlemi neden olmalıdır.

- Ctrl-drag işlemi bir kopyalama işlemi ile sonuçlanmalıdır.

- Başvuru tabanlı ve karma proje sistemleri, kaynak öğeye bağlantı (veya başvuru) ekleme kavramını destekler. Bu projeler sürükle ve bırak işleminin hedefi olduğunda **(Ctrl + Shift** tutulduğunda), projeye eklenen öğeye bir başvuru yla sonuçlanmalıdır

Tüm sürükle ve bırak işlemleri, başvuru tabanlı, dizin tabanlı ve karma projelerin birleşimleri arasında mantıklı değildir. Özellikle, kaynak dizin tabanlı proje, taşıma tamamlandıktan sonra kaynak öğeyi silmek zorunda kalacak, çünkü dizin tabanlı kaynak proje ve başvuru tabanlı hedef proje arasında bir taşıma işlemi ne izin vermek gibi davranmak sorunludur. Hedef başvuru tabanlı proje daha sonra silinmiş bir öğeye bir başvuru ile sona erer.

Hedef başvuru tabanlı proje kaynak öğenin bağımsız bir kopyasını yapmamalıdır, çünkü bu tür projeler arasında bir kopyalama çalışmasına izin vermek gibi davranmak da yanıltıcıdır. Benzer şekilde, dizin tabanlı bir proje başvuruları kalıcı olarak süremediği için Ctrl + Shift'in dizin tabanlı hedef projeye sürüklemesine izin verilmemelidir. Sürükle ve bırak işleminin desteklenmediğini zedele, IDE damlaya izin vermeli ve kullanıcıya damla yanmayacak imleci göstermelidir (aşağıdaki işaretçi tablosunda gösterilir).

Sürükle ve bırak davranışını düzgün bir şekilde uygulamak için sürüklenin kaynak projesinin doğasını hedef projeye iletmesi gerekir. (Örneğin, başvuru veya dizin tabanlı mı?) Bu bilgiler, kaynak tarafından sunulan pano biçimi yle gösterilir. Sürükleme (veya pano kopyalama işleminin kaynağı olarak) projenin `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` referans tabanlı mı yoksa dizin tabanlı mı olduğuna bağlı olarak, projenin sırasıyla veya sırasıyla sunması gerekir. Bu biçimlerin her ikisi de, dosya adı olmak `CF_HDROP` `NULL` yerine dizeler listelerinin `Projref` çift olarak sonlandırılan dizeleri (döndürüldİğİ `IVsSolution::GetProjrefOfItem` veya `::GetProjrefOfProject` uygun olduğu şekilde) olması dışında Windows biçimine benzer veri içeriğine sahiptir.

Bir damla (veya pano yapıştırma işleminin) hedefi olarak, bir proje her ikisini de `CF_VSREFPROJECTITEMS` kabul etmelidir ve `CF_VSSTGPROJECTITEMS`sürükle-bırak işleminin tam olarak işlenmesi hedef projenin ve kaynak projenin niteliğine bağlı olarak değişir. Kaynak proje, doğasını teklif edip `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS`sunmadığı veya . Bırakmanın hedefi kendi doğasını anlar ve böylece bir taşımanın, kopyalamanın veya bağlantının gerçekleştirilip gerçekleştirilmeyeceğine karar vermek için yeterli bilgiye sahiptir. Kullanıcı ayrıca Ctrl, Shift veya hem Ctrl hem de Shift tuşlarına basarak hangi sürükle ve bırak işleminin yapılması gerektiğini de değiştirir. Bırakma hedefinin hangi operasyonun kendi yöntemleri `DragEnter` nde `DragOver` ve yöntemlerinde önceden gerçekleştirileceğini doğru bir şekilde belirtmesi önemlidir. **Çözüm Gezgini,** kaynak proje ile hedef projenin aynı proje olup olmadığını otomatik olarak bilir.

Proje öğelerini Visual Studio örnekleri arasında sürüklemek (örneğin, devenv.exe'nin bir örneğinden diğerine) özellikle desteklenmez. **Çözüm Gezgini** de bunu doğrudan devre dışı kılabilir.

Kullanıcı her zaman bir öğe seçerek, hedef konuma sürükleyerek ve öğe düşürülmeden önce aşağıdaki fare işaretçilerinden hangisinin göründüğünü gözlemleyerek sürükle ve bırak işleminin etkisini belirleyebilmeli:

| Fare işaretçisi | Komut | Açıklama |
| :---: | --- | --- |
| ![Fare "damla yok" simgesi](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Damla yok | Öğe belirtilen konuma bırakılamaz. |
| ![Fare "kopyala" simgesi](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Kopyala | Öğe hedef konuma kopyalanır. |
| ![Fare "taşı" simgesi](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Taşı | Öğe hedef konuma taşınır. |
| ![Fare "referans ekle" simgesi](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Başvuru ekleme | Seçili öğeye bir başvuru hedef konuma eklenir. |

#### <a name="reference-based-projects"></a>Referans tabanlı projeler
 Aşağıdaki tablo, kaynak öğenin yapısına ve başvurulan tabanlı hedef projeler için basıldığında değiştirici tuşlarına göre gerçekleştirilmesi gereken sürükle ve bırak (yanı sıra kesme/kopyalama/yapıştırma) işlemlerini özetlemektedir:

| Değiştirici | Kategori | Kaynak öğe: Başvuru/Bağlantı | Kaynak öğe: Fiziksel öğe`CF_HDROP`veya dosya sistemi ( ) |
| --- | --- | --- | --- |
| Değiştirici yok | Eylem | Taşı | Bağlantı |
| Değiştirici yok | Hedef | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Değiştirici yok | Kaynak | Özgün öğeye başvuruyaz | Özgün öğeyi korur |
| Değiştirici yok | Sonuç | `DROPEFFECT_MOVE`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | `DROPEFFECT_LINK`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır |
| Shift+Sürükleme | Eylem | Taşı | Damla yok |
| Shift+Sürükleme | Hedef | Özgün öğeye başvuru ekler | Damla yok |
| Shift+Sürükleme | Kaynak | Özgün öğeye başvuruyaz | Damla yok |
| Shift+Sürükleme | Sonuç | `DROPEFFECT_MOVE`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | Damla yok |
| Ctrl+Sürükleme | Eylem | Kopyala | Damla yok |
| Ctrl+Sürükleme | Hedef | Özgün öğeye başvuru ekler | Damla yok |
| Ctrl+Sürükleme | Kaynak | Özgün öğeye başvurututar | Damla yok |
| Ctrl+Sürükleme | Sonuç | `DROPEFFECT_COPY`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | Damla yok |
| Ctrl+Shift+Sürükleme | Eylem | Bağlantı | Bağlantı |
| Ctrl+Shift+Sürükleme | Hedef | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Ctrl+Shift+Sürükleme | Kaynak | Özgün öğeye başvurututar | Özgün öğeyi korur |
| Ctrl+Shift+Sürükleme | Sonuç | `DROPEFFECT_LINK`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | `DROPEFFECT_LINK`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır |
| Ctrl+Shift+Sürükleme | Not | Windows Gezgini'ndeki kısayollar için sürükle ve bırak davranışıyla aynıdır. ||
| Kes/Yapıştır | Eylem | Taşı | Bağlantı |
| Kes/Yapıştır | Hedef | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Kes/Yapıştır | Kaynak | Özgün öğeye başvurututar|Özgün öğeyi korur |
| Kes/Yapıştır | Sonuç | Öğe depolamada orijinal konumda kalır | Öğe depolamada orijinal konumda kalır |
| Kopyala/Yapıştır | Eylem | Kopyala | Bağlantı |
| Kopyala/Yapıştır | Kaynak | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Kopyala/Yapıştır | Sonuç | Özgün öğeye başvurututar | Özgün öğeyi korur |
| Kopyala/Yapıştır | Eylem | Öğe depolamada orijinal konumda kalır | Öğe depolamada orijinal konumda kalır |

#### <a name="directory-based-projects"></a>Dizin tabanlı projeler
Aşağıdaki tablo, kaynak öğenin yapısına ve dizin tabanlı hedef projeler için basıldığında değiştirici tuşlarına göre yapılması gereken sürükle ve bırak (yanı sıra kesme/kopyalama/yapıştırma) işlemlerini özetlemektedir:

| Değiştirici | Kategori | Kaynak öğe: Başvuru/Bağlantı | Kaynak öğe: Fiziksel öğe`CF_HDROP`veya dosya sistemi ( ) |
|-----------------|----------| - | - |
| Değiştirici yok | Eylem | Taşı | Taşı |
| Değiştirici yok | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Değiştirici yok | Kaynak | Özgün öğeye başvuruyaz | Özgün öğeye başvuruyaz |
| Shift+Sürükleme | Eylem | Taşı | Taşı |
| Shift+Sürükleme | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Shift+Sürükleme | Kaynak | Özgün öğeye başvuruyaz | Öğeyi özgün konumdan siler |
| Shift+Sürükleme | Sonuç | `DROPEFFECT_MOVE`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | `DROPEFFECT_MOVE`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır |
| Ctrl+Sürükleme | Eylem | Kopyala | Kopyala |
| Ctrl+Sürükleme | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Ctrl+Sürükleme | Kaynak | Özgün öğeye başvurututar | Özgün öğeye başvurututar |
| Ctrl+Sürükleme | Sonuç | `DROPEFFECT_COPY`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | `DROPEFFECT_COPY`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır |
| Ctrl+Shift+Sürükleme | | Damla yok | Damla yok |
| Kes/Yapıştır | Eylem | Taşı | Taşı |
| Kes/Yapıştır | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Kes/Yapıştır | Kaynak | Özgün öğeye başvuruyaz | Öğeyi özgün konumdan siler |
| Kes/Yapıştır | Sonuç | Öğe depolamada orijinal konumda kalır | Öğe depolamadaki orijinal konumdan silinir |
| Kopyala/Yapıştır | Eylem | Kopyala | Kopyala |
| Kopyala/Yapıştır | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Kopyala/Yapıştır | Kaynak | Özgün öğeyi korur | Özgün öğeyi korur |
| Kopyala/Yapıştır | Sonuç | Öğe depolamada orijinal konumda kalır | Öğe orijinal konum ins depolama kalır |

#### <a name="mixed-target-projects"></a>Karma hedef projeler
Aşağıdaki tablo, kaynak öğenin yapısına ve karışık hedefli projeler için basıldığında değiştirici tuşlarına göre yapılması gereken sürükle ve bırak (yanı sıra kesme/kopyalama/yapıştırma) işlemlerini özetlemektedir:

| Değiştirici | Kategori | Kaynak öğe: Başvuru/Bağlantı | Kaynak öğe: Fiziksel öğe`CF_HDROP`veya dosya sistemi ( ) |
| --- | --- | --- | --- |
| Değiştirici yok | Eylem | Taşı | Taşı |
| Değiştirici yok | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Değiştirici yok | Kaynak | Özgün öğeye başvuruyaz | Özgün öğeye başvuruyaz |
| Değiştirici yok | Sonuç | `DROPEFFECT_ MOVE`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | `DROPEFFECT_ MOVE`eylem olarak döndürülür `::Drop` ve öğe depolama daki orijinal konumdan silinir |
| Shift+Sürükleme | Eylem | Taşı | Taşı |
| Shift+Sürükleme | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Shift+Sürükleme | Kaynak | Özgün öğeye başvuruyaz | Öğeyi özgün konumdan siler |
| Shift+Sürükleme | Sonuç | `DROPEFFECT_ MOVE`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | `DROPEFFECT_ MOVE`eylem olarak döndürülür `::Drop` ve öğe depolama daki orijinal konumdan silinir |
| Ctrl+Sürükleme | Eylem | Kopyala | Kopyala |
| Ctrl+Sürükleme | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Ctrl+Sürükleme | Kaynak | Özgün öğeye başvurututar | Özgün öğeyi korur |
| Ctrl+Sürükleme | Sonuç | `DROPEFFECT_ COPY`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | `DROPEFFECT_ COPY`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır |
| Ctrl+Shift+Sürükleme | Eylem | Bağlantı | Bağlantı |
| Ctrl+Shift+Sürükleme | Hedef | Özgün öğeye başvuru ekler | Özgün kaynak öğeye başvuru ekler |
| Ctrl+Shift+Sürükleme | Kaynak | Özgün öğeye başvurututar | Özgün öğeyi korur |
| Ctrl+Shift+Sürükleme | Sonuç | `DROPEFFECT_ LINK`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır | `DROPEFFECT_ LINK`hareket olarak döndürülür `::Drop` ve öğe depolama orijinal konumda kalır |
| Kes/Yapıştır | Eylem | Taşı | Taşı |
| Kes/Yapıştır | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Kes/Yapıştır | Kaynak | Özgün öğeye başvuruyaz | Öğeyi özgün konumdan siler |
| Kes/Yapıştır | Sonuç | Öğe depolamada orijinal konumda kalır | Öğe depolamadaki orijinal konumdan silinir |
| Kopyala/Yapıştır | Eylem | Kopyala | Kopyala |
| Kopyala/Yapıştır | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Kopyala/Yapıştır | Kaynak | Özgün öğeyi korur | Özgün öğeyi korur |
| Kopyala/Yapıştır | Sonuç | Öğe depolamada orijinal konumda kalır | Öğe depolamada orijinal konumda kalır |

**Çözüm Gezgini'nde**sürükleme uygulanırken bu ayrıntılar göz önünde bulundurulmalıdır:

- Birden çok seçim senaryosu için tasarım.

- Dosya adları (tam yol) hedef proje genelinde benzersiz olmalıdır veya açılan adada izin verilmemelidir.

- Klasör adları, düşürüldükleri düzeyde benzersiz (büyük/küçük harf duyarsız) olmalıdır.

- Sürükleme sırasında açık veya kapalı olan dosyalar arasında davranış farklılıkları vardır (yukarıdaki senaryolarda belirtilmez).

- Üst düzey dosyalar klasörlerdeki dosyalardan biraz farklı şekilde davranın.

Dikkat edilmesi gereken bir diğer konu da, açık tasarımcıları veya editörleri olan öğelerdeki taşıma işlemlerini nasıl işleyeceğinizdir. Beklenen davranış aşağıdaki gibidir (bu tüm proje türleri için geçerlidir):

1. Açık düzenleyicide/tasarımcıda kaydedilmemiş değişiklikler yoksa, düzenleyici/tasarımcı penceresi sessizce kapatılmalıdır.

2. Açık düzenleyici/tasarımcıda kaydedilmemiş değişiklikler varsa, sürüklenin kaynağı damlanın gerçekleşmesini beklemeli ve ardından pencereyi aşağıdaki gibi bir istemle kapatmadan önce kullanıcıdan açık belgelerdeki kaydedilmemiş değişiklikleri kaydetmesini istemelidir:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Bu, kullanıcıya hedef kopyalarını yapmadan önce devam eden çalışmaları kaydetme fırsatı verir. Bu işleme `IVsHierarchyDropDataSource2::OnBeforeDropNotify` etkinleştirmek için yeni bir yöntem eklendi.

Hedef daha sonra öğenin durumunu depolama alanında olduğu gibi kopyalar (kullanıcı **Hayır'ı**seçerse düzenleyicideki kaydedilmemiş değişiklikler dahil değildir). Hedef kopyalamaişlemini tamamladıktan sonra `IVsHierarchyDropDataSource::Drop`(in), kaynağa taşıma işleminin silme işleminin `IVsHierarchyDropDataSource::OnDropNotify`(içinde) silinen kısmını tamamlama fırsatı verilir.

Kaydedilmemiş değişiklikleri olan tüm editörler açık bırakılmalıdır. Kaydedilmemiş değişiklikleri olan bu belgeler için, bu, taşıma işleminin kopya bölümünün gerçekleştirileceği, ancak silme bölümünün iptal olacağı anlamına gelir. Kullanıcı **Hayır'ı**seçtiğinde birden çok seçim senaryosunda, kaydedilmemiş değişiklikleri olan bu belgeler kapatılmamalı veya kaldırılmamalıdır, ancak kaydedilmemiş değişiklikleri olmayanlar kapatılı ve kaldırılmalıdır.