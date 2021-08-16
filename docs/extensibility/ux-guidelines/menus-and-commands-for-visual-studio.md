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
ms.openlocfilehash: f137ba0db635587824ef0b574e090b8ba2b806d37855cd23a12978675ee8a81a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305119"
---
# <a name="menus-and-commands-for-visual-studio"></a>Visual Studio İçin Menüler ve Komutlar
## <a name="command-usage"></a>Komut kullanımı

### <a name="overview"></a>Genel Bakış
 Birçok Microsoft Office üründen oluşan bir paket olan Visual Studio'den farklı olarak, her biri komut kümelerinin genel IDE'ye Visual Studio içerir. IDE, kullanıcıya kullanılabilir olan işlevleri bağlama göre filtreleerek binlerce komutun karmaşıklığını yönetir.

 Kullanıcının bağlamı değişerek tasarım penceresinden kod düzenleme penceresine geçme gibi yeni bağlamla ilgili olmayan işlevler kaybolur. Aynı zamanda yeni işlevler Özellikler ve Araç Kutusu seçenekleri gibi ilgili dinamik bilgilerle birlikte ortaya çıkar. Kullanıcı kullanılabilir komut kümesi değiştirme fark etmez. Kullanıcının dikkati dağılırsa veya komutlar görüntüden kaybolursa kullanıcı arabirimi tasarımının ayarlanması gerekir. Kullanıcının geçerli bağlamı her zaman bir veya daha fazla şekilde (örneğin, IDE başlık çubuğunda, Özellikler penceresi veya Özellik Sayfaları iletişim kutusunda) belirtilmiştir.

 Komut çubukları, kullanıcı arabiriminde esneklik sağlar. Visual Studio ortamının yapısına Visual Studio tek komut yapıları ana menü ve ana komut çubuğudur. Bunlar hem özelleştirilebilir hem de hatta gizlenir. Uygulamanın durumuna bağlı olarak diğer komut çubukları görünür ve kaybolur. Araç pencereleri ve belge düzenleyicileri, pencere kenarlarının içine eklenmiş araç çubukları da içerebilir.

#### <a name="basic-guidelines"></a>Temel yönergeler

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Mümkün olduğunda mevcut paylaşılan komutları, komut gruplarını ve menüleri kullanın.
 Komutlar genellikle bağlama göre gösterildiği için mevcut paylaşılan menülerin ve komut gruplarının kullanılması, komut yapısının bağlam değişiklikleri arasında görece kararlı kalmasını sağlar. Paylaşılan komutları yeniden kullanarak ve yeni komutları ilgili paylaşılan komutlara yakın bir şekilde yerleştirmek de IDE karmaşıklığını azaltır ve daha kullanıcı dostu bir deneyim oluşturur. Yeni bir komutun tanımlanmış olması gerekirse, bunu mevcut bir paylaşılan komut grubuna yer anlamaya çalışabilirsiniz. Yeni bir grup tanımlanmalıdır, yeni bir üst düzey menü oluşturmadan önce ilgili bir komut grubunun yakınında mevcut paylaşılan bir menüye yer açın.

##### <a name="do-not-create-icons-for-every-command"></a>Her komut için simge oluşturma.
 Komut simgesi oluşturmadan önce dikkatli bir şekilde düşünebilirsiniz. Simgeler yalnızca şu komutlar için oluşturulacak:

- varsayılan araç çubuğunda görünür.

- kullanıcılar tarafından Özelleştir... iletişim kutusu aracılığıyla bir araç **çubuğuna eklenme olasılığı** vardır.

- başka bir Microsoft ürününde aynı eylemle ilişkili bir simgeye sahip.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Klavye kısayollarının ekini sınırlama
 Kullanıcıların büyük çoğunluğu, tüm kullanılabilir kısayolların çok küçük bir bölümünü çalıştırdı. Emin değilken özelliğinizi bir klavye kısayolu ile bağlamayın. Yeni kısayollar eklemeden önce kullanıcı deneyimi takımıyla birlikte çalışma.

