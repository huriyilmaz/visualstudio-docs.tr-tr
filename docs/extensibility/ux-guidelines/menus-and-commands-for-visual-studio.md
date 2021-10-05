---
title: Visual Studio için menüler ve komutlar | Microsoft Docs
description: Visual Studio için yeni özellikler oluşturduğunuzda komut çubuklarının Kullanıcı arabirimindeki esnekliğe nasıl izin vereceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5568205f0d8632942275816d130cfef6695bb779
ms.sourcegitcommit: 2eb12954b7b0ac9508fff11a86c54e880f3d104f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439749"
---
# <a name="menus-and-commands-for-visual-studio"></a>Visual Studio İçin Menüler ve Komutlar
## <a name="command-usage"></a>Komut kullanımı

### <a name="overview"></a>Genel Bakış
 birçok ayrı ürünü kapsayan Microsoft Office aksine Visual Studio, her biri kendi komut kümelerinin genel Visual Studio ıde 'sine katkıda bulunduğu birçok ürün içerir. IDE, içeriğe göre Kullanıcı tarafından kullanılabilen işlevselliği filtreleyerek binlerce komutun karmaşıklığını yönetir.

 Bir kullanıcının bağlam değişiklikleri (bir tasarım penceresinden kod düzenlemesi penceresine geçiş gibi), yeni bağlamla ilgisi olmayan işlevler kaybolur. Aynı zamanda yeni işlevsellik, Özellikler ve araç kutusu seçenekleri gibi ilgili dinamik bilgilerle birlikte yüzeylerdir. Kullanıcı, kullanılabilir komut kümesinin takas durumunu fark etmez. Kullanıcı, görüntülenen veya görünmeyen komutlar tarafından boşlandığında veya karıştırılandığında, Kullanıcı arabirimi tasarımının ayarlanması gerekir. Kullanıcının geçerli bağlamı her zaman IDE başlık çubuğu, Özellikler penceresi veya özellik sayfaları iletişim kutusu gibi bir veya daha fazla şekilde belirtilir.

 Komut çubukları Kullanıcı arabiriminde esneklik sağlar. Visual Studio ortamına ait tek komut yapıları ana menü ve ana komut çubuğudur ve bu, her ikisi de özelleştirilebilir ve hatta gizli olabilir. Diğer komut çubukları, uygulamanın durumuna göre görünür ve kaybolur. Araç pencereleri ve belge düzenleyicileri, pencere kenarları içinde katıştırılmış araç çubukları da içerebilir.

#### <a name="basic-guidelines"></a>Temel yönergeler

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Mümkün olduğunda mevcut paylaşılan komutları, komut gruplarını ve menüleri kullanın.
 Komutlar genellikle bağlam temelinde gösterildiğinden, var olan paylaşılan menülerin ve komut gruplarının kullanılması, komut yapısının bağlamdaki değişiklikler arasında görece tutarlı kalmasını sağlar. Paylaşılan komutları yeniden kullanmak ve ilgili paylaşılan komutlara yakın yeni komutların yerleştirilmesi, IDE karmaşıklığını da azaltır ve Kullanıcı dostu bir deneyim oluşturur. Yeni bir komutun tanımlanması gerekiyorsa, var olan bir paylaşılan komut grubuna yerleştirmeyi deneyin. Yeni bir grubun tanımlanması gerekiyorsa, yeni bir üst düzey menü oluşturmadan önce, mevcut bir paylaşılan menüye ilgili bir komut grubuna yakın bir yere yerleştirin.

##### <a name="do-not-create-icons-for-every-command"></a>Her komut için simgeler oluşturmayın.
 Komut simgesini oluşturmadan önce dikkatlice düşünün. Simgeler yalnızca şu komutlar için oluşturulmalıdır:

- Varsayılan bir araç çubuğunda görüntülenir.

- Kullanıcı tarafından bir araç çubuğuna **Özelleştirme...** iletişim kutusu aracılığıyla eklenebilir.

- başka bir Microsoft ürününde aynı eylemle ilişkili bir simgeye sahip.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Klavye kısayollarının eklenmesini sınırlayın
 Kullanıcıların büyük çoğunluğu, tüm kullanılabilir kısayolların küçük bir kısmını daha fazla kullanabilir. Şüpheli olduğunda, özelliği klavye kısayoluna bağlamayın. Yeni kısayollar eklemeden önce Kullanıcı deneyimi ekibinizle birlikte çalışın.

