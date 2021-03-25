---
title: Visual Studio için menüler ve komutlar | Microsoft Docs
description: Visual Studio için yeni özellikler oluşturduğunuzda, komut çubuklarının Kullanıcı arabiriminde esneklik için nasıl izin sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1061de343ae24dce163dd0a7665d58ec7aac3a3a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068394"
---
# <a name="menus-and-commands-for-visual-studio"></a>Visual Studio İçin Menüler ve Komutlar
## <a name="command-usage"></a>Komut kullanımı

### <a name="overview"></a>Genel Bakış
 Birçok ayrı ürünü kapsayan Microsoft Office aksine, Visual Studio her biri kendi komut kümelerini küresel Visual Studio IDE 'ye katkıda bulunan birçok ürün içerir. IDE, içeriğe göre Kullanıcı tarafından kullanılabilen işlevselliği filtreleyerek binlerce komutun karmaşıklığını yönetir.

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
 Komutlarınızın başkaları tarafından özelleştirildiğini ve bunları uygun şekilde tasarlayacağına dikkat edin. Gizli komut olarak böyle bir şey yoktur. Tüm Visual Studio komutları **araçlar > özelleştirme** iletişim kutusunda, komut penceresinde, otomatik olarak tamamlan, **araçlar > seçenekler > klavye** Iletişim kutusu ve GELIŞTIRME araçları ortamı (DTE) içinde görünür. Kullanıcılarınızın bunları kolayca bulabilmesi için. CTC dosyanızda bir ad ve araç ipucu verdiğinizden emin olun.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Gömülü bir araç çubuğunda paylaşılan komutları çoğaltmayın.
 Komutları kullanıcının odağının alanına yakın bir yere yerleştirmek yararlı olur. Bunu yapmanın bir yolu, araç pencerenizin veya belge düzenleyicisinin en üstünde gömülü bir araç çubuğu oluşturmaktır. Araç çubuğuna yerleştirilmiş komutlar, pencere içindeki içerik bölgesine özgü olmalıdır. Bu araç çubuklarında paylaşılan komutları çoğaltmayın. Örneğin, gömülü bir araç çubuğuna hiçbir yerde "Kaydet" simgesi yerleştirmeyin.

### <a name="content-and-command-visibility"></a>İçerik ve komut görünürlüğü
 Aşağıdaki kapsamlarda komutlar var: **ortam**, **hiyerarşi** ve **belge**. Her kapsamı, komut yerleşimine güven sağlamak için öğrenin.

 **Ortam** kapsamındaki komutlar birincil bağlam oluştururlar ve birden çok bağlam arasında paylaşılır. Belgeler ve araç pencerelerinin görünürlüğünü veya düzenlemesini değiştirir. Ortam kapsamındaki komutlar arasında **Yeni proje**, **sunucuya bağlanma**, **işlem iliştirme**, **kesme**, **kopyalama**, **Yapıştırma**, **bulma**, **Seçenekler**, **Özelleştirme**, **yeni pencere** ve **Yardım görüntüleme**.

 **Hiyerarşi** kapsamındaki komutlar, Visual Studio 'da **Proje**, **Takım** ve **veri** dahil hiyerarşileri yönetir. Bunlar, bir projenin alt içeriğiyle ilgilidir; Örneğin, **hata ayıklama**, **derleme**, **Test**, **mimari** veya **analiz**. Hiyerarşi kapsamındaki komutlar arasında **Yeni öğe ekleme**, **Yeni sorgu**, **proje ayarları**, **Yeni veri kaynağı ekleme**, **performansı Başlatma Sihirbazı** ve **Yeni Diyagram** bulunur.

 **Belge** kapsamındaki komutlar, kod, tasarım veya iş öğesi sorgusu (WIQ) gibi bir belgenin içeriğine göre davranır. Ayrıca araç penceresinin görünümü üzerinde çalışır veya başka bir araç penceresine özgü değildir. Belge kapsamı komutları Ayrıca, **projeden kaldır** gibi kendi hiyerarşilerine özgü dosya nesnelerine de davranır. Belge kapsamındaki komutlar arasında **yeniden düzenleme >**, **iş öğesinin kopyasını oluştur**, **Tümünü Genişlet**, **Tümünü Daralt** ve **Kullanıcı oluştur görevi**.

