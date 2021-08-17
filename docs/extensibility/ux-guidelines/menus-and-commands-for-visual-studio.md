---
title: Visual Studio | için Menüler ve Komutlar Microsoft Docs
description: Komut çubuklarının kullanıcı arabiriminde esneklik sağlamak için yeni özellikler oluşturmanızı nasıl Visual Studio.
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
ms.openlocfilehash: e786e9557a0a2188d6a220e5aaccd943cad8cd5c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028481"
---
# <a name="menus-and-commands-for-visual-studio"></a>Visual Studio İçin Menüler ve Komutlar
## <a name="command-usage"></a>Komut kullanımı

### <a name="overview"></a>Genel Bakış
 Birçok Microsoft Office üründen oluşan bir paket olan Visual Studio'den farklı olarak, her biri komut kümelerinin genel IDE'ye Visual Studio içerir. IDE, kullanıcıya kullanılabilir olan işlevleri bağlama göre filtreleerek binlerce komutun karmaşıklığını yönetir.

 Kullanıcının bağlamı değişerek tasarım penceresinden kod düzenleme penceresine geçme gibi yeni bağlamla ilgili olmayan işlevler kaybolur. Aynı zamanda yeni işlevler Özellikler ve Araç Kutusu seçenekleri gibi ilgili dinamik bilgilerle birlikte ortaya çıkar. Kullanıcı kullanılabilir komut kümesi değiştirme fark etmez. Kullanıcının dikkati dağılırsa veya komutlar görüntüden kaybolursa kullanıcı arabirimi tasarımının ayarlanması gerekir. Kullanıcının geçerli bağlamı her zaman bir veya daha fazla şekilde (örneğin, IDE başlık çubuğunda, Özellikler penceresi veya Özellik Sayfaları iletişim kutusunda) belirtilmiştir.

 Komut çubukları, kullanıcı arabiriminde esneklik sağlar. Visual Studio ortamının yapısına Visual Studio komut yapıları ana menü ve ana komut çubuğudur. Bunlar hem özelleştirilebilir hem de gizlenir. Uygulamanın durumuna bağlı olarak diğer komut çubukları görünür ve kaybolur. Araç pencereleri ve belge düzenleyicileri, pencere kenarlarının içine eklenmiş araç çubukları da içerebilir.

#### <a name="basic-guidelines"></a>Temel yönergeler

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Mümkün olduğunda mevcut paylaşılan komutları, komut gruplarını ve menüleri kullanın.
 Komutlar genellikle bağlama göre gösterildiği için mevcut paylaşılan menülerin ve komut gruplarının kullanılması, komut yapısının bağlam değişiklikleri arasında görece kararlı kalmasını sağlar. Paylaşılan komutları yeniden kullanarak ve yeni komutları ilgili paylaşılan komutlara yakın bir şekilde yerleştirmek de IDE karmaşıklığını azaltır ve daha kullanıcı dostu bir deneyim oluşturur. Yeni bir komutun tanımlanmış olması gerekirse mevcut paylaşılan bir komut grubuna yer düzenlemeyi deneyin. Yeni bir grup tanımlanmalıdır, yeni bir üst düzey menü oluşturmadan önce ilgili bir komut grubunun yakınında mevcut paylaşılan bir menüye yer açın.

##### <a name="do-not-create-icons-for-every-command"></a>Her komut için simge oluşturma.
 Komut simgesi oluşturmadan önce dikkatli bir şekilde düşünebilirsiniz. Simgeler yalnızca şu komutlar için oluşturulacak:

- varsayılan araç çubuğunda görünür.

- kullanıcılar tarafından Özelleştir... iletişim kutusu aracılığıyla bir araç **çubuğuna eklenme olasılığı** vardır.

- başka bir Microsoft ürününde aynı eylemle ilişkili bir simgeye sahip.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Klavye kısayollarının ekini sınırlama
 Kullanıcıların büyük çoğunluğu, tüm kullanılabilir kısayolların çok küçük bir bölümünü çalıştırdı. Emin değilken özelliğinizi bir klavye kısayolu ile bağlamayın. Yeni kısayollar eklemeden önce kullanıcı deneyimi takımıyla birlikte çalışma.

##### <a name="give-commands-a-default-menu-placement"></a>Komutlara varsayılan menü yerleşimi verme.
 Komutlarınızı başkaları tarafından özelleştirecek ve uygun şekilde tasarlaycaz. Gizli komut diye bir şey yoktur. Tüm Visual Studio komutları **Araçlar >** Özelleştir iletişim kutusunda, Komut Penceresi, otomatik tamamlama, Araçlar > Seçenekleri **> Klavye** iletişim kutusunda ve Geliştirme Araçları Ortamı'na (DTE) görünür. Komutlarınızı kullanıcıların kolayca bulmaları için .ctc dosyanıza bir ad ve araç ipucu veriniz.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Eklenmiş araç çubuğunda paylaşılan komutları yineleme.
 Komutları kullanıcının odağının yakınına yakın bir yere yer yapmak yararlıdır. Bunu yapmak için araç pencerenizin veya belge düzenleyicinizin üst kısmında ekli bir araç çubuğu oluşturabilirsiniz. Araç çubuğuna yerleştirilen komutlar, pencere içindeki içerik bölgeye özgü olması gerekir. Paylaşılan komutları bu araç çubukları üzerinde çoğaltamazsınız. Örneğin, hiçbir zaman ekli araç çubuğunun içine bir "Kaydet" simgesi ekleme.

