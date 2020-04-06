---
title: Visual Studio için Menüler ve Komutlar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f22b7ac4377b600208c079b6af1eff7fc3cbfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698380"
---
# <a name="menus-and-commands-for-visual-studio"></a>Visual Studio İçin Menüler ve Komutlar
## <a name="command-usage"></a>Komut kullanımı

### <a name="overview"></a>Genel Bakış
 Birçok ayrı üründen oluşan bir paket olan Microsoft Office'in aksine Visual Studio, her birinin komuta setlerini küresel Visual Studio IDE'ye katkıda bulunan birçok ürün içerir. IDE, içeriğe göre kullanıcının kullanabileceği işlevselliği filtreleyerek binlerce komutun karmaşıklığını yönetir.

 Bir kullanıcının bağlamı değiştiğinde (örneğin, tasarım penceresinden kod düzenleme penceresine geçiş yapmak gibi) yeni bağlamla ilgisi olmayan işlevkaybolur. Aynı zamanda, özellikler ve araç kutusu seçenekleri gibi ilgili dinamik bilgilerle birlikte yeni işlevsellik yüzeyler. Kullanıcı, kullanılabilir komut kümesinin değiş tokuşuna dikkat etmemelidir. Kullanıcının dikkati dağılıyorsa veya görünen veya kaybolan komutlar yüzünden kafası karışıyorsa, Kullanıcı Arabirimi tasarımının ayarlanması gerekir. Kullanıcının geçerli bağlamı her zaman IDE başlık çubuğu, Özellikler penceresi veya Özellik Sayfaları iletişim kutusu gibi bir veya daha fazla şekilde gösterilir.

 Komut çubukları UI'de esneklik sağlar. Visual Studio ortamına bağlı tek komut yapıları ana menü ve hem özelleştirilebilir hem de gizli ana komut çubuğudur. Diğer komut çubukları, uygulamanın durumuna bağlı olarak görünür ve kaybolur. Araç pencereleri ve belge düzenleyicileri pencere kenarlarında gömülü araç çubukları da içerebilir.

#### <a name="basic-guidelines"></a>Temel yönergeler

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Varolan paylaşılan komutları, komut gruplarını ve menüleri mümkün olduğunca kullanın.
 Komutlar genellikle içeriğe göre gösterildiğinden, varolan paylaşılan menülerin ve komut gruplarının kullanımı, komut yapısının bağlamdaki değişiklikler arasında nispeten kararlı kalmasını sağlar. Paylaşılan komutları yeniden kullanmak ve ilgili paylaşılan komutlara yakın yeni komutlar yerleştirmek de IDE karmaşıklığını azaltır ve daha kullanıcı dostu bir deneyim oluşturur. Yeni bir komutun tanımlanması gerekiyorsa, bu komutu varolan bir paylaşılan komut grubuna yerleştirmeyi deneyin. Yeni bir grubun tanımlanması gerekiyorsa, yeni bir üst düzey menü oluşturmadan önce bu grubun ilgili komut grubuna yakın varolan paylaşılan bir menüye yerleştirin.

##### <a name="do-not-create-icons-for-every-command"></a>Her komut için simgeler oluşturmayın.
 Bir komut simgesi oluşturmadan önce dikkatlice düşünün. Simgeler yalnızca şu komutlar için oluşturulmalıdır:

- varsayılan araç çubuğunda görünür.

- **özelleştir...** iletişim kutusu aracılığıyla kullanıcılar tarafından bir araç çubuğuna eklenmesi olasıdır.

- başka bir Microsoft ürününde aynı eylemle ilişkili bir simgeye sahip.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Klavye kısayollarının eklenmesini sınırlama
 Kullanıcıların büyük çoğunluğu tüm mevcut kısayolların küçük bir kısmını kullanır. Şüpheye düştüğünüzde, özelliğinizi klavye kısayolu'na bağlamayın. Yeni kısayollar eklemeden önce kullanıcı deneyimi ekibinizle birlikte çalışın.

