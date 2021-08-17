---
title: Visual Studio için uygulama desenleri | Microsoft Docs
description: Visual Studio yeni özellikler için pencere kullanım desenleri de dahil olmak üzere belge pencereleri, araç pencereleri ve kalıcı iletişim kutuları arasındaki fark hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 189fcf6521daa9385dc2292d40e796d068c637a9a60c54562b52413b65f33b5a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400793"
---
# <a name="application-patterns-for-visual-studio"></a>Visual Studio İçin Uygulama Desenleri
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Pencere etkileşimleri

### <a name="overview"></a>Genel Bakış
Visual Studio ' de kullanılan iki ana pencere türü belge düzenleyicilerinde ve araç penceresdir. Nadir, ancak mümkün olan büyük, geçici olmayan iletişim kutulardır. Bunlar kabukta kalıcı olsalar da, desenleri temelde farklıdır. Bu bölüm belge pencereleri, araç pencereleri ve kalıcı iletişim kutuları arasındaki farkı ele alır. İletişim [kutularında](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)kalıcı iletişim kutusu desenleri ele alınmıştır.

### <a name="comparing-window-usage-patterns"></a>Pencere kullanım düzenlerini karşılaştırma
**Belge pencereleri** neredeyse her zaman belge kutusu içinde görüntülenir. Bu, belge düzenleyicisine bir "Orta aşama" verir ve ek araç pencerelerini etrafında düzenlemenizi sağlar.

Bir **araç penceresi** genellikle IDE 'nin kenarına karşı daraltılmış ayrı, daha küçük bir pencere olarak görüntülenir. Bu görünür, gizli veya otomatik gizli olabilir. Ancak bazen araç pencereleri, pencerede **pencere/sabitleme** özelliğinin denetlenerek belge kutusu içinde sunulur. bu, daha fazla gerçek bir tasarım kararı sağlar, ancak aynı zamanda ortak bir tasarım kararına sahiptir: Visual Studio ile tümleştirmeye çalıştığınızda, özelliğinizdeki bir araç penceresi mi yoksa bir belge penceresi mi görüntülemesi gerektiğine karar vermelisiniz.

Visual Studio **engelleyici olmayan iletişim kutuları** önerilmez. Çoğu kalıcı iletişim kutusu, tanım, kayan araç pencereleri ve bu şekilde uygulanmalıdır. Kabuk tarafına yerleştirilmiş normal bir araç penceresinin boyutunun çok sınırlandırabileceği durumlarda kalıcı iletişim kutularına izin verilir. Ayrıca, kullanıcının iletişim kutusunu ikincil bir monitöre taşıyabileceği durumlarda bunlara izin verilir.

İhtiyaç duyduğunuz kapsayıcı türünü dikkatle düşünün. UI tasarımıyla ilgili yaygın kullanım deseninin konuları aşağıdaki tabloda verilmiştir.

||Belge penceresi|Araç penceresi|Kalıcı olmayan iletişim kutusu|
|-|---------------------|-----------------|---------------------|
| **Position** (Pozisyon) | Her zaman belge içinde konumlandırılır ve IDE 'nin kenarlarını sabitlemez. Ana kabuktan ayrı olarak kayan olması için "çekiliyor" olabilir. | Genellikle IDE 'nin kenarları etrafında yerleştirilmiş, ancak kayan, otomatik gizli (ayrılmış) veya belge kutusu içine yerleştirilmiş olacak şekilde özelleştirilebilir.|IDE 'den ayrı olan büyük kayan pencere. |
| **Modeli Yürüt** | *Gecikmeli tamamlama*<br /><br /> Verileri bir belgeye kaydetmek için kullanıcının **dosyayı &gt; kaydetmesi**, **farklı kaydet** veya **Tümünü Kaydet** komutunu vermesi gerekir. Belge penceresi, "dirbağlı" olarak bulunan ve Kaydet komutlarından birine taahhüt edilen verilerin kavramıdır. Bir belge penceresi kapatılırken tüm içerikler diske kaydedilir veya kaybedilir. | *Anında yürütme*<br /><br /> Hiçbir kaydetme modeli yok. Bir dosyayı düzenlemede yardımcı olan Inspector araç pencereleri için, dosyanın etkin düzenleyici veya tasarımcı 'da açık olması ve düzenleyici ya da tasarımcı kaydetme 'nin sahibi olması gerekir. | *Gecikmeli veya anında yürütme*<br /><br /> Genellikle, büyük bir kalıcı olmayan iletişim kutusu, değişiklikleri yürütmek için bir eylem gerektirir ve iletişim kutusu oturumunda yapılan değişiklikleri geri kaydeden bir "Iptal" işlemine izin verir.  Bu, bir araç penceresinden kalıcı olmayan bir iletişim kutusunu bu şekilde fark eden, Windows her zaman hemen bir yürütme modeline sahiptir. |
| **Görünürlük** | *Aç/oluştur (dosya) ve Kapat*<br /><br /> Belge pencerelerini açmak, mevcut bir belge açılarak ya da yeni bir belge oluşturmak için şablon kullanılarak yapılır. "Open \<specific editor> " komutu yoktur. | *Gizleme ve gösterme*<br /><br /> Tek örnekli araç pencereleri gizlenebilir veya gösteriliyor olabilir. Araç penceresi içindeki içerikler ve durumlar görünüm veya gizli olup olmadığını kalıcı hale getirin. Çok örnekli araç pencereleri de kapatılabilir ve gizli olabilir. Çok örnekli bir araç penceresi kapatıldığında, araç penceresi içindeki içerik ve durum atılır. | *Bir komuttan başlatılan*<br /><br /> İletişim kutuları, görev tabanlı bir komuttan başlatılır. |
| **Örnekler** | *Çoklu örnek*<br /><br /> Birkaç düzenleyici aynı anda açılabilir ve farklı dosyalar düzenlenebilir, ancak bazı düzenleyiciler aynı dosyanın birden fazla düzenleyicide açılmasını da sağlar ( **pencere &gt; yeni pencere** komutu kullanılarak).<br /><br /> tek bir düzenleyici bir veya birden çok dosyayı aynı anda (Project tasarımcı) düzenlenebilir olabilir. | *Tek veya çok örnekli*<br /><br /> İçerik, bağlamı yansıtacak şekilde değişir (özellik tarayıcısında olduğu gibi) veya odağı/bağlamı diğer pencereler (Görev Listesi, Çözüm Gezgini) ile gönderin.<br /><br /> Tek örnekli ve çok örnekli araç pencereleri, önemli bir neden olmadıkça, etkin belge penceresiyle ilişkilendirilmelidir. | *Tek örnekli* |
| **Örnekler** | Kod Düzenleyicisi gibi **metin düzenleyicileri**<br /><br /> Form Tasarımcısı veya modelleme yüzeyi gibi **tasarım yüzeyleri**<br /><br /> Bildirim Tasarımcısı gibi **iletişim kutularına benzer Denetim düzenleri** | **Çözüm Gezgini** , çözüm içinde yer alan bir çözüm ve proje sağlar<br /><br /> **Sunucu Gezgini** , kullanıcının pencerede açılmasını seçtiği sunucuların ve veri bağlantılarının hiyerarşik bir görünümünü sağlar. Veritabanı hiyerarşisinden bir sorgu gibi bir nesne açmak, bir belge penceresi açar ve kullanıcının sorguyu düzenlemesine izin verir.<br /><br /> **Özellik tarayıcısı** , bir belge penceresinde veya başka bir araç penceresinde seçilen nesne için özellikleri görüntüler. Özellikler, hiyerarşik kılavuz görünümünde veya karmaşık iletişim kutusu benzeri denetimlerde sunulur ve kullanıcının bu özellikler için değerleri ayarlamaya izin verir. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Araç pencereleri

### <a name="overview"></a>Genel Bakış
Araç pencereleri, kullanıcının belge penceresinde gerçekleşen işini destekler. Visual Studio sağladığı ve işleyebilecekleri temel bir kök nesneyi temsil eden bir hiyerarşiyi göstermek için kullanılabilirler.

IDE 'de yeni bir araç penceresi düşünürken yazarların şunları yapmanız gerekir:

