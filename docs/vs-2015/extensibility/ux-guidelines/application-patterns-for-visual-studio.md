---
title: Uygulama Desenleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af70b191e4b9061d08acdc7f76ade843dee41709
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114134"
---
# <a name="application-patterns-for-visual-studio"></a>Visual Studio İçin Uygulama Desenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Pencere etkileşimleri

### <a name="overview"></a>Genel Bakış
 Visual Studio 'da kullanılan iki ana pencere türü belge düzenleyicilerdir ve araç pencereleri. Nadir, ancak mümkün olan büyük, geçici olmayan iletişim kutulardır. Bunlar kabukta kalıcı olsalar da, desenleri temelde farklıdır. Bu konu belge pencereleri, araç pencereleri ve kalıcı iletişim kutuları arasındaki farkı ele alır. İletişim [kutularında](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)kalıcı iletişim kutusu desenleri ele alınmıştır.

### <a name="comparing-window-usage-patterns"></a>Pencere kullanım düzenlerini karşılaştırma
 **Belge pencereleri** neredeyse her zaman belge kutusu içinde görüntülenir. Bu, belge düzenleyicisine bir "Orta aşama" verir ve ek araç pencerelerini etrafında düzenlemenizi sağlar.

 Bir **araç penceresi** çoğunlukla, IDE 'nin kenarına karşı görünür, gizli veya otomatik gizli olabilen ayrı, daha küçük bir pencere olarak görüntülenir. Ancak, bazı durumlarda, penceredeki **Pencere/yerleştirme** özelliğinin denetimi geri alınarak, bazen belge kutusu içinde sunulur. Bu, yaygın bir tasarım kararı elde etmeksizin daha gerçekçi bir şekilde sonuçlanır: Visual Studio ile tümleştirmeye çalıştığınızda, özelliğinizdeki bir araç penceresi mi yoksa bir belge penceresi mi görüntülemesi gerektiğine karar vermelisiniz.

 **Kalıcı Iletişimler** Visual Studio 'da teşvik edilmez. Büyük bir ölçüde, tanım – kayan araç pencereleri ve bu şekilde uygulanmalıdır. Kabuk tarafına yerleştirilmiş normal bir araç penceresinin boyutunun çok sınırlandırabileceği durumlarda kalıcı iletişim kutularına izin verilir. Ayrıca, kullanıcının iletişim kutusunu ikincil bir monitöre taşıyabileceği durumlarda bunlara izin verilir.

 İhtiyaç duyduğunuz kapsayıcı türünü dikkatle düşünün. UI tasarımıyla ilgili yaygın kullanım deseninin konuları aşağıdaki tabloda verilmiştir.

||Belge penceresi|Araç penceresi|Kalıcı olmayan iletişim kutusu|
|-|---------------------|-----------------|---------------------|
|**Position** (Pozisyon)|Her zaman belge içinde konumlandırılır ve IDE 'nin kenarlarını sabitlemez. Ana kabuktan ayrı olarak kayan olması için "çekiliyor" olabilir.|Genellikle IDE 'nin kenarları etrafında yerleştirilmiş, ancak kayan, otomatik gizli (ayrılmış) veya belge kutusu içine yerleştirilmiş olacak şekilde özelleştirilebilir.|IDE 'den ayrı olan büyük kayan pencere.|
|**Modeli Yürüt**|*Gecikmeli tamamlama*<br /><br /> Verileri bir belgeye kaydetmek için kullanıcının dosyayı vermesi/kaydetmesi, farklı Kaydet veya Tümünü Kaydet komutunu vermesi gerekir. Belge penceresi, "dirbağlı" olarak bulunan ve Kaydet komutlarından birine taahhüt edilen verilerin kavramıdır. Bir belge penceresi kapatılırken tüm içerikler diske kaydedilir veya kaybedilir.|*Anında yürütme*<br /><br /> Hiçbir kaydetme modeli yok. Bir dosyayı düzenlemede yardımcı olan Inspector araç pencereleri için, dosyanın etkin düzenleyici veya tasarımcı 'da açık olması ve düzenleyici ya da tasarımcı kaydetme 'nin sahibi olması gerekir.|*Gecikmeli veya anında yürütme*<br /><br /> Genellikle, büyük bir kalıcı olmayan iletişim kutusu, değişiklikleri yürütmek için bir eylem gerektirir ve iletişim kutusu oturumunda yapılan değişiklikleri geri kaydeden bir "Iptal" işlemine izin verir.  Bu, bir araç penceresinden kalıcı olmayan bir iletişim kutusunu bu şekilde fark eden, Windows her zaman hemen bir yürütme modeline sahiptir.|
|**Görünürlük**|*Aç/oluştur (dosya) ve Kapat*<br /><br /> Belge pencerelerini açmak, mevcut bir belge açılarak ya da yeni bir belge oluşturmak için şablon kullanılarak yapılır. "Open \<specific editor> " komutu yoktur.|*Gizleme ve gösterme*<br /><br /> Tek örnekli araç pencereleri gizlenebilir veya gösteriliyor olabilir. Araç penceresi içindeki içerikler ve durumlar görünüm veya gizli olup olmadığını kalıcı hale getirin. Çok örnekli araç pencereleri de kapatılabilir ve gizli olabilir. Çok örnekli bir araç penceresi kapatıldığında, araç penceresi içindeki içerik ve durum atılır.|*Bir komuttan başlatılan*<br /><br /> İletişim kutuları, görev tabanlı bir komuttan başlatılır.|
|**Örnekler**|*Çoklu örnek*<br /><br /> Birkaç düzenleyici aynı anda açılabilir ve farklı dosyalar düzenlenebilir, ancak bazı düzenleyiciler aynı dosyanın birden fazla düzenleyicide açılmasını da sağlar ( **pencere > yeni pencere** komutu kullanılarak).<br /><br /> Tek bir düzenleyici bir veya birden çok dosyayı aynı anda (Proje Tasarımcısı) düzenlenebilir olabilir.|*Tek veya çok örnekli*<br /><br /> İçerik, bağlamı yansıtacak şekilde değişir (özellik tarayıcısında olduğu gibi) veya odağı/bağlamı diğer pencereler (Görev Listesi, Çözüm Gezgini) ile gönderin.<br /><br /> Tek örnekli ve çok örnekli araç pencereleri, önemli bir neden olmadıkça, etkin belge penceresiyle ilişkilendirilmelidir.|*Tek örnekli*|
|**Örnekler**|Kod Düzenleyicisi gibi **metin düzenleyicileri**<br /><br /> Form Tasarımcısı veya modelleme yüzeyi gibi **tasarım yüzeyleri**<br /><br /> Bildirim Tasarımcısı gibi **iletişim kutularına benzer Denetim düzenleri**|**Çözüm Gezgini** , çözüm içinde yer alan bir çözüm ve proje sağlar<br /><br /> **Sunucu Gezgini** , kullanıcının pencerede açılmasını seçtiği sunucuların ve veri bağlantılarının hiyerarşik bir görünümünü sağlar. Sorgu gibi veritabanı hiyerarşisinden bir nesne açmak, bir belge penceresi açar ve kullanıcının sorguyu düzenlemesine izin verir.<br /><br /> **Özellik tarayıcısı** , bir belge penceresinde veya başka bir araç penceresinde seçilen nesne için özellikleri görüntüler. Özellikler, hiyerarşik kılavuz görünümünde veya karmaşık iletişim kutusu benzeri denetimlerde sunulur ve kullanıcının bu özellikler için değerleri ayarlamaya izin verir.||

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Araç pencereleri

### <a name="overview"></a>Genel Bakış
 Araç pencereleri, kullanıcının belge penceresinde gerçekleşen işini destekler. Bunlar, Visual Studio 'Nun sağladığı ve işleyebileceği temel bir kök nesneyi temsil eden bir hiyerarşiyi göstermek için kullanılabilirler.

 IDE 'de yeni bir araç penceresi düşünürken yazarların şunları yapmanız gerekir:

- Görev için uygun olan araç pencerelerini kullanın ve benzer işlevlerle yenilerini oluşturun. Yeni araç pencereleri yalnızca, benzer bir pencereyle tümleştirilebilen önemli ölçüde farklı bir "araç" veya işlevsellik sunduklarında ya da mevcut bir pencereyi bir Özet hub 'ına çevirip oluşturulmamalıdır.

- Gerekirse, araç penceresinin üst kısmında standart bir komut çubuğu kullanın.

- Denetim sunusu ve klavye gezintisi için diğer araç pencerelerinin zaten mevcut desenlerle tutarlı olun.

- Diğer araç pencerelerinin denetim sunumlarıyla tutarlı olun.

- Belgeye özgü araç pencereleri, mümkün olduğunda otomatik görünür olmalıdır, böylece yalnızca üst belge etkinleştirildiğinde görünürler.