### <a name="command-placement-decisions"></a>Komut yerleştirme kararları
 Bir komut oluşturmaya karar verdikten sonra, uygun yerleştirmesini ve klavye kısayolunun oluşturulup oluşturulmayacağını belirlemeniz gerekir. Komutun nereye yerleştirileceğini belirlemek için bu karar yolunu izleyin:

 ![Komut yerleştirme karar grafiği](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Visual Studio 'da komut yerleştirme için karar yolu**

### <a name="command-placement-in-menus"></a>Menülerde komut yerleşimi

#### <a name="main-menu-bar"></a>Ana menü çubuğu
 Ana menü çubuğu, Kullanıcı arabirimine katkıda bulunan tüm içeriğe özgü menü paketlerinin komutları için standart konum olmalıdır. Ana menü çubuğu, ortamın hangi komutların görünür olduğunu denetlemek için kullandığı diğer komut yapılarından farklıdır. Diğer tüm komut çubukları, bir menü veya bir araç çubuğunda yerleştirilmiş olan komutları yalnızca bağlamdan devre dışı bırakır.

 Ortam, ana menü çubuğunun tamamında yerleşik olarak bulunan ve IDE ve birden çok görev etki alanı üzerinde ortak olan bir komutlar kümesi tanımlar. Bu komutlar, ortama hangi VSPackages yüklendiğine bakılmaksızın her zaman görünür. VSPackages bu komut kümesini genişletebilse de, her üründen ve komutlarının yerleştirilmesi her ekibin sorumluluğundadır.

 Visual Studio ana menüsünün yapısı aşağıdaki menü kategorilerine ayrılabilir:

##### <a name="core-menus"></a>Temel menüler

- Dosya

- Düzenle

- Görüntüle

- Araçlar

- Pencere

- Help

##### <a name="project-specific-menus"></a>Projeye özgü menüler

- Project

- Derleme

- Hata Ayıklama

##### <a name="context-specific-menus"></a>İçeriğe özgü menüler

- Takım

- Veriler

- Test

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

- Açılır menüler yalnızca bir düzey derinlikte olmalıdır. bazı Visual Studio menü öğelerinde basamaklı alt menüler var, ancak bu model teşvik edilmez.

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

     ![Visual Studio 'da bölünmüş düğmeler](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Bölünmüş düğme örneği. Sol taraftaki altı komut, bunun yerine tek bir düğmeye uyadır.**

#### <a name="product-specific-toolbars"></a>Ürüne özgü araç çubukları
 Her ürün, sık kullanılan ve önemli komutları içeren varsayılan bir araç çubuğu sağlayabilir ve ürün yüklendikten sonra Visual Studio ilk kez başlatıldığında her bir ürünün varsayılan araç çubuğu görünür.

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

 ![Belirtme çizgileri olan Visual Studio Biçim menüsü](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Visual Studio 'da menü grupları**

### <a name="reducing-and-reusing-commands"></a>Komutları azaltma ve yeniden kullanma
 Komutlar, kullanıcının belirli bir zamanda gördüğü komutların sayısını azaltmak için genellikle bağlam temelinde gösterilir. Ancak, komut yapısının bağlamdaki değişiklikler arasında görece kararlı kalmasını sağlamak için var olan paylaşılan menüleri ve komut gruplarını de yeniden kullanmanız gerekir.

 Paylaşılan komutları yeniden kullanmak ve ilgili paylaşılan komutlara yakın yeni komutların yerleştirilmesi IDE karmaşıklığını azaltır ve Kullanıcı dostu daha kolay bir deneyim oluşturur.

## <a name="naming-commands"></a>Adlandırma komutları

### <a name="naming-conventions"></a>Adlandırma kuralları
 Tutarlı komut adlandırması, kullanıcıların komut satırını kullanarak ya da bir klavye kısayoluna bağlayarak komutları bulabilmesi ve yürütebilmesi için kritik öneme sahiptir. Komut adları, kullanıcının bir araç çubuğunda veya basamaklı ya da bağlam menüsünde görüntülendiğinde bir komutun ne amaçla çalıştığını anlamalarına de yardımcı olur.

#### <a name="when-naming-commands"></a>Komutları adlandırırken:

- Kolayca yerelleştirilebilir olacak şekilde metin oluşturun. Metni yerelleştirme hakkında daha fazla bilgi için bkz. [Yerelleştirme en iyi yöntemleri](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Kısa olmalıdır. Komutların üçten fazla kelime kullanması gerekir.

- Büyük/küçük harf kullanımı kullan: her sözcüğün ilk harfi büyük harfle yazılmalıdır. Visual Studio 'da metin biçimlendirme hakkında daha fazla bilgi için bkz. [metin stili](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Komutun yerleştirileceği yere göz atın. Bu, üst düzey bir menü veya açılır pencere mi? Örneğin, bir açılır pencere içindeki hizalama komutları gruplandırılırken, en üst düzey komut "hizalı" olmalıdır ve açılır menü komutları "Left," "Right," "Center," "hizalı" olmalıdır. "Sola Hizala" veya "Sağa Hizala" açılan menü komutlarını adlandırmak gereksiz olacaktır.

     ![Visual Studio Biçim menüsü](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Komutlarla simgeler kullanma
 Komutlarla birlikte simge eşleştirme Sparing olun. Benzersiz bir görüntünün bir komutla ilişkilendirilmesi, kullanıcının bu komutu belirleyebilme özelliğini hastens, görüntü fazla kullanımı ile birlikte görsel dağınıklık ve inefficiency oluşur. Aşağıdaki kurallar, bir komut simgesi oluşturulup oluşturulmayacağını saptarken yardımcı olur.

#### <a name="use-an-icon-with-a-command-only-if"></a>Komutuyla yalnızca şu durumlarda bir simge kullanın:

- Aynı komutta, Microsoft Office uygulamalardan biri gibi, başka bir önemli Microsoft ürününde onunla ilişkili bir simge vardır.

- Komut varsayılan bir araç çubuğuna yerleştirilecek.

- Komut, kullanıcıların **"Özelleştir..."** iletişim kutusunu kullanarak bir araç çubuğuna ekleyebileceği özel bir komuttur.

## <a name="access-and-shortcut-keys"></a>Erişim ve kısayol tuşları

### <a name="overview"></a>Genel Bakış
 İki tür klavye anahtarı ataması vardır:

- **Erişim anahtarları** (Hızlandırıcılar olarak da bilinir), komut için menüler ve iletişim kutusu kullanıcı arabirimindeki her bir etikete aracılığıyla klavye erişimine izin verir. Erişim tuşları çoğunlukla erişilebilirlik amaçlıdır, tüm menülere ve çoğu iletişim kutusu denetimine atanır, bu, yalnızca geçerli pencereyi etkiler ve yerelleştirilir.

- **Kısayol tuşları** çoğunlukla Control (Ctrl) ve function (fn) anahtar dizilerini kullanır. Bunlar, gelişmiş kullanıcılar için daha fazla tasarlanırlar ve verimliliğine yardımcı olur. Bunlar yalnızca en sık kullanılan komutlara atanır ve ana menüyü atlayarak hızlı erişime izin verir. Kısayol tuşlarının yeniden başlatılması amaçlanmıştır ve bu nedenle, profil düzeni ile tutarlı bir şekilde atanması gerekir. Kısayol tuş düzenleri profilden profile farklılık gösterebilir. Kullanıcı, kısayol tuşlarını **araçlar > seçenekler > klavyeden** özelleştirebilir.

### <a name="assigning-access-keys"></a>Erişim anahtarları atanıyor
 Erişim tuşları alt ve alfasayısal anahtarlardan oluşur. Her menü öğesine özel durum olmadan bir erişim anahtarı atayın. Erişim anahtarları atamak için Windows ve ortak kuralları izleyin. Örneğin, **> yeni dosya** için erişim anahtarı her zaman **alt, F, N** olmalıdır.

 ' I ' (büyük veya küçük harf) veya küçük harf ' l ' gibi tek pikselli harfler kullanmayın ve bunları ayırt etmek zor olacak şekilde harflerin (g, j, p, q ve y) karakterlerini kullanmaktan kaçının.

 Mümkün olduğunda yinelenen anahtarlar kullanmaktan kaçının. Tekrarların kaçınılmaz olduğu durumlarda, menü sistemi, anahtarı kullanan tüm komutlarda geçiş yaparak çakışmaları işler. Örnek olarak, "N" erişim anahtarını çoğaltan Dosya menüsünün altındaki kuramsal bir "numara" komutu için **alt, f, n** yeni bir dosya oluşturacak ve **alt, f, n, n** "Number" komutunu gerçekleştirecek.

### <a name="assigning-shortcut-keys"></a>Kısayol tuşları atama
 Yeni kısayol tuşları atamaktan kaçının, çünkü bunlar her komut için gerekli değildir ve fazla kullanılıyorsa sistemin (ve Kullanıcı belleğinin) vergisine dahil edilmez. Müşteri Deneyimini Geliştirme Programı (CEIP) verileri, Visual Studio kullanıcılarının tümleşik kısayolların yalnızca küçük bir alt kümesini kullanacağını gösterir.

 Kısayolları tanımlarken bu kuralları izleyin:

- **Control (Ctrl) ve function (fn) anahtar dizilerini kullanın.**

- **Sık kullanılan kısayolları koru.** En popüler kısayolları koruyun.

- **Düzenleyici kısayollarının kolayca türünü kolaylaştırın.** Geliştiricilerin daha fazla kod yazarken ihtiyacı olan komutlara kolay tür kısayolları bağlayın. Örneğin, **Edit. InvokeSmartTag** ' ın CTRL +/gibi bir hızlı kısayol tuşuna sahip olması gerekir ve alt + SHIFT + F10 tuşlarına basın.

- **Tutarlı temalı kısayollar için çaba harcar.**

- **Hangi değiştirici anahtarların çalıştırılacağını öğrenmek için Windows kılavuzları ' nı izleyin.** Tüm belgeye uygulanan komutlar gibi büyük ölçekli etkileri olan komutlar için CTRL tuş bileşimlerini kullanın. Standart kısayol tuşu eylemlerini genişleten veya tamamlayan komutlar için SHIFT tuş bileşimlerini kullanın. Ctrl + Alt kombinasyonlarını kullanmayın.

- **Gereksiz kısayolları kaldırın.** Eski bir özellik varsa, bir erişim anahtarı aynı komuta hızlı erişim sağlıyorsa, çok seyrek erişimli (CEIP verilerinden 10 ' dan az) veya (CEIP verilerinden en az 100 kez) kullanılan kısayolları kaldırmayı göz önünde bulundurun. Örneğin: alt, H, C, yardım/Içerik açar.

  Kısayol kullanılabilirliğini kontrol etmenin basit bir yolu yoktur. Bir kısayol eklemek istiyorsanız aşağıdaki adımları izleyin:

1. Kendi ile gruplamak için benzer komutların olup olmadığını öğrenmek için [Visual Studio 2013 kısayollarının](http://visualstudioshortcuts.com/2013/) listesini denetleyin.

2. **Araçlar > seçenekler > ortam > klavye** ' ye gidin ve kısayolunuzu test edin. "Aşağıdaki ek klavye eşleme şemasını uygula" altında listelenen her bir klavye eşleme şemasını işaretleyin. Genel, C#, VB ve C++ profillerini, bu kişiler benzersiz kısayollar paylaştığından denetleyin. Kısayolunuz bu yerlerden herhangi birinde eşlenmişse kullanılabilir.