### <a name="content-and-command-visibility"></a>İçerik ve komut görünürlüğü
 Komutlar şu kapsamlarda bulunur: **Ortam,** **Hiyerarşi** ve **Belge.** Komut yerleştirmeye güveni olmak için her kapsamı bilmek.

 Ortam kapsamındaki **komutlar** birincil bağlamı sağlar ve birden çok bağlam arasında paylaşılır. Belgelerin ve araç pencerelerinin görünürlüğünü veya düzenlemesini değiştirebilirler. Ortam kapsamındaki komutlar arasında **New Project**, Bağlan **To Server**, Attach **Process**, **Cut**, **Copy**, **Paste**, **Find**, **Options**, **Customize**, **New Window** ve View Help komutları **yer aldı.**

 Hiyerarşi kapsamındaki **komutlar,** Project , Team ve Data gibi **Visual Studio** **hiyerarşileri** **yönetir.** Projenin alt metniyle ilgilidir; **örneğin,** Hata **Ayıklama,** Derleme, **Test** Etme, **Mimari** veya Analiz **Etme.** Hiyerarşi kapsamındaki komutlar arasında Yeni Öğe **Ekle,** **Yeni** Sorgu , **Project Ayarlar,** Yeni Veri Kaynağı **Ekle,** Performans Başlatma Sihirbazı **ve** Yeni Diyagram **yer alır.**

 Belge **kapsamındaki komutlar,** kod, tasarım veya iş öğesi sorgusu (WIQ) gibi bir belgenin içeriğine göre hareket ederler. Ayrıca, bir araç penceresinin görünümüne göre hareket veya bu araç penceresine özgü de olabilir. Belge kapsamı komutları ayrıca hiyerarşiye özgü dosya nesneleri üzerinde de hareket eder. Örneğin, Dosyadan kaldır **Project.** Belge kapsamındaki komutlar arasında Yeniden Düzenleme ve **yeniden düzenleme >,** İş Öğesinin Kopyasını **Oluştur,** Tüm Öğesini **Genişlet,** Tümleri Daralt **ve** Kullanıcı Görevi **Oluştur'lar yer alan komutlar vardır.**