- Pencere içeriğinin klavyeden gezindiğinden emin olun (destek ok tuşları).

#### <a name="tool-window-states"></a>Araç penceresi durumları
 Visual Studio araç pencerelerinin bazıları Kullanıcı tarafından etkinleştirilen farklı durumlara sahiptir (otomatik gizleme özelliği gibi). Otomatik görünür gibi diğer durumlar, araç pencerelerinin doğru bağlamda görünmesine izin verir ve gerekli olmadığında gizleyin. Toplamda beş araç penceresi durumu vardır.

- **Sabitlenmiş/sabitlenmiş** araç pencereleri, belge alanının dört taraflarından herhangi birine iliştirilebilir. Raptiye simgesi araç penceresi başlık çubuğunda görünür. Araç penceresi, kabuğun ve diğer araç pencerelerinin kenarına yatay veya dikey olarak yerleştirilebilir ve ayrıca sekme bağlantılı olabilir.

- **Otomatik gizli** araç pencereleri sabitlenmemiş. Pencere, belge alanının kenarında bir sekmeden (araç penceresi ve onun simgesiyle birlikte) basılı bırakarak görüş alabilir. Araç penceresi, bir Kullanıcı sekmenin üzerine geldiğinde slaytlar çıkar.

- **Otomatik görünür** araç pencereleri, düzenleyici gibi başka bir kullanıcı arabirimi parçası başlatıldığında veya odaklandığında otomatik olarak görünür.

- **Kayan** araç pencereleri IDE dışında hareket ettirildiğinde. Bu, birden çok izleyici yapılandırması için kullanışlıdır.