##### <a name="give-commands-a-default-menu-placement"></a>Komutlara varsayılan bir menü yerleşimi verin.
 Komutlarınızın başkaları tarafından özelleştirildiğini ve bunları uygun şekilde tasarlayacağına dikkat edin. Gizli komut olarak böyle bir şey yoktur. tüm Visual Studio komutları **araçlar > özelleştir** iletişim kutusunda, komut penceresinde, otomatik olarak, **araçlar > seçenekler > klavye** iletişim kutusunda ve geliştirme araçları ortamında (DTE) görünür. Kullanıcılarınızın bunları kolayca bulabilmesi için. CTC dosyanızda bir ad ve araç ipucu verdiğinizden emin olun.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Gömülü bir araç çubuğunda paylaşılan komutları çoğaltmayın.
 Komutları kullanıcının odağının alanına yakın bir yere yerleştirmek yararlı olur. Bunu yapmanın bir yolu, araç pencerenizin veya belge düzenleyicisinin en üstünde gömülü bir araç çubuğu oluşturmaktır. Araç çubuğuna yerleştirilmiş komutlar, pencere içindeki içerik bölgesine özgü olmalıdır. Bu araç çubuklarında paylaşılan komutları çoğaltmayın. Örneğin, gömülü bir araç çubuğuna hiçbir yerde "Kaydet" simgesi yerleştirmeyin.

### <a name="content-and-command-visibility"></a>İçerik ve komut görünürlüğü
 Aşağıdaki kapsamlarda komutlar var: **ortam**, **hiyerarşi** ve **belge**. Her kapsamı, komut yerleşimine güven sağlamak için öğrenin.

 **Ortam** kapsamındaki komutlar birincil bağlam oluştururlar ve birden çok bağlam arasında paylaşılır. Belgeler ve araç pencerelerinin görünürlüğünü veya düzenlemesini değiştirir. ortam kapsamındaki komutlar arasında **yeni Project**, **sunucu Bağlan**, **işlem**, **kesme**, **kopyalama**, **yapıştırma**, **bulma**, **seçenekler**, **özelleştirme**, **yeni pencere** ve **yardım görüntüleme**.

 **hiyerarşi** kapsamındaki komutlar, **Project**, **ekip** ve **verileri** de içeren Visual Studio hiyerarşileri yönetir. Bunlar, bir projenin alt içeriğiyle ilgilidir; Örneğin, **hata ayıklama**, **derleme**, **Test**, **mimari** veya **analiz**. hiyerarşi kapsamındaki komutlar arasında **yeni öğe ekleme**, **yeni sorgu**, **Project Ayarlar**, **yeni veri kaynağı ekleme**, **performansı başlatma sihirbazı** ve **yeni diyagram** bulunur.

 **Belge** kapsamındaki komutlar, kod, tasarım veya iş öğesi sorgusu (WIQ) gibi bir belgenin içeriğine göre davranır. Ayrıca araç penceresinin görünümü üzerinde çalışır veya başka bir araç penceresine özgü değildir. Belge kapsamı komutları Ayrıca, kendi hiyerarşilerine özgü olan dosya nesnelerini de ( **Project kaldır** gibi) de çalışır. Belge kapsamındaki komutlar arasında **yeniden düzenleme >**, **iş öğesinin kopyasını oluştur**, **Tümünü Genişlet**, **Tümünü Daralt** ve **Kullanıcı oluştur görevi**.

