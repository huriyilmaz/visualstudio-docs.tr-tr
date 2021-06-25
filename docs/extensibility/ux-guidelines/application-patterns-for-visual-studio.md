---
title: Visual Studio | için Uygulama Desenleri Microsoft Docs
description: Belge pencereleri, araç pencereleri ve yeni özellikler için pencere kullanım desenleri de dahil olmak üzere modelsiz iletişim kutuları arasındaki farkı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2726c7096bbf4606fbab2c32b01ffd197549e13c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899192"
---
# <a name="application-patterns-for-visual-studio"></a>Visual Studio İçin Uygulama Desenleri
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Pencere etkileşimleri

### <a name="overview"></a>Genel Bakış
Belgelerde kullanılan iki ana pencere Visual Studio belge düzenleyicileri ve araç pencereleridir. Nadir de olsa, büyük, modeless iletişim kutuları da mümkündür. Bunların hepsi kabukta modelsiz olsa da, bunların desenleri temelde farklıdır. Bu bölüm belge pencereleri, araç pencereleri ve modeless iletişim kutuları arasındaki farkı kapsar. Kalıcı iletişim kutusu desenleri İletişim [Kutuları'nın kapsamındadır.](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

### <a name="comparing-window-usage-patterns"></a>Pencere kullanım desenlerini karşılaştırma
**Belge pencereleri** neredeyse her zaman belge içinde görüntülenir. Bu, ek araç pencerelerini düzenlemek için belge düzenleyicisine bir "orta aşama" sağlar.

Araç **penceresi genellikle** IDE'nin kenarına göre daraltılmış ayrı ve daha küçük bir pencere olarak görüntülenir. Bu, görünür, gizli veya otomatik olarak gizli olabilir. Ancak bazen araç pencereleri, pencere üzerinde **Window/Docking** özelliğinin işaretini kaldırarak belge içinde gösterilir. Bunun sonucunda daha fazla alan elde etmek, aynı zamanda ortak bir tasarım kararına da neden olur: Visual Studio ile tümleştiri yapmaya çalışırken, özelliğinizin bir araç penceresi mi yoksa belge penceresi mi görüntülemesi gerektiğine karar verebilirsiniz.

**Modsuz iletişim kutuları** için önerilmez Visual Studio. Çoğu modsuz iletişim kutusu tanım gereği kayan araç pencereleridir ve bu şekilde uygulanması gerekir. Kabuğun tarafına yerleştirilen normal bir araç penceresinin boyutunun fazla sınırlayıcı olduğu durumlarda, modeless iletişim kutularına izin verilir. Ayrıca, kullanıcının iletişim kutusunu ikincil bir izleyiciye taşıma olasılığı olan durumlarda da izin verilir.

Hangi kapsayıcı türüne ihtiyacınız olduğunu dikkatle düşünmelisiniz. Kullanıcı arabirimi tasarımıyla ilgili yaygın kullanım düzeni konuları aşağıdaki tabloda vemektedir.

||Belge penceresi|Araç penceresi|Modeless (Modeless) iletişim kutusu|
|-|---------------------|-----------------|---------------------|
| **Position** (Pozisyon) | Her zaman belge yuvasına yerleştirildi ve IDE'nin kenarlarına yerleştirmez. Ana kabuktan ayrı olarak kayan bir şekilde "çekilebilir". | Genellikle IDE'nin kenarlarında sekmeyle yerleştirme, ancak kayan, otomatik gizlenen (bağlı olmayan) veya belge yuvası içinde yerleştirilen olarak özelleştirilebilir.|IDE'den ayrı büyük kayan pencere. |
| **Modeli işleme** | *Gecikmeli işleme*<br /><br /> Verileri bir belgeye kaydetmek için kullanıcının Dosya **Kaydetme,** Farklı **&gt; Kaydet** veya Hepsini Kaydet **komutunu oluşturması** gerekir. Belge penceresinde, içindeki veriler kavramı "yenilendi" ve ardından kaydetme komutlarından biri ile işlendi. Bir belge penceresi kapatılıyorsa tüm içerikler diske kaydedilir veya kaybolur. | *Anında işleme*<br /><br /> Kaydetme modeli yoktur. Bir dosyayı düzenlemeye yardımcı olan denetçi aracı pencerelerinde dosyanın etkin düzenleyicide veya tasarımcıda açık olması ve kaydetmenin düzenleyici veya tasarımcıya ait olması gerekir. | *Gecikmeli veya hemen işleme*<br /><br /> Genellikle büyük bir modsuz iletişim kutusu, değişiklikleri işlemek için bir eylem gerektirir ve iletişim kutusu oturumunda yapılan değişiklikleri geri alan bir "İptal" işlemi sağlar.  Bu, bu araç pencerelerinden modsuz bir iletişim kutusunun her zaman anında işleme modeline sahip olduğunu gösterir. |
| **Görünürlük** | *Aç/Oluştur (dosya) ve Kapat*<br /><br /> Belge pencerelerini açmak için var olan bir belgeyi açmak veya şablon kullanarak yeni bir belge oluşturmak gerekir. \<specific editor>"Aç" komutu yoktur. | *Gizleme ve gösterme*<br /><br /> Tek örnekli araç pencereleri gizli veya gösterebilirsiniz. Görünümde veya gizli araç penceresindeki içerikler ve eyaletler kalıcı olur. Çok örnekli araç pencereleri hem kapatabilirsiniz hem de gizlenir. Çok örnekli bir araç penceresi kapatılan araç penceresi içindeki içerik ve durum atılır. | *Bir komuttan başlatıldı*<br /><br /> İletişim kutuları görev tabanlı bir komuttan başlatıldı. |
| **Örnekler** | *Multi*<br /><br /> Çeşitli düzenleyiciler aynı anda ve farklı dosyaları düzenleyerek açabilirsiniz, ancak bazı düzenleyiciler aynı dosyanın birden fazla düzenleyicide açılmasına da olanak sağlar **(Windows &gt; Yeni** Pencere komutu kullanılarak).<br /><br /> Tek bir düzenleyici aynı anda bir veya birden çok dosya düzenliyor olabilir (Proje Tasarımcısı). | *Tek veya çok örnekli*<br /><br /> İçerikler bağlamı yansıtacak şekilde (Property Browser'da olduğu gibi) veya odağı/bağlamı diğer pencerelere (Görev Listesi, Çözüm Gezgini).<br /><br /> Hem tek örnekli hem de çok örnekli araç pencereleri, ilgi çekici bir neden olmadığı sürece etkin belge penceresiyle ilişkili olması gerekir. | *Tek örnekli* |
| **Örnekler** | **Kod düzenleyicisi gibi** metin düzenleyicileri<br /><br /> **Form tasarımcısı veya** modelleme yüzeyi gibi tasarım yüzeyleri<br /><br /> **Bildirim Tasarımcısı gibi iletişim kutularına** benzer düzenleri denetleme | Bu **Çözüm Gezgini** çözümü ve çözümün içinde yer alan projeleri sağlar<br /><br /> Bu **Sunucu Gezgini,** kullanıcının pencerede açmayı seçen sunucuların ve veri bağlantılarının hiyerarşik bir görünümünü sağlar. Veritabanı hiyerarşisinde sorgu gibi bir nesneyi açmak bir belge penceresi açar ve kullanıcının sorguyu düzenlemesini sağlar.<br /><br /> Özellik **Tarayıcısı,** seçilen nesnenin özelliklerini bir belge penceresinde veya başka bir araç penceresinde görüntüler. Özellikler hiyerarşik kılavuz görünümünde veya iletişim kutusu gibi karmaşık denetimlerde görüntülenir ve kullanıcının bu özellikler için değerleri ayarlamasına izin verir. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Araç pencereleri

### <a name="overview"></a>Genel Bakış
Araç pencereleri, kullanıcının belge pencerelerde olan çalışmalarını destekler. Bunlar, bir temel kök nesnesini temsil eden bir hiyerarşiyi görüntülemek için kullanılabilir ve Visual Studio tarafından kullanılabilir.

IDE'de yeni bir araç penceresi göz önünde bulundurarak yazarların:

- Görev için uygun mevcut araç pencerelerini kullanın ve benzer işlevlere sahip yenilerini oluşturmaz. Yeni araç pencereleri yalnızca benzer bir pencereyle tümleştirilene kadar çok farklı bir "araç" veya işlev sunuyorsa ya da mevcut bir pencereyi özet hub'a dönüştürerek oluşturulmaktadır.

- Gerekirse araç penceresinin üst kısmında standart bir komut çubuğu kullanın.

- Denetim sunumu ve klavye gezintisi için diğer araç pencerelerde zaten mevcut olan desenlerle tutarlı olun.

- Diğer araç pencerelerde denetim sunumuyla tutarlı olun.

- Mümkün olduğunda belgeye özgü araç pencerelerini otomatik görünür hale getir, böylece yalnızca üst belge etkinleştirildiğinde görünürler.

- Pencere içeriklerinin klavye tarafından gezinilebilir olduğundan emin olmak (destek ok tuşları).

#### <a name="tool-window-states"></a>Araç penceresi durumları
Visual Studio araç pencerelerinin bazıları kullanıcı tarafından etkinleştirilen (otomatik gizleme özelliği gibi) farklı durumlara sahiptir. Otomatik görünür gibi diğer eyaletler, araç pencerelerini doğru bağlamda göstermelerine ve gerek duyulmasa gizlemelerine olanak sağlar. Toplamda beş araç penceresi durumları vardır.

- **Sabitlenmiş/sabitlenmiş** araç pencereleri, belge alanı dört tarafının herhangi bir tarafına iliştirilmiş olabilir. Araç penceresi başlık çubuğunda itme simgesi görünür. Araç penceresi, kabuğun ve diğer araç pencerelerinin kenarına yatay veya dikey olarak sabitlenmenin yanı sıra sekme bağlantılı da olabilir.

- **Otomatik olarak gizlenen** araç pencereleri,pinin dışıdır. Pencere, belge alanı kenarına bir sekme (araç penceresinin adı ve simgesiyle birlikte) bırakarak gözden kaydırabilirsiniz. Kullanıcı sekmenin üzerine geldiğinde araç penceresi kayar.

- **Düzenleyici gibi başka** bir kullanıcı arabirimi parçası başlatıldığında veya odaklanıyorsa otomatik olarak görünen araç pencereleri otomatik olarak görünür.

- **Kayan** araç pencereleri IDE'nin dışına çıkar. Bu, çok monitörlü yapılandırmalar için kullanışlıdır.

- **Sekmeli belge** aracı pencereleri, belge yuvasına yerleştirebilirsiniz. Bu, Object Browser gibi çerçevenin kenarlarına yerleştirmeye izin verenden daha fazla alan gereken büyük araç pencereleri için kullanışlıdır.

![Araç penceresi durumları Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Araç penceresi durumları Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Tek örnekli ve çok örnekli
Araç pencereleri tek örnekli veya çok örneklidir. Bazı tek örnekli araç pencereleri etkin belge penceresiyle ilişkilendirilirken, çok örnekli araç pencereleri ilişkili olabilir. Çok örnekli araç pencereleri, pencerenin **&gt; yeni bir örneğini** oluşturarak Window New Window komutuna yanıt verir. Aşağıdaki görüntüde, pencerenin bir örneği etkin olduğunda Yeni Pencere komutunu etkinleştiren bir araç penceresi gösterilir:

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
| Araç Kutusu | Tüm tasarımcılar için tutarlı bir sürükle kaynak sağlayarak tasarım yüzeyleri üzerine bırakacak öğeleri depolamak için kullanılan araç penceresi. |
| Başlangıç Sayfası | Geliştirici haberlerinin akışlarına, Visual Studio ve son projelere erişimi olan Visual Studio portalı. Kullanıcılar ayrıca "Common7\IDE\StartPages Visual Studio program dosyaları dizininden StartPage.xaml dosyasını Visual Studio documents dizinindeki StartPages klasörüne kopyalayıp XAML'i el ile düzenleyerek veya Visual Studio veya başka bir kod düzenleyicisinde açarak özel başlangıç sayfaları \" oluşturabilir. |

::: moniker-end

::: moniker range=">=vs-2019"

| Araç penceresi | İşlev |
| --- | --- |
| Araç Kutusu | Tüm tasarımcılar için tutarlı bir sürükle kaynak sağlayarak tasarım yüzeyleri üzerine bırakacak öğeleri depolamak için kullanılan araç penceresi. |

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

Belge düzenleme tutarlı bir kullanıcı deneyimi gerektirir. Kullanıcının pencere yönetimi ve komutları bulmak yerine sahip olduğu göreve odaklanmasına izin vermek için, bu belge türünü düzenlemek için kullanıcı görevlerine en uygun belge görünümü stratejisini seçin.

#### <a name="common-interactions-for-the-document-well"></a>Belge için ortak etkileşimler

- Ortak Yeni Dosya ve Açık Dosya deneyimlerinden **tutarlı bir** **etkileşim modeli** elde edin.

- Belge penceresi açıldığında ilgili pencerelerde ve menülerde ilgili işlevleri güncelleştirin.

- Menü komutları Düzenle, Biçimlendir ve Görünüm menüleri **gibi** ortak **menülerle** uygun şekilde **tümleştirilmiştir.** Çok fazla özel komut varsa yeni bir menü oluşturulabilir. Bu yeni menü yalnızca belgenin odağı olduğunda görünür olmalıdır.

- Ekli araç çubuğu düzenleyicinin en üstüne yerleştirilebilirsiniz. Bu, düzenleyicinin dışında görünen ayrı bir araç çubuğuna sahip olmak için tercih edilir.

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

Belgeyi iyi kullanan çeşitli düzenleyici dışı türler de vardır. Belgeleri kendileri düzenlemezler ancak belge pencerelerinin standart etkileşimlerini izlemeleri gerekir.

- **Raporlar:** IntelliTrace raporu, Hyper-V raporu, profil oluşturma raporu

- **Pano:** Tanılama Merkezi

#### <a name="text-based-editors"></a>Metin tabanlı düzenleyiciler

- Belge önizleme sekmesi modeline katılarak belgeyi açmadan önizlemeye olanak sağlar.

- Belgenin yapısı, belge ana hatları gibi bir yardımcı araç penceresinde temsil olabilir.

- IntelliSense (uygunsa) diğer kod düzenleyicileriyle tutarlı bir şekilde davranır.

- Açılır pencere veya yardımcı kullanıcı arabirimi, CodeLens gibi mevcut benzer kullanıcı arabirimi için benzer stilleri ve desenleri takip eder.

- Belge durumuyla ilgili iletiler, belgenin üst kısmında veya durum çubuğunda bir bilgi çubuğu denetiminde sunulacaktır.

- Kullanıcı, paylaşılan Yazı Tipleri ve Renkler sayfasını **veya** düzenleyiciye özgü bir > Araçlar ve Seçenekler sayfasını kullanarak yazı tiplerinin ve renklerin görünümünü özelleştirenin.

#### <a name="design-surfaces"></a>Tasarım yüzeyleri

- Boş bir tasarımcının yüzeyde nasıl çalışmaya başlay gerektiğini belirten bir filigran olması gerekir.

- Görünüm değiştirme mekanizmaları, bir kod düzenleyicisini açmak için çift tıklama gibi mevcut desenleri veya belge penceresindeki sekmeleri kullanarak her iki bölmeyle de etkileşime olanak sağlar.

- Son derece özel bir araç penceresi gerekli olmadığı sürece tasarım yüzeyine öğe ekleme araç kutusu aracılığıyla yapılması gerekir.

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

- Kullanıcı, paylaşılan Yazı Tipleri ve Renkler sayfasını veya düzenleyiciye **özgü** > Seçenekler sayfasını kullanarak yazı tiplerinin/renklerin görünümünü özelleştirenin.

#### <a name="reports"></a>Raporlar

- Raporlar genellikle yalnızca bilgidir ve Kaydet modeline katılmaz. Ancak, genişletilen ve daraltan diğer ilgili bilgilerin veya bölümlerin bağlantıları gibi etkileşim içerebilirler.

- Yüzeydeki çoğu komut düğme değil köprü olması gerekir.

- Düzen bir üst bilgi içermeli ve standart rapor düzeni yönergelerini izlemeli.

#### <a name="dashboards"></a>Panolar

- Panoların kendi kendilerine bir etkileşim modeli yok ancak farklı araçlar sunabilirsiniz.

- Modeli kaydet'e katılmaz.

- Kullanıcıların düzenleyiciyi etkinleştirerek ve denetimler aracılığıyla sekmeyle ya da standart mnemonics kullanarak yalnızca klavye kullanarak denetimlerle etkileşim kurabilecekleri gerekir.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Diyalog

### <a name="introduction"></a>Giriş
Çalışma Visual Studio iletişim kutuları genellikle kullanıcının çalışması için ayrı bir birimi desteklemeli ve sonra da bu birim çıkarılır.

bir iletişim kutusuna ihtiyacınız olduğunu belirlediyebilirsiniz, tercih sırasına göre üç seçeneğiniz vardır:

1. Özelliklerinizi, Visual Studio'daki paylaşılan iletişim Visual Studio.

2. Mevcut benzer bir iletişim kutusunda bulunan deseni kullanarak kendi iletişim kutusunu oluşturun.

3. Etkileşim ve düzen yönergelerini takip eden yeni bir iletişim kutusu oluşturun.

Bu bölümde, iş akışlarında doğru iletişim kutusu deseninin Visual Studio ve iletişim kutusu tasarımı için ortak kuralların nasıl seçkili olduğu açıktır.

### <a name="themes"></a>Temalar
Visual Studio iletişim kutuları iki temel stilden birini takip eder:

#### <a name="standard-unthemed"></a>Standart (themed)
İletişim kutularının çoğu standart yardımcı iletişim kutularıdır ve bunların birikmiş olması gerekir. Ortak denetimleri yeniden şablonlaştırarak veya stilleştirilmiş "modern" düğmeler veya denetimler oluşturma girişiminde bulundurarak. Denetimler ve chrome görünümü, [iletişim kutuları için standart Windows Masaüstü etkileşim yönergelerini izleyin.](/windows/desktop/uxguide/win-dialog-box)

#### <a name="themed"></a>Temalı
Özel "imza" iletişim kutuları, themed olabilir. Stille ilişkili bazı özel etkileşim desenlerine de sahip olan, themed iletişim kutuları ayrı bir görünüme sahiptir. İletişim kutusu yalnızca şu gereksinimleri karşılarsa temaya ekleyin:

- İletişim kutusu, sık sık veya birçok kullanıcı tarafından (örneğin, Yeni Proje iletişim kutusu) görülen ve kullanılan yaygın **bir deneyimdir.**

- İletişim kutusu öne çıkan ürün markası öğelerini (örneğin, Hesap Ayarları **iletişim kutusu)** içerir.

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
Basit bir iletişim kutusu, denetimlerin tek bir kalıcı pencerede sunumu olur. Bu sunu, alan seçici gibi karmaşık denetim desenlerinin çeşitlemelerini içerebilir. Basit iletişim kutuları için standart genel düzeni ve karmaşık denetim gruplamaları için gereken belirli düzenleri izleyin.

![>Ad Anahtarı Oluştur seçeneği, Visual Studio'da basit bir iletişim kutusu örneğidir.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Create Strong Name Key ( Güçlü Ad Anahtarı Oluştur) içinde basit bir iletişim Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Katmanlı iletişim kutuları
Katmanlı iletişim kutuları sekmeleri, panoları ve ekli ağaçları içerir. Tek bir kullanıcı arabiriminde sunulan birden fazla denetim grubu olduğunda, gerçek Emlak için kullanılır. Gruplandırmalar, kullanıcının herhangi bir anda hangi gruplandırmanın görüzi seçebilmesini sağlayacak şekilde katmanlıdır.

En kolay durumda, gruplandırmalar arasında geçiş mekanizması bir sekme denetimidir. Kullanılabilecek birkaç alternatif vardır. En uygun stili seçme hakkında bilgi için bkz. önceliklendirme ve katmanlama.

**Araç &gt; seçenekleri** iletişim kutusu, katıştırılmış ağaç kullanan katmanlı bir iletişim örneğidir:

![Araçlar > seçenekler, Visual Studio 'daki katmanlı bir iletişim örneğidir.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Araçlar > seçenekler, Visual Studio 'daki katmanlı bir iletişim örneğidir.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> 'Nı
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
İletişim kutuları ilk başlatmada IDE içinde ortalanmalıdır. Yeniden boyutlandırılamayan iletişim kutularının son konumunun kalıcı olması gerekmez, bu nedenle sonraki başlangıçlarda ortalanmış olarak görünürler.

Yeniden boyutlandırılabilir iletişimler için, boyutun sonraki başlangıçlarda kalıcı olması gerekir. Yeniden boyutlandırılabilir kalıcı iletişim kutuları için, konumun kalıcı olması gerekmez. IDE içinde ortalanan bunları görüntülemek, kullanıcının görüntüleme yapılandırması değiştirildiğinde, iletişim kutusunun öngörülemeyen veya kullanılamaz bir konumda görüntülenmesini önler.

Yeniden konumlandırılabilir olmayan iletişim kutuları için, iletişim kutusu sıklıkla daha büyük bir iş akışının tamsayı parçası olarak kullanıldığından, kullanıcının konumu sonraki başlangıçlarda tutulmalıdır.

İletişim kutuları diğer iletişim kutularını oluştururken, en üstteki iletişim kutusu, kullanıcının yeni bir yere gezindikleri bir kullanıcı tarafından belirgin olması için üst öğeden sağa ve aşağı doğru basamaklanmalıdır.

#### <a name="modality"></a>Moduna
Kalıcı olması, kullanıcıların devam etmeden önce iletişim kutusunu tamamlaması veya iptal edebilmesi için gerekli olduğu anlamına gelir. Kalıcı iletişim kutuları kullanıcının ortamın diğer bölümleriyle etkileşime engel olduğundan, özelliğin görev akışı bunları mümkün olduğunca az bir şekilde kullanmalıdır. Kalıcı bir işlem gerektiğinde, Visual Studio 'nun özelliklerini tümleştirebilmeniz için bir dizi paylaşılan iletişim kutusu vardır. Yeni bir iletişim kutusu oluşturmanız gerekiyorsa, benzer işlevlerle mevcut bir iletişim kutusunun etkileşim düzenine uyun.

Kullanıcıların tek seferde iki etkinlik gerçekleştirmesi gerektiğinde (yeni kod yazarken **bul** ve **Değiştir** gibi), kullanıcının aralarında kolayca geçiş yapabilmesi için iletişim kutusu kalıcı olmalıdır. Visual Studio genellikle bu tür Düzenleyici destekleyici bağlantılı görev için araç pencerelerini kullanır.

#### <a name="control-configuration"></a>Denetim yapılandırması
Visual Studio 'da aynı şeyi gerçekleştiren mevcut denetim yapılandırmalarına uygun olun.

#### <a name="title-bars"></a>Başlık çubukları

- Başlık çubuğundaki metin, onu başlatan komutun adını yansıtmalıdır.

- İletişim kutusu başlık çubuklarında hiçbir simge kullanılmamalıdır. Sistemin bir tane gerektirmesi durumunda, Visual Studio logosu ' nı kullanın.

- İletişim kutularında Küçült veya büyüt düğmeleri olmamalıdır.

- Başlık çubuğundaki Yardım düğmeleri kullanım dışı bırakılmıştır. Bunları yeni iletişim kutularına eklemeyin. Bunlar mevcut olduğunda, görevle ilgili kavramsal olan bir yardım konusu başlatacaktır.

  ![Visual Studio iletişim kutularında başlık çubukları için kılavuz belirtimleri](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Visual Studio iletişim kutularında başlık çubukları için kılavuz belirtimleri

#### <a name="control-buttons"></a>Denetim düğmeleri
Genel olarak, **Tamam**, **iptal** ve **Yardım** düğmeleri, iletişim kutusunun sağ alt köşesinde yatay olarak düzenlenmelidir. İletişim kutusunun alt kısmında, denetim düğmeleriyle görsel karışıklık sunacak diğer birkaç düğme varsa, alternatif dikey yığına izin verilir.

![Visual Studio iletişim kutularında denetim düğmeleri için kabul edilebilir konfigürasyonlar](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Visual Studio iletişim kutularında denetim düğmeleri için kabul edilebilir konfigürasyonlar

İletişim kutusu varsayılan bir denetim düğmesi içermelidir. Varsayılan olarak kullanılacak en iyi komutu belirlemek için, aşağıdaki seçeneklerden birini belirleyin (öncelik sırasına göre listelenmiştir):

- Varsayılan olarak en güvenli ve en güvenli komutu seçin. Bu, veri kaybını önlemeyi ve istenmeyen sistem erişiminin oluşmasını önlemek için en olası komutu seçme anlamına gelir.

- Veri kaybı ve güvenlik faktörleri yoksa, kolaylık doğrultusunda varsayılan komutu seçin. En olası komut, varsayılan olarak dahil olmak üzere, iletişim kutusu sık veya yinelenen görevleri desteklediğinde kullanıcının iş akışını iyileştirir.

Varsayılan komut için kalıcı bir bozucu eylem seçmekten kaçının. Böyle bir komut varsa, bunun yerine varsayılan olarak güvenli bir komut seçin.

#### <a name="access-keys"></a>Erişim tuşları
**Tamam**, **iptal** veya **Yardım** düğmeleri için erişim tuşları kullanmayın. Bu düğmeler, varsayılan olarak kısayol tuşlarıyla eşlenir:

| Düğme adı | Klavye kısayolu |
| --- | --- |
| Tamam | Enter |
| İptal | Esc |
| Help | F1 |

#### <a name="imagery"></a>Canlandırın
İletişim kutularında görüntüleri gelişigüzel kullanın. Yalnızca alanı kullanmak için iletişim kutularında büyük simgeler kullanmayın. Yalnızca ileti, uyarı simgeleri veya durum animasyonları gibi kullanıcıya iletiyi almak için önemli bir parçasıysa görüntüleri kullanın.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Öncelik verme ve katmanlama

#### <a name="prioritizing-your-ui"></a>Kullanıcı arabiriminize öncelik verme
Belirli kullanıcı arabirimi öğelerini Forefront 'e getirmek ve iletişim kutularına daha gelişmiş davranış ve Seçenekler (belirsiz komutlar dahil) yerleştirmek gerekebilir. Yaygın olarak kullanılan işlevselliği, bu BT için yer açarak Forefront 'e taşıyın ve iletişim kutusu gösterildiğinde bir metin etiketiyle Kullanıcı arabiriminde varsayılan olarak görünür hale getirin.

#### <a name="layering-your-ui"></a>Kullanıcı arabiriminizi katmanlama
Bir iletişim kutusunun gerekli olduğunu, ancak kullanıcıya sunmak istediğiniz ilgili işlevselliğin basit bir iletişim kutusunda görüntülendiklerinin ötesinde olduğunu belirlediyseniz, Kullanıcı ARABIRIMINIZI katmanmanız gerekir. Visual Studio 'Nun kullandığı en yaygın katmanlama yöntemleri, sekmeler ve hallyöntemleri veya panolardır. Bazı durumlarda, genişleyebilir ve daraltılabilen bölgeler uygun olabilir. Uyarlamalı Kullanıcı Arabirimi genellikle Visual Studio 'da önerilmez.

Sekme benzeri denetimler aracılığıyla farklı katman Kullanıcı arabirimi yöntemlerinin avantajları ve dezavantajları vardır. Durumunuza uygun bir katman tekniği seçtiğinizden emin olmak için aşağıdaki listeyi gözden geçirin.

##### <a name="tabbing"></a>Sekmeyle gitmeyi

| Anahtarlama mekanizması | Avantajlar ve uygun kullanım | Olumsuz ve uygunsuz kullanım |
| --- | --- | --- |
| Sekme denetimi | İletişim kutusu sayfalarını mantıksal olarak ilgili kümeler halinde gruplandır<br /><br />İletişim kutusundaki ilgili denetimlerin sayfalarında beşten az beş (veya iletişim kutusu genelinde bir satıra sığan sekme sayısı) için faydalıdır<br /><br />Sekme etiketleri kısa olmalı: içeriği kolayca tanımlayabiliyor bir veya iki sözcük<br /><br />Ortak bir sistem iletişim kutusu stili<br /><br />Örnek: **Dosya Gezgini &gt; Özellikleri** | Açıklayıcı kısa etiketler yapmak zor olabilir<br /><br />Genellikle son beş sekmeyi tek bir iletişim kutusunda ölçeklendirmez<br /><br />Bir satır için çok fazla sekmeniz varsa uygun değil (alternatif katmanlama tekniği kullanın)<br /><br />Genişletilebilir değil |
| Kenar çubuğu gezintisi | Sekmelerden daha fazla kategoriye uyum sağlayacak basit geçiş cihazı<br /><br />Kategorilerin düz listesi (hiyerarşi yok)<br /><br />Genişletilebilir<br /><br />Örnek: **Özelleştir... &gt; Komut Ekle** | Üçten az grup varsa yatay alan iyi bir kullanım değildir<br /><br />Görev açılan liste için daha uygun olabilir |
| Ağaç denetimi | Sınırsız kategoriye izin verir<br /><br />Kategorilerin gruplama ve/veya hiyerarşisi için izin verir<br /><br />Genişletilebilir<br /><br />Örnek: **Araçlar &gt; Seçenekleri** | İç içe geçmiş hiyerarşiler aşırı yatay kaydırmaya neden olabilir<br /><br />Visual Studio fazla ağaç görünümlerine sahiptir |
| Sihirbazı | Kullanıcıya görev tabanlı, sıralı adımlarda yol gösteren görev tamamlama konusunda yardımcı olur: Sihirbaz üst düzey bir görevi temsil eder ve tek tek paneller, genel görevi gerçekleştirmek için gereken alt görevleri temsil eder<br /><br />Görev Kullanıcı Arabirimi sınırlarını aştıklarından, kullanıcının görevi tamamlamak için birden çok düzenleyici ve araç pencereleri kullanmak zorunda olduğu zamanlarda kullanışlıdır<br /><br />Görev dallara ayrım gerektirdiği zaman kullanışlıdır<br /><br />Görev adımlar arasında bağımlılıklar içerdiğinde kullanışlıdır<br /><br />Farklı benzer iletişim kutularının sayısını azaltmak için bir iletişim kutusunda tek bir karar fork ile birkaç benzer görev sunabilirsiniz | Sıralı iş akışı gerektirmeyen herhangi bir görev için uygun değil<br /><br />Kullanıcılar çok fazla adımla sihirbaz tarafından bunalabilir ve kafa karıştırabilir<br /><br />Sihirbazlar doğal olarak sınırlı ekran alanlıdır |

##### <a name="hallways-or-dashboards"></a>Yer panoları veya panolar
İletişim kutuları ve panolar, diğer iletişim kutularına ve pencerelere fırlatma noktası olarak hizmet eden iletişim kutuları veya panellerdir. İyi tasarlanmış "yer", yalnızca en yaygın seçenekleri, komutları ve ayarları hemen ortaya çıkararak kullanıcının ortak görevleri gerçekleştirmeye hazır olduğunu gösterir. Gerçek hayattaki bir kapının arkalarında bulunan odalara erişmesi için yol sağladığı gibi, burada da daha az yaygın olan kullanıcı arabirimi, ana hizmetten erişilebilen ilgili işlevlerin ayrı "odaları" (genellikle diğer iletişim kutuları) halinde toplanır.

Alternatif olarak, daha az yaygın olan işlevleri ayrı konumlarda yeniden düzenleme yerine tüm kullanılabilir işlevleri tek bir koleksiyonda sunan bir kullanıcı arabirimi yalnızca bir panodur.

![Outlook'ta ek kullanıcı arabirimini açığa çıkararak kavram oluşturma](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Outlook'ta ek kullanıcı arabirimini açığa çıkararak kavram oluşturma

##### <a name="adaptive-ui"></a>Uyarlamalı Kullanıcı Arabirimi
Kullanıcı arabirimini kullanım veya kullanıcının kendi kendine bildirilen deneyimine göre göstermek veya gizleme, diğer bölümleri gizlerken gerekli kullanıcı arabirimini göstermenin bir diğer yoludur. Kullanıcı arabiriminin ne Visual Studio veya gizley karar verme algoritmaları karmaşık olabilir ve kurallar bazı durumlar için her zaman yanlış olacağını için bu önerilmez.

## <a name="projects"></a><a name="BKMK_Projects"></a> Proje

### <a name="projects-in-the-solution-explorer"></a>Çözüm Gezgini'daki projeler
Projelerin çoğu başvuru tabanlı, dizin tabanlı veya karışık olarak sınıflandırılır. Üç proje türü de aynı anda proje Çözüm Gezgini. Projelerle çalışırken kullanıcı deneyiminin kökü bu pencerenin içinde yer alır. Farklı proje düğümleri başvuru, dizin veya karma mod türünde projeler olsa da, projeye özgü kullanıcı desenlerine ayrılmadan önce başlangıç noktası olarak uygulanması gereken ortak bir etkileşim deseni vardır.

Projeler her zaman:

- Proje içeriklerini düzenlemek için proje klasörleri ekleme olanağını destekleme

- Proje kalıcılığı için tutarlı bir model koruma

Projeler ayrıca şu için tutarlı etkileşim modellerini de korumalı:

- Proje öğelerini kaldırma

- Belgeleri kaydetme

- Proje özelliği düzenleme

- Projeyi alternatif görünümde düzenleme

- Sürükle ve bırak işlemleri

### <a name="drag-and-drop-interaction-model"></a>Sürükleyip bırakma etkileşim modeli
Projeler genellikle kendilerini başvuru tabanlı (depolamadaki proje öğelerine yapılan başvuruları kalıcı olarak bulundurabilir), dizin tabanlı (yalnızca projenin hiyerarşisinde fiziksel olarak depolanan proje öğelerini kalıcı olarak kalıcı olarak bulundurabilir) veya karma (başvuruları veya fiziksel öğeleri kalıcı olarak bulundurabilir) olarak sınıflandırır. IDE, proje içindeki üç proje türüne de aynı anda **Çözüm Gezgini.**

Sürükle ve bırak perspektifinden bakıldığında, aşağıdaki özellikler aşağıdaki özellikler uygulama içindeki her proje türüne **Çözüm Gezgini:**

- **Başvuru tabanlı proje:** Önemli nokta, projenin bir başvuru etrafında depolama alanı içinde bir öğeye sürüklemesidir. Başvuru tabanlı bir proje taşıma işlemi için bir kaynak olarak davranacaksa, yalnızca öğeye yönelik başvuru projeden kaldırmalıdır. Öğe sabit sürücüden silinmemelidir. Başvuru tabanlı bir proje taşıma (veya kopyalama) işlemi için hedef olarak davranacaksa, öğenin özel bir kopyasını yapmadan özgün kaynak öğeye bir başvuru eklemesi gerekir.

- **Dizin tabanlı proje:** Bir sürükle ve bırak bakış noktasından, proje başvuru yerine fiziksel öğenin etrafında sürüklenerek. Dizin tabanlı bir proje taşıma işlemi için kaynak olarak davranacaksa, fiziksel öğeyi sabit sürücüden silmenin yanı sıra projeden kaldırması gerekir. Dizin tabanlı bir proje taşıma (veya kopyalama) işlemi için hedef olarak davranacaksa, kaynak öğenin hedef konumda bir kopyasını yapmalı.

- **Karma hedef projesi:** Sürükle ve bırak açısından bu tür bir projenin davranışı, sürüklenen öğenin doğasına (depolama veya öğenin kendisi için bir başvuru) göre hareket eder. Başvurular ve fiziksel öğeler için doğru davranış yukarıda açıklanmıştır.

projesinde yalnızca bir proje türü **Çözüm Gezgini** sürükle ve bırak işlemleri kolay olurdu. Her proje sistemi kendi sürükle ve bırak davranışını tanımlayabilme özelliğine sahip olduğundan, tahmin edilebilir bir kullanıcı deneyimi sağlamak için bazı yönergeler (Windows Gezgini sürükle ve bırak davranışına göre) izlensin:

- Çalışma alanı içinde değiştirilmemiş bir **sürükleme Çözüm Gezgini** (Ctrl veya Shift tuşları basılı tutulmazken) taşıma işlemiyle sonuçlandır.

- Shift-drag işlemi de taşıma işlemiyle sonuçlandır.

- Ctrl tuşunu basılı tutarak sürükleme işlemi kopyalama işlemiyle sonuçlandır.

- Başvuru tabanlı ve karma proje sistemleri, kaynak öğeye bağlantı (veya başvuru) eklemeyi destekler. Bu projeler sürükle ve bırak işlemi hedefi olduğunda **(Ctrl + Shift** tuşunu basılı tutarak), projeye eklenen öğeye başvuruyla sonuçlandır

Tüm sürükle ve bırak işlemleri başvuru tabanlı, dizin tabanlı ve karma projelerin birleşimleri arasında mantıklı değildir. Özellikle, kaynak dizin tabanlı projenin taşıma işlemi tamamlandıktan sonra kaynak öğeyi silmesi gerektir olduğundan, dizin tabanlı bir kaynak proje ile başvuru tabanlı hedef proje arasında taşıma işlemine izin verme gibi davranması sorunludur. Hedef başvuru tabanlı proje daha sonra silinmiş bir öğeye başvuru ile sonuçlandır.

Hedef başvuru tabanlı projenin kaynak öğenin bağımsız bir kopyasını yapmaması gerektiği için bu tür projeler arasında kopyalama işlemi yapmaya izin vermek de yanıltıcıdır. Benzer şekilde, dizin tabanlı bir proje başvuruları kalıcı hale alamayamadığı için Ctrl + Shift ile dizin tabanlı hedef projeye sürüklemeye izin verilmeyecektir. Sürükle ve bırak işlemi desteklenmiyorsa, IDE bırakmaya izin vereme ve kullanıcıya bırakmasız imleç göstermeli (aşağıdaki işaretçi tablosunda gösterilmiştir).

Sürükle ve bırak davranışını düzgün bir şekilde uygulamak için, sürüklemenin kaynak projesinin doğasının hedef projeyle iletişim kurması gerekir. (Örneğin, başvuru mu yoksa dizin tabanlı mı?) Bu bilgiler, kaynak tarafından sunulan pano biçimiyle belirtilmiştir. Sürükle (veya pano kopyalama) işlemi kaynağı olarak, projenin başvuru tabanlı mı yoksa dizin tabanlı mı olduğuna bağlı olarak bir proje sırasıyla veya `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` sunmalıdır. Bu biçimlerin her ikisi de Windows biçimine benzer, ancak dosya adı yerine dize listelerinin çift sonlandırılan bir dize listesi (veya uygun şekilde döndürüldü) olması dışında aynı veri içeriğine `CF_HDROP` `NULL` `Projref` `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` sahiptir.

Bir bırakmanın (veya pano yapıştırma işlemi) hedefi olarak, bir proje hem hem de kabul eder ancak sürükle ve bırak işlemi tam olarak işleme, hedef projenin ve kaynak projenin doğasına bağlı olarak `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` değişir. Kaynak proje, veya teklifine göre doğasını `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` bildirer. Bırakmanın hedefi kendi doğasını anlar ve bu nedenle taşıma, kopyalama veya bağlantının gerçekleştirilip gerçekleştirilecekleri konusunda karar vermek için yeterli bilgiye sahip olur. Kullanıcı ayrıca Ctrl, Shift veya hem Ctrl hem de Shift tuşlarına basarak hangi sürükle ve bırak işlemi gerçekleştirileceklerini de değiştirmektedir. Bırakma hedefinin, ve yöntemlerinde hangi işlemi önceden gerçekleştirilecek olduğunu düzgün şekilde belirtmek `DragEnter` `DragOver` önemlidir. Kaynak **Çözüm Gezgini** projenin ve hedef projenin aynı proje olup olmadığını otomatik olarak bilir.

Proje öğelerinin Visual Studio (örneğin, bir devenv.exe diğerine) sürüklenme özellikle desteklanmaz. Bu **Çözüm Gezgini** bunu da doğrudan devre dışı bıraktır.

Kullanıcı her zaman bir öğeyi seçerek, hedef konuma sürükleyerek ve öğe bırakılamadan önce aşağıdaki fare işaretçilerinin hangilerinin görüntülendiğinden gözlemleyerek sürükle ve bırak işlemi etkisini belirleye çalışması gerekir:

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
| Ctrl+Shift+Sürükleme | Not | Windows Gezgini'nde kısayollar için sürükle ve bırak davranışıyla aynı. ||
| Kes/Yapıştır | Eylem | Taşı | Bağlantı |
| Kes/Yapıştır | Hedef | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Kes/Yapıştır | Kaynak | Özgün öğe başvurularını korur|Özgün öğeyi korur |
| Kes/Yapıştır | Sonuç | Öğe depolamada özgün konumda kalır | Öğe depolamada özgün konumda kalır |
| Kopyala/Yapıştır | Eylem | Kopyala | Bağlantı |
| Kopyala/Yapıştır | Kaynak | Özgün öğeye başvuru ekler | Özgün öğeye başvuru ekler |
| Kopyala/Yapıştır | Sonuç | Özgün öğe başvurularını korur | Özgün öğeyi korur |
| Kopyala/Yapıştır | Eylem | Öğe depolamada özgün konumda kalır | Öğe depolamada özgün konumda kalır |

#### <a name="directory-based-projects"></a>Dizin tabanlı projeler
Aşağıdaki tabloda, kaynak öğenin yapısına ve dizin tabanlı hedef projeler için basılmış değiştirici tuşlarına bağlı olarak gerçekleştirilecek sürükle ve bırak (kesme/kopyalama/yapıştırma) işlemleri özetlenmiştir:

| Değiştirici | Kategori | Kaynak öğe: Başvuru/Bağlantı | Kaynak öğe: Fiziksel öğe veya dosya sistemi ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Değiştirici yok | Eylem | Taşı | Taşı |
| Değiştirici yok | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Değiştirici yok | Kaynak | Özgün öğe başvurularını siler | Özgün öğe başvurularını siler |
| Shift+Drag | Eylem | Taşı | Taşı |
| Shift+Drag | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Shift+Drag | Kaynak | Özgün öğe başvurularını siler | Öğeyi özgün konumdan siler |
| Shift+Drag | Sonuç | `DROPEFFECT_MOVE` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | `DROPEFFECT_MOVE` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır |
| Ctrl+Sürükle | Eylem | Kopyala | Kopyala |
| Ctrl+Sürükle | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Ctrl+Sürükle | Kaynak | Özgün öğe başvurularını korur | Özgün öğe başvurularını korur |
| Ctrl+Sürükle | Sonuç | `DROPEFFECT_COPY` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır | `DROPEFFECT_COPY` öğesinden eylem olarak `::Drop` döndürülür ve öğe depolamada özgün konumda kalır |
| Ctrl+Shift+Sürükleme | | Bırakma yok | Bırakma yok |
| Kes/Yapıştır | Eylem | Taşı | Taşı |
| Kes/Yapıştır | Hedef | Öğeyi hedef konuma kopyalar | Öğeyi hedef konuma kopyalar |
| Kes/Yapıştır | Kaynak | Özgün öğe başvurularını siler | Öğeyi özgün konumdan siler |
| Kes/Yapıştır | Sonuç | Öğe depolamada özgün konumda kalır | Öğe depolamada özgün konumdan silindi |
| Kopyala/Yapıştır | Eylem | Kopyala | Kopyala |
| Kopyala/Yapıştır | Hedef | Özgün öğeye başvuru ekler | Öğeyi hedef konuma kopyalar |
| Kopyala/Yapıştır | Kaynak | Özgün öğeyi korur | Özgün öğeyi korur |
| Kopyala/Yapıştır | Sonuç | Öğe depolamada özgün konumda kalır | Öğe, depolamada özgün konumda kalır |

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