##### <a name="give-commands-a-default-menu-placement"></a>Komutlara varsayılan menü yerleşimi verme.
 Komutlarınızı başkaları tarafından özelleştirecek ve uygun şekilde tasarlaycaz. Gizli komut diye bir şey yoktur. Tüm Visual Studio komutları **Araçlar >** Özelleştir iletişim kutusunda, Komut Penceresi, otomatik tamamlama, Araçlar > Seçenekler **> Klavye** iletişim kutusunda ve Geliştirme Araçları Ortamı'na (DTE) görünür. Komutlarınızı kullanıcıların kolayca bulmaları için .ctc dosyanıza bir ad ve araç ipucu veriniz.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Eklenmiş araç çubuğunda paylaşılan komutları yineleme.
 Komutları kullanıcının odağının yakınına yakın bir yere yer yapmak yararlıdır. Bunu yapmak için araç pencerenizin veya belge düzenleyicinizin üst kısmında ekli bir araç çubuğu oluşturabilirsiniz. Araç çubuğuna yerleştirilen komutlar, pencere içindeki içerik bölgeye özgü olması gerekir. Paylaşılan komutları bu araç çubukları üzerinde çoğaltamazsınız. Örneğin, hiçbir zaman ekli araç çubuğunun içine bir "Kaydet" simgesi ekleme.

### <a name="content-and-command-visibility"></a>İçerik ve komut görünürlüğü
 Komutlar şu kapsamlarda bulunur: **Ortam,** **Hiyerarşi** ve **Belge.** Komut yerleştirmeye güveni olmak için her kapsamı bilmek.

 Ortam kapsamındaki **komutlar** birincil bağlamı sağlar ve birden çok bağlam arasında paylaşılır. Belgelerin ve araç pencerelerinin görünürlüğünü veya düzenlemesini değiştirebilirler. Ortam kapsamındaki komutlar arasında **New Project**, Bağlan **To Server**, Attach **Process**, **Cut**, **Copy**, **Paste**, Find , **Options**, **Customize**, **New Window** ve View Help komutları **yer aldı.** 

 Hiyerarşi kapsamındaki **komutlar,** Visual Studio **,** Team ve Data Project **hiyerarşileri** **yönetir.** Projenin alt metniyle ilgilidir; **örneğin,** Hata **Ayıklama,** Derleme, **Test** Etme, **Mimari** veya Analiz **Etme.** Hiyerarşi kapsamındaki komutlar arasında Yeni Öğe **Ekle,** **Yeni** Sorgu , **Project Ayarlar, Yeni** Veri Kaynağı **Ekle,** **Performans** Başlatma Sihirbazı ve Yeni Diyagram yer **alır.**

 Belge **kapsamındaki komutlar,** kod, tasarım veya iş öğesi sorgusu (WIQ) gibi bir belgenin içeriğine göre hareket ederler. Ayrıca, bir araç penceresinin görünümüne göre hareket veya bu araç penceresine özgü de olabilir. Belge kapsamı komutları ayrıca hiyerarşiye özgü dosya nesneleri üzerinde de hareket eder. Örneğin, **Dosyadan kaldır Project.** Belge kapsamındaki komutlar arasında Yeniden Düzenleme ve **Yeniden >,** **İş** Öğesinin Kopyasını **Oluştur,** Tüm Öğesini **Genişlet,** Tümleri Daralt ve Kullanıcı Görevi **Oluştur'lar yer alan komutlar vardır.**

