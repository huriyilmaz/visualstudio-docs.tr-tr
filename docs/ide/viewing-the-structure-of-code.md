---
title: Sınıf görünümü, çağrı hiyerarşisi, nesne tarayıcısı, kod tanım penceresi
ms.date: 09/19/2019
ms.topic: reference
f1_keywords:
- vs.documentoutline.window
- vs.objectbrowser
- vs.classview
- VS.CodeDefinitionView
- VS.CodeDefinitionWindow
- vs.componentpicker
- vs.callbrowser
helpviewer_keywords:
- document outline window
- Visual Studio, object browser
- call hierarchy
- Visual Studio, document outline window
- code definition window [Visual Studio]
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b73a4660c9e0dad66ceb73c04852601765174264
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303059"
---
# <a name="view-the-structure-of-code-using-different-tool-windows"></a>Farklı araç pencerelerini kullanarak kodun yapısını görüntüleme

**Sınıf Görünümü,** **Çağrı Hiyerarşisi,** Nesne **Tarayıcısı**ve **Kod Tanımı** (yalnızca C++) dahil olmak üzere çeşitli araç pencerelerini kullanarak Visual Studio'daki sınıfları ve üyelerini inceleyebilirsiniz. Bu araç pencereleri Visual Studio projelerinde, .NET bileşenlerinde, COM bileşenlerinde, dinamik bağlantı kitaplıklarında (DLL) ve tür kitaplıklarında (TLB) kodu inceleyebilir.

**Ayrıca,** projelerinizdeki türleri ve üyeleri göz atmak, sembolleri aramak, bir yöntemin çağrı hiyerarşisini görüntülemek, simge başvurularını bulmak ve daha fazlasını, birden çok araç penceresi arasında geçiş yapmak zorunda kalmadan aramak için Solution Explorer'ı da kullanabilirsiniz.

Visual Studio Enterprise sürümünüz varsa, kod *haritalarınızı* kodlarınızın yapısını ve tüm çözümdeki bağımlılıklarını görselleştirmek için kullanabilirsiniz. Daha fazla bilgi için [kod eşlemleriyle Harita bağımlılıklarına](../modeling/map-dependencies-across-your-solutions.md)bakın.

## <a name="class-view-visual-basic-c-c"></a>Sınıf Görünümü (Visual Basic, C#, C++)

**Sınıf Görünümü,** Çözüm **Gezgini'nin** bir parçası ve ayrı bir pencere olarak gösterilir. **Sınıf Görünümü** bir uygulamanın öğelerini görüntüler. Üst bölmede ad alanları, türler, arabirimler, sayısallaştırmalar ve sınıflar, alt bölme ise üst bölmede seçilen türe ait üyeleri görüntüler. Bu pencereyi kullanarak, kaynak kodundaki üye tanımlarına (veya öğe çözümünüz dışında tanımlanmışsa Nesne Tarayıcısı'na) geçebilirsiniz. **Object Browser**

**Sınıf Görünümü'ndeki**öğelerini görüntülemek için bir proje derlemeniz gerekmez. Projenizdeki kodu değiştirirken pencere yenilenir.

Proje düğümünü seçerek ve **Yeni Öğe Ekle** iletişim kutusunu açmak için **Ekle** düğmesini seçerek projenize kod ekleyebilirsiniz. Kod ayrı bir dosyaya eklenir.

Projeniz kaynak kodu denetimi için iade edilirse, her **Sınıf Görünümü** öğesi dosyanın kaynak kodu durumunu gösteren bir simge görüntüler. **Kullanıma Alma,** **Giriş**Yap ve Son Sürümü **Al** gibi yaygın kaynak kod denetimi komutları da öğenin kısayol menüsünde kullanılabilir.

### <a name="class-view-toolbar"></a>Sınıf Görünüm araç çubuğu

**Sınıf Görünümü** araç çubuğu aşağıdaki komutları içerir:

|||
|-|-|
|**Yeni Klasör**|Sık kullanılan öğeleri düzenleyebileceğiniz sanal bir klasör veya alt klasör oluşturur. Etkin çözüm (*.suo*) dosyasına kaydedilirler. Kodunuzdaki bir öğeyi yeniden adlandırdıktan veya sildikten sonra, sanal bir klasörde hata düğümü olarak görünebilir. Bu sorunu düzeltmek için hata düğümünü silin. Bir öğeyi yeniden adlandırdıysanız, onu proje hiyerarşisinden klasöre yeniden taşıyabilirsiniz.|
|**Geri**|Daha önce seçili öğeye doğru geziner.|
|**İleri**|Bir sonraki seçili öğeye doğru geziner.|
|**Sınıf Diyagramı'nı Görüntüle** (yalnızca yönetilen kod projeleri)|**Sınıf Görünümü'nde**bir ad alanı veya tür seçtiğinizde kullanılabilir olur. Bir ad alanı seçildiğinde, sınıf diyagramı içinde bulunan tüm türleri gösterir. Bir tür seçildiğinde, sınıf diyagramı yalnızca bu türü gösterir.|

### <a name="class-view-settings"></a>Sınıf Görünüm ayarları

Araç çubuğundaki **Sınıf Görünümü Ayarları** düğmesi aşağıdaki ayarlara sahiptir:

|||
|-|-|
|**Taban Türlerini Göster**|Temel türleri görüntülenir.|
|**Proje Referanslarını Göster**|Proje başvuruları görüntülenir.|
|**Gizli Türleri ve Üyeleri Göster**|Gizli türler ve üyeler (istemciler tarafından kullanılmak üzere tasarlanmamıştır) açık gri metinde görüntülenir.|
|**Genel Üyeleri Göster**|Ortak üyeler görüntülenir.|
|**Korumalı Üyeleri Göster**|Korumalı üyeler görüntülenir.|
|**Özel Üyeleri Göster**|Özel üyeler görüntülenir.|
|**Diğer Üyeleri Göster**|Dahili (veya Visual Basic'teki Arkadaş) üyeleri de dahil olmak üzere diğer üye türleri görüntülenir.|
|**Devralınan Üyeleri Göster**|Devralınan üyeler görüntülenir.|

### <a name="class-view-shortcut-menu"></a>Sınıf Görünümü kısayol menüsü

**Sınıf Görünümü'ndeki** kısayol (veya sağ tıklatma) menüsü, seçilen proje türüne bağlı olarak aşağıdaki komutları içerebilir:

|||
|-|-|
|**Tanıma Git**|Öğe açık projede tanımlanmamışsa, kaynak koddaki veya **Nesne Tarayıcısı'ndaki**öğenin tanımını bulur.|
|**Tanıma Gözat**|**Nesne Tarayıcısında**seçili öğeyi görüntüler.|
|**Tüm Başvuruları Bul**|Şu anda seçili nesne öğesini bulur ve sonuçları Sonuçları **Bul** penceresinde görüntüler.|
|**Filtre Türüne** (yalnızca yönetilen kod)|Yalnızca seçili türü veya ad alanını görüntüler. **Bul** kutusunun yanındaki **Bul** (**X**) düğmesini seçerek filtreyi kaldırabilirsiniz.|
|**Kopyala**|Öğenin tam nitelikli adını kopyalar.|
|**Alfabetik sıralama**|Türleri ve üyeleri ada göre alfabetik olarak listeler.|
|**Üye Türüne Göre Sırala**|Türleri ve üyeleri türe göre sırayla listeler (örneğin, sınıflar arabirimlerden önce, arabirimler temsilcilerden önce gelir ve yöntemler özelliklerden önce gelir).|
|**Üye Erişimine Göre Sırala**|Genel veya özel gibi erişim türüne göre türleri ve üyeleri sırayla listeler.|
|**Üye Türüne Göre Gruplandırma**|Türleri ve üyeleri nesne türüne göre gruplara ayırır.|
|**Bildirgeye Git** (yalnızca C++ kodu)|Varsa, kaynak koddaki tür veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa, kaynak koddaki tür veya üyenin tanımını görüntüler.|
|**Başvuruya Git**|Varsa, kaynak koddaki türe veya üyeye bir başvuru görüntüler.|
|**Çağrı Hiyerarşisi'ni görüntüle**|**Çağrı Hiyerarşisi** penceresinde seçili yöntemi görüntüler.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Çağrı Hiyerarşisi penceresi (Visual Basic, C#, C++)

**Çağrı Hiyerarşisi** penceresi, belirli bir yöntemin veya özelliğin çağrıldığı yeri gösterir. Ayrıca, bu yöntemden çağrılan yöntemleri listeler. Çağrı grafiğinin, belirli bir kapsamdaki yöntemler arasında arayan-callee ilişkilerini gösteren birden çok düzeylerini görüntüleyebilirsiniz.

Düzenleyicide bir yöntem (veya özellik veya oluşturucu) seçip kısayol menüsünde **Çağrı Hiyerarşisini** Görüntüle'yi seçerek **Çağrı Hiyerarşisi** penceresini görüntüleyebilirsiniz. Ekran aşağıdaki görüntüye benzemelidir:

![Visual Studio'da Çağrı Hiyerarşisi penceresi](../ide/media/multiplenodes.png)

Araç çubuğundaki açılır listeyi kullanarak hiyerarşinin kapsamını belirtebilirsiniz: çözüm, geçerli proje veya geçerli belge.

Ana bölme, yönteme gelen ve gelen çağrıları görüntüler ve **Çağrı Siteleri** bölmesi seçili aramanın konumunu görüntüler. Sanal veya soyut olan üyeler için geçersiz **kılma yöntemi ad** düğümü görüntülenir. Arabirim üyeleri için bir **Uygulama yöntemi ad** düğümü görüntülenir.

**Çağrı Hiyerarşisi** penceresi, yöntemin olay işleyicisi olarak eklendiği veya bir temsilciye atandığı yerleri içeren yöntem grubu başvurularını bulamaz. Bu başvuruları bulmak için **Tüm Başvuruları Bul** komutunu kullanın.

**Çağrı Hiyerarşisi** penceresindeki kısayol menüsü aşağıdaki komutları içerir:

|||
|-|-|
|**Yeni Kök Olarak Ekle**|Seçili düğümü yeni bir kök düğüm olarak ekler.|
|**Kök kaldırma**|Seçili kök düğümünü ağaç görünüm bölmesinden kaldırır.|
|**Tanıma Git**|Yöntemin özgün tanımına yönlendirin.|
|**Tüm Başvuruları Bul**|Projede seçili yönteme yapılan tüm başvuruları bulur.|
|**Kopyala**|Seçili düğümü kopyalar (ancak alt düğümlerini değil).|
|**Yenile**|Bilgileri yeniler.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a>Nesne Tarayıcısı

**Nesne Tarayıcı** penceresi projelerinizdeki kodun açıklamalarını görüntüler.

Pencerenin üst kısmındaki açılır listeyi kullanarak görüntülemek istediğiniz bileşenleri filtreleyebilirsiniz. Özel bileşenler yönetilen kod yürütülebilir, kitaplık derlemeleri, tür kitaplıkları ve *.ocx* dosyalarını içerebilir. C++ özel bileşenleri eklemek mümkün değildir.

::: moniker range="vs-2017"

Özel ayarlar Visual Studio kullanıcı uygulama dizininde kaydedilir, *%APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat*.

::: moniker-end

::: moniker range=">=vs-2019"

Özel ayarlar Visual Studio kullanıcı uygulama dizininde kaydedilir, *%APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat*.

::: moniker-end

**Nesne** Tarayıcısı'nın sol bölmesi derlemeleri gösterir. İçerdikleri ad alanlarını görüntülemek için derlemeleri genişletebilir ve ardından içerdikleri türleri görüntülemek için ad alanlarını genişletebilirsiniz. Bir tür seçtiğinizde, üyeleri (özellikler ve yöntemler gibi) sağ bölmede listelenir. Sağ alt bölmede seçili öğe hakkında ayrıntılı bilgiler görüntülenir.

Pencerenin üst kısmındaki **Arama** kutusunu kullanarak belirli bir öğeyi arayabilirsiniz. Aramalar büyük/küçük harf duyarsızdır. Arama sonuçları sol bölmede görüntülenir. Aramayı temizlemek için **Arama** kutusunun yanındaki **AramaYı Temizle** (**X**) düğmesini seçin.

**Nesne Tarayıcısı** yaptığınız seçimleri izler ve araç çubuğundaki **İleri** ve **Geri** düğmelerini kullanarak seçimleriniz arasında gezinebilirsiniz.

**Nesne** Tarayıcısı'nı, bir öğe (derleme, ad alanı, tür veya üye) seçerek ve araç çubuğundaki **Başvuru Ekle** düğmesini seçerek açık bir çözüme montaj başvurusu eklemek için kullanabilirsiniz.

### <a name="object-browser-settings"></a>Nesne Tarayıcı ayarları

Araç çubuğundaki **Nesne Tarayıcı Ayarları** düğmesini kullanarak aşağıdaki görünümlerden birini belirtebilirsiniz:

|||
|-|-|
|**Ad Boşluklarını Görüntüle**|Sol bölmede fiziksel kapsayıcılar yerine ad alanlarını görüntüler. Birden çok fiziksel kapsayıcıda depolanan ad alanları birleştirilir.|
|**Kapsayıcıları Görüntüle**|Sol bölmede ad boşlukları yerine fiziksel kapsayıcıları görüntüler. **Görünüm Ad Alanları** ve **Görünüm Kapsayıcıları** birbirini dışlayan ayarlardır.|
|**Taban Türlerini Göster**|Taban türlerini görüntüler.|
|**Gizli Türleri ve Üyeleri Göster**|Gizli türleri ve üyeleri (istemciler tarafından kullanılmak üzere tasarlanmamıştır) açık gri metinde görüntüler.|
|**Genel Üyeleri Göster**|Herkese açık üyeleri görüntüler.|
|**Korumalı Üyeleri Göster**|Korumalı üyeleri görüntüler.|
|**Özel Üyeleri Göster**|Özel üyeleri görüntüler.|
|**Diğer Üyeleri Göster**|Dahili (veya Visual Basic'teki Arkadaş) üyeleri de dahil olmak üzere diğer üye türlerini görüntüler.|
|**Devralınan Üyeleri Göster**|Devralınan üyeleri görüntüler.|
|**Uzatma Yöntemlerini Göster**|Uzantı yöntemlerini görüntüler.|

### <a name="object-browser-shortcut-menu-commands"></a>Nesne Tarayıcı kısayol menü komutları

**Nesne** Tarayıcısı'ndaki kısayol (veya sağ tıklatma) menüsü, seçilen öğenin türüne bağlı olarak aşağıdaki komutları içerebilir:

|||
|-|-|
|**Tanıma Gözat**|Seçili öğenin birincil düğüm'üni gösterir.|
|**Tüm Başvuruları Bul**|Şu anda seçili nesne öğesini bulur ve sonuçları Sonuçları **Bul** penceresinde görüntüler.|
|**Filtre yazın**|Yalnızca seçili türü veya ad alanını görüntüler. **Aramayı Temizle** düğmesini seçerek filtreyi kaldırabilirsiniz.|
|**Kopyala**|Öğenin tam nitelikli adını kopyalar.|
|**Kaldır**|Kapsam özel bir bileşen kümesiyse, seçili bileşeni kapsamdan kaldırır.|
|**Alfabetik sıralama**|Türleri ve üyeleri ada göre alfabetik olarak listeler.|
|**Nesne Türüne Göre Sırala**|Türleri ve üyeleri türe göre sırayla listeler (örneğin, sınıflar arabirimlerden önce, arabirimler temsilcilerden önce gelir ve yöntemler özelliklerden önce gelir).|
|**Nesne Erişimine Göre Sırala**|Genel veya özel gibi erişim türüne göre türleri ve üyeleri sırayla listeler.|
|**Nesne Türüne Göre Gruplandırma**|Türleri ve üyeleri nesne türüne göre gruplara ayırır.|
|**Bildirgeye Git** (yalnızca C++ projeleri)|Varsa, kaynak koddaki tür veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa, kaynak koddaki tür veya üyenin tanımını görüntüler.|
|**Başvuruya Git**|Varsa, kaynak koddaki türe veya üyeye bir başvuru görüntüler.|
|**Çağrı Hiyerarşisi'ni görüntüle**|**Çağrı Hiyerarşisi** penceresinde seçili yöntemi görüntüler.|

## <a name="code-definition-window-c"></a>Kod Tanımı penceresi (C++)

**Kod Tanımı** penceresi, etkin projede seçili bir C++ türü veya üyenin tanımını görüntüler. Tür veya üye kod düzenleyicisinde veya kod görünümü penceresinde seçilebilir.

Bu pencere salt okunur olsa da, kesme noktaları veya yer imleri ayarlayabilirsiniz. Görüntülenen tanımı değiştirmek için kısayol menüsünde **Tanımı Edit'i** seçin. Bu, kod düzenleyicisindeki kaynak dosyayı açar ve ekleme noktasını tanımın başladığı satıra taşır.

> [!NOTE]
> Visual Studio 2015'ten itibaren **Kod Tanımı** penceresi yalnızca C++ kodu ile kullanılabilir.

### <a name="code-definition-shortcut-menu"></a>Kod Tanımı kısayol menüsü

**Kod Tanımı** penceresindeki kısayol (veya sağ tıklatma) menüsü aşağıdaki komutları içerebilir:

|||
|-|-|
|**Hızlı Eylemler ve Yeniden Düzenlemeler**||
|**Yeniden Adlandır**||
|**Dosya Ekle Grafiği Oluştur**||
|**Tanıma Göz At**||
|**Tanıma Git**|Tanım (veya kısmi sınıflar için tanımları) bulur ve **sonuçları bul** penceresinde görüntüler.|
|**Bildirime Git**||
|**Tüm Başvuruları Bul**|Çözümdeki türe veya üyeye yapılan başvuruları bulur.|
|**Çağrı Hiyerarşisi'ni görüntüle**|**Çağrı Hiyerarşisi** penceresinde yöntemi görüntüler.|
|**Üstbilgi / Kod Dosyası Değiştirme**||
|**Testleri Çalıştır**|Projede birim testleri varsa, seçili kod için testleri çalıştırın.|
|**Hata Ayıklama Testleri**||
|**Kesme noktası**|Kesme noktası (veya izleme noktası) ekler.|
|**İmlec'e Çalıştır**|Programı hata ayıklama modunda imlecin konumuna çalıştırır.|
|**Kod Parçacığı**||
|**Kes**, **Kopyala**, **Yapıştır**||
|**Ek Açıklama**||
|**Anahat**|Standart anahat komutları.|
|**Rescan**||
|**Tanımı Nı Edin**|Ekleme noktasını kod penceresindeki tanıma taşır.|
|**Kodlama'yı seçin**|Dosya için kodlama ayarlayabilmeniz için **Kodlama** penceresini açar.|

## <a name="document-outline-window"></a>Belge Anahat penceresi

**Belge Anahat** penceresini, XAML sayfası veya Windows Form tasarımcısı tasarımcısı gibi tasarımcı görünümleriyle birlikte veya HTML sayfalarıyla kullanabilirsiniz. Bu pencere, formun veya sayfanın mantıksal yapısını görüntüleyebilmeniz ve derinden katıştırılmış veya gizlenmiş denetimler bulabilmeniz için öğeleri ağaç görünümünde görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıf Görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md)