- **Sekmeli belge** aracı pencereleri, belge kutusu içine yerleştirilebilir. Bu, Nesne Tarayıcısı gibi büyük araç pencereleri için yararlıdır, bu da çerçeve kenarlarına takmaya kıyasla daha fazla reel olması gerekir.

  ![Visual Studio 'da araç penceresi durumları](../../extensibility/ux-guidelines/media/0702-01-toolwindowstates.png "0702-01_ToolWindowStates")

  **Visual Studio 'da araç penceresi durumları**

#### <a name="single-instance-and-multi-instance"></a>Tek örnekli ve çoklu örnek
 Araç pencereleri tek örnekli veya çok örnekli. Bazı tek örnekli araç pencereleri etkin belge penceresiyle ilişkilendirilebilir, ancak çoklu örnek araç pencereleri de olmayabilir. Çoklu örnek araç pencereleri, pencerenin yeni bir örneğini oluşturarak pencere/yeni pencere komutuna yanıt verir. Aşağıdaki görüntüde, bir pencere örneği etkinken yeni pencere komutunu etkinleştiren bir araç penceresi gösterilmektedir:

 ![Visual Studio 'da komutları etkinleştiren araç penceresi](../../extensibility/ux-guidelines/media/0702-02-toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")

 **Pencerenin bir örneği etkinken ' yeni pencere ' komutunu etkinleştiren araç penceresi**

 Tek örnekli araç pencereleri gizlenebilir veya gösterilebileceği gibi, birden çok örnekli araç pencereleri de kapatılabilir ve gizli olabilir. Tüm araç pencereleri yerleşik, sekme bağlantılı, kayan veya birden çok belgeli arabirim (MDI) alt penceresi olarak ayarlanabilir (bir belge penceresine benzer). Tüm araç pencereleri, pencere menüsündeki uygun pencere yönetim komutlarına yanıt vermelidir:

 ![Visual Studio 'da pencere yönetimi komutları](../../extensibility/ux-guidelines/media/0702-03-windowmanagementcontrols.png "0702-03_WindowManagementControls")

 **Visual Studio Pencere menüsündeki pencere yönetimi komutları**

#### <a name="document-specific-tool-windows"></a>Belgeye özgü araç pencereleri
 Bazı araç pencereleri, belirli bir belge türüne göre değiştirmek için tasarlanmıştır. Bu pencereler, IDE 'deki etkin belge penceresi için geçerli olan işlevleri yansıtmak üzere sürekli olarak günceldir.

 İçeriği seçili düzenleyiciyi yansıtacak şekilde değişen araç pencereleri örnekleri araç kutusu ve belge ana hatlarıyla bulunur. Bu pencereler, bir düzenleyici pencereye bağlam sunmayan odağa sahip olduğunda bir filigran gösterir.

#### <a name="navigable-list-tool-windows"></a>Gezinilebilir liste aracı pencereleri
 Bazı araç pencereleri, kullanıcının etkileşime girebileceği gezinebilir öğelerin bir listesini görüntüler. Bu pencere türünde, pencere etkin değil olsa da listedeki geçerli öğe için her zaman geri bildirim olmalıdır. Liste, aynı zamanda pencerede seçili olan öğeyi değiştirerek, **Sayfaynextlocation** ve **Sayfayprevlocation** komutlarına yanıt vermelidir

 Gezinilebilir liste araç pencereleri örnekleri Çözüm Gezgini ve sonuçları bul penceresidir.

### <a name="tool-window-types"></a>Araç penceresi türleri

#### <a name="common-tool-windows-and-their-functions"></a>Ortak araç pencereleri ve işlevleri

|Tür|Araç penceresi|İşlev|
|----------|-----------------|--------------|
|**Hiyerarşi**|Çözüm Gezgini|Projelerde, çeşitli dosyalarda ve çözüm öğelerinde bulunan belgelerin listesini görüntüleyen hiyerarşik ağaç. Projelerin içindeki öğelerin gösterilmesi proje türüne sahip paket tarafından tanımlanır (örneğin, başvuru tabanlı, dizin tabanlı veya karma mod türleri).|
|**Hiyerarşi**|Sınıf Görünümü|Sınıfların ve çalışma kümesindeki nesnelerin hiyerarşik bir ağacı, dosyaların kendileri bağımsız olarak.|
|**Hiyerarşi**|Sunucu Gezgini|Çözümdeki tüm sunucuları ve veri bağlantılarını görüntüleyen hiyerarşik bir ağaç.|
|**Hiyerarşi**|Belge Anahattı|Etkin belgenin hiyerarşik yapısı.|
|**Kılavuz**|Özellikler|Seçili nesnenin özelliklerinin listesini, bu özellikleri düzenlemek için değer seçiciler ile birlikte görüntüleyen bir kılavuz.|
|**Kılavuz**|Görev Listesi|Kullanıcının görevler ve açıklamalar oluşturmasına/düzenlemesine/silmesine izin veren bir kılavuz.|
|**İçerik**|Yardım|"Nasıl yapılır?" yönteminden farklı yardım alma yöntemlerine kullanıcıların erişmesine izin veren bir pencere videoları MSDN forumlarına.|
|**İçerik**|Dinamik yardım|Geçerli seçime uygun yardım konularına ilişkin bağlantıları görüntüleyen bir araç penceresi.|
|**İçerik**|Nesne Tarayıcısı|Sol bölmedeki hiyerarşik nesne bileşenlerinin listesi ve sağ sütundaki nesnenin özellikleri ve yöntemleri içeren iki sütunlu bir çerçeve kümesi.|
|**İletişim**|Bul, gelişmiş bul|Kullanıcının çözüm içindeki çeşitli dosyaları bulmasına veya bulmasına ve değiştirmesine izin veren bir iletişim kutusu.|
|**Diğer**|Araç Kutusu|Tasarım yüzeylerine bırakılacak öğeleri depolamak için kullanılan araç penceresi, tüm tasarımcılar için tutarlı bir sürükleme kaynağı sağlar.|
|**Diğer**|Başlangıç Sayfası|Geliştirici haberleri, Visual Studio yardım ve son projelere erişimi olan kullanıcının portalı Visual Studio 'ya. Kullanıcılar ayrıca, StartPage. xaml dosyasını "Common7\IDE\StartPages\" Visual Studio Program Files dizininden Visual Studio belgeler dizinindeki StartPages klasörüne kopyalayarak ve ardından XAML 'yi el ile ya da Visual Studio veya başka bir kod düzenleyicisinde açarak, özel başlangıç sayfaları oluşturabilir.|
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Otolar||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Hemen||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Çıktı|Çıktı penceresi, her metin olayına veya bildirireceğiniz duruma sahip olduğunuzda kullanılabilir.|
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Bellek||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Kesme noktaları||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Çalışıyor||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Belgeler||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Çağrı yığını||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Ayarlanmalıdır||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|PortQry||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Ayrıştırılmış kod||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|Kayıtların||
|**Hata ayıklayıcı:** görevleri ve izleme etkinliklerini hata ayıklamaya özgü bir Windows grubu|İş Parçacıkları||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Belge Düzenleyicisi kuralları

### <a name="document-interactions"></a>Belge etkileşimleri
 "Belge iyi", IDE içindeki en büyük alandır ve kullanıcının, ek araç pencereleri yardımıyla görevlerini tamamlaması için genellikle ilgilenmesini odaklı yerdir. Belge düzenleyicileri, kullanıcının Visual Studio içinde açtığı ve kaydettiği temel iş birimlerini temsil eder. Çözüm Gezgini veya diğer etkin hiyerarşi pencereleri ile bağlı bir seçim kesin bir şekilde korunur. Kullanıcı bu hiyerarşi pencerelerinin birine işaret edebilir ve belgenin nerede olduğunu ve çözüm, proje ya da Visual Studio paketi tarafından sunulan başka bir kök nesneyle ilişkisini biliyor olmalıdır.

 Belge düzenlemesi için tutarlı bir kullanıcı deneyimi gerekir. Kullanıcının pencere yönetimi ve komutları bulma yerine görev üzerinde odaklanmasını sağlamak için, bu belge türünü düzenlemekte Kullanıcı görevlerine en uygun bir belge görünümü stratejisi seçin.

#### <a name="common-interactions-for-the-document-well"></a>Belge kutusu için ortak etkileşimler

- Ortak **yeni dosya** ve **Açık dosya** deneyimlerinde tutarlı bir etkileşim modeli saklayın.

- Belge penceresi açıldığında ilgili Windows ve menülerde ilgili işlevselliği güncelleştirin.

- Menü komutları **düzenleme**, **Biçim**ve **görüntüleme** menüleri gibi ortak menülere uygun şekilde tümleşiktir. Önemli miktarda özelleştirilmiş komut varsa, yalnızca belge odağa sahip olduğunda görünür olan yeni bir menü oluşturulabilir.

- Düzenleyicinin üst kısmına gömülü bir araç çubuğu yerleştirilebilecek. Bu, düzenleyicinin dışında görünen ayrı bir araç çubuğunun olmasını tercih edilir.

- Çözüm Gezgini veya benzer etkin hiyerarşi penceresinde her zaman bir seçimi sürdürün.

- Çözüm Gezgini bir belgeye çift tıklamak, **Açık**olarak aynı eylemi gerçekleştirmelidir.

- Bir belge türünde birden fazla düzenleyici kullanılıyorsa, kullanıcının, dosyaya sağ tıklayıp kısayol menüsünden **birlikte Aç** ' ı **seçerek, belirtilen** belge türünde varsayılan eylemi geçersiz kılabilir veya sıfırlayabilmesi gerekir.

- Bir belge kutusu içinde sihirbaz oluşturmayın.

### <a name="user-expectations-for-specific-document-types"></a>Belirli belge türleri için Kullanıcı beklentileri
 Birçok farklı temel belge Düzenleyicisi türü vardır ve her birinin aynı türdeki diğer kullanıcılarla tutarlı bir etkileşimler kümesi vardır.

- **Metin tabanlı Düzenleyici:** kod düzenleyici, günlük dosyaları

- **Tasarım yüzeyi:** WPF form Tasarımcısı, Windows Forms

- **Iletişim kutusu stili Düzenleyicisi:** Bildirim Tasarımcısı, proje özellikleri

- **Model Tasarımcısı:** iş akışı Tasarımcısı, codemap, mimari diyagramı, ilerleme

  Ayrıca, belge iyi kullanan birkaç düzenleyici olmayan tür vardır. Belgelerin kendileri düzenlenmemesi sırasında, belge pencereleri için standart etkileşimleri izlemesi gerekir.

- **Raporlar:** IntelliTrace raporu, Hyper-V raporu, Profil Oluşturucu raporu

- **Pano:** Tanılama Merkezi

#### <a name="text-based-editors"></a>Metin tabanlı düzenleyiciler

- Belge, Önizleme sekmesi modeline katılıyorsa belgeyi açmadan önizlemeye izin verir.

- Belgenin yapısı bir belge anahattı gibi bir yardımcı araç penceresi içinde temsil edilebilir.

- IntelliSense (uygunsa), diğer kod düzenleyicilerle tutarlı şekilde davranır.

- Açılır pencereler veya yardımcı UI, CodeLens gibi benzer kullanıcı arabirimi için benzer stilleri ve desenleri izler.

- Belge durumuyla ilgili iletiler, belgenin üst kısmında veya durum çubuğunda bir bilgi çubuğu denetiminde sunulacaktır.

- Kullanıcının yazı tipi ve renklerin görünümünü, paylaşılan yazı tipleri ve renkler sayfası veya düzenleyiciye özgü bir **araç > seçenekleri** sayfası kullanarak özelleştirebilmelidir.

#### <a name="design-surfaces"></a>Tasarım yüzeyleri

- Boş bir tasarımcı, yüzeyi üzerinde nasıl çalışmaya başladığına işaret eden bir filigrana sahip olmalıdır.

- Görünüm değiştirme mekanizmaları, bir kod Düzenleyicisi açmak için çift tıklama veya belge penceresi içindeki sekmeler her iki bölme ile etkileşime izin veren gibi varolan desenleri izler.

- Son derece özel bir araç penceresi gerekli olmadığı takdirde tasarım yüzeyine öğe eklemek araç kutusu aracılığıyla yapılmalıdır.

- Yüzeydeki öğeler, tutarlı bir seçim modeline uyar.

- Katıştırılmış araç çubukları, **Kaydet**gibi yaygın komutları değil yalnızca belgeye özgü komutları içerir.

#### <a name="dialog-style-editors"></a>İletişim kutusu stili düzenleyiciler

- Denetim düzeni normal iletişim kutusu düzen kurallarını izlemelidir.

- Düzenleyicideki sekmelerin belge sekmelerinin görünümüyle eşleşmesi gerekir, bu, izin verilen iki iç sekme stilinden biriyle eşleşmelidir.

- Kullanıcılar yalnızca klavye kullanarak denetimlerle etkileşime girebilmelidir; Düzenleyici ve sekme ile denetim aracılığıyla ya da standart anımsatıcıları kullanarak.

- Tasarımcı ortak kaydetme modelini kullanmalıdır. Diğer düğmelerin uygun olmasına rağmen, yüzeye hiçbir genel kaydetme veya kaydetme düğmesi yerleştirilmemelidir.

#### <a name="model-designers"></a>Model tasarımcıları

- Boş bir tasarımcı, yüzeyi üzerinde nasıl çalışmaya başladığına işaret eden bir filigrana sahip olmalıdır.

- Tasarım yüzeyine öğe eklemek araç kutusu aracılığıyla yapılmalıdır.

- Yüzeydeki öğeler, tutarlı bir seçim modeline uyar.

- Katıştırılmış araç çubukları, **Kaydet**gibi yaygın komutları değil yalnızca belgeye özgü komutları içerir.

- Bir gösterge, yüzeyde veya bir filigraya ya da bir Filigranda görünebilir.

- Kullanıcı, bir **araçlar > seçenekler** sayfası, paylaşılan yazı tipleri ve renkler sayfası veya düzenleyiciye özgü bir seçenek kullanarak yazı tiplerinin/renklerin görünümünü özelleştirebilmelidir.

#### <a name="reports"></a>Raporlar

- Raporlar genellikle bilgi amaçlıdır ve kaydetme modeline katılmaz. Ancak, bunları genişleterek ve daraltarak diğer ilgili bilgilere veya bölümlerine bağlantılar gibi etkileşim de içerebilir.

- Yüzeyde komutların çoğu düğme değil köprüler olmalıdır.

- Düzen bir üst bilgi içermeli ve standart rapor düzeni kılavuzunu izlemelidir.

#### <a name="dashboards"></a>Panolar

- Panolar kendisine bir etkileşim modeli içermez, ancak çeşitli araçlar sunmak için bir yol olarak görev yapar.

- Kayıt modeline katılmaz.

- Kullanıcılar, yalnızca klavyeyi kullanarak, düzenleyici ve sekme aracılığıyla veya standart anımsatıcıları kullanarak denetimlerle etkileşime girebilmelidir.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>İletişimlerinin

### <a name="introduction"></a>Giriş
 Visual Studio 'daki iletişim kutuları, genellikle kullanıcının işinin tek bir ayrı birimini desteklemelidir ve sonra da kapatılır.

 Bir iletişim kutusunun gerekli olduğunu belirlediyseniz, tercih sırasına göre üç seçeneğiniz vardır:

1. Özelliklerinizi Visual Studio 'daki paylaşılan diyalogların biriyle tümleştirin.

2. Varolan benzer bir iletişim kutusunda bulunan bir model kullanarak kendi iletişim alanınızı oluşturun.

3. Etkileşim ve Düzen kılavuzlarını izleyerek yeni bir iletişim kutusu oluşturun.

   Bu konu başlığında, Visual Studio iş akışlarında doğru iletişim kutusu deseninin ve iletişim kutusu tasarımının ortak kurallarının nasıl seçeceğiniz açıklanmaktadır.

### <a name="themes"></a>Temalar
 Visual Studio 'daki iletişim kutuları iki temel stillerden birini izler:

#### <a name="standard-unthemed"></a>Standart (temalı)
 İletişim kutularının çoğu standart yardımcı program iletişim kutusunlardır ve temalı olması gerekir. Ortak denetimleri yeniden şablon oluşturun veya stilize bir "modern" düğme ya da denetim oluşturmayı deneyin. Denetimler ve Chrome görünümü, [iletişim kutuları için standart Windows Masaüstü etkileşim kılavuzlarını](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx)izleyin.

#### <a name="themed"></a>Uygulanmış
 Özel "imza" iletişimleri temalı olabilir. Temalı iletişim kutularının ayrı bir görünümü vardır ve bu stille ilişkili özel etkileşim desenleri de vardır. Diyaloğa yalnızca bu gereksinimleri karşılaması durumunda temaya:

- İletişim kutusu, genellikle veya çok sayıda kullanıcı tarafından (örneğin, **Yeni proje** iletişim kutusu) görünecek ve kullanılan yaygın bir deneyimdir.

- İletişim kutusu, belirgin ürün markası öğeleri (örneğin, **Hesap ayarları** iletişim kutusu) içerir.

- İletişim kutusu, diğer temalı iletişim kutularını (örneğin, **bağlı hizmet ekle** iletişim kutusu) içeren daha büyük bir akışın integral bir parçası olarak görüntülenir.

- İletişim kutusu, bir ürün sürümünü yükseltmekte veya farklılaştırmakta bir stratejik rol oynayan bir deneyimin önemli bir parçasıdır.

  Bir temalı iletişim kutusu oluştururken, uygun ortam renklerini kullanın ve doğru düzeni ve etkileşim düzenlerini izleyin. (Bkz. [Visual Studio Için düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md))

### <a name="dialog-design"></a>İletişim kutusu tasarımı
 İyi tasarlanmış iletişim kutuları aşağıdaki öğeleri dikkate alır:

- Desteklenen Kullanıcı görevi

- İletişim kutusu metin stili, dili ve terminolojisi

- Denetim seçimi ve UI kuralları

- Görsel düzen belirtimi ve denetim hizalaması

- Klavye erişimi

#### <a name="content-organization"></a>İçerik organizasyonu
 Bu temel iletişim türleri arasındaki farkları göz önünde bulundurun:

- [Basit iletişim kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) tek bir kalıcı pencerede denetimleri sunar. Sunum, bir alan seçici veya simge çubuğu dahil olmak üzere karmaşık denetim desenlerinin çeşitlemelerini içerebilir.

- [Katmanlı iletişim kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) , tek bir kullanıcı arabirimi birden çok denetim grubunu içerdiğinde ekranın en çok bir parçasını oluşturmak için kullanılır. İletişim kutusu gruplandırmaları, kullanıcının belirli bir anda hangi gruplamayı göremeyeceğini seçebilmesi için sekme denetimleri, gezinti listesi denetimleri veya düğmeler aracılığıyla "katmanlı" olur.

- [Sihirbazlar](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) , bir görevin tamamlanmasına yönelik bir dizi adım aracılığıyla kullanıcıyı yönlendirmek için faydalıdır. Sıralı panellerde bir dizi seçenek sunulur, bazen önceki panelde yapılan seçime bağlı olarak farklı iş akışları ("dallar") ile tanışın.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Basit iletişim kutuları
 Basit bir iletişim kutusu, tek bir kalıcı pencerede denetimlerin sunumudur. Bu sunu, alan seçici gibi karmaşık denetim desenlerinin çeşitlemelerini içerebilir. Basit iletişim kutuları için standart genel düzeni ve karmaşık denetim gruplandırmaları için gereken belirli düzenleri izleyin.

 ![Visual Studio 'da basit iletişim kutusu](../../extensibility/ux-guidelines/media/0704-01-createstrongnamekey.png "0704-01_CreateStrongNameKey")

 **Tanımlayıcı ad anahtarı oluşturma, Visual Studio 'da basit bir iletişim kutusu örneğidir.**

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Katmanlı iletişim kutuları
 Katmanlı iletişim kutuları sekmeleri, panoları ve katıştırılmış ağaçları içerir. Tek bir kullanıcı arabiriminde sunulan birden fazla denetim grubu olduğunda, gerçek Emlak için kullanılır. Gruplandırmalar, kullanıcının herhangi bir anda hangi gruplandırmanın görüzi seçebilmesini sağlayacak şekilde katmanlıdır.

 En kolay durumda, gruplandırmalar arasında geçiş mekanizması bir sekme denetimidir. Kullanılabilecek birkaç alternatif vardır. En uygun stili seçme hakkında bilgi için bkz. önceliklendirme ve katmanlama.

 **Araçlar > seçenekleri** iletişim kutusu, katıştırılmış ağaç kullanan katmanlı bir iletişim örneğidir:

 ![Visual Studio 'da katmanlı iletişim kutusu](../../extensibility/ux-guidelines/media/0704-02-toolsoptions.png "0704-02_ToolsOptions")

 **Araçlar > seçenekler, Visual Studio 'daki katmanlı bir iletişim örneğidir.**

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>'Nı
 Sihirbazlar, bir görevin tamamlanması için bir mantıksal adım dizisi aracılığıyla kullanıcıyı yönlendirmesinde faydalıdır. Sıralı panellerde bir dizi seçenek sunulur ve bir sonraki adıma geçmeden önce Kullanıcı her bir adımla devam etmelidir. Yeterli varsayılan değer varsa, **son** düğmesi etkinleştirilir.

 Kalıcı sihirbazlar şu görevler için kullanılır:

- Kullanıcı seçeneklerine bağlı olarak farklı yolların sunulduğu dallanmayı içerir

- Sonraki adımların önceki adımlardan Kullanıcı girişine bağlı olduğu adımlar arasındaki bağımlılıkları içerir

- , Kullanıcı arabiriminin sunulan seçimleri ve her adımda olası sonuçları açıklamak için kullanılması gerektiği kadar karmaşıktır

- İşlem, herhangi bir değişiklik kaydedilmeden önce tamamen tamamlanması gereken bir adım kümesi gerektirir

### <a name="common-conventions"></a>Ortak kurallar
 İletişim kutularınızla en iyi tasarımı ve işlevleri elde etmek için, iletişim kutusu boyutu, konum, standartlar, denetim yapılandırma ve hizalama, Kullanıcı arabirimi metni, başlık çubukları, denetim düğmeleri ve erişim anahtarlarına yönelik bu kuralları izleyin.

 Düzen 'e özgü yönergeler için bkz. [Visual Studio Için düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Boyut
 İletişim kutuları minimum 1024x768 ekran çözünürlüğüne sığmalıdır ve ilk iletişim kutusu boyutu 900x700 pikseli aşmamalıdır. İletişim kutuları yeniden boyutlandırılabilir, ancak bir gereksinim değildir.

 Yeniden boyutlandırılabilir iletişim kutularına yönelik iki öneri vardır:

1. Bu en küçük boyut, kırpma olmadan denetim kümesi için optimize edilecek iletişim kutusu için tanımlanır ve makul yerelleştirme büyümesini karşılayacak şekilde ayarlanır.

2. Kullanıcı tarafından ölçeklendirilmiş boyutun oturumdan oturuma devam etmesi. Örneğin, Kullanıcı bir iletişim kutusunu %150 olarak ölçeklendirirken, iletişim kutusunun sonraki bir başlatması %150 ' de görüntülenir.

#### <a name="position"></a>Konum
 İletişim kutuları ilk başlatmada IDE içinde ortalanmalıdır. Yeniden boyutlandırılabilir iletişimler için, iletişim kutusunun son konumunun kalıcı olması gerekmez, bu nedenle sonraki başlangıçlarda ortalanmış olarak görünür. Yeniden boyutlandırılabilir iletişimler için, boyutun sonraki başlangıçlarda kalıcı olması gerekir. Kalıcı olan yeniden boyutlandırılabilir iletişim kutuları için, konumun kalıcı olması gerekmez. IDE içinde ortalanan bunları görüntülemek, kullanıcının görüntüleme yapılandırması değiştirildiğinde, iletişim kutusunun öngörülemeyen veya kullanılamaz bir konumda görüntülenmesini önler. Yeniden konumlandırılabilir olmayan iletişim kutuları için, iletişim kutusunun daha büyük bir iş akışının integral parçası olarak sıklıkla kullanılabilmesi için, kullanıcının konumu sonraki başlangıçlarda saklanması gerekir.

 İletişim kutuları diğer iletişim kutularını oluştururken, en üstteki iletişim kutusu, kullanıcının yeni bir yere gezindikleri için daha belirgin olması için üst öğenin sağına doğru ve aşağı doğru bir şekilde basamaklı olması gerekir.

#### <a name="modality"></a>Moduna
 Kalıcı olması, kullanıcıların devam etmeden önce iletişim kutusunu tamamlaması veya iptal edebilmesi için gerekli olduğu anlamına gelir. Kalıcı iletişim kutuları kullanıcının ortamın diğer bölümleriyle etkileşime engel olduğundan, özelliğin görev akışı bunları mümkün olduğunca az bir şekilde kullanmalıdır. Kalıcı bir işlem gerektiğinde, Visual Studio 'nun özelliklerini tümleştirebilmeniz için bir dizi paylaşılan iletişim kutusu vardır. Yeni bir iletişim kutusu oluşturmanız gerekiyorsa, benzer işlevlerle mevcut bir iletişim kutusunun etkileşim düzenine uyun.

 Kullanıcıların tek seferde iki etkinlik gerçekleştirmesi gerektiğinde (örneğin, yeni kod yazarken **bul** ve **Değiştir** ), kullanıcının aralarında kolayca geçiş yapabilmesi için iletişim kutusu modsuz olmalıdır. Visual Studio genellikle bu tür Düzenleyici destekleyici bağlantılı görev için araç pencerelerini kullanır.

#### <a name="control-configuration"></a>Denetim yapılandırması
 Visual Studio 'da aynı şeyi gerçekleştiren mevcut denetim yapılandırmalarına uygun olun.

#### <a name="title-bars"></a>Başlık çubukları

- Başlık çubuğundaki metin, onu başlatan komutun adını yansıtmalıdır.

- İletişim kutusu başlık çubuklarında hiçbir simge kullanılmamalıdır. Sistemin bir tane gerektirmesi durumunda, Visual Studio logosu ' nı kullanın.

- İletişim kutularında Küçült veya büyüt düğmeleri olmamalıdır.

- Başlık çubuğundaki Yardım düğmeleri kullanım dışı bırakılmıştır. Bunları yeni iletişim kutularına eklemeyin. Bunlar mevcut olduğunda, görevle ilgili kavramsal olan bir yardım konusu başlatacaktır.

  ![Visual Studio için başlık çubuğu belirtimleri](../../extensibility/ux-guidelines/media/0704-03-titlebarspecs.png "0704-03_TitleBarSpecs")

  **Visual Studio iletişim kutularındaki başlık çubukları için kılavuz belirtimleri.**

#### <a name="control-buttons"></a>Denetim düğmeleri
 Genel olarak, **Tamam** / **iptal** / **Yardım** düğmeleri iletişim kutusunun sağ alt köşesinde yatay olarak düzenlenmelidir. İletişim kutusunun alt kısmında, denetim düğmeleriyle görsel karışıklık sunacak diğer birkaç düğme varsa, alternatif dikey yığına izin verilir.

 ![Visual Studio 'da denetim düğmesi yapılandırması](../../extensibility/ux-guidelines/media/0704-04-controlbuttonconfig.png "0704-04_ControlButtonConfig")

 **Visual Studio iletişim kutularında denetim düğmeleri için kabul edilebilir konfigürasyonlar**

 İletişim kutusu varsayılan bir denetim düğmesi içermelidir. Varsayılan olarak kullanılacak en iyi komutu belirlemek için, aşağıdaki seçeneklerden birini belirleyin (öncelik sırasına göre listelenmiştir):

- Varsayılan olarak en güvenli ve en güvenli komutu seçin. Bu, veri kaybını önlemeyi ve istenmeyen sistem erişiminin oluşmasını önlemek için en olası komutu seçme anlamına gelir.

- Veri kaybı ve güvenlik faktörleri yoksa, kolaylık doğrultusunda varsayılan komutu seçin. En olası komut, varsayılan olarak dahil olmak üzere, iletişim kutusu sık veya yinelenen görevleri desteklediğinde kullanıcının iş akışını iyileştirir.

  Varsayılan komut için kalıcı bir bozucu eylem seçmekten kaçının. Böyle bir komut varsa, bunun yerine varsayılan olarak güvenli bir komut seçin.

#### <a name="access-keys"></a>Erişim tuşları
 **Tamam** / Yardım düğmelerini**iptal etmek**için erişim tuşlarını kullanmayın / **Help** . Bu düğmeler, varsayılan olarak kısayol tuşlarıyla eşlenir:

|Düğme adı|Klavye kısayolu|
|-----------------|-----------------------|
|Tamam|Enter|
|İptal|Esc|
|Yardım|F1|

#### <a name="imagery"></a>Canlandırın
 İletişim kutularında görüntüleri gelişigüzel kullanın. Yalnızca alanı kullanmak için iletişim kutularında büyük simgeler kullanmayın. Yalnızca ileti, uyarı simgeleri veya durum animasyonları gibi kullanıcıya iletiyi almak için önemli bir parçasıysa görüntüleri kullanın.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Öncelik verme ve katmanlama

#### <a name="prioritizing-your-ui"></a>Kullanıcı arabiriminize öncelik verme
 Belirli kullanıcı arabirimi öğelerini Forefront 'e getirmek ve iletişim kutularına daha gelişmiş davranış ve Seçenekler (belirsiz komutlar dahil) yerleştirmek gerekebilir. Yaygın olarak kullanılan işlevselliği, bu BT için yer açarak Forefront 'e taşıyın ve iletişim kutusu gösterildiğinde bir metin etiketiyle Kullanıcı arabiriminde varsayılan olarak görünür hale getirin.

#### <a name="layering-your-ui"></a>Kullanıcı arabiriminizi katmanlama
 Bir iletişim kutusunun gerekli olduğunu, ancak kullanıcıya sunmak istediğiniz ilgili işlevselliğin basit bir iletişim kutusunda görüntülendiklerinin ötesinde olduğunu belirlediyseniz, Kullanıcı ARABIRIMINIZI katmanmanız gerekir. Visual Studio 'Nun kullandığı en yaygın katmanlama yöntemleri, sekmeler ve hallyöntemleri veya panolardır. Bazı durumlarda, genişleyebilir ve daraltılabilen bölgeler uygun olabilir. Uyarlamalı Kullanıcı Arabirimi genellikle Visual Studio 'da önerilmez.

 Sekme benzeri denetimler aracılığıyla farklı katman Kullanıcı arabirimi yöntemlerinin avantajları ve dezavantajları vardır. Durumunuza uygun bir katman tekniği seçtiğinizden emin olmak için aşağıdaki listeyi gözden geçirin.

##### <a name="tabbing"></a>Sekmeyle gitmeyi

|Anahtarlama mekanizması|Avantajlar ve uygun kullanım|Olumsuz ve uygunsuz kullanım|
|-------------------------|------------------------------------|-----------------------------------------|
|Sekme denetimi|İletişim kutusu sayfalarını mantıksal olarak ilgili kümeler halinde gruplandır<br /><br /> İletişim kutusundaki ilgili denetimlerin sayfalarında beşten az beş (veya iletişim kutusu genelinde bir satıra sığan sekme sayısı) için faydalıdır<br /><br /> Sekme etiketleri kısa olmalıdır: içeriği kolayca tanımlayabilen bir veya iki sözcük<br /><br /> Ortak bir sistem iletişim kutusu stili<br /><br /> Örnek: **dosya gezgini > öğe özellikleri**|Açıklayıcı kısa Etiketler yapmak zor olabilir<br /><br /> Genellikle bir iletişim kutusunda geçen beş sekmeyi ölçeklendirmez<br /><br /> Tek satır için çok fazla sekmeye sahipseniz uygun değildir; alternatif bir katman tekniği kullanın<br /><br /> Genişletilebilir değil|
|Kenar çubuğu gezintisi|Sekmeden daha fazla kategori barındırabilecek basit anahtarlama cihazı<br /><br /> Kategorilerin düz listesi (hiyerarşi yok)<br /><br /> Genişletilmiş<br /><br /> Örnek: **Customize... > Add komutu**|Üçten az grup varsa yatay boşluk iyi bir şekilde kullanılamaz<br /><br /> Görev bir açılan bir liste için daha uygun olabilir|
|Ağaç denetimi|Sınırsız kategori sağlar<br /><br /> Kategorilerin gruplandırılmasına ve/veya hiyerarşisine izin verir<br /><br /> Genişletilmiş<br /><br /> Örnek: **araçlar > seçenekler**|Yoğun iç içe geçmiş hiyerarşiler aşırı yatay kaydırmaya neden olabilir<br /><br /> Visual Studio, ağaç görünümlerinin aşırı yerleriyle karşılaştı|
|Ekleme|Görev tabanlı, sıralı adımlar aracılığıyla görev tamamlamada yardımcı olur. Sihirbaz, üst düzey bir görevi temsil eder ve tek tek panolar, genel görevi gerçekleştirmek için gereken alt görevleri temsil eder.<br /><br /> Kullanıcının görevi tamamlaması için birden fazla düzenleyici ve araç penceresi kullanması gerektiği gibi, görev Kullanıcı arabirimi sınırlarını aştığında yararlı olur<br /><br /> Görev dallandırma gerektirdiğinde faydalıdır<br /><br /> Görev, adımlar arasında bağımlılıklar içerdiğinde faydalıdır<br /><br /> Farklı benzer iletişim kutularının sayısını azaltmak için tek bir karar çatalına sahip birkaç benzer görevin bir iletişim kutusunda sunulabilmesini sağlar.|Sıralı iş akışı gerektirmeyen tüm görevler için uygun değil<br /><br /> Kullanıcılar çok fazla adımla sihirbaz tarafından kafa karışmış ve kafa karışabilir<br /><br /> Sihirbazlar, doğal olarak sınırlı ekran Emlak|

##### <a name="hallways-or-dashboards"></a>Hallyollar veya panolar
 Hallyollar ve panolar, diğer iletişim kutuları ve pencereler için işaret başlatma işlevi sunan iletişim kutuları veya panellerdir. İyi tasarlanmış "Hallway", kullanıcının ortak görevleri kolayca yerine getirebilmesine olanak sağlayan en yaygın seçenekleri, komutları ve ayarları hemen gösterir. Gerçek dünyada bir koridordaki gibi, doorways arkasındaki odalara erişmek için, daha az ortak kullanıcı arabirimi, ana koridordaki erişilebilen ilgili işlevlerin ayrı "Odalar" (genellikle diğer iletişim kutularında) olarak toplanır.

 Alternatif olarak, daha az yaygın işlevselliği ayrı konumlara yeniden düzenleme yerine tek bir koleksiyondaki tüm kullanılabilir işlevleri sunan bir kullanıcı arabirimi yalnızca bir panodur.

 ![Outlook 'ta Hallway kavramı](../../extensibility/ux-guidelines/media/0704-08-hallway.png "0704-08_Hallway")

 **Outlook 'ta ek UI gösterme için Hallway kavramı**

##### <a name="adaptive-ui"></a>Uyarlamalı Kullanıcı arabirimi
 Kullanım veya kullanıcının kendi kendine bildirilen deneyimi temel alınarak Kullanıcı ARABIRIMINI göstermek veya gizlemek, diğer bölümleri gizlerken gerekli Kullanıcı arabirimini sunmaya yönelik başka bir yoldur. UI 'nin ne zaman gösterileceğini veya gizleyeceğine karar vermek için algoritmalar karmaşık olabilir ve bazı durumlarda kurallar her zaman yanlış olur.

## <a name="projects"></a><a name="BKMK_Projects"></a>Projeyle

### <a name="projects-in-the-solution-explorer"></a>Çözüm Gezgini projeler
 Çoğu proje başvuru tabanlı, dizin tabanlı veya karma olarak sınıflandırılır. Her üç tür proje Çözüm Gezgini eşzamanlı olarak desteklenir. Bu pencerenin içinde, projelerle çalışan kullanıcı deneyiminin kökü yer alır. Farklı proje düğümleri başvuru, dizin veya karma mod türü projeler olsa da, projeye özgü Kullanıcı düzenlerine ayrılan bir başlangıç noktası olarak uygulanması gereken ortak bir etkileşim deseni vardır.

 Projeler her zaman olmalıdır:

- Proje içeriğini düzenlemek için proje klasörleri ekleme özelliğini destekleme

- Proje kalıcılığı için tutarlı bir model koruma

  Projeler, için tutarlı etkileşim modellerini de korumalıdır:

- Proje öğeleri kaldırılıyor

- Belgeler kaydediliyor

- Proje özelliği düzenlemesi

- Projeyi alternatif bir görünümde Düzenle

- Sürükle ve bırak işlemleri

### <a name="drag-and-drop-interaction-model"></a>Sürükleme ve bırakma etkileşimi modeli
 Projeler genellikle başvuruları başvuru tabanlı olarak sınıflandırır (yalnızca depolamadaki proje öğelerine başvuruları kalıcı hale getirebilecektir), dizin tabanlı (yalnızca bir projenin hiyerarşisinde fiziksel olarak depolanan proje öğelerini kalıcı hale getirebiliyor) veya karma (başvuruları veya fiziksel öğeleri kalıcı hale getirebiliyor). IDE, **Çözüm Gezgini**aynı anda tüm üç tür projeleri de karşılar.

 Bir sürükle ve bırak perspektifinden, aşağıdaki özellikler **Çözüm Gezgini**içindeki her proje türü için geçerlidir:

- **Başvuru tabanlı proje:** Anahtar noktası, projenin depolamadaki bir öğeye başvuru etrafında sürüklenmesi. Başvuru temelli bir proje, bir taşıma işlemi için kaynak görevi gören zaman, yalnızca projeden öğeye başvuruyu kaldırmalıdır. Öğe gerçekten sabit sürücüden silinmemelidir. Başvuru temelli bir proje, taşıma (veya kopyalama) işlemi için hedef görevi gören bir işlem, öğenin özel bir kopyasını oluşturmadan özgün kaynak öğesine bir başvuru eklemektir.

- **Dizin tabanlı proje:** Bir sürükleme ve bırakma noktasından proje, bir başvuru yerine fiziksel öğenin etrafında sürüklemektir. Dizin tabanlı bir proje bir taşıma işlemi için kaynak görevi gördüğü zaman, fiziksel öğenin sabit sürücüden silinmesi ve projeden kaldırılması gerekir. Dizin tabanlı bir proje, taşıma (veya kopyalama) işlemi için hedef görevi gören zaman, kaynak öğenin bir kopyasını hedef konumunda yapması gerekir.

- **Karma hedef proje:** Bir sürükle ve bırak noktasından, bu proje türünün davranışı sürüklediğiniz öğenin yapısını (depolama alanı veya öğenin kendisindeki bir öğe başvurusu) temel alır. Başvurular ve fiziksel öğeler için doğru davranış yukarıda açıklanmıştır.

  **Çözüm Gezgini**bir proje türü varsa, sürükle ve bırak işlemleri basittir. Her proje sistemi kendi sürükle ve bırak davranışını tanımlayabildiğinden, öngörülebilir bir kullanıcı deneyimi sağlamak için belirli yönergelerin (Windows Gezgini sürükle ve bırak davranışına göre) izlenmesi gerekir:

- **Çözüm Gezgini** değiştirilmemiş bir sürükleme işlemi (ne CTRL ne de SHIFT tuşu basılı tutulduğunda) bir taşıma işlemine neden olmalıdır.

- Shift-Sürükle işlemi de bir taşıma işlemine neden olmalıdır.

- CTRL-Sürükle işlemi bir kopyalama işlemine neden olmalıdır.

- Başvuru tabanlı ve karışık proje sistemleri, kaynak öğeye bağlantı (veya başvuru) ekleme kavramını destekler. Bu projeler bir sürükle ve bırak işleminin hedefi olduğunda ( **Ctrl + Shift** tuşu basılı tutulduğunda), projeye eklenmekte olan öğe için bir başvuruya neden olmalıdır

  Her sürükleme ve bırakma işlemi, başvuru tabanlı, dizin tabanlı ve karışık projelerin kombinasyonları arasında senyana değildir. Özellikle, kaynak dizin tabanlı projenin taşıma tamamlandıktan sonra kaynak öğeyi silmesi gerektiğinden, dizin tabanlı bir kaynak proje ve başvuru tabanlı hedef proje arasında taşıma işlemine izin vermek, özellikle de soruna neden olur. Hedef başvuru tabanlı proje, silinen bir öğeye yönelik bir başvuruya sahip olur.

  Hedef başvuru tabanlı proje kaynak öğenin bağımsız bir kopyasını yapmadığından, bu tür projeler arasında kopyalama işlemine izin vermek için de yanıltıcı hale gelir. Benzer şekilde, dizin tabanlı bir proje başvuruları sürdüremediği için Ctrl + Shift tuşlarına basarak dizin tabanlı bir hedef projeye sürüklemeye izin verilmemelidir. Sürükle ve bırak işleminin desteklenmediği durumlarda, IDE 'nin bırakmaya izin vermemesini ve kullanıcıya hiçbir zaman bırakma imlecini (aşağıdaki işaretçi tablosunda gösterilen) göstermesi gerekir.

  Sürükle ve bırak davranışını doğru bir şekilde uygulamak için, sürükleme işleminin kaynak projesi kendi yapısını (örneğin, başvuru veya dizin tabanlı mi?) hedef projeye iletmek için gereklidir. Bu bilgiler, kaynak tarafından sunulan Pano biçimiyle belirtilir. Bir sürükle (veya Pano kopyalama işleminin) kaynağı olarak, projenin başvuru tabanlı veya dizin tabanlı olmasına bağlı olarak, bir proje sırasıyla **CF_VSREFPROJECTITEM**S ya da **CF_VSSTGPROJECTITEMS** sunmalıdır. Bu biçimlerin her ikisi de aynı veri içeriğine sahiptir. Bu, dosya adları yerine, bu tür dizeler hariç Windows **CF_HDROP** biçimine benzer, **projref** dizelerinin ( **IVsSolution:: GetProjrefOfItem** veya **:: GetProjrefOfProject** öğesinden döndürülen) çift**null** sonlandırılmış bir listesidir.

  Bir bırakma (veya Pano yapıştırma işleminin) hedefi olarak, bir proje hem **CF_VSREFPROJECTITEMS** hem de **CF_VSSTGPROJECTITEMS**kabul etmelidir, ancak sürükle ve bırak işleminin tam olarak işlenmesi hedef projenin ve kaynak projenin doğasına göre farklılık gösterir. Kaynak proje, **CF_VSREFPROJECTITEMS** veya **CF_VSSTGPROJECTITEMS**sunup kendi yapısını bildirir. Bırakma hedefi kendi yapısını anlamıştır ve bu nedenle, bir taşıma, kopyalama veya bağlantının gerçekleştirilip gerçekleştirilmeyeceği konusunda kararlar almak için yeterli bilgiye sahip olur. Kullanıcı aynı zamanda CTRL, SHIFT veya CTRL ve Shift tuşlarına basarak hangi sürükle ve bırak işleminin gerçekleştirileceğini de değiştirir. Bırakma hedefinin, **DragEnter** ve **DragOver yöntemlerine göre** hangi işlemin gerçekleştirileceğini doğru şekilde belirtmesi önemlidir. **Çözüm Gezgini** , kaynak projenin ve hedef projenin aynı proje olup olmadığını otomatik olarak bilir.

  Proje öğelerini Visual Studio örnekleri arasında sürüklemek (örneğin, bir devenv.exe örneğinden diğerine) özellikle desteklenmez. **Çözüm Gezgini** ayrıca doğrudan bunu devre dışı bırakır.

  Kullanıcı her zaman bir öğe seçerek bir sürükle-bırak işleminin etkisini tespit etmelidir, hedef konuma sürükleyebilir ve öğe bırakılmadan önce aşağıdaki fare işaretçilerinden hangisinin göründüğünü gözlemleyebilmelidir:

|Fare işaretçisi|Komut|Açıklama|
|-------------------|-------------|-----------------|
|![Fare "bırakma yok" simgesi](../../extensibility/ux-guidelines/media/0706-01-mousenodrop.png "0706-01_MouseNoDrop")|Bırakma yok|Öğe belirtilen konuma bırakılamaz.|
|![Fare "Kopyala" simgesi](../../extensibility/ux-guidelines/media/0706-02-mousecopy.png "0706-02_MouseCopy")|Kopyala|Öğe hedef konuma kopyalanacak.|
|![Fare "taşı" simgesi](../../extensibility/ux-guidelines/media/0706-03-mousemove.png "0706-03_MouseMove")|Taşı|Öğe hedef konuma taşınacak.|
|![Fare "Başvuru Ekle" simgesi](../../extensibility/ux-guidelines/media/0706-04-mouseaddref.png "0706-04_MouseAddRef")|Başvuru ekleme|Hedef konuma seçili öğe için bir başvuru eklenecektir.|

#### <a name="reference-based-projects"></a>Başvuru tabanlı projeler
 Aşağıdaki tabloda, kaynak öğenin niteliği ve başvurulan temel hedef projeler için basılan değiştirici tuşları temelinde gerçekleştirilmesi gereken sürükle ve bırak (Ayrıca kesme/kopyalama/yapıştırma) işlemleri özetlenmektedir:

|Değiştirici|İşlem|Kaynak öğe: başvuru/bağlantı|Kaynak öğe: fiziksel öğe veya dosya sistemi (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Değiştirici yok|Eylem|Taşı|Bağlantı|
|Değiştirici yok|Hedef|Özgün öğeye başvuru ekler|Özgün öğeye başvuru ekler|
|Değiştirici yok|Kaynak|Özgün öğeye başvuruyu siler|Özgün öğeyi korur|
|Değiştirici yok|Sonuç|**DROPEFFECT_MOVE** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|**DROPEFFECT_LINK** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|
|SHIFT + sürükleyin|Eylem|Taşı|Bırakma yok|
|SHIFT + sürükleyin|Hedef|Özgün öğeye başvuru ekler|Bırakma yok|
|SHIFT + sürükleyin|Kaynak|Özgün öğeye başvuruyu siler|Bırakma yok|
|SHIFT + sürükleyin|Sonuç|**DROPEFFECT_MOVE** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|Bırakma yok|
|CTRL + sürükleyin|Eylem|Kopyala|Bırakma yok|
|CTRL + sürükleyin|Hedef|Özgün öğeye başvuru ekler|Bırakma yok|
|CTRL + sürükleyin|Kaynak|Özgün öğeye başvuruyu saklar|Bırakma yok|
|CTRL + sürükleyin|Sonuç|**DROPEFFECT_COPY** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|Bırakma yok|
|CTRL + SHIFT + sürükleyin|Eylem|Bağlantı|Bağlantı|
|CTRL + SHIFT + sürükleyin|Hedef|Özgün öğeye başvuru ekler|Özgün öğeye başvuru ekler|
|CTRL + SHIFT + sürükleyin|Kaynak|Özgün öğeye başvuruyu saklar|Özgün öğeyi korur|
|CTRL + SHIFT + sürükleyin|Sonuç|**DROPEFFECT_LINK** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|**DROPEFFECT_LINK** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|
|CTRL + SHIFT + sürükleyin|Not|Windows Gezgini 'ndeki kısayollar için sürükle ve bırak davranışı ile aynı.||
|Kes/Yapıştır|Eylem|Taşı|Bağlantı|
|Kes/Yapıştır|Hedef|Özgün öğeye başvuru ekler|Özgün öğeye başvuru ekler|
|Kes/Yapıştır|Kaynak|Özgün öğeye başvuruyu saklar|Özgün öğeyi korur|
|Kes/Yapıştır|Sonuç|Öğe, depolamada orijinal konumda kalıyor|Öğe, depolamada orijinal konumda kalıyor|
|Kopyala/Yapıştır|Eylem|Kopyala|Bağlantı|
|Kopyala/Yapıştır|Kaynak|Özgün öğeye başvuru ekler|Özgün öğeye başvuru ekler|
|Kopyala/Yapıştır|Sonuç|Özgün öğeye başvuruyu saklar|Özgün öğeyi korur|
|Kopyala/Yapıştır|Eylem|Öğe, depolamada orijinal konumda kalıyor|Öğe, depolamada orijinal konumda kalıyor|

#### <a name="directory-based-projects"></a>Dizin tabanlı projeler
 Aşağıdaki tabloda, kaynak öğenin doğası ve dizin tabanlı hedef projeler için basılan değiştirici tuşları temelinde gerçekleştirilmesi gereken sürükle ve bırak (Ayrıca kesme/kopyalama/yapıştırma) işlemleri özetlenmektedir:

|Değiştirici|İşlem|Kaynak öğe: başvuru/bağlantı|Kaynak öğe: fiziksel öğe veya dosya sistemi (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Değiştirici yok|Eylem|Taşı|Taşı|
|Değiştirici yok|Hedef|Öğeyi hedef konuma kopyalar|Öğeyi hedef konuma kopyalar|
|Değiştirici yok|Kaynak|Özgün öğeye başvuruyu siler|Özgün öğeye başvuruyu siler|
|Değiştirici yok|Sonuç|**DROPEFFECT_ taşıma** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|**DROPEFFECT_ taşıma** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|
|SHIFT + sürükleyin|Eylem|Taşı|Taşı|
|SHIFT + sürükleyin|Hedef|Öğeyi hedef konuma kopyalar|Öğeyi hedef konuma kopyalar|
|SHIFT + sürükleyin|Kaynak|Özgün öğeye başvuruyu siler|Öğeyi özgün konumdan siler|
|SHIFT + sürükleyin|Sonuç|**DROPEFFECT_ taşıma** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|**DROPEFFECT_ taşıma** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|
|CTRL + sürükleyin|Eylem|Kopyala|Kopyala|
|CTRL + sürükleyin|Hedef|Öğeyi hedef konuma kopyalar|Öğeyi hedef konuma kopyalar|
|CTRL + sürükleyin|Kaynak|Özgün öğeye başvuruyu saklar|Özgün öğeye başvuruyu saklar|
|CTRL + sürükleyin|Sonuç|**DROPEFFECT_ kopyalama** , öğesinden eylem olarak döndürüldü **::D ROP** ve öğe depolamada orijinal konumda kalıyor|**DROPEFFECT_ kopyalama** , öğesinden eylem olarak döndürüldü **::D ROP** ve öğe depolamada orijinal konumda kalıyor|
|CTRL + SHIFT + sürükleyin||Bırakma yok|Bırakma yok|
|Kes/Yapıştır|Eylem|Taşı|Taşı|
|Kes/Yapıştır|Hedef|Öğeyi hedef konuma kopyalar|Öğeyi hedef konuma kopyalar|
|Kes/Yapıştır|Kaynak|Özgün öğeye başvuruyu siler|Öğeyi özgün konumdan siler|
|Kes/Yapıştır|Sonuç|Öğe, depolamada orijinal konumda kalıyor|Öğe, depolama alanındaki özgün konumdan silindi|
|Kopyala/Yapıştır|Eylem|Kopyala|Kopyala|
|Kopyala/Yapıştır|Hedef|Özgün öğeye başvuru ekler|Öğeyi hedef konuma kopyalar|
|Kopyala/Yapıştır|Kaynak|Özgün öğeyi korur|Özgün öğeyi korur|
|Kopyala/Yapıştır|Sonuç|Öğe, depolamada orijinal konumda kalıyor|Öğe orijinal konum bileşenleri deposunda kalıyor|

#### <a name="mixed-target-projects"></a>Karma hedef projeler
 Aşağıdaki tabloda, kaynak öğenin doğası ve karma hedef projeler için basılan değiştirici tuşları temelinde gerçekleştirilmesi gereken sürükle ve bırak (Ayrıca kesme/kopyalama/yapıştırma) işlemleri özetlenmektedir:

|Değiştirici|İşlem|Kaynak öğe: başvuru/bağlantı|Kaynak öğe: fiziksel öğe veya dosya sistemi (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Değiştirici yok|Eylem|Taşı|Taşı|
|Değiştirici yok|Hedef|Özgün öğeye başvuru ekler|Öğeyi hedef konuma kopyalar|
|Değiştirici yok|Kaynak|Özgün öğeye başvuruyu siler|Özgün öğeye başvuruyu siler|
|Değiştirici yok|Sonuç|**DROPEFFECT_ taşıma** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|**DROPEFFECT_ taşıma** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumdan silindi|
|SHIFT + sürükleyin|Eylem|Taşı|Taşı|
|SHIFT + sürükleyin|Hedef|Özgün öğeye başvuru ekler|Öğeyi hedef konuma kopyalar|
|SHIFT + sürükleyin|Kaynak|Özgün öğeye başvuruyu siler|Öğeyi özgün konumdan siler|
|SHIFT + sürükleyin|Sonuç|**DROPEFFECT_ taşıma** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumda kalır|**DROPEFFECT_ taşıma** , öğesinden eylem olarak döndürülür **::D ROP** ve öğe depolamada orijinal konumdan silindi|
|CTRL + sürükleyin|Eylem|Kopyala|Kopyala|
|CTRL + sürükleyin|Hedef|Özgün öğeye başvuru ekler|Öğeyi hedef konuma kopyalar|
|CTRL + sürükleyin|Kaynak|Özgün öğeye başvuruyu saklar|Özgün öğeyi korur|
|CTRL + sürükleyin|Sonuç|**DROPEFFECT_ kopyalama** , öğesinden eylem olarak döndürüldü **::D ROP** ve öğe depolamada orijinal konumda kalıyor|**DROPEFFECT_ kopyalama** , öğesinden eylem olarak döndürüldü **::D ROP** ve öğe depolamada orijinal konumda kalıyor|
|CTRL + SHIFT + sürükleyin|Eylem|Bağlantı|Bağlantı|
|CTRL + SHIFT + sürükleyin|Hedef|Özgün öğeye başvuru ekler|Özgün kaynak öğesine başvuru ekler|
|CTRL + SHIFT + sürükleyin|Kaynak|Özgün öğeye başvuruyu saklar|Özgün öğeyi korur|
|CTRL + SHIFT + sürükleyin|Sonuç|**DROPEFFECT_ bağlantı** , öğesinden eylem olarak döndürülüyor **::D ROP** ve öğe depolamada orijinal konumda kalıyor|**DROPEFFECT_ bağlantı** , öğesinden eylem olarak döndürülüyor **::D ROP** ve öğe depolamada orijinal konumda kalıyor|
|Kes/Yapıştır|Eylem|Taşı|Taşı|
|Kes/Yapıştır|Hedef|Öğeyi hedef konuma kopyalar|Öğeyi hedef konuma kopyalar|
|Kes/Yapıştır|Kaynak|Özgün öğeye başvuruyu siler|Öğeyi özgün konumdan siler|
|Kes/Yapıştır|Sonuç|Öğe, depolamada orijinal konumda kalıyor|Öğe, depolama alanındaki özgün konumdan silindi|
|Kopyala/Yapıştır|Eylem|Kopyala|Kopyala|
|Kopyala/Yapıştır|Hedef|Özgün öğeye başvuru ekler|Öğeyi hedef konuma kopyalar|
|Kopyala/Yapıştır|Kaynak|Özgün öğeyi korur|Özgün öğeyi korur|
|Kopyala/Yapıştır|Sonuç|Öğe, depolamada orijinal konumda kalıyor|Öğe, depolamada orijinal konumda kalıyor|

 **Çözüm Gezgini**sürüklemeyi uygularken bu ayrıntılar dikkate alınmalıdır:

- Birden çok seçim senaryosu için tasarım.

- Dosya adları (tam yol) hedef proje genelinde benzersiz olmalıdır veya bırakmaya izin verilmemelidir.

- Klasör adları, bırakılmakta oldukları düzeyde benzersiz (büyük/küçük harf duyarsız) olmalıdır.

- Sürükleme sırasında açık veya kapalı olan dosyalar arasında davranış farklılıkları vardır (yukarıdaki senaryolarda bahsedilmez).

- Üst düzey dosyalar, klasörlerdeki dosyalardan biraz farklı davranır.

  ' Nin farkında olması için başka bir sorun da açık tasarımcı veya düzenleyicilerin bulunduğu öğelerde taşıma işlemlerinin nasıl işleneceği. Beklenen davranış aşağıdaki gibidir (Bu, tüm proje türleri için geçerlidir):

1. Açık düzenleyici/tasarımcı kaydedilmemiş değişiklikler içermiyorsa, düzenleyici/tasarımcı penceresi sessizce kapatılmalıdır.

2. Açık düzenleyici/tasarımcı, kaydedilmemiş değişikliklere sahip olursa, sürüklediğiniz kaynak bırakma işleminin gerçekleşmesini bekler ve ardından kullanıcıdan, aşağıdaki gibi bir istem ile pencereyi kapatmadan önce açık belgelerde kaydedilmemiş değişiklikleri kaydetmesini ister:

   ```
   ==========================================================
        One or more open documents have unsaved changes.
   Do you want to save uncommitted changes before proceeding?
                     [Yes]  [No]  [Cancel]
   ==========================================================
   ```

   Bu, kullanıcıya hedef kopyalarını yapmadan önce devam etmekte olan işleri kaydetme fırsatı sağlar. Bu işlemeyi etkinleştirmek için yeni bir **IVsHierarchyDropDataSource2:: OnBeforeDropNotify** yöntemi eklenmiştir.

   Hedef daha sonra öğenin durumunu depolama alanında olduğu gibi kopyalayacaktır (Kullanıcı **Hayır**' ı seçtiyse düzenleyicide kaydedilmemiş değişiklikleri dahil edilmez). Hedef kopyalamayı tamamladıktan sonra ( **IVsHierarchyDropDataSource::D ROP**), kaynak, taşıma işleminin silme bölümünü ( **IVsHierarchyDropDataSource:: ondropnotıfy**) tamamlamaya yönelik fırsat olarak sunulur.

   Kaydedilmemiş değişiklikleri olan düzenleyicilerin açık bırakılması gerekir. Kaydedilmemiş değişiklikleri olan bu belgeler için, taşıma işleminin kopyalama bölümünün gerçekleştirileceği, ancak silme bölümünün iptal edilmeyeceği anlamına gelir. Kullanıcı **Hayır**' ı seçtiğinde birden çok seçim senaryosunda, kaydedilmemiş değişiklikler içeren belgeler kapanmamalıdır veya kaldırılmamalıdır, ancak kaydedilmemiş değişiklikler olmaksızın kapanmamalıdır ve kaldırılmalıdır.