### <a name="command-placement-decisions"></a>Komut yerleştirme kararları
 Komut oluşturmaya karar verdiktan sonra, bunun uygun yerleşimini ve klavye kısayolu oluşturulıp oluşturula olmadığını belirlemeniz gerekir. Komutun nereye kurulacaklarını kurmak için bu karar yolunu izleyin:

 ![Komut yerleştirme karar grafiği](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Visual Studio'de komut yerleştirme için karar Visual Studio**

### <a name="command-placement-in-menus"></a>Menülerde komut yerleştirme

#### <a name="main-menu-bar"></a>Ana menü çubuğu
 Ana menü çubuğu, kullanıcı arabirimine katkıda bulunan bağlama özgü menü paketlerinin komutları için standart konum olabilir. Ana menü çubuğu, ortamın hangi komutların görünür olduğunu kontrol etmek için kullandığı diğer komut yapılarından farklıdır. Diğer tüm komut çubukları, bir menüye veya araç çubuğuna yerleştirilseler de bağlam dışında olan komutları devre dışı bırakmalarıdır.

 Ortam, ana menü çubuğunda yerleşik olarak yer alan ve IDE'nin tamamında ve birden çok görev etki alanı arasında ortak olan bir komut kümesi tanımlar. Bu komutlar ortama hangi VSPackage'ların yüklendiğinden bağımsız olarak her zaman görünür. VSPackage'lar bu komut dizisini genişletese de, her üründen gelen komut kümesi ve komutlarının yerleştirilmesi her ekibin sorumluluğundadır.

 Ana men Visual Studio aşağıdaki menü kategorilerine ayrılır:

##### <a name="core-menus"></a>Çekirdek menüler

- Dosya

- Düzenle

- Görüntüle

- Araçlar

- Pencere

- Help

##### <a name="project-specific-menus"></a>Project menüler

- Project

- Derleme

- Hata Ayıklama

##### <a name="context-specific-menus"></a>Bağlama özgü menüler

- Takım

- Veriler

- Test etme

- Mimari

- Analiz

##### <a name="document-specific-menus"></a>Belgeye özgü menüler

- Biçimlendir

- Tablo

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Ana menüleri tasarlarken şu kurallara uyun:

- Verilen bağlamda en üst düzey 25 öğeyi aşma

- Menülerin yüksekliği hiçbir zaman 600 pikseli aşmamalı.

- Ultimate SKU'su ve Genel Profil gibi birden çok bağlamda bir ana menüyü değerlendirin.

- Flyout menüleri kabul edilebilir.

- Flyout menüleri en az üç öğe ve en fazla yedi öğe içermeli.

- Açılır menüler yalnızca bir düzey derine Visual Studio menü öğelerinin basamaklı alt menüleri vardır, ancak bu düzen teşvik değildir.

- En fazla altı ayırıcı kullanın. Gruplamalar aşağıdaki çizime bağlı kalmalı:

     ![Ana menü gruplama yönergeleri](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

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

- **Kısayol tuşları** çoğunlukla Denetim (Ctrl) ve İşlev (Fn) anahtar dizilerini kullanır. Bunlar daha ileri düzey kullanıcılar için tasarlanmıştır ve üretkenlikte yardımcı olur. Bunlar yalnızca en sık kullanılan komutlara atanır ve ana menü atlanırken hızlı erişime izin verir. Kısayol anahtarlarının ezberleneme amacı vardır ve bu nedenle profil şemasıyla tutarlı bir şekilde atanmaları gerekir. Kısayol anahtarı düzenleri profilden profile farklılık gösterebilir. Kullanıcı, Araçlar ve Seçenekler ve Klavye **> kısayol tuşlarını > özelleştirilebilir.**

### <a name="assigning-access-keys"></a>Erişim anahtarları atama
 Erişim anahtarları Alt artı alfasayısal anahtarlardan oluşur. Özel durum olmadan her menü öğesinin erişim anahtarını attayabilirsiniz. Erişim Windows atamak için genel kuralları ve yönergeleri izleyin. Örneğin, Yeni Dosya > **için erişim** anahtarı her zaman **Alt, F, N olabilir.**

 Ayırt etmek zor olduğu için 'i' (büyük veya küçük harf) veya küçük harf 'l' gibi tek piksel genişlikli harfler kullanmayın ve karakterleri alt karakterlerle (g, j, p, q ve y) kullanmaktan kaçının.

 Mümkün olduğunda yinelenen anahtarlar kullanmaktan kaçının. Yinelemenin kaçınılmaz olduğu durumlarda, menü sistemi çakışmaları anahtarı kullanan tüm komutlar üzerinden sızarak işlemeye devam ediyor. Örneğin, Dosya menüsünün altındaki "N" erişim anahtarını çoğaltan varsayımsal bir "Sayı" komutu için **Alt, F, N** yeni bir dosya oluşturabilir ve **Alt, F, N, N** "Sayı" komutunu gerçekleştirecek.

### <a name="assigning-shortcut-keys"></a>Kısayol tuşları atama
 Yeni kısayol tuşları atamaktan kaçının çünkü bunlar her komut için gerekli değildir ve aşırı kullanım varsa sistemi (ve kullanıcı belleğini) vergiler. Veri kümesinden Müşteri Deneyimini Geliştirme Programı (CEIP), kullanıcıların Visual Studio kısayolların yalnızca küçük bir alt kümesini kullanabileceğini gösterir.

 Kısayolları tanımlarken şu kuralları izleyin:

- **Denetim (Ctrl) ve İşlev (Fn) anahtar dizilerini kullanın.**

- **Sık kullanılan kısayolları koruma.** En popüler kısayolları koruma.

- **Düzenleyici kısayollarını kolayca yazabilirsiniz.** Geliştiricilerin kod yazarken en çok ihtiyaçları olan komutlara türü kolay kısayollar bağlayın. Örneğin, **Edit.InvokeSmartTag'ın** Alt+Shift+F10 değil Ctrl+/ gibi bir hızlı kısayol tuşu olması gerekir.

- **Tutarlı bir şekilde thema kısayollar elde edebilirsiniz.**

- **Hangi Windows anahtarlarını belirlemek için aşağıdaki yönergeleri izleyin.** Belgenin tamamı için geçerli olan komutlar gibi büyük ölçekli etkileri olan komutlar için Ctrl tuş birleşimlerini kullanın. Standart kısayol tuşunun eylemlerini genişleten veya tamamlayan komutlar için Shift tuş birleşimlerini kullanın. Ctrl+Alt birleşimleri kullanma.

- **Fazlalık kısayolları kaldırın.** Eski bir özelliğiniz varsa, erişim anahtarı aynı komuta hızlı erişim sağlarsa, aşırı seyrek (CEIP verilerinden 10 kat daha az) veya orta seyreklik (CEIP verilerinden 100'den az) ile kullanılan kısayolları kaldırmayı göz önünde bulundurabilirsiniz. Örneğin: Alt, H, C Yardım/İçerik'i açar.

  Kısayol kullanılabilirliğini denetlemenin basit bir yolu yok. Kısayol eklemek için şu adımları izleyin:

1. Kullanıcılarınızı grup [Visual Studio 2013 benzer](http://visualstudioshortcuts.com/2013/) komutlar olup olmadığını belirlemek için bu kısayollar listesini kontrol edin.

2. Tools **> Options > > >'a gidin ve** kısayolunu test edin. "Aşağıdaki ek klavye eşleme düzenini uygula" altında listelenen her klavye eşleme düzenini kontrol edin. Genel, C#, VB ve C++ profillerini kontrol edin çünkü bunlar benzersiz kısayolları paylaşır. Kısayol, bu yerlerin hiçbirsinde eşlenmemişse kullanılabilir.