##### <a name="give-commands-a-default-menu-placement"></a>Komutlara varsayılan menü yerleşimi verin.
 Komutlarınızın başkaları tarafından özelleştirileceğini unutmayın ve bunları buna göre tasarlayın. Gizli komut diye bir şey yoktur. Tüm Visual Studio komutları **Araçlar > Özelleştir** iletişim kutusunda, Komut Penceresinde, otomatik tamamlamada, **Araçlar > Seçenekleri > Klavye** iletişim kutusunda ve Geliştirme Araçları Ortamında (DTE) görünür. Komutlarınıza .ctc dosyanızda bir ad ve araç ipucu verdiğinizden emin olun, böylece kullanıcılar bunları kolayca bulabilir.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Katıştırılmış bir araç çubuğunda paylaşılan komutları çoğaltmayın.
 Komutları kullanıcının odak alanına yakın bir yere yerleştirmek yararlıdır. Bunu yapmanın bir yolu, araç pencerenizin veya belge düzenleyicinizin üst kısmında gömülü bir araç çubuğu oluşturmaktır. Araç çubuğuna yerleştirilen komutlar pencereiçindeki içerik bölgesine özgü olmalıdır. Bu araç çubuklarındaki paylaşılan komutları çoğaltmayın. Örneğin, katıştırılmış bir araç çubuğunun içine asla bir "Kaydet" simgesi yerleştirmeyin.

### <a name="content-and-command-visibility"></a>İçerik ve komut görünürlüğü
 Komutlar aşağıdaki kapsamlarda vardır: **Çevre**, **Hiyerarşi**ve **Belge**. Komut yerleşimine güvene bilmek için her kapsamı bilin.

 **Çevre** kapsamındaki komutlar birincil bağlamı belirler ve birden çok bağlam arasında paylaşılır. Belgelerin ve araç pencerelerinin görünürlüğünü veya düzenini değiştirirler. Ortam kapsamındaki komutlar arasında **Yeni Proje,** **Sunucuya Bağlan**, **İşlem Ekle**, Kesme , **Kopyala**, **Yapıştır**, **Bul**, **Seçenekler**, **Özelleştir**, **Yeni Pencere**, ve **Yardım Görüntüleyin**. **Cut**

 **Hiyerarşi** kapsamındaki komutlar Visual Studio'da **Project,** **Team**ve **Data**gibi hiyerarşileri yönetir. Bunlar bir projenin alt bağlamı ile ilgilidir - örneğin, **Hata Ayıklama**, **Yapı**, **Test**, **Mimari**, veya **Analiz**. Hiyerarşi kapsamındaki komutlar arasında **Yeni Öğe Ekle**, Yeni **Sorgu**, **Proje Ayarları**, Yeni Veri Kaynağı **Ekle**, **Performans Sihirbazı Başlat**ve Yeni **Diyagram**vardır.

 **Belge** kapsamındaki komutlar, kod, tasarım veya iş öğesi sorgusu (WIQ) gibi bir belgenin içeriğine göre hareket eder. Ayrıca bir araç penceresinin görünümünde hareket ederler veya bu araç penceresine başka bir şekilde özeldirler. Belge kapsamı komutları, **Project'ten Kaldır**gibi hiyerarşiye özgü dosya nesnelerinde de hareket eder. Belge kapsamındaki komutlar arasında **Refactor > Rename**, **İş Öğesi Kopya oluşturma**, **Tümünü Genişlet**, **Tümünü Daralt**ve **Kullanıcı Görevi Oluştur**.