- Görev için uygun olan araç pencerelerini kullanın ve benzer işlevlerle yenilerini oluşturun. Yeni araç pencereleri yalnızca, benzer bir pencereyle tümleştirilebilen önemli ölçüde farklı bir "araç" veya işlevsellik sunduklarında ya da mevcut bir pencereyi bir Özet hub 'ına çevirip oluşturulmamalıdır.

- Gerekirse, araç penceresinin üst kısmında standart bir komut çubuğu kullanın.

- Denetim sunusu ve klavye gezintisi için diğer araç pencerelerinin zaten mevcut desenlerle tutarlı olun.

- Diğer araç pencerelerinin denetim sunumlarıyla tutarlı olun.

- Belgeye özgü araç pencerelerini mümkün olduğunda otomatik görünür hale getirin, böylece yalnızca üst belge etkinleştirildiğinde görünürler.

- Pencere içeriğinin klavyeden gezindiğinden emin olun (destek ok tuşları).

#### <a name="tool-window-states"></a>Araç penceresi durumları
Visual Studio araç pencereleri, bazıları kullanıcı etkin olan farklı durumlara sahiptir (otomatik gizleme özelliği gibi). Otomatik görünür gibi diğer durumlar, araç pencerelerinin doğru bağlamda görünmesine izin verir ve gerekli olmadığında gizleyin. Toplamda beş araç penceresi durumu vardır.

- **Sabitlenmiş/sabitlenmiş** araç pencereleri, belge alanının dört taraflarından herhangi birine iliştirilebilir. Raptiye simgesi araç penceresi başlık çubuğunda görünür. Araç penceresi, kabuğun ve diğer araç pencerelerinin kenarına yatay veya dikey olarak yerleştirilebilir ve ayrıca sekme bağlantılı olabilir.

- **Otomatik gizli** araç pencereleri sabitlenmemiş. Pencere, belge alanının kenarında bir sekmeden (araç penceresi ve onun simgesiyle birlikte) görüşün dışına çıkmanıza izin verebilir. Araç penceresi, bir Kullanıcı sekmenin üzerine geldiğinde slaytlar çıkar.

- **Otomatik görünür** araç pencereleri, bir düzenleyici gibi başka bir kullanıcı arabirimi parçası başlatıldığında veya odaklandığında otomatik olarak görünür.

- **Kayan** araç pencereleri IDE dışında hareket ettirildiğinde. Bu, birden çok izleyici yapılandırması için kullanışlıdır.

- **Sekmeli belge** aracı pencereleri, belge kutusu içine yerleştirilebilir. Bu, Nesne Tarayıcısı gibi büyük araç pencereleri için kullanışlıdır. Bu, çerçevenin kenarlarına takmaya kıyasla daha fazla gerçek bir emlak gerektiren bir seçenektir.