### <a name="command-placement-decisions"></a>Komut yerleştirme kararları
 Komut oluşturmaya karar verdiktan sonra, bunun uygun yerleşimini ve klavye kısayolu oluşturulıp oluşturula olmadığını belirlemeniz gerekir. Komutun nereye kurulacaklarını kurmak için bu karar yolunu izleyin:

 ![Komut yerleştirme karar grafiği](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Visual Studio'da komut yerleştirme için karar Visual Studio**

### <a name="command-placement-in-menus"></a>Menülerde komut yerleştirme

#### <a name="main-menu-bar"></a>Ana menü çubuğu
 Ana menü çubuğu, kullanıcı arabirimine katkıda bulunan bağlama özgü menü paketlerinin komutları için standart konum olabilir. Ana menü çubuğu, ortamın hangi komutların görünür olduğunu kontrol etmek için kullandığı diğer komut yapılarından farklıdır. Diğer tüm komut çubukları, bir menüye veya araç çubuğuna yerleştirilseler de bağlam dışında olan komutları devre dışı bırakmalarıdır.

 Ortam, ana menü çubuğunda yerleşik olarak yer alan ve IDE'nin tamamında ve birden çok görev etki alanı arasında ortak olan bir komut kümesi tanımlar. Bu komutlar ortama hangi VSPackage'ların yüklendiğinden bağımsız olarak her zaman görünür. VSPackage'lar bu komut dizisini genişletese de, her üründen gelen komut kümesi ve komutlarının yerleştirilmesi her ekibin sorumluluğundadır.

 Ana menü Visual Studio aşağıdaki menü kategorilerine ayrılır:

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

- Şekildeki her bir gruplamanın olması gerekli değildir, ancak ek gruplamalar eklemek kısıtlanmıştır.

- Her gruplamada iki ile yedi menü öğesi arasında bir öğe olması gerekir.

#### <a name="main-menu-ordering"></a>Ana menü sıralama
 Yeni bir üst düzey öğe eklemeden önce, komutu mevcut bir üst düzey menüye yerleştirmeyi göz önünde bulundurabilirsiniz. Yeni bir üst düzey menü eklerken, menüyü doğru konuma eklemeyin. Menenin projeye, bağlama veya belgeye özgü olup olmadığını belirleyin. Üst düzey menenin adını kısa ve yalnızca bir sözcük kullanın.

 Çekirdek menüler, komutların geri kalanını rezervasyona tabi bulundurabilir. Dosya, Düzenle ve Görünüm her zaman solda, Araçlar, Pencere ve Yardım her zaman sağ tarafta yer aladır.

#### <a name="context-menus"></a>Bağlam menüleri
 Bağlam menülerine çok fazla işlev yerleştirmek, öğrenmesi zor bir arabirime neden olur. Tüm önemli işlevlerin ana menü çubuğundan kullanılabilir olması gerekir. Yinelenen komutları önlemek için komutların yerleşimi mevcut komutlarla uzlaştırılmalıdır. Bağlam menüleri için kabuk, bağlam menüsünün çözüme, proje düğümüne veya proje öğesine bağlı olarak dahil edilecek standart menü gruplarını tanımlar.

 Bağlam menülerini tasarlarken ana menüyle aynı kurallara ve ayrıca:

- 25 üst düzey menü öğesini aşmayın.

- Flyout menüleri kabul edilebilir ancak bir düzey derini aşması gerekir; hiçbir zaman basamaklı çıkışları kullanmaz.

- En fazla altı ayırıcı kullanın.

### <a name="command-placement-in-toolbars"></a>Araç çubuklarında komut yerleştirme

#### <a name="general-toolbars"></a>Genel araç çubukları
 Araç çubuklarını tasarlar ve tasarlarken şu standartları izleyin:

- Düğme başına birden fazla fiil kullanma. Tek düğme = bir eylem.

- Simgeyle birlikte metni yalnızca etiketle pekiştirme gerekirse kullanın.

- Bir oturumda birden çok kez değiştirecek özellikler için özel olarak bir birleşik giriş kutusu kullanın. Aksi takdirde, özelliğini başka bir yerde ortaya çıkarabilirsiniz.

- Birleşik giriş kutusunun genişliği, kutu içindeki en uzun öğenin genişliğine + %30'a eşit olur. Örneğin, en uzun öğe 200 piksel ise birleşik giriş kutusu 260 piksel genişliğinde olmalıdır.

- Ayırıcıların kullanımını sınırla. Açılan liste şeklinin görsel ayırıcı olarak davranması nedeniyle, açılan liste yanında ayırıcının kullanımı bir anti-desendir.

- Simge grupları üç ile altı arasında simge içermeli.

- Niteleyiciler birden çok yararlı komutla sonuçlanabiliyorsa, son ayarı depolar bir bölme düğmesi kullanın:

     ![Bölme düğmeleri Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Bölme düğmesi örneği. Sol tarafta yer alan altı komut bunun yerine tek bir düğmeye sığmanıza neden olabilir.**

#### <a name="product-specific-toolbars"></a>Ürüne özgü araç çubukları
 Her ürün, sık kullanılan ve önemli komutları içeren varsayılan bir araç çubuğu sağlar ve ürün yüklendikten sonra ilk kez Visual Studio her ürünün varsayılan araç çubuğu görüntüleyebilirsiniz.

 Ürünler ayrıca IDE tarafından sağlanan paylaşılan komut gruplarında ve menülerde de kullanılabilir. Her paylaşılan komut grubu, ilgili komutları kullanıcı için anlamlı bir şekilde düzenlemek için paylaşılan bir menüye yerleştirilir. Karmaşıklığı azaltmak için bu paylaşılan komut yapısından yararlanılır.

#### <a name="global-toolbars"></a>Genel araç çubukları
 Genel araç çubuklarının kutudan hemen bir satıra sığacak şekilde olması gerekir. Yeni bir genel araç çubuğu oluştururken, bu araç çubuğu türü için yönergeleri izleyin.

 **Genel araç çubuğu yönergeleri:**

- Her araç çubuğunun ortak denetimlerde (kavramaper, taşma) 24 pikseli vardır.

- Her araç çubuğu düğmesi doldurma dahil olmak üzere 22 piksel genişliğindedir. Simgeyi bölme düğmesi yapmak 11 piksel daha genişlik ekler.

- Araç çubukları arasında komutların çoğaltılmasına izin verilir.

  **Belirli bir dosya türü etkin** olduğunda belgeye özgü araç çubukları görünür ve farklı bir dosya türü etkin olduğunda kaybolur.

- Belgeye özgü araç çubuklarda 12'den fazla düğme olmayabilir.

- Araç çubuğunun toplam genişliği 300 pikseli aşmaz.

- Her dosya türünün bir ekli araç çubuğu veya belgeye özgü bir genel araç çubuğu olabilir, ancak her ikisi birden olmaz.

  **Belirli bir bağlam ayar olduğunda** bağlama özgü araç çubukları görünür ve uzun süreler boyunca etkin kalma eğilimindedir.

- Bağlama özgü tüm araç çubukları için düğme sınırı 18'tir.

- Kullanıcıların çoğu bağlam etkin olduğunda bu araç çubuğunun komutlarını tutarlı bir şekilde kullanmazsa, bu araç çubuğunu bir bağlamla ilişkilendirmeyin.

- Bağlamdan çıkarken araç çubuğunun kaybolduğundan emin olmak. Bu araç çubuklarının hiçbiri başlangıçta görünmez.

  **Bağlam eklemeden araç çubukları hiçbir** zaman otomatik olarak görünmez. Bunlar yalnızca kullanıcı etkinleştir olduğunda gösterir. En fazla genişliği 200 pikselin altında tut.

### <a name="general-organization-and-shell-defined-groups"></a>Genel kuruluş ve kabuk tanımlı gruplar
 Mevcut paylaşılan komutları, komut gruplarını ve menüleri kullanın. Yeni bir komutun tanımlanmış olması gerekirse mevcut paylaşılan bir komut grubuna yer düzenlemeyi deneyin. Yeni bir grup tanımlanmalıdır, yeni bir üst düzey menü oluşturmadan önce bunu ilgili bir komut grubunun yakın bir paylaşılan menüsüne eklemeye deneyin. Bu, IDE'de tutarlı komut yerleşimi sağlarken komut karmaşıklığını azaltır.

 Genellikle **tasarımcı** stili belge pencereleri bağlamında gösterilen paylaşılan Biçim menüsü aşağıdaki görüntüde gösterilmiştir:

 ![Visual Studio Callouts ile Biçim menüsü](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Visual Studio'de menü grupları**

### <a name="reducing-and-reusing-commands"></a>Komutları azaltma ve yeniden kullanın
 Komutlar genellikle kullanıcının herhangi bir zamanda gördüğü komut sayısını azaltmak için bağlama göre gösterilir. Ancak, komut yapısının bağlam değişiklikleri arasında görece kararlı kalmasını sağlamak için mevcut paylaşılan menüleri ve komut gruplarını da yeniden kullanmalıdır.

 Paylaşılan komutları yeniden kullanarak ve yeni komutları ilgili paylaşılan komutlara yakın bir şekilde yerleştirmek, IDE karmaşıklığını azaltır ve daha kullanıcı dostu bir deneyim oluşturur.

## <a name="naming-commands"></a>Adlandırma komutları

### <a name="naming-conventions"></a>Adlandırma kuralları
 Tutarlı komut adlandırması, kullanıcıların komut satırı veya klavye kısayolunu kullanarak komutları bulup yürütmeleri için kritik öneme sahiptir. Komut adları, kullanıcının bir araç çubuğunda veya basamaklı ya da bağlam menüsünde görüntülendiğinde komutun hangi amaca hizmet ettiğine de yardımcı olur.

#### <a name="when-naming-commands"></a>Komutları adlandırarak:

- Kolayca yerelleştirilebilir olacak şekilde metin oluşturun. Metni yerelleştirme hakkında daha fazla bilgi için [bkz. Yerelleştirme en iyi yöntemleri.](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)

- Kısa ve öz bir şekilde ifade etmek. Komutlar en fazla üç sözcük kullanmalı.

- Başlık-büyük/büyük harf kullanımını kullanın: her sözcüğün ilk harfi büyük harfe büyük yazarak yaz yazarak. Uygulama içinde metin biçimlendirme hakkında daha fazla Visual Studio bkz. [Metin stili.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

- Komutun nereye yerleştiril olacağını göz önünde bulundurabilirsiniz. Üst düzey bir menüde mi yoksa açılır menüde mi? Örneğin, hizalama komutlarını bir flyout içinde gruplamada, üst düzey komut "Hizala" ve flyout komutları "Left", "Right," "Center" "Justify" ve sosyete şeklindedir. Bu, "Sola Hizala" veya "Sağa Hizala" flyout komutlarını ifade etmek için yedekli olabilir.

     ![Visual Studio Biçim menüsü](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Komutları olan simgeleri kullanma
 Komutlarla simge eşleştirmeyi kullanmaya devam edin. Benzersiz bir görüntüyü bir komutla irdelemek kullanıcının bu komutu tanımlama becerisini daha fazla olsa da, fazla kullanım nedeniyle görsel dağınıklık ve verimsellik oluşur. Aşağıdaki kurallar, komut simgesinin oluşturulıp oluşturul olmadığına karar verirken yardımcı olur.

#### <a name="use-an-icon-with-a-command-only-if"></a>Yalnızca şu komutlarla bir simge kullanın:

- Aynı komutta, microsoft uygulamalarının biri gibi öne çıkan başka bir Microsoft ürününde ilişkili bir Microsoft Office vardır.

- Komut varsayılan araç çubuğuna yerleştirilir.

- Komut, kullanıcıların **"Özelleştir..."** iletişim kutusunu kullanarak bir araç çubuğuna ekleme olasılığı olan özel bir komuttır.

## <a name="access-and-shortcut-keys"></a>Erişim ve kısayol tuşları

### <a name="overview"></a>Genel Bakış
 İki tür klavye anahtarı ataması vardır:

- **Erişim tuşları** (hızlandırıcılar olarak da bilinir), komut menüleri aracılığıyla ve iletişim kutusu kullanıcı arabiriminde her etikete klavye erişimi sağlar. Erişim anahtarları çoğunlukla erişilebilirlik amaçlıdır, tüm menülere atanır ve iletişim kutusu denetimlerinin çoğu ezberleme amaçlı değildir, yalnızca geçerli pencereyi etkiler ve yerelleştirilmiştir.

- **Kısayol tuşları** çoğunlukla Control (Ctrl) ve function (fn) anahtar dizilerini kullanır. Bunlar, gelişmiş kullanıcılar için daha fazla tasarlanırlar ve verimliliğine yardımcı olur. Bunlar yalnızca en sık kullanılan komutlara atanır ve ana menüyü atlayarak hızlı erişime izin verir. Kısayol tuşlarının yeniden başlatılması amaçlanmıştır ve bu nedenle, profil düzeni ile tutarlı bir şekilde atanması gerekir. Kısayol tuş düzenleri profilden profile farklılık gösterebilir. Kullanıcı, kısayol tuşlarını **araçlar > seçenekler > klavyeden** özelleştirebilir.

### <a name="assigning-access-keys"></a>Erişim anahtarları atanıyor
 Erişim tuşları alt ve alfasayısal anahtarlardan oluşur. Her menü öğesine özel durum olmadan bir erişim anahtarı atayın. erişim anahtarları atamaya yönelik Windows ve ortak kuralları izleyin. Örneğin, **> yeni dosya** için erişim anahtarı her zaman **alt, F, N** olmalıdır.

 ' I ' (büyük veya küçük harf) veya küçük harf ' l ' gibi tek pikselli harfler kullanmayın ve bunları ayırt etmek zor olacak şekilde harflerin (g, j, p, q ve y) karakterlerini kullanmaktan kaçının.

 Mümkün olduğunda yinelenen anahtarlar kullanmaktan kaçının. Tekrarların kaçınılmaz olduğu durumlarda, menü sistemi, anahtarı kullanan tüm komutlarda geçiş yaparak çakışmaları işler. Örnek olarak, "N" erişim anahtarını çoğaltan Dosya menüsünün altındaki kuramsal bir "numara" komutu için **alt, f, n** yeni bir dosya oluşturacak ve **alt, f, n, n** "Number" komutunu gerçekleştirecek.

### <a name="assigning-shortcut-keys"></a>Kısayol tuşları atama
 Yeni kısayol tuşları atamaktan kaçının, çünkü bunlar her komut için gerekli değildir ve fazla kullanılıyorsa sistemin (ve Kullanıcı belleğinin) vergisine dahil edilmez. Müşteri Deneyimini Geliştirme Programı (ceıp) verileri, Visual Studio kullanıcıların tümleşik kısayolların yalnızca küçük bir alt kümesini kullanacağını gösterir.

 Kısayolları tanımlarken bu kuralları izleyin:

- **Control (Ctrl) ve function (fn) anahtar dizilerini kullanın.**

- **Sık kullanılan kısayolları koru.** En popüler kısayolları koruyun.

- **Düzenleyici kısayollarının kolayca türünü kolaylaştırın.** Geliştiricilerin daha fazla kod yazarken ihtiyacı olan komutlara kolay tür kısayolları bağlayın. Örneğin, **Edit. InvokeSmartTag** ' ın CTRL +/gibi bir hızlı kısayol tuşuna sahip olması gerekir ve alt + SHIFT + F10 tuşlarına basın.

- **Tutarlı temalı kısayollar için çaba harcar.**

- **hangi değiştirici anahtarların çalıştırılacağını öğrenmek için Windows yönergeleri izleyin.** Tüm belgeye uygulanan komutlar gibi büyük ölçekli etkileri olan komutlar için CTRL tuş bileşimlerini kullanın. Standart kısayol tuşu eylemlerini genişleten veya tamamlayan komutlar için SHIFT tuş bileşimlerini kullanın. Ctrl + Alt kombinasyonlarını kullanmayın.

- **Gereksiz kısayolları kaldırın.** Eski bir özellik varsa, bir erişim anahtarı aynı komuta hızlı erişim sağlıyorsa, çok seyrek erişimli (CEIP verilerinden 10 ' dan az) veya (CEIP verilerinden en az 100 kez) kullanılan kısayolları kaldırmayı göz önünde bulundurun. Örneğin: alt, H, C, yardım/Içerik açar.

  Kısayol kullanılabilirliğini kontrol etmenin basit bir yolu yoktur. Bir kısayol eklemek istiyorsanız aşağıdaki adımları izleyin:

1. kendi ile gruplamak için benzer komutların olup olmadığını öğrenmek için [Visual Studio 2013 kısayollarının](http://visualstudioshortcuts.com/2013/) listesini denetleyin.

2. **Araçlar > seçenekler > ortam > klavye** ' ye gidin ve kısayolunuzu test edin. "Aşağıdaki ek klavye eşleme şemasını uygula" altında listelenen her bir klavye eşleme şemasını işaretleyin. Genel, C#, VB ve C++ profillerini, bu kişiler benzersiz kısayollar paylaştığından denetleyin. Kısayolunuz bu yerlerden herhangi birinde eşlenmişse kullanılabilir.