### <a name="command-placement-decisions"></a>Komut yerleştirme kararları
 Bir komut oluşturmaya karar verdikten sonra, uygun yerleştirmesini ve klavye kısayolunun oluşturulup oluşturulmayacağını belirlemeniz gerekir. Komutun nereye yerleştirileceğini belirlemek için bu karar yolunu izleyin:

 ![Komut yerleştirme karar grafiği](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Visual Studio 'de komut yerleştirme için karar yolu**

### <a name="command-placement-in-menus"></a>Menülerde komut yerleşimi

#### <a name="main-menu-bar"></a>Ana menü çubuğu
 Ana menü çubuğu, Kullanıcı arabirimine katkıda bulunan tüm içeriğe özgü menü paketlerinin komutları için standart konum olmalıdır. Ana menü çubuğu, ortamın hangi komutların görünür olduğunu denetlemek için kullandığı diğer komut yapılarından farklıdır. Diğer tüm komut çubukları, bir menü veya bir araç çubuğunda yerleştirilmiş olan komutları yalnızca bağlamdan devre dışı bırakır.

 Ortam, ana menü çubuğunun tamamında yerleşik olarak bulunan ve IDE ve birden çok görev etki alanı üzerinde ortak olan bir komutlar kümesi tanımlar. Bu komutlar, ortama hangi VSPackages yüklendiğine bakılmaksızın her zaman görünür. VSPackages bu komut kümesini genişletebilse de, her üründen ve komutlarının yerleştirilmesi her ekibin sorumluluğundadır.

 Visual Studio ana menünün yapısı aşağıdaki menü kategorilerine ayrılabilir:

##### <a name="core-menus"></a>Temel menüler

- Dosya

- Düzenle

- Görüntüle

- Araçlar

- Pencere

- Help

##### <a name="project-specific-menus"></a>Project özgü menüler

- Project

- Derleme

- Hata Ayıklama

##### <a name="context-specific-menus"></a>İçeriğe özgü menüler

- Takım

- Veriler

- Test etme

- Mimari

- Analiz

##### <a name="document-specific-menus"></a>Belgeye özgü menüler

- Biçimlendir

- Tablo

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Ana menüleri tasarlarken, bu kurallara bağlı olarak:

- Belirli bir bağlamda 25 üst düzey öğeyi aşmayın

- Menüler, yüksekliği asla 600 piksel aşmamalıdır.

- Ana menüyü, en son SKU ve genel profilde olduğu gibi birden çok bağlamda değerlendirin.

- Açılır menüler kabul edilebilir.

- Açılır menüler en az üç öğe içermeli ve en fazla yedi tane olmalıdır.

- açılır menüler yalnızca bir düzey derinlikte olmalıdır; bazı Visual Studio menü öğelerinde basamaklı alt menüler var, ancak bu model teşvik edilmez.

- Altıdan fazla ayırıcı kullanın. Gruplandırmalar aşağıdaki çizime uymalıdır:

     ![Ana menü gruplandırması için yönergeler](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Her gruplandırmanın gruplandırılmasına gerek duyulmadığından, ek gruplandırmaları eklemek kısıtlıdır.

- Her gruplama iki ile yedi arasında menü öğesinden oluşmalıdır.

#### <a name="main-menu-ordering"></a>Ana menü sıralaması
 Yeni bir üst düzey öğe eklemeden önce, komutu varolan bir üst düzey menüye yerleştirmeyi düşünün. Yeni bir üst düzey menü eklerken doğru konuma yerleştirdiğinizden emin olun. Menünün proje, bağlam veya belgeye özgü olup olmadığına karar verin. Üst düzey menünün adını kısa tutun ve yalnızca bir kelime kullanın.

 Temel menülerde komutların geri kalanı yer almalıdır. Dosya, düzenleme ve görünüm her zaman sol tarafta olmalıdır ve araçlar, pencere ve yardım her zaman doğru olmalıdır.

#### <a name="context-menus"></a>Bağlam menüleri
 Bağlam menülerinde çok fazla işlevsellik yerleştirilmesi, zor öğrenme arabirimine neden olur. Tüm önemli işlevler ana menü çubuğu aracılığıyla kullanılabilir olmalıdır. Yinelenen komutların olmaması için komutların yerleştirilmesi mevcut komutlarla mutabık kılınmalıdır. Bağlam menüleri için kabuk, bağlam menüsünün çözüm, proje düğümü veya proje öğesi için olup olmadığına bağlı olarak eklenmesi gereken standart menü gruplarını tanımlar.

 Bağlam menülerini tasarlarken, ana menü ve ek olarak aynı kurallara bağlı olarak:

- 25 üst düzey menü öğesini aşmayın.

- Açılır menüler kabul edilebilir ancak bir düzey derinlikten fazla olmamalıdır. hiçbir şekilde basamaklı değiştirmeme kullanmayın.

- Altıdan fazla ayırıcı kullanın.

### <a name="command-placement-in-toolbars"></a>Araç çubuklarında komut yerleşimi

#### <a name="general-toolbars"></a>Genel araç çubukları
 Araç çubuklarını tasarlarken ve düzenleme sırasında şu standartları izleyin:

- Düğme başına birden fazla fiil kullanmayın. Bir düğme = bir eylem.

- Yalnızca etiketle yeniden zorlanması gerekiyorsa, simgenin yanında bulunan metni kullanın.

- Tek bir oturumda birden çok kez geçiş yapılacak özellikler için özel bir açılan kutu kullanın. Aksi takdirde, özelliği başka bir yerde kullanıma sunun.

- Birleşik giriş kutusunun genişliği, Box + %30 ' daki en uzun öğenin genişliğine eşit olmalıdır. Örneğin, en uzun öğe 200 piksel ise, Birleşik giriş kutusu 260 piksel genişliğinde olmalıdır.

- Ayırıcılar kullanımını sınırlayın. Açılan menü şeklinin bir görsel ayırıcı olarak davrandığı için, DropDown 'ın yanındaki bir ayırıcısının kullanımı bir anti-örünmedir.

- Simge grupları üçden altıya kadar simge içermelidir.

- Niteleyiciler birden çok yararlı komuta neden oluyorsa, son ayarı depolayan bir bölünmüş düğme kullanın:

     ![Visual Studio düğmeleri bölme](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Bölünmüş düğme örneği. Sol taraftaki altı komut, bunun yerine tek bir düğmeye uyadır.**

#### <a name="product-specific-toolbars"></a>Ürüne özgü araç çubukları
 her ürün, sık kullanılan ve önemli komutları içeren varsayılan bir araç çubuğu sağlayabilir ve ürün yüklendikten sonra Visual Studio her ürünün varsayılan araç çubuğunun ilk kez başlatılması gerekir.

 Ürünler Ayrıca IDE tarafından sunulan paylaşılan komut grupları ve menülerinden de faydalanır. Her paylaşılan komut grubu, ilgili komutların Kullanıcı için anlamlı bir şekilde düzenlenmesi amacıyla paylaşılan bir menüye yerleştirilir. Karmaşıklığı azaltmak için bu paylaşılan komut yapısının yararlanmak önemlidir.

#### <a name="global-toolbars"></a>Genel araç çubukları
 Genel araç çubuklarının, kutudan hemen bir satıra sığması gerekir. Yeni bir genel araç çubuğu oluştururken, bu araç çubuğu türü için yönergeleri izleyin.

 **Genel araç çubuğu yönergeleri:**

- Her araç çubuğunun ortak denetimlerde (kavrayıcı, taşma) 24 piksel vardır.

- Her araç çubuğu düğmesi, doldurma dahil 22 piksel geniştir. Simgenin bölünmüş düğme haline getirilmesi, 11 piksel genişliğinde bir genişlik ekler.

- Komutların araç çubuklarında çoğaltılmasını izin verilir.

  Belirli bir dosya türü etkin olduğunda **belgeye özgü araç çubukları** görünür ve farklı bir dosya türü etkin hale geldiğinde kaybolur.

- Belgeye özgü araç çubuklarında 12 ' den fazla düğme bulunmayabilir.

- Araç çubuğunun toplam genişliği 300 pikselden fazla olamaz.

- Her dosya türü, katıştırılmış bir araç çubuğuna veya bir belgeye özgü genel araç çubuğuna sahip olabilir, ancak her ikisine birden bulunamaz.

  Belirli bir bağlam ayarlandığında ve genişletilmiş dönemler için etkin kalmazsa, **içeriğe özgü araç çubukları** görüntülenir.

- Tüm içeriğe özgü araç çubukları için düğme sınırı 18 ' dir.

- Çoğu Kullanıcı, bağlam etkin olduğunda bu araç çubuğunun komutlarını sürekli olarak kullanmayacaksa, bu araç çubuğunu bir bağlamla ilişkilendirmeyin.

- İçerikten çıkarken araç çubuğunun kaybolduğundan emin olun. Bu araç çubuklarının hiçbiri başlangıçta görünmemelidir.

  **Bağlam Içermeyen araç çubukları** hiçbir şekilde otomatik olarak görünmez. Bu, yalnızca Kullanıcı tarafından etkinleşdiğinde gösterilir. En büyük genişliği 200 piksel altında tutun.

### <a name="general-organization-and-shell-defined-groups"></a>Genel kuruluş ve kabuk tanımlı gruplar
 Varolan paylaşılan komutları, komut gruplarını ve menüleri kullanın. Yeni bir komutun tanımlanması gerekiyorsa, var olan bir paylaşılan komut grubuna yerleştirmeyi deneyin. Yeni bir grubun tanımlanması gerekiyorsa, yeni bir üst düzey menü oluşturmadan önce, var olan bir paylaşılan menüye ilgili bir komut grubuna yakın bir yere yerleştirmeyi deneyin. Bu, IDE 'de tutarlı komut yerleşimi sağlarken komut karmaşıklığını azaltır.

 Genellikle Tasarımcı stili belge pencerelerinin bağlamında gösterilen paylaşılan **Biçim** menüsü aşağıdaki görüntüde gösterilmiştir:

 ![Visual Studio Belirtme çizgileri olan Biçim menüsü](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Visual Studio menü grupları**

### <a name="reducing-and-reusing-commands"></a>Komutları azaltma ve yeniden kullanma
 Komutlar, kullanıcının belirli bir zamanda gördüğü komutların sayısını azaltmak için genellikle bağlam temelinde gösterilir. Ancak, komut yapısının bağlamdaki değişiklikler arasında görece kararlı kalmasını sağlamak için var olan paylaşılan menüleri ve komut gruplarını de yeniden kullanmanız gerekir.

 Paylaşılan komutları yeniden kullanmak ve ilgili paylaşılan komutlara yakın yeni komutların yerleştirilmesi IDE karmaşıklığını azaltır ve Kullanıcı dostu daha kolay bir deneyim oluşturur.

## <a name="naming-commands"></a>Adlandırma komutları

### <a name="naming-conventions"></a>Adlandırma kuralları
 Tutarlı komut adlandırması, kullanıcıların komut satırını kullanarak ya da bir klavye kısayoluna bağlayarak komutları bulabilmesi ve yürütebilmesi için kritik öneme sahiptir. Komut adları, kullanıcının bir araç çubuğunda veya basamaklı ya da bağlam menüsünde görüntülendiğinde bir komutun ne amaçla çalıştığını anlamalarına de yardımcı olur.

#### <a name="when-naming-commands"></a>Komutları adlandırırken:

- Kolayca yerelleştirilebilir olacak şekilde metin oluşturun. Metni yerelleştirme hakkında daha fazla bilgi için bkz. [Yerelleştirme en iyi yöntemleri](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Kısa olmalıdır. Komutların üçten fazla kelime kullanması gerekir.

- Büyük/küçük harf kullanımı kullan: her sözcüğün ilk harfi büyük harfle yazılmalıdır. Visual Studio metin biçimlendirme hakkında daha fazla bilgi için bkz. [metin stili](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Komutun yerleştirileceği yere göz atın. Bu, üst düzey bir menü veya açılır pencere mi? Örneğin, bir açılır pencere içindeki hizalama komutları gruplandırılırken, en üst düzey komut "hizalı" olmalıdır ve açılır menü komutları "Left," "Right," "Center," "hizalı" olmalıdır. "Sola Hizala" veya "Sağa Hizala" açılan menü komutlarını adlandırmak gereksiz olacaktır.

     ![Visual Studio Biçim menüsü](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Komutlarla simgeler kullanma
 Komutlarla birlikte simge eşleştirme Sparing olun. Benzersiz bir görüntünün bir komutla ilişkilendirilmesi, kullanıcının bu komutu belirleyebilme özelliğini hastens, görüntü fazla kullanımı ile birlikte görsel dağınıklık ve inefficiency oluşur. Aşağıdaki kurallar, bir komut simgesi oluşturulup oluşturulmayacağını saptarken yardımcı olur.

#### <a name="use-an-icon-with-a-command-only-if"></a>Komutuyla yalnızca şu durumlarda bir simge kullanın:

- aynı komutta, Microsoft Office uygulamalardan biri gibi, başka bir önemli Microsoft ürününde onunla ilişkili bir simge vardır.

- Komut varsayılan bir araç çubuğuna yerleştirilecek.

- Komut, kullanıcıların **"Özelleştir..."** iletişim kutusunu kullanarak bir araç çubuğuna ekleyebileceği özel bir komuttur.

## <a name="access-and-shortcut-keys"></a>Erişim ve kısayol tuşları

### <a name="overview"></a>Genel Bakış
 İki tür klavye anahtarı ataması vardır:

- **Erişim anahtarları** (Hızlandırıcılar olarak da bilinir), komut için menüler ve iletişim kutusu kullanıcı arabirimindeki her bir etikete aracılığıyla klavye erişimine izin verir. Erişim tuşları çoğunlukla erişilebilirlik amaçlıdır, tüm menülere ve çoğu iletişim kutusu denetimine atanır, bu, yalnızca geçerli pencereyi etkiler ve yerelleştirilir.

- **Kısayol tuşları** çoğunlukla Denetim (Ctrl) ve İşlev (Fn) anahtar dizilerini kullanır. Bunlar daha ileri düzey kullanıcılar için tasarlanmıştır ve üretkenlikte yardımcı olur. Bunlar yalnızca en sık kullanılan komutlara atanır ve ana menü atlanırken hızlı erişime izin verir. Kısayol anahtarlarının ezberleneme amacı vardır ve bu nedenle profil şemasıyla tutarlı bir şekilde atanmaları gerekir. Kısayol anahtarı düzenleri profilden profile farklılık gösterebilir. Bir kullanıcı, Araçlar ve Seçenekler ve **Klavye > kısayol > özelleştirilebilir.**

### <a name="assigning-access-keys"></a>Erişim anahtarları atama
 Erişim anahtarları Alt artı alfasayısal anahtarlardan oluşur. Özel durum olmadan her menü öğesinin erişim anahtarını attayabilirsiniz. Erişim Windows atamak için aşağıdaki adımları ve yaygın kuralları izleyin. Örneğin, Yeni Dosya > **için erişim** anahtarı her zaman **Alt, F, N olabilir.**

 Ayırt etmek zor olduğu için 'i' (büyük veya küçük harfle) veya küçük harf 'l' gibi tek piksel genişlikli harfler kullanmayın ve karakterleri alt karakterlerle (g, j, p, q ve y) kullanmaktan kaçının.

 Mümkün olduğunda yinelenen anahtarlar kullanmaktan kaçının. Yinelemenin kaçınılmaz olduğu durumlarda, menü sistemi çakışmaları anahtarı kullanan tüm komutlar üzerinden sızarak işlemeye devam ediyor. Örneğin, Dosya menüsünün altındaki "N" erişim anahtarını çoğaltan varsayımsal bir "Sayı" komutu için **Alt, F, N** yeni bir dosya oluşturabilir ve **Alt, F, N, N** "Sayı" komutunu gerçekleştirecek.

### <a name="assigning-shortcut-keys"></a>Kısayol tuşları atama
 Yeni kısayol tuşları atamaktan kaçının çünkü bunlar her komut için gerekli değildir ve aşırı kullanım varsa sistemi (ve kullanıcı belleğini) vergiler. Veri kümesinden Müşteri Deneyimini Geliştirme Programı (CEIP), kullanıcıların Visual Studio kısayolların yalnızca küçük bir alt kümesini kullanabileceğini gösterir.

 Kısayolları tanımlarken şu kuralları izleyin:

- **Denetim (Ctrl) ve İşlev (Fn) anahtar dizilerini kullanın.**

- **Sık kullanılan kısayolları koruma.** En popüler kısayolları koruma.

- **Düzenleyici kısayollarını kolayca yazın.** Geliştiricilerin kod yazarken en çok ihtiyaçları olan komutlara türü kolay kısayollar bağlayın. Örneğin, **Edit.InvokeSmartTag'ın** Alt+Shift+F10 değil Ctrl+/ gibi bir hızlı kısayol tuşu olması gerekir.

- **Tutarlı bir şekilde thema kısayollar elde edebilirsiniz.**

- **Hangi Windows anahtarlarını belirlemek için aşağıdaki yönergeleri izleyin.** Belgenin tamamı için geçerli olan komutlar gibi büyük ölçekli etkileri olan komutlar için Ctrl tuş birleşimlerini kullanın. Standart kısayol tuşunun eylemlerini genişleten veya tamamlayan komutlar için Shift tuş birleşimlerini kullanın. Ctrl+Alt birleşimleri kullanma.

- **Fazlalık kısayolları kaldırın.** Eski bir özelliğiniz varsa, erişim anahtarı aynı komuta hızlı erişim sağlarsa, aşırı seyrek (CEIP verilerinden 10 kat daha az) veya orta seyreklik (CEIP verilerinden 100'den az) ile kullanılan kısayolları kaldırmayı göz önünde bulundurabilirsiniz. Örneğin: Alt, H, C, Yardım/İçerik'i açar.

  Kısayol kullanılabilirliğini denetlemenin basit bir yolu yok. Kısayol eklemek için şu adımları izleyin:

1. Kullanıcılarınızı grup [Visual Studio 2013 benzer](/visualstudio/ide/default-keyboard-shortcuts-in-visual-studio) komutlar olup olmadığını belirlemek için bu kısayollar listesini kontrol edin.

2. Araçlar ve **> Seçenekleri'ne > Klavye > kısayolunu** test edin. "Aşağıdaki ek klavye eşleme düzenini uygula" altında listelenen her klavye eşleme düzenini kontrol edin. Genel, C#, VB ve C++ profillerini kontrol edin çünkü bunlar benzersiz kısayolları paylaşır. Kısayol, bu yerlerin hiçbirsinde eşlenmemişse kullanılabilir.