![Araç penceresi Visual Studio durumları](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Araç penceresi Visual Studio durumları

#### <a name="single-instance-and-multi-instance"></a>Tek örnekli ve çoklu örnek
Araç pencereleri tek örnekli veya çok örneklidir. Bazı tek örnekli araç pencereleri etkin belge penceresiyle ilişkilendirilirken, çok örnekli araç pencereleri ilişkili değildir. Çok örnekli araç pencereleri, pencerenin **&gt; yeni bir örneğini** oluşturarak Window New Window komutuna yanıt verir. Aşağıdaki görüntüde, pencerenin bir örneği etkin olduğunda Yeni Pencere komutunu etkinleştiren bir araç penceresi gösterilir:

![Pencere örneği etkin olduğunda 'Yeni Pencere' komutunu etkinleştiren araç penceresi](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Pencere örneği etkin olduğunda 'Yeni Pencere' komutunu etkinleştiren araç penceresi

Tek örnekli araç pencereleri gizlenirken veya gösterken, çok örnekli araç pencereleri hem kapat hem de gizlenir. Tüm araç pencereleri yuvalanır, sekme bağlantılı, kayan veya Multiple-Document Arabirimi (MDI) alt penceresi olarak (belge penceresine benzer) olarak ayarlanır. Tüm araç pencereleri, Pencere menüsündeki uygun pencere yönetimi komutlarına yanıt ver verebiliyor:

![Visual Studio Window menüsündeki pencere yönetimi komutları](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Visual Studio Window menüsündeki pencere yönetimi komutları

#### <a name="document-specific-tool-windows"></a>Belgeye özgü araç pencereleri
Bazı araç pencereleri, belirli bir belge türüne göre değişecek şekilde tasarlanmıştır. Bu pencereler, IDE'de etkin belge penceresi için geçerli olan işlevselliği yansıtacak şekilde sürekli olarak güncelleştirmesi.

İçerikleri seçilen düzenleyiciyi yansıtacak şekilde değişen araç pencerelerine örnek olarak Araç Kutusu ve Belge Ana Hatları yer almaktadır. Bu pencereler, pencereye bağlam sun göstermeyen bir düzenleyicinin odağı olduğunda bir filigran gösterir.

#### <a name="navigable-list-tool-windows"></a>Gezinilebilir liste aracı pencereleri
Bazı araç pencereleri, kullanıcının etkileşimde bulunarak gezinilebilir öğelerin listesini görüntüler. Bu tür bir pencerede, pencere etkin olsa bile listede mevcut öğe için her zaman geri bildirim olması gerekir. Liste, pencerede seçili olan öğeyi de değiştirerek **GoToNextLocation** ve **GoToPrevLocation** komutlarına yanıt verilmelidir

Gezinilebilir liste aracı pencerelerinin örnekleri, Çözüm Gezgini ve Sonuçları Bul penceresidir.

### <a name="tool-window-types"></a>Araç penceresi türleri

#### <a name="common-tool-windows-and-their-functions"></a>Ortak araç pencereleri ve işlevleri

**Hiyerarşik araç pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Çözüm Gezgini | Projelerde, çeşitli dosyalarda ve çözüm öğelerinde yer alan belgelerin listesini görüntüleyen hiyerarşik ağaç. Proje içindeki öğelerin görüntüsü, proje türünün sahibi olan paket tarafından tanımlanır (örneğin, başvuru tabanlı, dizin tabanlı veya karma mod türleri). |
| Sınıf Görünümü | Dosyaların kendilerinden bağımsız olarak, çalışma belge kümesinde sınıfların ve çeşitli öğelerin hiyerarşik ağacı. |
| Sunucu Gezgini | Çözümde tüm sunucuları ve veri bağlantılarını görüntüleyen hiyerarşik ağaç. |
| Belge Anahattı | Etkin belgenin hiyerarşik yapısı. |

**Kılavuz aracı pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Özellikler | Seçili nesne için özelliklerin listesini ve bu özellikleri düzenlemek için değer seçicileri görüntüleyen kılavuz. |
| Görev Listesi | Kullanıcının görev ve açıklama oluşturma/düzenleme/silme gerçekleştirmesi için bir kılavuz. |

**İçerik aracı pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Help | Kullanıcıların "Nasıl Yapabilirim?" üzerinden çeşitli yardım alma yöntemlerine erişmelerini sağlayan bir pencere videolarını MSDN forumlarına gönderin. |
| Dinamik Yardım | Geçerli seçime uygun yardım konularının bağlantılarını görüntüleyen bir araç penceresi. |
| Nesne Tarayıcısı | Sol bölmede hiyerarşik nesne bileşenlerinin ve sağ sütundaki nesnenin özellikleriyle yöntemlerinin listesini içeren iki sütunlu bir çerçeve kümesi. |

**İletişim kutusu araç pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Bul | Kullanıcının çözüm içindeki çeşitli dosyaları bulup değiştirmesini sağlayan bir iletişim kutusu. |
| Gelişmiş Bul | Kullanıcının çözüm içindeki çeşitli dosyaları bulup değiştirmesini sağlayan bir iletişim kutusu. |

**Diğer araç pencereleri**

::: moniker range="vs-2017"

| Araç penceresi | İşlev |
| --- | --- |
| Araç Kutusu | Tasarım yüzeyleri üzerine bırakacak öğeleri depolamak için kullanılan araç penceresi, tüm tasarımcılar için tutarlı bir sürükle kaynak sağlar. |
| Başlangıç Sayfası | Geliştirici haberlerinin akışlarına, Visual Studio ve son projelere erişimi olan Visual Studio portalı. Kullanıcılar ayrıca "Common7\IDE\StartPages Visual Studio program dosyaları dizininden StartPage.xaml dosyasını Visual Studio belgeleri dizinindeki StartPages klasörüne kopyalayıp XAML'i el ile düzenleyerek veya Visual Studio veya başka bir kod düzenleyicisinde açarak özel başlangıç sayfaları \" oluşturabilir. |

::: moniker-end

::: moniker range=">=vs-2019"

| Araç penceresi | İşlev |
| --- | --- |
| Araç Kutusu | Tasarım yüzeyleri üzerine bırakacak öğeleri depolamak için kullanılan araç penceresi, tüm tasarımcılar için tutarlı bir sürükle kaynak sağlar. |

::: moniker-end

**Hata ayıklayıcı aracı pencereleri**

| Araç penceresi | İşlev |
| --- | --- |
| Otomobil ||
| Hemen ||
| Çıktı | Çıkış penceresi, bildirilebilecek metin olayları veya durumunuz olduğunda kullanılabilir. |
| Bellek ||
| Kesme noktaları ||
| Çalışma ||
| Belgeler ||
| Çağrı Yığını ||
| Yerli ||
| Saatler ||
| Demontaj ||
| Kayd -eder ||
| İş Parçacıkları ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Belge düzenleyicisi kuralları

### <a name="document-interactions"></a>Belge etkileşimleri
"Belge kutusu", IDE içindeki en büyük alandır ve kullanıcının ek araç pencerelerinden yardım alarak görevlerini tamamlamak için dikkatini odakta olduğu yerdir. Belge düzenleyicileri, kullanıcının açtığı ve çalışma alanı içinde kaydeden temel iş Visual Studio. Bunlar, diğer etkin hiyerarşi pencerelerine veya Çözüm Gezgini güçlü bir seçim anlayışını korur. Kullanıcı bu hiyerarşi pencerelerinden birini işaret ediyor ve belgenin nerede yer içerdiğini ve çözümle, projeyle ya da bir Visual Studio paketi tarafından sağlanan başka bir kök nesneyle ilişkisini biliyor olmalıdır.

Belge düzenleme tutarlı bir kullanıcı deneyimi gerektirir. Kullanıcının pencere yönetimi ve komutları bulmak yerine, sahip olduğu göreve odaklanmasına izin vermek için, bu belge türünü düzenlemek için kullanıcı görevlerine en uygun belge görünümü stratejisini seçin.

#### <a name="common-interactions-for-the-document-well"></a>Belge için ortak etkileşimler

- Ortak Yeni Dosya ve Açık Dosya deneyimlerinden **tutarlı bir** **etkileşim modeli** elde edin.

- Belge penceresi açıldığında ilgili pencerelerde ve menülerde ilgili işlevleri güncelleştirin.

- Menü komutları Düzenle, Biçimlendir ve Görüntüle menüleri **gibi** ortak **menülerle** uygun şekilde **tümleştirilmiştir.** Çok fazla özel komut varsa yeni bir menü oluşturulabilir. Bu yeni menü yalnızca belgenin odağı olduğunda görünür olmalıdır.

- Düzenleyicinin en üstüne eklenmiş bir araç çubuğu yer almaktadır. Bu, düzenleyicinin dışında görünen ayrı bir araç çubuğuna sahip olmak için tercih edilir.

- Her zaman bir seçimi Çözüm Gezgini hiyerarşi penceresinde sürdürün.

- Dosyanın içinde bir belgeye çift Çözüm Gezgini Aç ile aynı eylemi **gerçekleştirmesi gerekir.**

- Bir belge türünde birden fazla düzenleyici kullanılabilirse, kullanıcı dosyaya sağ tıklar ve kısayol menüsünden  Birlikte Aç'ı seçerek Birlikte Aç iletişim  kutusunu kullanarak belirli bir belge türünde varsayılan eylemi geçersiz kabilecek veya sıfırlayabilecektir.

- Belge içinde sihirbaz oluşturma.

### <a name="user-expectations-for-specific-document-types"></a>Belirli belge türleri için kullanıcı beklentileri
Birkaç farklı temel belge düzenleyicisi türü vardır ve her biri aynı türde diğerleriyle tutarlı bir etkileşim kümesine sahip olur.

- **Metin tabanlı düzenleyici: kod** düzenleyicisi, günlük dosyaları

- **Tasarım yüzeyi:** WPF formları tasarımcısı, Windows formları

- **İletişim kutusu stili düzenleyici:** Bildirim Tasarımcısı, proje özellikleri

- **Model tasarımcısı: iş** akışı tasarımcısı, kod haritası, mimari diyagramı, ilerleme

Belgeyi iyi kullanan çeşitli düzenleyici dışı türler de vardır. Belgeleri kendileri düzenlemezler ancak belge pencereleri için standart etkileşimleri izlemeleri gerekir.

- **Raporlar:** IntelliTrace raporu, Hyper-V raporu, profil oluşturma raporu

- **Pano:** Tanılama Hub'ı

#### <a name="text-based-editors"></a>Metin tabanlı düzenleyiciler

- Belge önizleme sekmesi modeline katılarak belgeyi açmadan önizlemeye olanak sağlar.

- Belgenin yapısı, belge ana hatları gibi bir yardımcı araç penceresinde temsil olabilir.

- IntelliSense (uygunsa) diğer kod düzenleyicileriyle tutarlı bir şekilde davranır.

- Açılır pencere veya yardımcı kullanıcı arabirimi, CodeLens gibi mevcut benzer kullanıcı arabirimi için benzer stilleri ve desenleri takip eder.

- Belge durumuyla ilgili iletiler, belgenin üst kısmında veya durum çubuğunda bir bilgi çubuğu denetiminde sunulacaktır.

- Kullanıcı, paylaşılan Yazı Tipleri ve Renkler sayfasını **veya** düzenleyiciye özgü > Araçlar ve Seçenekler sayfasını kullanarak yazı tiplerinin ve renklerin görünümünü özelleştirenene sahip olması gerekir.

#### <a name="design-surfaces"></a>Tasarım yüzeyleri

- Boş bir tasarımcının yüzeyde nasıl çalışmaya başlay gerektiğini belirten bir filigran olması gerekir.

- Görünüm değiştirme mekanizmaları, bir kod düzenleyicisini açmak için çift tıklama gibi mevcut desenleri veya belge penceresindeki sekmeleri kullanarak her iki bölmeyle de etkileşime olanak sağlar.

- Son derece özel bir araç penceresi gerekli olmadığı sürece tasarım yüzeyine öğe ekleme Araç Kutusu aracılığıyla yapılması gerekir.

- Yüzeydeki öğeler tutarlı bir seçim modelini takip eder.

- Katıştırılmış araç çubukları yalnızca belgeye özgü komutlar içerir; Kaydet gibi yaygın komutlar **değildir.**

#### <a name="dialog-style-editors"></a>İletişim kutusu stili düzenleyiciler

- Denetim düzeni normal iletişim kutusu düzeni kurallarına uymalı.

- Düzenleyici içindeki sekmeler belge sekmelerinin görünümüyle eşleşmez, izin verilen iki iç sekme stiliyle eşleşmeleri gerekir.

- Kullanıcıların yalnızca klavye kullanarak denetimlerle etkileşim kurabilecek olması gerekir; düzenleyiciyi etkinleştirerek ve denetimler aracılığıyla sekmeyle ya da standart mnemonics kullanarak.

- Tasarımcı ortak Kaydet modelini kullandır. Genel kaydet veya işleme düğmeleri yüzeye yerleştirilmaz, ancak diğer düğmeler uygun olabilir.

#### <a name="model-designers"></a>Model tasarımcıları

- Boş bir tasarımcının yüzeyde nasıl çalışmaya başlay gerektiğini belirten bir filigran olması gerekir.

- Tasarım yüzeyine öğe eklemenin Araç Kutusu aracılığıyla yapılması gerekir.

- Yüzeydeki öğeler tutarlı bir seçim modelini takip eder.

- Katıştırılmış araç çubukları yalnızca belgeye özgü komutlar içerir; Kaydet gibi yaygın komutlar **değildir.**

- Ekranda gösterge veya filigran gibi bir gösterge görünebilir.

- Kullanıcı, paylaşılan Yazı Tipleri ve Renkler sayfasını veya düzenleyiciye özgü bir **>** Araçlar ve Seçenekler sayfasını kullanarak yazı tiplerinin/renklerin görünümünü özelleştirene sahip olması gerekir.

#### <a name="reports"></a>Raporlar

- Raporlar genellikle yalnızca bilgidir ve Kaydet modeline katılmaz. Ancak, genişletilen ve daraltan diğer ilgili bilgilerin veya bölümlerin bağlantıları gibi etkileşim içerebilirler.

- Yüzeydeki çoğu komut, düğmeler değil köprüler olabilir.

- Düzen bir üst bilgi içermeli ve standart rapor düzeni yönergelerini izlemeli.

#### <a name="dashboards"></a>Panolar

- Panoların kendi kendilerine bir etkileşim modeli vardır ancak farklı araçlar sunabilirsiniz.

- Modeli kaydet'e katılmaz.

- Kullanıcıların düzenleyiciyi etkinleştirerek ve denetimler aracılığıyla sekmeyle ya da standart mnemonics kullanarak yalnızca klavye kullanarak denetimlerle etkileşim kurabilecekleri gerekir.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Diyalog

### <a name="introduction"></a>Giriş
Çalışma Visual Studio iletişim kutuları genellikle kullanıcının çalışması için ayrı bir birimi desteklemeli ve sonra da bu birim çıkarılır.

bir iletişim kutusuna ihtiyacınız olduğunu belirlediyebilirsiniz, tercih sırasına göre üç seçeneğiniz vardır:

1. Özelliklerinizi, Visual Studio'daki paylaşılan iletişim kutularıyla tümleştirin.

2. Mevcut benzer bir iletişim kutusunda bulunan deseni kullanarak kendi iletişim kutusunu oluşturun.

3. Etkileşim ve düzen yönergelerini takip eden yeni bir iletişim kutusu oluşturun.

Bu bölümde, iş akışlarında doğru iletişim kutusu deseninin Visual Studio ve iletişim kutusu tasarımı için ortak kuralların nasıl seçkili olduğu açıktır.

### <a name="themes"></a>Temalar
Aşağıdaki iletişim Visual Studio iki temel stilden birini takip eder:

#### <a name="standard-unthemed"></a>Standart (unthemed)
İletişim kutularının çoğu standart yardımcı iletişim kutularıdır ve bunların birikmiş olması gerekir. Ortak denetimleri yeniden şablonlaştırarak veya stilleştirilmiş "modern" düğmeler veya denetimler oluşturma girişiminde bulundurarak. Denetimler ve chrome görünümü, [iletişim kutuları Windows Desktop etkileşim yönergelerini izleyin.](/windows/desktop/uxguide/win-dialog-box)

#### <a name="themed"></a>Temalı
Özel "imza" iletişim kutuları, themed olabilir. Stille ilişkili bazı özel etkileşim desenlerine de sahip olan, themed iletişim kutuları ayrı bir görünüme sahiptir. İletişim kutusu yalnızca şu gereksinimleri karşılarsa temaya ekleyin:

- İletişim kutusu sık görülen ve kullanılan yaygın bir deneyimdir veya birçok kullanıcı tarafından (örneğin, Yeni oturum **açma Project** kullanılır.

- İletişim kutusu, öne çıkan ürün markası öğelerini (örneğin, Hesap adı **Ayarlar** içerir).

- İletişim kutusu, diğer themed iletişim kutularını (örneğin, Bağlı Hizmet Ekle iletişim kutusu) içeren daha büyük bir akışın **ayrılmaz bir parçası olarak** görünür.

- İletişim kutusu, bir ürün sürümünün tanıtımında veya farklılığında stratejik bir rol oynayan bir deneyimin önemli bir bölümüdür.

Bir themed iletişim kutusu oluştururken uygun ortam renklerini kullanın ve doğru düzen ve etkileşim desenlerini izleyin. [(Bkz. Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)düzeni.)

### <a name="dialog-design"></a>İletişim kutusu tasarımı
İyi tasarlanmış iletişim kutuları aşağıdaki öğeleri dikkate alır:

- Desteklenen kullanıcı görevi

- İletişim kutusu metin stili, dili ve terminolojisi

- Denetim seçimi ve kullanıcı arabirimi kuralları

- Görsel düzeni belirtimi ve denetim hizalaması

- Klavye erişimi

#### <a name="content-organization"></a>İçerik kuruluşu
Bu temel iletişim kutusu türleri arasındaki farkları göz önünde bulundurabilirsiniz:

- [Basit iletişim kutuları,](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) denetimleri tek bir kalıcı pencerede gösterir. Sunu, alan seçici veya simge çubuğu gibi karmaşık denetim desenlerinin çeşitlemelerini içerebilir.

- [Katmanlı iletişim kutuları,](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) tek bir kullanıcı arabirimi parçası birden çok denetim grubu içerirken ekran emlaklarından en iyi şekilde emin olmak için kullanılır. İletişim kutusunun gruplamaları sekme denetimleri, gezinti listesi denetimleri veya düğmeler aracılığıyla "katmanlıdır"; böylece kullanıcı herhangi bir anda hangi gruplamanın göreceğini seçebilir.

- [Sihirbazlar,](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) kullanıcıya bir görevin tamamlanmasına yönelik mantıksal bir adım dizisi aracılığıyla yönlendiren yararlı olur. Sıralı panellerde bir dizi seçenek sunulur ve bazen önceki panelde yapılan seçime bağlı olarak farklı iş akışları ("dallar") sunulur.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Basit iletişim kutuları
Basit bir iletişim kutusu, denetimlerin tek bir kalıcı pencerede sunumu sağlar. Bu sunu, alan seçici gibi karmaşık denetim desenlerinin çeşitlemelerini içerebilir. Basit iletişim kutuları için standart genel düzeni ve karmaşık denetim gruplamaları için gereken belirli düzenleri izleyin.

![>Adı Anahtarı Oluştur seçeneği, Visual Studio'da basit bir iletişim kutusu örneğidir.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Create Strong Name Key ( Güçlü Ad Anahtarı Oluştur) seçeneği, Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Katmanlı iletişim kutuları
Katmanlı iletişim kutuları sekmeleri, panoları ve ekli ağaçları içerir. Bunlar, tek bir kullanıcı arabiriminde sunulan birden çok denetim grubu olduğunda, emlakları en üst düzeye çıkarmak için kullanılır. Kullanıcı herhangi bir anda hangi gruplamayı göreceğini seçesin diye gruplamalar katmanlıdır.

En basit durumda, gruplamalar arasında geçiş mekanizması bir sekme denetimidir. Çeşitli alternatifler mevcuttur. En uygun stili seçme hakkında bilgi için bkz. Öncelik belirleme ve katmanlama.

Araçlar **Seçenekleri &gt; iletişim** kutusu, ekli ağaç kullanan katmanlı iletişim kutusunun bir örneğidir:

![Araçlar > Seçenekler, verilerde katmanlı iletişim kutusu Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Araçlar > Seçenekler, verilerde katmanlı iletişim kutusu Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> Sihirbaz
Sihirbazlar, bir görevi tamamlarken kullanıcıya mantıksal bir adım dizisi aracılığıyla yol gösterir. Sıralı panellerde bir dizi seçenek sunulur ve kullanıcının bir sonraki adıma devam etmeden önce her adımda devam etmek zorunda olması gerekir. Yeterli varsayılan değerler kullanılabilir olduğunda **Son** düğmesi etkinleştirilir.

 Kalıcı sihirbazlar, şu görevler için kullanılır:

- Kullanıcı seçimlerini bağlı olarak farklı yolların sun olduğu dallama içerir

- Sonraki adımların önceki adımlardan gelen kullanıcı girişine bağlı olduğu adımlar arasındaki bağımlılıkları içerir

- Sunulan seçimleri ve her adımda olası sonuçları açıklamak için kullanıcı arabiriminin kullanılamaları yeterince karmaşıktır

- İşlemseldir ve herhangi bir değişiklik işlenmeden önce bir dizi adımın tamamının tamamlanması gerekir

### <a name="common-conventions"></a>Ortak kuralları
İletişim kutularınız ile en iyi tasarımı ve işlevselliği elde etmek için iletişim kutusu boyutu, konumu, standartları, denetim yapılandırması ve hizalaması, kullanıcı arabirimi metni, başlık çubukları, denetim düğmeleri ve erişim anahtarları ile ilgili bu kuralları izleyin.

Yerleşime özgü yönergeler için [bkz. Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)için düzen.

#### <a name="size"></a>Boyut
İletişim kutuları en az 1024x768 ekran çözünürlüğüne sığmalı ve ilk iletişim kutusu boyutu 900x700 pikseli aşmamalı. İletişim kutuları yeniden boyutlandırılabilir, ancak bu bir gereksinim değildir.

Yeniden boyutlandırılabilir iletişim kutuları için iki öneri vardır:

1. Bu minimum boyut, denetim kümesi için kırpma olmadan iyileştirilen ve makul yerelleştirme büyümesine uyum sağlayacak şekilde ayarlayacak iletişim kutusu için tanımlanmış bir boyutdur.

2. Kullanıcı ölçeğinde boyutun oturumdan oturuma kalıcı olduğunu. Örneğin, kullanıcı bir iletişim kutusunu %150'ye ölçeklendirse, iletişim kutusunun sonraki başlatması %150'de görüntülenir.

#### <a name="position"></a>Konum
İletişim kutuları, ilk başlatmada IDE'nin ortalarında görün gerekir. Yeniden boyutlandırılamaz iletişim kutularının son konumunun kalıcı olması gerek değildir, bu nedenle sonraki başlatmalarda ortalarda görünürler.

Yeniden boyutlandırılabilir iletişim kutuları için, sonraki başlatmalarda boyut kalıcı hale gerekir. Yeniden boyutlandırılabilir kalıcı iletişim kutuları için konumun kalıcı olması gerek değildir. Bunları IDE'nin ortalarında görüntülemek, iletişim kutusunun, kullanıcının görüntü yapılandırması değiştirilse öngörülemeyen veya kullanılamaz bir konumda görünme olasılığını önler.

Yeniden konumlandırılab olan modeless iletişim kutuları için, iletişim kutusu daha büyük bir iş akışının ayrılmaz bir parçası olarak sık sık kullanılab olabileceği için, sonraki başlatmalarda kullanıcının konumu korunarak korundu.

İletişim kutularının başka iletişim kutuları oluşturması gerektiği zaman, kullanıcıya yeni bir yere gidilene kadar en üstteki iletişim kutusu sağdan ve aşağı basamaklamalı.

#### <a name="modality"></a>Modalite
Kalıcı olmak, kullanıcıların devam etmeden önce iletişim kutusunu tamamlaması veya iptal ettiği anlamına gelir. Kalıcı iletişim kutuları kullanıcının ortamın diğer bölümleriyle etkileşim kurması engellenmiş olduğu için, özelliğinizin görev akışı bunları mümkün olduğunca az kullanmalıdır. Kalıcı bir işlem gerektiğinde, Visual Studio bir dizi paylaşılan iletişim kutusu olduğunda özelliklerinizi tümleştirin. Yeni bir iletişim kutusu oluşturmanız gerekirse, benzer işlevlere sahip mevcut bir iletişim kutusunun etkileşim desenini izleyin.

Kullanıcıların aynı anda yeni kod yazarken  Bul  ve Değiştir gibi iki etkinlik gerçekleştirmesi gerektiği zaman, kullanıcının aralarında kolayca geçiş yapmak için iletişim kutusunun modersız olması gerekir. Visual Studio düzenleyiciyi destekleyen bu tür bağlantılı görev için genellikle araç pencerelerini kullanır.

#### <a name="control-configuration"></a>Yapılandırmayı denetleme
Aynı şeyi aynı şekilde gerçekleştiren mevcut denetim yapılandırmaları ile tutarlı Visual Studio.

#### <a name="title-bars"></a>Başlık çubukları

- Başlık çubuğundaki metin, onu başlatan komutun adını yansıtmalı.

- İletişim kutusu başlık çubuklarında simge kullanılmamalı. Sistemin bir tane gerektirdiği durumlarda, Visual Studio kullanın.

- İletişim kutuları simge durumuna küçült veya ekranı kapla düğmelerine sahip olmayabilir.

- Başlık çubuğundaki yardım düğmeleri kullanım dışıdır. Bunları yeni iletişim kutularına ekleme. Mevcut olduğunda, kavramsal olarak görevle ilgili bir Yardım konusu başlatmaları gerekir.

  ![Visual Studio iletişim kutularında başlık çubukları için Visual Studio belirtimleri](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Visual Studio iletişim kutularında başlık çubukları için Visual Studio belirtimleri

#### <a name="control-buttons"></a>Denetim düğmeleri
Genel olarak, **Tamam** **,** İptal **ve** Yardım düğmeleri iletişim kutusunun sağ alt köşesinde yatay olarak düzen gerekir. İletişim kutusunun alt kısmında denetim düğmeleriyle görsel karışıklığa neden olacak başka düğmeler varsa alternatif dikey yığına izin verilir.

![İletişim kutularında denetim düğmeleri için kabul edilebilir Visual Studio yapılandırmalar](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />İletişim kutularında denetim düğmeleri için kabul edilebilir Visual Studio yapılandırmalar

İletişim kutusu bir varsayılan denetim düğmesi içermeli. Varsayılan olarak kullanmak üzere en iyi komutu belirlemek için aşağıdaki seçeneklerden birini belirleyin (öncelik sırasına göre listelenir):

- Varsayılan olarak en güvenli ve en güvenli komutu seçin. Bu, büyük olasılıkla veri kaybını önlemek ve sistem erişimine engel olmak için komutunun seçerek devam etmek anlamına gelir.

- Veri kaybı ve güvenlik faktörleri arasında yer yoksa, kolaylık sağlamasına göre varsayılan komutu seçin. Varsayılan olarak en olası komutun dahil olması, iletişim kutusu sık veya yinelenen görevleri desteklediğinde kullanıcının iş akışını iyiler.

Varsayılan komut için kalıcı olarak yıkıcı bir eylem seçmekten kaçının. Böyle bir komut varsa, varsayılan olarak daha güvenli bir komut seçin.

#### <a name="access-keys"></a>Erişim tuşları
Tamam, İptal veya Yardım **düğmeleri** **için** erişim **anahtarlarını kullanma.** Bu düğmeler varsayılan olarak kısayol tuşlarına eşlenmiş olur:

| Düğme adı | Klavye kısayolu |
| --- | --- |
| Tamam | Enter |
| İptal | Esc |
| Help | F1 |

#### <a name="imagery"></a>Görüntü
İletişim kutularında görüntüleri sık sık kullanın. İletişim kutularında yalnızca alan açmak için büyük simgeler kullanma. Görüntüleri yalnızca uyarı simgeleri veya durum animasyonları gibi iletiyi kullanıcıya iletmenin önemli bir parçası ise kullanın.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Öncelik belirleme ve katmanlama

#### <a name="prioritizing-your-ui"></a>Kullanıcı arabiriminizi önceliklendirme
Belirli kullanıcı arabirimi öğelerini ön plana getirmek ve iletişim kutularına daha gelişmiş davranış ve seçenekler (belirsiz komutlar dahil) koymak gerekebilir. Yaygın olarak kullanılan işlevselliği ön plana çıkararak ve iletişim kutusu gösterildiğinde kullanıcı arabiriminde varsayılan olarak bir metin etiketiyle görünür hale getirerek.

#### <a name="layering-your-ui"></a>Kullanıcı arabiriminizi katmanlama
Bir iletişim kutusunun gerekli olduğunu belirlediyebilirsiniz, ancak kullanıcıya sunmak istediğiniz ilgili işlevsellik basit bir iletişim kutusunda görüntülenebilir öğesinin ötesine giderse, kullanıcı arabiriminizi katmanlamanız gerekir. En yaygın katmanlama yöntemleri Visual Studio sekmeler ve yer panolardır. Bazı durumlarda genişlet ve daraltan bölgeler uygun olabilir. Uyarlamalı kullanıcı arabirimi genellikle kullanıcı arabiriminde Visual Studio.

Sekme gibi denetimler aracılığıyla kullanıcı arabirimini katmanlamanın farklı yöntemlerinin avantajları ve dezavantajları vardır. Durumunuz için uygun bir katmanlama tekniği seçtiğinizden emin olmak için aşağıdaki listeyi gözden geçirebilirsiniz.

##### <a name="tabbing"></a>Sekme

| Değiştirme mekanizması | Avantajlar ve uygun kullanım | Dezavantajlar ve uygunsuz kullanım |
| --- | --- | --- |
| Sekme denetimi | İletişim kutusu sayfalarını ilgili kümelere mantıksal olarak grupla<br /><br />İletişim kutusundaki ilgili denetimlerin beşten az sayfası (veya iletişim kutusunda bir satıra sığan sekme sayısı) için kullanışlıdır<br /><br />Sekme etiketleri kısa olmalı: içeriği kolayca tanımlayabiliyor bir veya iki sözcük<br /><br />Ortak sistem iletişim kutusu stili<br /><br />Örnek: **Dosya Gezgini &gt; Özellikleri** | Açıklayıcı kısa etiketler yapmak zor olabilir<br /><br />Genellikle son beş sekmeyi tek bir iletişim kutusunda ölçeklendirmez<br /><br />Bir satır için çok fazla sekmeniz varsa uygun değil (alternatif katmanlama tekniği kullanın)<br /><br />Genişletilebilir değil |
| Kenar çubuğu gezintisi | Sekmelerden daha fazla kategoriye uyum sağlayacak basit geçiş cihazı<br /><br />Kategorilerin düz listesi (hiyerarşi yok)<br /><br />Genişletilebilir<br /><br />Örnek: **Özelleştir... &gt; Komut Ekle** | Üçten az grup varsa yatay alan iyi bir kullanım değildir<br /><br />Görev açılan liste için daha uygun olabilir |
| Ağaç denetimi | Sınırsız kategoriye izin verir<br /><br />Kategorilerin gruplama ve/veya hiyerarşisi için izin verir<br /><br />Genişletilebilir<br /><br />Örnek: **Araçlar &gt; Seçenekleri** | İç içe geçmiş hiyerarşiler aşırı yatay kaydırmaya neden olabilir<br /><br />Visual Studio fazla ağaç görünümlerine sahiptir |
| Sihirbazı | Kullanıcıya görev tabanlı, sıralı adımlarda yol gösteren görev tamamlama konusunda yardımcı olur: Sihirbaz üst düzey bir görevi temsil eder ve tek tek paneller, genel görevi gerçekleştirmek için gereken alt görevleri temsil eder<br /><br />Kullanıcının görevi tamamlamak için birden çok düzenleyici ve araç pencereleri kullanmak zorunda olduğu durumda olduğu gibi, görev Kullanıcı Arabirimi sınırlarını aştı mı yararlı olur<br /><br />Görev dallara ayrım gerektirdiği zaman kullanışlıdır<br /><br />Görev adımlar arasında bağımlılıklar içerdiğinde kullanışlıdır<br /><br />Farklı benzer iletişim kutularının sayısını azaltmak için bir iletişim kutusunda tek bir karar fork ile birkaç benzer görev sunabilirsiniz | Sıralı iş akışı gerektirmeyen herhangi bir görev için uygun değil<br /><br />Kullanıcılar çok fazla adımla sihirbaz tarafından bunalabilir ve kafa karıştırabilir<br /><br />Sihirbazlar doğal olarak sınırlı ekran alanlıdır |

##### <a name="hallways-or-dashboards"></a>Yer panoları veya panolar
İletişim kutuları ve panolar, diğer iletişim kutularına ve pencerelere fırlatma noktası olarak hizmet eden iletişim kutuları veya panellerdir. İyi tasarlanmış "yer", yalnızca en yaygın seçenekleri, komutları ve ayarları hemen ortaya çıkararak kullanıcının ortak görevleri gerçekleştirmeye hazır olduğunu gösterir. Gerçek hayattaki bir kapının arkalarında bulunan odalara erişmeye yönelik yollar sağladığı gibi, burada da daha az yaygın olan kullanıcı arabirimi, ana hizmetten erişilebilen ilgili işlevlerin ayrı "odaları" (genellikle diğer iletişim kutuları) halinde toplanır.

Alternatif olarak, daha az yaygın olan işlevleri ayrı konumlarda yeniden düzenleme yerine tüm kullanılabilir işlevleri tek bir koleksiyonda sunan bir kullanıcı arabirimi yalnızca bir panodur.

![Kullanıcı arabiriminde ek kullanıcı arabirimini ortaya çıkararak Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Kullanıcı arabiriminde ek kullanıcı arabirimini açığa çıkararak Outlook

##### <a name="adaptive-ui"></a>Uyarlamalı Kullanıcı Arabirimi
Kullanıcı arabirimini kullanım veya kullanıcının kendi kendine bildirilen deneyimine göre göstermek veya gizleme, diğer bölümleri gizlerken gerekli kullanıcı arabirimini göstermenin bir diğer yoludur. Kullanıcı arabirimini ne Visual Studio gizlemeye karar verme algoritmaları karmaşık olabilir ve kurallar bazı durumlarda her zaman yanlış olur.

## <a name="projects"></a><a name="BKMK_Projects"></a> Proje

### <a name="projects-in-the-solution-explorer"></a>Çözüm Gezgini'daki projeler
Projelerin çoğu başvuru tabanlı, dizin tabanlı veya karışık olarak sınıflandırılır. Üç proje türü de aynı anda proje Çözüm Gezgini. Projelerle çalışırken kullanıcı deneyiminin kökü bu pencerenin içinde yer alır. Farklı proje düğümleri başvuru, dizin veya karma mod türünde projeler olsa da, projeye özgü kullanıcı desenlerine ayrılmadan önce başlangıç noktası olarak uygulanması gereken ortak bir etkileşim deseni vardır.

Projeler her zaman:

- Proje içeriklerini düzenlemek için proje klasörleri ekleme olanağını destekleme

- Proje kalıcılığı için tutarlı bir model koruma

Projeler ayrıca şu için tutarlı etkileşim modellerini de korumalı:

- Proje öğelerini kaldırma

- Belgeleri kaydetme

- Project özelliği düzenleme

- Projeyi alternatif görünümde düzenleme

- Sürükle ve bırak işlemleri

### <a name="drag-and-drop-interaction-model"></a>Sürükleyip bırakma etkileşim modeli
Projeler genellikle kendilerini başvuru tabanlı (depolamadaki proje öğelerine yapılan başvuruları kalıcı olarak bulundurabilir), dizin tabanlı (yalnızca projenin hiyerarşisinde fiziksel olarak depolanan proje öğelerini kalıcı olarak kalıcı olarak bulundurabilir) veya karma (başvuruları veya fiziksel öğeleri kalıcı olarak bulundurabilir) olarak sınıflandırır. IDE, proje içindeki üç proje türüne de aynı anda **Çözüm Gezgini.**

Sürükle ve bırak perspektifinden bakıldığında, aşağıdaki özellikler aşağıdaki özellikler uygulama içindeki her proje türüne **Çözüm Gezgini:**

- **Başvuru tabanlı proje:** Önemli nokta, projenin bir başvuru etrafında depolama alanı içinde bir öğeye sürüklemesidir. Başvuru tabanlı bir proje taşıma işlemi için kaynak olarak davranacaksa, yalnızca öğeye yönelik başvuru projeden kaldırmalıdır. Öğe, sabit sürücüden silinmemelidir. Başvuru tabanlı bir proje taşıma (veya kopyalama) işlemi için hedef olarak davranacaksa, öğenin özel bir kopyasını yapmadan özgün kaynak öğeye bir başvuru eklemesi gerekir.

- **Dizin tabanlı proje:** Bir sürükle ve bırak bakış noktasından, proje başvuru yerine fiziksel öğenin etrafında sürüklenerek. Dizin tabanlı bir proje taşıma işlemi için kaynak olarak davranacaksa, fiziksel öğeyi sabit sürücüden silmenin yanı sıra projeden kaldırması gerekir. Dizin tabanlı bir proje taşıma (veya kopyalama) işlemi için hedef olarak davranacaksa, kaynak öğenin hedef konumda bir kopyasını yapmalı.

- **Karma hedef projesi:** Sürükle ve bırak açısından bu tür bir projenin davranışı, sürüklenen öğenin doğasına (depolama veya öğenin kendisi için bir başvuru) göre hareket eder. Başvurular ve fiziksel öğeler için doğru davranış yukarıda açıklanmıştır.

projesinde yalnızca bir proje türü Çözüm Gezgini **sürükle** ve bırak işlemleri kolay olurdu. Her proje sistemi kendi sürükle ve bırak davranışını tanımlayabilme özelliğine sahip olduğundan, tahmin edilebilir bir kullanıcı deneyimi sağlamak için bazı yönergeler (Windows Gezgini sürükle ve bırak davranışına göre) izlensin:

- İşlemde değiştirilmemiş bir sürükleme **Çözüm Gezgini** (Ctrl veya Shift tuşları basılı tutulmazken) bir taşıma işlemiyle sonuçlandır.

- Shift-drag işlemi de taşıma işlemiyle sonuçlandır.

- Ctrl tuşunu basılı tutarak sürükleme işlemi kopyalama işlemiyle sonuçlandır.

- Başvuru tabanlı ve karma proje sistemleri, kaynak öğeye bağlantı (veya başvuru) eklemeyi destekler. Bu projeler sürükle ve bırak işlemi için hedef olduğunda **(Ctrl + Shift** tuşunu basılı tutarak), projeye eklenen öğenin başvurusuyla sonuçlandır

Tüm sürükle ve bırak işlemleri başvuru tabanlı, dizin tabanlı ve karma projelerin bileşimleri arasında mantıklı değildir. Özellikle, kaynak dizin tabanlı projenin taşıma işlemi tamamlandıktan sonra kaynak öğeyi silmesi gerektir olduğundan, dizin tabanlı bir kaynak proje ile başvuru tabanlı hedef proje arasında taşıma işlemine izin verme gibi davranması sorunludur. Hedef başvuru tabanlı proje daha sonra silinmiş bir öğeye başvuru ile sonuçlandır.

Hedef başvuru tabanlı projenin kaynak öğenin bağımsız bir kopyasını yapmaması gerektiği için bu tür projeler arasında kopyalama işlemi yapmaya izin vermek de yanıltıcıdır. Benzer şekilde, dizin tabanlı bir proje başvuruları kalıcı hale alamayamadığı için Ctrl + Shift ile dizin tabanlı hedef projeye sürüklemeye izin verilmeyecektir. Sürükle ve bırak işlemi desteklenmiyorsa, IDE bırakmaya izin vereme ve kullanıcıya bırakmasız imleç göstermeli (aşağıdaki işaretçi tablosunda gösterilmiştir).

Sürükle ve bırak davranışını düzgün bir şekilde uygulamak için, sürüklemenin kaynak projesinin doğasının hedef projeyle iletişim kurması gerekir. (Örneğin, başvuru mu yoksa dizin tabanlı mı?) Bu bilgiler, kaynak tarafından sunulan pano biçimiyle belirtilmiştir. Sürükle (veya pano kopyalama) işlemi kaynağı olarak, projenin başvuru tabanlı mı yoksa dizin tabanlı mı olduğuna bağlı olarak bir proje sırasıyla veya `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` sunmalıdır. Bu biçimlerin her ikisi de aynı veri içeriğine sahiptir ve bu da Windows biçimine benzer ancak dosya adı yerine dize listesi çift sonlandırılan bir dize listesidir (veya uygun olduğunda `CF_HDROP` `NULL` `Projref` `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` döndürülür).

Bir bırakmanın (veya pano yapıştırma işlemi) hedefi olarak, bir proje hem hem de kabul eder ancak sürükle ve bırak işlemi tam olarak işleme, hedef projenin ve kaynak projenin doğasına bağlı olarak `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` değişir. Kaynak proje, veya teklifine göre kendi doğasını `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` bildirer. Bırakmanın hedefi kendi doğasını anlar ve bu nedenle taşıma, kopyalama veya bağlantının gerçekleştirilip gerçekleştirilip gerçekleştirilecekleri konusunda karar vermek için yeterli bilgiye sahip olur. Kullanıcı ayrıca Ctrl, Shift veya hem Ctrl hem de Shift tuşlarına basarak hangi sürükle ve bırak işlemi gerçekleştirileceklerini de değiştirmektedir. Bırakma hedefinin, ve yöntemlerinde hangi işlemi önceden gerçekleştirilecek olduğunu düzgün şekilde belirtmek `DragEnter` `DragOver` önemlidir. Kaynak **Çözüm Gezgini** projenin ve hedef projenin aynı proje olup olmadığını otomatik olarak bilir.

Proje öğelerinin bir Visual Studio (örneğin, bir devenv.exe diğerine) sürüklenme özellikle desteklanmaz. Bu **Çözüm Gezgini** bunu da doğrudan devre dışı bıraktır.

Kullanıcı her zaman bir öğeyi seçerek, hedef konuma sürükleyerek ve öğe bırakmadan önce aşağıdaki fare işaretçilerinin hangilerinin görüntülendiğinden gözlemleyerek sürükle ve bırak işlemi etkisini belirleyene kadar her zaman belirleye çalışması gerekir:

| Fare işaretçisi | Komut | Açıklama |
| :---: | --- | --- |
| ![Fare "bırak" simgesi](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Bırakma yok | Öğe belirtilen konuma bırakılır. |
| ![Fare "kopyala" simgesi](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Kopyala | Öğe hedef konuma kopyalanır. |
| ![Fare "taşı" simgesi](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Taşı | Öğe hedef konuma taşınır. |
| ![Fare "başvuru ekle" simgesi](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Başvuru ekleme | Seçilen öğeye yönelik bir başvuru hedef konuma eklenir. |

#### <a name="reference-based-projects"></a>Başvuru tabanlı projeler
 Aşağıdaki tabloda, kaynak öğenin yapısına ve başvurulan hedef projeler için basılmış değiştirici tuşlarına bağlı olarak gerçekleştirilecek sürükle ve bırak (kesme/kopyalama/yapıştırma) işlemleri özetlenmiştir:

| Değiştirici | Kategori | Kaynak öğe: Başvuru/Bağlantı | Kaynak öğe: Fiziksel öğe veya dosya sistemi ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Değiştirici yok | Eylem | Taşı | Bağlantı |
| Değiştirici yok | Hedef | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Değiştirici yok | Kaynak | Özgün öğe başvurularını siler | Özgün öğeyi korur |
| Değiştirici yok | Sonuç | `DROPEFFECT_MOVE` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | `DROPEFFECT_LINK` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır |
| Shift+Drag | Eylem | Taşı | Bırakma yok |
| Shift+Drag | Hedef | Özgün öğeye başvuru ekler | Bırakma yok |
| Shift+Drag | Kaynak | Özgün öğe başvurularını siler | Bırakma yok |
| Shift+Drag | Sonuç | `DROPEFFECT_MOVE` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | Bırakma yok |
| Ctrl+Sürükle | Eylem | Kopyala | Bırakma yok |
| Ctrl+Sürükle | Hedef | Özgün öğeye başvuru ekler | Bırakma yok |
| Ctrl+Sürükle | Kaynak | Özgün öğe başvurularını korur | Bırakma yok |
| Ctrl+Sürükle | Sonuç | `DROPEFFECT_COPY` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | Bırakma yok |
| Ctrl+Shift+Sürükleme | Eylem | Bağlantı | Bağlantı |
| Ctrl+Shift+Sürükleme | Hedef | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Ctrl+Shift+Sürükleme | Kaynak | Özgün öğe başvurularını korur | Özgün öğeyi korur |
| Ctrl+Shift+Sürükleme | Sonuç | `DROPEFFECT_LINK` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | `DROPEFFECT_LINK` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır |
| Ctrl+Shift+Sürükleme | Not | Gezgin'de kısayollar için sürükle ve bırak davranışıyla Windows. ||
| Kes/Yapıştır | Eylem | Taşı | Bağlantı |
| Kes/Yapıştır | Hedef | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Kes/Yapıştır | Kaynak | Özgün öğe başvurularını korur|Özgün öğeyi korur |
| Kes/Yapıştır | Sonuç | Öğe depolamada özgün konumda kalır | Öğe depolamada özgün konumda kalır |
| Kopyala/Yapıştır | Eylem | Kopyala | Bağlantı |
| Kopyala/Yapıştır | Kaynak | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Kopyala/Yapıştır | Sonuç | Özgün öğeye başvuruyu saklar | Özgün öğeyi korur |
| Kopyala/Yapıştır | Eylem | Öğe, depolamada orijinal konumda kalıyor | Öğe, depolamada orijinal konumda kalıyor |

#### <a name="directory-based-projects"></a>Dizin tabanlı projeler
Aşağıdaki tabloda, kaynak öğenin doğası ve dizin tabanlı hedef projeler için basılan değiştirici tuşları temelinde gerçekleştirilmesi gereken sürükle ve bırak (Ayrıca kesme/kopyalama/yapıştırma) işlemleri özetlenmektedir:

| Değiştirici | Kategori | Kaynak öğe: başvuru/bağlantı | Kaynak öğe: fiziksel öğe veya dosya sistemi ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Değiştirici yok | Eylem | Taşı | Taşı |
| Değiştirici yok | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Değiştirici yok | Kaynak | Özgün öğeye başvuruyu siler | Özgün öğeye başvuruyu siler |
| SHIFT + sürükleyin | Eylem | Taşı | Taşı |
| SHIFT + sürükleyin | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| SHIFT + sürükleyin | Kaynak | Özgün öğeye başvuruyu siler | Öğeyi özgün konumdan siler |
| SHIFT + sürükleyin | Sonuç | `DROPEFFECT_MOVE` bir eylem, `::Drop` ve öğe depolamada orijinal konumda kaldığı için döndürülür | `DROPEFFECT_MOVE` bir eylem, `::Drop` ve öğe depolamada orijinal konumda kaldığı için döndürülür |
| CTRL + sürükleyin | Eylem | Kopyala | Kopyala |
| CTRL + sürükleyin | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| CTRL + sürükleyin | Kaynak | Özgün öğeye başvuruyu saklar | Özgün öğeye başvuruyu saklar |
| CTRL + sürükleyin | Sonuç | `DROPEFFECT_COPY` bir eylem, `::Drop` ve öğe depolamada orijinal konumda kaldığı için döndürülür | `DROPEFFECT_COPY` bir eylem, `::Drop` ve öğe depolamada orijinal konumda kaldığı için döndürülür |
| CTRL + SHIFT + sürükleyin | | Bırakma yok | Bırakma yok |
| Kes/Yapıştır | Eylem | Taşı | Taşı |
| Kes/Yapıştır | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Kes/Yapıştır | Kaynak | Özgün öğeye başvuruyu siler | Öğeyi özgün konumdan siler |
| Kes/Yapıştır | Sonuç | Öğe, depolamada orijinal konumda kalıyor | Öğe, depolama alanındaki özgün konumdan silindi |
| Kopyala/Yapıştır | Eylem | Kopyala | Kopyala |
| Kopyala/Yapıştır | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Kopyala/Yapıştır | Kaynak | Özgün öğeyi korur | Özgün öğeyi korur |
| Kopyala/Yapıştır | Sonuç | Öğe, depolamada orijinal konumda kalıyor | Öğe orijinal konum bileşenleri deposunda kalıyor |

#### <a name="mixed-target-projects"></a>Karma hedef projeler
Aşağıdaki tabloda, kaynak öğenin yapısına ve karma hedef projeler için basılmış değiştirici tuşlarına bağlı olarak gerçekleştirilecek sürükle ve bırak (kesme/kopyalama/yapıştırma) işlemleri özetlenmiştir:

| Değiştirici | Kategori | Kaynak öğe: Başvuru/Bağlantı | Kaynak öğe: Fiziksel öğe veya dosya sistemi ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Değiştirici yok | Eylem | Taşı | Taşı |
| Değiştirici yok | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Değiştirici yok | Kaynak | Özgün öğe başvurularını siler | Özgün öğe başvurularını siler |
| Değiştirici yok | Sonuç | `DROPEFFECT_ MOVE` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | `DROPEFFECT_ MOVE` öğesinden eylem olarak döndürülür `::Drop` ve öğe depolamada özgün konumdan silinir |
| Shift+Drag | Eylem | Taşı | Taşı |
| Shift+Drag | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Shift+Drag | Kaynak | Özgün öğe başvurularını siler | Öğeyi özgün konumdan siler |
| Shift+Drag | Sonuç | `DROPEFFECT_ MOVE` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | `DROPEFFECT_ MOVE` öğesinden eylem olarak döndürülür `::Drop` ve öğe depolamada özgün konumdan silinir |
| Ctrl+Sürükle | Eylem | Kopyala | Kopyala |
| Ctrl+Sürükle | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Ctrl+Sürükle | Kaynak | Özgün öğe başvurularını korur | Özgün öğeyi korur |
| Ctrl+Sürükle | Sonuç | `DROPEFFECT_ COPY` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | `DROPEFFECT_ COPY` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır |
| Ctrl+Shift+Sürükleme | Eylem | Bağlantı | Bağlantı |
| Ctrl+Shift+Sürükleme | Hedef | Özgün öğeye başvuru ekler | Özgün kaynak öğeye başvuru ekler |
| Ctrl+Shift+Sürükleme | Kaynak | Özgün öğe başvurularını korur | Özgün öğeyi korur |
| Ctrl+Shift+Sürükleme | Sonuç | `DROPEFFECT_ LINK` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | `DROPEFFECT_ LINK` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır |
| Kes/Yapıştır | Eylem | Taşı | Taşı |
| Kes/Yapıştır | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Kes/Yapıştır | Kaynak | Özgün öğe başvurularını siler | Öğeyi özgün konumdan siler |
| Kes/Yapıştır | Sonuç | Öğe depolamada özgün konumda kalır | Öğe depolamada özgün konumdan silindi |
| Kopyala/Yapıştır | Eylem | Kopyala | Kopyala |
| Kopyala/Yapıştır | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Kopyala/Yapıştır | Kaynak | Özgün öğeyi korur | Özgün öğeyi korur |
| Kopyala/Yapıştır | Sonuç | Öğe depolamada özgün konumda kalır | Öğe, depolamada orijinal konumda kalıyor |

**Çözüm Gezgini** sürüklemeyi uygularken bu ayrıntılar dikkate alınmalıdır:

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

Bu, kullanıcıya hedef kopyalarını yapmadan önce devam etmekte olan işleri kaydetme fırsatı sağlar. `IVsHierarchyDropDataSource2::OnBeforeDropNotify`Bu işlemeyi etkinleştirmek için yeni bir yöntem eklenmiştir.

Hedef daha sonra öğenin durumunu depolama alanında olduğu gibi kopyalayacaktır (Kullanıcı **Hayır**' ı seçtiyse düzenleyicide kaydedilmemiş değişiklikleri dahil edilmez). Hedef kopyalamayı tamamladıktan sonra (' de `IVsHierarchyDropDataSource::Drop` ), kaynak taşıma işleminin silme bölümünü (içinde) tamamlamaya yönelik fırsat olarak verilir `IVsHierarchyDropDataSource::OnDropNotify` .

Kaydedilmemiş değişiklikleri olan düzenleyicilerin açık bırakılması gerekir. Kaydedilmemiş değişiklikleri olan bu belgeler için, taşıma işleminin kopyalama bölümünün gerçekleştirileceği, ancak silme bölümünün iptal edilmeyeceği anlamına gelir. Kullanıcı **Hayır**' ı seçtiğinde birden çok seçim senaryosunda, kaydedilmemiş değişiklikler içeren belgeler kapanmamalıdır veya kaldırılmamalıdır, ancak kaydedilmemiş değişiklikler olmaksızın kapanmamalıdır ve kaldırılmalıdır.