### <a name="command-placement-decisions"></a>Komuta yerleştirme kararları
 Bir komut oluşturmaya karar verdikten sonra, komutun uygun yerleşimini ve klavye kısayolu oluşturup oluşturmayacağını belirlemeniz gerekir. Komutun nereye yerleştirilen isap için bu karar yolunu izleyin:

 ![Komut yerleştirme karar çizelgesi](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Visual Studio'da komut yerleştirme için karar yolu**

### <a name="command-placement-in-menus"></a>Menülerde komut yerleşimi

#### <a name="main-menu-bar"></a>Ana menü çubuğu
 Ana menü çubuğu, UI'ye katkıda bulunan içeriğe özgü menü paketlerinin komutları için standart konum olmalıdır. Ana menü çubuğu, ortamın hangi komutların görünür olduğunu denetlemek için kullandığı diğer komut yapılarından farklıdır. Diğer tüm komut çubukları, ister bir menüye ister araç çubuğuna yerleştirilsinler, bağlam dışı komutları devre dışı kılabilir.

 Ortam, tüm IDE ve birden çok görev etki alanında ortak olan ana menü çubuğunda yerleşik bir komut kümesi tanımlar. Bu komutlar, vspackages ortama yüklenir ne olursa olsun her zaman görünür. VSPackages bu komut kümesini genişletebilse de, her üründen komut kümesi ve komutlarının yerleştirilmesi her takımın sorumluluğundadır.

 Visual Studio ana menüsünün yapısı aşağıdaki menü kategorilerine ayrılabilir:

##### <a name="core-menus"></a>Çekirdek menüler

- Dosya

- Düzenle

- Görüntüle

- Araçlar

- Pencere

- Yardım

##### <a name="project-specific-menus"></a>Projeye özel menüler

- Project

- Yapı

- Hata ayıklama

##### <a name="context-specific-menus"></a>İçerime özel menüler

- Takım

- Veriler

- Test etme

- Mimari

- Çözümleme

##### <a name="document-specific-menus"></a>Belgeye özel menüler

- Biçimlendir

- Tablo

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Ana menüler tasarlarken şu kurallara uyun:

- Belirli bir bağlamda 25 üst düzey öğeyi aşmayın

- Menülerin yüksekliği 600 pikseli geçmemelidir.

- Bir ana menüyü Ultimate SKU ve Genel Profil gibi birden çok bağlamda değerlendirin.

- Flyout menüleri kabul edilebilir.

- Flyout menüleri en az üç öğe ve en fazla yedi öğe içermelidir.

- Flyout menüleri sadece bir seviye derin gitmeli - bazı Visual Studio menü öğeleri basamaklı alt menüler var, ama bu desen teşvik edilmez.

- En fazla altı ayırıcı kullanın. Gruplandırmalar aşağıdaki çizime uymalıdır:

     ![Ana menü gruplandırma yönergeleri](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Şekilde her gruplandırmanın olması gerekli olmasa da, ek gruplandırmalar eklemek kısıtlanır.

- Her gruplandırmanın iki ila yedi menü öğesi olmalıdır.

#### <a name="main-menu-ordering"></a>Ana menü siparişi
 Yeni bir üst düzey öğe eklemeden önce, komutu varolan bir üst düzey menüye yerleştirmeyi düşünün. Yeni bir üst düzey menü eklerken, doğru konuma yerleştirdiğinizden emin olun. Menünün projeye, içeriğe veya belgeye özgü olup olmadığına karar verin. Üst düzey menünün adını kısa tutun ve yalnızca bir sözcük kullanın.

 Çekirdek menüler komutların geri kalanını bookend gerekir. Dosya, Edit ve Görünüm her zaman solda olmalı ve Araçlar, Pencere ve Yardım her zaman sağda olmalıdır.

#### <a name="context-menus"></a>Bağlam menüleri
 Bağlam menüleri içinde çok fazla işlevsellik yerleştirmek, öğrenmesi zor bir arabirim le sonuçlanır. Tüm büyük işlevler ana menü çubuğundan kullanılabilir olmalıdır. Yinelenen komutlardan kaçınmak için komutların yerleştirilmesi varolan komutlarla bağdaştırılmalıdır. İçerik menüleri için kabuk, bağlam menüsünün çözüm, proje düğümü veya proje öğesi için olup olmadığına bağlı olarak eklenmesi gereken standart menü gruplarını tanımlar.

 Bağlam menüleri tasarlarken, ana menüyle aynı kurallara uyun ve ek olarak:

- 25 üst düzey menü öğeyi geçmeyin.

- Flyout menüleri kabul edilebilir dir ancak bir seviye derinliğini aşmamalıdır - asla basamaklı uçuşlar kullanmayın.

- En fazla altı ayırıcı kullanın.

### <a name="command-placement-in-toolbars"></a>Araç çubuklarına komut yerleştirme

#### <a name="general-toolbars"></a>Genel araç çubukları
 Araç çubukları tasarlarken ve düzenlerken aşağıdaki standartlara uyun:

- Düğme başına birden fazla fiil kullanmayın. Bir düğme = bir eylem.

- Yalnızca etiketle güçlendirilmesi gerekiyorsa simgenin yanında metin kullanın.

- Tek oturumda birden çok kez değiştirilecek özellikler için yalnızca açılan kutu kullanın. Aksi takdirde, özelliği başka bir yerde ortaya çıkarır.

- Açılan kutunun genişliği, kutu içindeki en uzun öğenin genişliğine + %30'a eşit olmalıdır. Örneğin, en uzun öğe 200 piksel ise, açılan kutu 260 piksel genişliğinde olmalıdır.

- Ayırıcıların kullanımını sınırlandırın. Açılır bırakmanın yanında bir ayırıcının kullanımı bir anti-desendir, çünkü açılır bırakmanın şekli görsel bir ayırıcı görevi görür.

- Simge grupları üç ila altı simge içermelidir.

- Niteleyiciler birden çok kullanışlı komutla sonuçlanıyorsa, son ayarı depolayan bir bölme düğmesi kullanın:

     ![Visual Studio'da düğmeleri böl](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Bölünmüş düğme örneği. Soldaki altı komut bunun yerine tek bir düğmeye sığabilir.**

#### <a name="product-specific-toolbars"></a>Ürüne özel araç çubukları
 Her ürün, sık kullanılan ve önemli komutları içeren varsayılan bir araç çubuğu sağlayabilir ve her ürünün varsayılan araç çubuğu, ürün yüklendikten sonra Visual Studio başlatıldığında ilk kez görünmelidir.

 Ürünler ayrıca, IDE tarafından sağlanan paylaşılan komut gruplarından ve menülerden de yararlanmalıdır. Paylaşılan her komut grubu, ilgili komutları kullanıcı için anlamlı bir şekilde düzenlemek amacıyla paylaşılan bir menüye yerleştirilir. Karmaşıklığı azaltmak için bu paylaşılan komut yapısından yararlanmak önemlidir.

#### <a name="global-toolbars"></a>Genel araç çubukları
 Genel araç çubuklarının kutunun hemen dışında bir satıra sığması gerekir. Yeni bir genel araç çubuğu oluştururken, bu araç çubuğu türü için yönergeleri izleyin.

 **Genel araç çubuğu yönergeleri:**

- Her araç çubuğuortak denetimlerde 24 piksele (kavrayan, taşma) sahiptir.

- Her araç çubuğu düğmesi dolgu dahil 22 piksel genişliğindedir. Simgeyi bölünmüş düğme yapmak 11 piksel daha genişlik ekler.

- Komutların araç çubukları arasında çoğaltılmasına izin verilir.

  **Belgeye özgü araç çubukları,** belirli bir dosya türü etkin olduğunda görünür ve farklı bir dosya türü etkin olduğunda kaybolur.

- Belgeye özgü araç çubuklarında 12'den fazla düğme olmayabilir.

- Araç çubuğunun toplam genişliği 300 pikseli geçemez.

- Her dosya türünde bir katıştırılmış araç çubuğu veya belgeye özgü bir genel araç çubuğu olabilir, ancak her ikisi birden olmayabilir.

  **İçerime özgü araç çubukları,** belirli bir bağlam ayarlandığında görünür ve uzun süre etkin kalma eğilimindedir.

- İçerime özgü tüm araç çubukları için düğme sınırı 18'dir.

- Çoğu kullanıcı bağlam etkin olduğunda bu araç çubuğunun komutlarını tutarlı bir şekilde kullanmıyorsa, bu araç çubuğunu bir bağlamla ilişkilendirmeyin.

- Bağlam çıkarken araç çubuğunun kaybolduğundan emin olun. Bu araç çubuklarının hiçbiri başlangıç ta görünmemelidir.

  **Bağlamı olmayan araç çubukları** hiçbir zaman otomatik olarak görünmez. Bunlar yalnızca kullanıcı bunları etkinleştirdiğinde gösterir. Maksimum genişliği 200 pikselin altında tutun.

### <a name="general-organization-and-shell-defined-groups"></a>Genel organizasyon ve kabuk tanımlı gruplar
 Varolan paylaşılan komutları, komut gruplarını ve menüleri kullanın. Yeni bir komutun tanımlanması gerekiyorsa, bu komutu varolan bir paylaşılan komut grubuna yerleştirmeyi deneyin. Yeni bir grubun tanımlanması gerekiyorsa, yeni bir üst düzey menü oluşturmadan önce bu grubun ilgili komut grubuna yakın varolan paylaşılan bir menüye yerleştirmeyi deneyin. Bu, IDE'de tutarlı komut yerleşimi sağlarken komut karmaşıklığını azaltır.

 Genellikle tasarımcı tarzı belge pencereleri bağlamında gösterilen paylaşılan **Biçim** menüsü aşağıdaki resimde gösterilmiştir:

 ![İlave ler içeren Visual Studio Format menüsü](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Visual Studio'da menü grupları**

### <a name="reducing-and-reusing-commands"></a>Komutları azaltma ve yeniden kullanma
 Komutlar, kullanıcının herhangi bir zamanda gördüğü komut sayısını azaltmak için genellikle içeriğe göre gösterilir. Ancak, komut yapısının bağlamdaki değişiklikler arasında nispeten kararlı kalmasını sağlamak için varolan paylaşılan menüleri ve komut gruplarını da yeniden kullanmanız gerekir.

 Paylaşılan komutları yeniden kullanmak ve ilgili paylaşılan komutlara yakın yeni komutlar yerleştirmek IDE karmaşıklığını azaltır ve daha kullanıcı dostu bir deneyim oluşturur.

## <a name="naming-commands"></a>Adlandırma komutları

### <a name="naming-conventions"></a>Adlandırma kuralları
 Tutarlı komut adlandırma, kullanıcıların komut satırını kullanarak veya klavye kısayolu'na bağlanarak komutları bulup yürütebilmeleri için önemlidir. Komut adları, kullanıcının bir komutun araç çubuğunda veya basamaklı veya bağlam menüsünde görüntülendiğinde hangi amaca hizmet ettiğini anlamasında da yardımcı olur.

#### <a name="when-naming-commands"></a>Komutları adlandırırken:

- Kolayca yerelleştirilebilir şekilde metin oluşturma. Metni yerelleştirme hakkında daha fazla şey için [yerelleştirme en iyi uygulamaları](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)bakın.

- Kısa ve öz ol. Komutlar en fazla üç sözcük kullanmalıdır.

- Başlık-büyük harf kullanın: her sözcüğün ilk harfi büyük harfle yazılmalıdır. Visual Studio'da metin biçimlendirme hakkında daha fazla bilgi için [Metin stiline](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)bakın.

- Komutun nereye yerleştirileceğini göz önünde bulundurun. Üst düzey bir menüde mi yoksa uçuşta mı? Örneğin, bir uçuşta hizalama komutlarını gruplandırmayaparken, üst düzey komut "Hizala" ve uçuş komutları "Sol", "Sağ", "Merkez", "Yaslama" ve benzeri olmalıdır. Flyout komutlarına "Sola Hizala" veya "Sağa Hizala" komutları vermek gereksiz olacaktır.

     ![Visual Studio Format menüsü](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Komutlarla simgeleri kullanma
 Komutlarla simge eşleştirme kullanımında dikkatli olun. Benzersiz bir görüntüyü bir komutla ilişkilendirmek, kullanıcının bu komutu tanımlama yeteneğini hızlandırsa da, görüntü aşırı kullanımıyla görsel dağınıklık ve verimsizlik oluşur. Komut simgesi oluşturup oluşturmayacağınızkonusunda aşağıdaki kurallar yardımcı olur.

#### <a name="use-an-icon-with-a-command-only-if"></a>Yalnızca şu şekilde komut içeren bir simge kullanın:

- Aynı komut, Microsoft Office uygulamalarından biri gibi başka bir önemli Microsoft ürününde onunla ilişkili bir simgeye sahiptir.

- Komut varsayılan araç çubuğuna yerleştirilir.

- Komut, kullanıcıların **"Özelleştir..."** iletişim kutusunu kullanarak bir araç çubuğuna ekleme olasılığının yüksek olduğu özel bir komutdur.

## <a name="access-and-shortcut-keys"></a>Erişim ve kısayol tuşları

### <a name="overview"></a>Genel Bakış
 İki tür klavye tuşu ataması vardır:

- **Erişim tuşları** (hızlandırıcıolarak da bilinir), komut vermek için menüler aracılığıyla ve iletişim arabirimi ara durumundaki her etikete klavye erişimine izin verir. Erişim anahtarları çoğunlukla erişilebilirlik amacıyladır, tüm menülere ve çoğu iletişim kutusu denetimine atanır, ezberlenmemesi gerekir, yalnızca geçerli pencereyi etkiler ve yerelleştirilmiştir.

- **Kısayol tuşları** çoğunlukla Denetim (Ctrl) ve Fonksiyon (Fn) tuş dizilerini kullanır. Onlar gelişmiş kullanıcılar ve verimlilik yardım için daha fazla tasarlanmıştır. Bunlar yalnızca en sık kullanılan komutlara atanır ve ana menüyü atlarken hızlı erişime izin verirler. Kısayol anahtarlarının ezberlemesi amaçlanmıştır ve bu nedenle profil düzenine uygun olarak atanmalıdır. Kısayol anahtar düzenleri profilden profile değişebilir. Bir **kullanıcı, Araçlar > Seçenekleri > Klavye**aracılığıyla kısayol tuşlarını özelleştirebilir.

### <a name="assigning-access-keys"></a>Erişim anahtarlarını atama
 Erişim anahtarları Alt artı alfasayısal tuş(lar)'dan oluşur. İstisnasız her menü öğesine bir erişim anahtarı atayın. Erişim anahtarları atamak için Windows'u ve ortak kuralları izleyin. örneğin, Dosya > **Yeni'nin** erişim anahtarı her zaman **Alt, F, N**olmalıdır.

 'i' (büyük veya küçük harf) veya küçük 'l' gibi tek piksel genişliğinde harfler kullanmayın ve bu ayırt etmek zor olduğu gibi descenders (g, j, p, q ve y) karakterleri kullanmaktan kaçının.

 Mümkün olduğunda yinelenen anahtarları kullanmaktan kaçının. Yinelemenin kaçınılmaz olduğu durumlarda, menü sistemi anahtarı kullanan tüm komutları bisiklete binerek çakışmaları işler. Örnek olarak, Dosya menüsünün altında "N" erişim anahtarını yineleyen varsayımsal bir "Sayı" komutu için **Alt, F, N** yeni bir dosya oluşturur ve **Alt, F, N, N** "Sayı" komutunu gerçekleştirir.

### <a name="assigning-shortcut-keys"></a>Kısayol anahtarlarını atama
 Her komut için gerekli olmadığından ve aşırı kullanıldığında sistemi (ve kullanıcı belleği) vergilendirdikleri için yeni kısayol anahtarları atamaktan kaçının. Müşteri Deneyimini Geliştirme Programı'ndan (CEIP) elde edilen veriler, Visual Studio kullanıcılarının tümleşik kısayolların yalnızca küçük bir alt kümesini kullandığını gösterir.

 Kısayolları tanımlarken aşağıdaki kurallara uyun:

- **Denetim (Ctrl) ve Fonksiyon (Fn) tuş dizilerini kullanın.**

- **Sık kullanılan kısayolları koruyun.** En popüler kısayolları koruyun.

- **Düzenleyici kısayollarını yazmayı kolaylaştırın.** Kod yazarken geliştiricilerin en çok ihtiyaç duyduğu komutlara türü kolay kısayollar bağlayın. Örneğin, **Edit.InvokeSmartTag'ın** Alt+Shift+F10 gibi değil, Ctrl+/ gibi hızlı bir kısayol anahtarına sahip olması gerekir.

- **Sürekli temalı kısayollar için çabalayın.**

- **Hangi değiştirici anahtarların çalıştırılalamasını belirlemek için Windows yönergelerini izleyin.** Belgenin tamamına uygulanan komutlar gibi büyük ölçekli etkileri olan komutlar için Ctrl tuş kombinasyonlarını kullanın. Standart kısayol anahtarının eylemlerini genişleten veya tamamlayan komutlar için Shift tuşu birleşimlerini kullanın. Ctrl+Alt kombinasyonları kullanmayın.

- **Gereksiz kısayolları kaldırın.** Eski bir özelliğiniz varsa, bir erişim anahtarı aynı komuta hızlı erişim sağlıyorsa, aşırı sıklık (CEIP verilerinden 10 kat daha az) veya orta frekanslı (CEIP verilerinden 100'den az) kullanılan kısayolları kaldırmayı düşünün. Örneğin: Alt, H, C Yardım/İçerik'i açar.

  Kısayol kullanılabilirliğini denetlemenin basit bir yolu yoktur. Kısayol eklemek istiyorsanız aşağıdaki adımları izleyin:

1. Visual Studio [2013 kısayollarının](http://visualstudioshortcuts.com/2013/) listesini kontrol edin ve sizinkiyle gruplandırmak için benzer komutlar olup olmadığını belirleyin.

2. Araçlar **> Seçenekler > Ortam > Klavye'ye** gidin ve kısayolunuzu test edin. "Aşağıdaki ek klavye eşleme düzenini uygulayın" altında listelenen her klavye eşleme düzenini denetleyin. Benzersiz kısayolları paylaştığından Genel, C#, VB ve C++ profillerini denetleyin. Kısayol, bu yerlerden herhangi birinde eşlenmediyse kullanılabilir.
