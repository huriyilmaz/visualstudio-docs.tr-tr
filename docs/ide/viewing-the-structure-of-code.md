---
title: Sınıf görünümü, çağrı hiyerarşisi, nesne tarayıcısı, kod tanımı penceresi
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fc7ade360ac586f09eb838057251172be5d0e81
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647299"
---
# <a name="view-the-structure-of-code-using-different-tool-windows"></a>Farklı araç pencerelerini kullanarak kodun yapısını görüntüleme

**Sınıf görünümü**, **çağrı hiyerarşisi**, **nesne tarayıcısı**ve **kod tanımı** (C++ yalnızca) gibi çeşitli araç pencerelerini kullanarak Visual Studio 'da sınıfları ve üyelerini inceleyebilirsiniz. Bu araç pencereleri Visual Studio projeleri, .NET bileşenleri, COM bileşenleri, dinamik bağlantı kitaplıkları (DLL) ve tür kitaplıkları (TLB) içinde kodu inceleyebilir.

Ayrıca, projelerinizdeki türlere ve üyelere gözatıp, sembolleri aramak, bir yöntemin Çağrı hiyerarşisini görüntülemek, sembol başvurularını bulmak ve birden çok araç penceresi arasında geçiş yapmak zorunda kalmadan, **Çözüm Gezgini** de kullanabilirsiniz.

Visual Studio Enterprise sürümüne sahipseniz, kodunuzun yapısını ve tüm çözüm içindeki bağımlılıklarını görselleştirmek için *kod eşlemelerini* kullanabilirsiniz. Daha fazla bilgi için bkz. [kod eşlemeleriyle harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Sınıf Görünümü (Visual Basic, C#, C++)

**Sınıf görünümü** , **Çözüm Gezgini** bir parçası olarak ve ayrı bir pencere olarak gösterilir. **Sınıf görünümü** bir uygulamanın öğelerini görüntüler. Üstteki bölmede ad alanları, türler, arabirimler, numaralandırmalar ve sınıflar görüntülenir ve alt bölmede üst bölmede seçilen türe ait Üyeler görüntülenir. Bu pencereyi kullanarak, kaynak kodundaki üye tanımlarına (veya öğe çözümünüz dışında tanımlanmışsa **nesne tarayıcısı** taşıyabilirsiniz) geçebilirsiniz.

**Sınıf görünümü**öğelerini görüntülemek için bir proje derlemek zorunda değilsiniz. Projenizdeki kodu değiştirirken pencere yenilenir.

Proje düğümünü seçerek ve **Ekle** düğmesini seçerek **Yeni öğe Ekle** iletişim kutusunu açmak için projenize kod ekleyebilirsiniz. Kod ayrı bir dosyaya eklenir.

Projeniz kaynak kodu denetimine iade edildiğinde, her **sınıf görünümü** öğesi dosyanın kaynak kodu durumunu gösteren bir simge görüntüler. **Kullanıma alma,** **Iade**etme ve **en son sürümü Al** gibi ortak kaynak kodu denetim komutları, öğesi için kısayol menüsünde de mevcuttur.

### <a name="class-view-toolbar"></a>Sınıf Görünümü araç çubuğu

**Sınıf görünümü** araç çubuğu aşağıdaki komutları içerir:

|||
|-|-|
|**Yeni klasör**|Sık kullanılan öğeleri düzenleyebileceğiniz bir sanal klasör veya alt klasör oluşturur. Bunlar, etkin çözüm ( *. suo*) dosyasına kaydedilir. Kodunuzda bir öğeyi yeniden adlandırdıktan veya sildikten sonra, bir sanal klasörde hata düğümü olarak görünebilir. Bu sorunu düzeltmek için, hata düğümünü silin. Bir öğeyi yeniden adlandırdıysanız proje hiyerarşisinden klasörü yeniden klasöre taşıyabilirsiniz.|
|**Geri**|Daha önce seçilen öğeye gider.|
|**Tirler**|Sonraki seçili öğeye gider.|
|**Sınıf diyagramını görüntüle** (yalnızca yönetilen kod projeleri)|**Sınıf görünümü**bir ad alanı veya tür seçtiğinizde kullanılabilir hale gelir. Bir ad alanı seçildiğinde, sınıf diyagramı içindeki tüm türleri gösterir. Bir tür seçildiğinde, sınıf diyagramı yalnızca bu türü gösterir.|

### <a name="class-view-settings"></a>Sınıf Görünümü ayarları

Araç çubuğundaki **Sınıf Görünümü ayarları** düğmesi aşağıdaki ayarlara sahiptir:

|||
|-|-|
|**Temel türleri göster**|Temel türler görüntülenir.|
|**Proje başvurularını göster**|Proje başvuruları görüntülenir.|
|**Gizli türleri ve üyeleri göster**|Gizli türler ve Üyeler (istemciler tarafından kullanılmak üzere tasarlanmamıştır) açık gri metinde görüntülenir.|
|**Ortak üyeleri göster**|Ortak Üyeler görüntülenir.|
|**Korumalı üyeleri göster**|Korunan Üyeler görüntülenir.|
|**Özel üyeleri göster**|Özel Üyeler görüntülenir.|
|**Diğer üyeleri göster**|İç (veya Visual Basic arkadaş) Üyeler dahil diğer üye türleri görüntülenir.|
|**Devralınan üyeleri göster**|Devralınan Üyeler görüntülenir.|

### <a name="class-view-shortcut-menu"></a>Sınıf Görünümü kısayol menüsü

**Sınıf görünümü** ' deki kısayol (veya sağ tıklama) menüsünde, seçilen proje türüne bağlı olarak aşağıdaki komutlar bulunabilir:

|||
|-|-|
|**Tanıma Git**|Öğe açık projede tanımlanmamışsa, kaynak kodundaki veya **nesne tarayıcısı**içindeki öğenin tanımını bulur.|
|**Tanıma gözatatıon**|**Nesne tarayıcısı**seçili öğeyi görüntüler.|
|**Tüm başvuruları bul**|Şu anda seçili olan nesne öğesini bulur ve sonuçları **Bul sonuçları** penceresinde görüntüler.|
|**Türe Filtre Uygula** (yalnızca yönetilen kod)|Yalnızca seçilen türü veya ad alanını görüntüler. **Bul** kutusunun yanında bulunan **bul** (**X**) düğmesini seçerek filtreyi kaldırabilirsiniz.|
|**Kopyala**|Öğenin tam adını kopyalar.|
|**Alfabetik olarak Sırala**|Türleri ve üyeleri ada göre alfabetik olarak listeler.|
|**Üye türüne göre sırala**|Türlerine göre sırasıyla türler ve üyeleri listeler (Bu tür sınıfların önüne ve arabirimlerin önüne arabirimler ve yöntemlerin önündeki Yöntemler).|
|**Üye erişimine göre sırala**|Türleri ve üyeleri, genel veya özel gibi erişim türüne göre sıralar.|
|**Üye türüne göre grupla**|Türleri ve üyeleri nesne türüne göre gruplar halinde sıralar.|
|**Bildirime git** (C++ yalnızca kod)|Varsa, kaynak kodundaki tür veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa, kaynak kodundaki tür veya üyenin tanımını görüntüler.|
|**Başvuruya git**|Varsa, kaynak kodundaki tür veya üyenin başvurusunu görüntüler.|
|**Çağrı hiyerarşisini görüntüle**|Seçilen yöntemi **çağrı hiyerarşisi** penceresinde görüntüler.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Çağrı hiyerarşisi penceresi (Visual Basic, C#, C++)

**Çağrı hiyerarşisi** penceresi, belirli bir yöntemin veya özelliğin nerede çağrıldığını gösterir. Ayrıca, bu yöntemden çağrılan yöntemleri de listeler. Çağrı grafiğinin birden çok düzeyini, belirli bir kapsamdaki Yöntemler arasında arayan-çağrılan ilişkilerini gösteren bir şekilde görüntüleyebilirsiniz.

Düzenleyicide bir Yöntem (veya özellik veya Oluşturucu) seçerek **çağrı hiyerarşisi** penceresini görüntüleyebilir ve ardından kısayol menüsünde **Çağrı hiyerarşisini görüntüle** ' yi seçebilirsiniz. Ekran aşağıdaki görüntüye benzemelidir:

![Visual Studio 'da çağrı hiyerarşisi penceresi](../ide/media/multiplenodes.png)

Araç çubuğundaki açılan listeyi kullanarak hiyerarşinin kapsamını belirtebilirsiniz: çözüm, geçerli proje veya geçerli belge.

Ana bölmede, yöntemine ve yönteminden yapılan çağrılar görüntülenir ve **siteleri çağır** bölmesi seçilen çağrının konumunu görüntüler. Sanal veya soyut olan üyeler için bir **geçersiz kılma yöntemi adı** düğümü görüntülenir. Arabirim üyeleri için bir **Implements Yöntem adı** düğümü görüntülenir.

**Çağrı hiyerarşisi** penceresi, bir yöntemin olay işleyicisi olarak eklendiği veya bir temsilciye atandığı yerleri dahil olmak üzere metot grubu başvurularını bulmaz. Bu başvuruları bulmak için, **tüm başvuruları bul** komutunu kullanın.

**Çağrı hiyerarşisi** penceresindeki kısayol menüsü aşağıdaki komutları içerir:

|||
|-|-|
|**Yeni kök olarak ekle**|Seçili düğümü yeni bir kök düğüm olarak ekler.|
|**Kökü Kaldır**|Seçili kök düğümü ağaç görünümü bölmesinden kaldırır.|
|**Tanıma Git**|Bir yöntemin orijinal tanımına gider.|
|**Tüm başvuruları bul**|Seçili yönteme ait tüm başvuruları projede bulur.|
|**Kopyala**|Seçili düğümü kopyalar (alt düğümleri değil).|
|**Yenileyebilir**|Bilgileri yeniler.|

## <a name="BKMK_ObjectBrowser"></a>Nesne Tarayıcısı

**Nesne tarayıcısı** penceresinde, projelerinizdeki kodun açıklamaları görüntülenir.

Pencerenin üst kısmındaki açılan listeyi kullanarak görüntülemek istediğiniz bileşenlere filtre uygulayabilirsiniz. Özel bileşenler, yönetilen kod yürütülebilir dosyaları, kitaplık derlemeleri, tür kitaplıkları ve *. ocx* dosyalarını içerebilir. Özel bileşenler eklemek C++ mümkün değildir.

::: moniker range="vs-2017"

Özel ayarlar, Visual Studio Kullanıcı uygulama dizininde, *%AppData%\microsoft\visualstudio\15.0\ObjBrowEX.dat*dizinine kaydedilir.

::: moniker-end

::: moniker range=">=vs-2019"

Özel ayarlar, Visual Studio Kullanıcı uygulama dizininde, *%AppData%\microsoft\visualstudio\16.0\ObjBrowEX.dat*dizinine kaydedilir.

::: moniker-end

**Nesne tarayıcısı** sol bölmesi derlemeleri gösterir. Derlemeleri içerdikleri ad alanlarını görüntüleyecek şekilde genişletebilir ve ardından içerdikleri türleri göstermek için ad alanlarını genişletebilirsiniz. Bir tür seçtiğinizde, üyeleri (Özellikler ve yöntemler gibi) sağ bölmede listelenir. Sağ alt bölmede seçili öğeyle ilgili ayrıntılı bilgiler görüntülenir.

Pencerenin üst kısmındaki **arama** kutusunu kullanarak belirli bir öğe için arama yapabilirsiniz. Aramalar büyük/küçük harfe duyarlıdır. Arama sonuçları sol bölmede görüntülenir. Bir aramayı temizlemek için **arama** kutusunun yanındaki **Aramayı Temizle** (**X**) düğmesini seçin.

**Nesne tarayıcısı** yaptığınız seçimleri izler ve araç çubuğundaki **İleri** ve **geri** düğmelerini kullanarak seçimleriniz arasında gezinebilirsiniz.

Bir öğeyi (derleme, ad alanı, tür veya üye) seçerek ve araç çubuğundaki **Başvuru Ekle** düğmesini seçerek açık bir çözüme derleme başvurusu eklemek için **nesne tarayıcısı** kullanabilirsiniz.

### <a name="object-browser-settings"></a>Nesne Tarayıcısı ayarları

Araç çubuğundaki **nesne tarayıcısı ayarları** düğmesini kullanarak, aşağıdaki görünümlerden birini belirtebilirsiniz:

|||
|-|-|
|**Ad alanlarını görüntüle**|Sol bölmedeki fiziksel kapsayıcılar yerine ad alanlarını görüntüler. Birden fazla fiziksel kapsayıcıda depolanan ad alanları birleştirilir.|
|**Kapsayıcıları görüntüle**|Sol bölmedeki ad alanları yerine fiziksel kapsayıcıları görüntüler. **Ad alanlarını** ve **Görünüm kapsayıcılarını** görüntüleme birbirini dışlamalı ayarlar.|
|**Temel türleri göster**|Temel türleri görüntüler.|
|**Gizli türleri ve üyeleri göster**|Açık gri metinde gizli türleri ve üyeleri (istemciler tarafından kullanılmak üzere tasarlanmamıştır) görüntüler.|
|**Ortak üyeleri göster**|Ortak üyeleri görüntüler.|
|**Korumalı üyeleri göster**|Korumalı üyeleri görüntüler.|
|**Özel üyeleri göster**|Özel üyeleri görüntüler.|
|**Diğer üyeleri göster**|İç (veya arkadaş Visual Basic) Üyeler dahil diğer üye türlerini görüntüler.|
|**Devralınan üyeleri göster**|Devralınan üyeleri görüntüler.|
|**Uzantı yöntemlerini göster**|Uzantı yöntemlerini görüntüler.|

### <a name="object-browser-shortcut-menu-commands"></a>Nesne Tarayıcısı kısayol menü komutları

**Nesne tarayıcısı** ' deki kısayol (veya sağ tıklama) menüsünde, seçilen öğe türüne bağlı olarak aşağıdaki komutlar bulunabilir:

|||
|-|-|
|**Tanıma gözatatıon**|Seçili öğenin birincil düğümünü gösterir.|
|**Tüm başvuruları bul**|Şu anda seçili olan nesne öğesini bulur ve sonuçları **Bul sonuçları** penceresinde görüntüler.|
|**Türe göre filtrele**|Yalnızca seçilen türü veya ad alanını görüntüler. **Aramayı Temizle** düğmesini seçerek filtreyi kaldırabilirsiniz.|
|**Kopyala**|Öğenin tam adını kopyalar.|
|**Kaldır**|Kapsam özel bir bileşen kümesi ise, seçili bileşeni kapsamdan kaldırır.|
|**Alfabetik olarak Sırala**|Türleri ve üyeleri ada göre alfabetik olarak listeler.|
|**Nesne türüne göre sırala**|Türlerine göre sırasıyla türler ve üyeleri listeler (Bu tür sınıfların önüne ve arabirimlerin önüne arabirimler ve yöntemlerin önündeki Yöntemler).|
|**Nesne erişimine göre sırala**|Türleri ve üyeleri, genel veya özel gibi erişim türüne göre sıralar.|
|**Nesne türüne göre Gruplandır**|Türleri ve üyeleri nesne türüne göre gruplar halinde sıralar.|
|**Bildirime git** (C++ yalnızca projeler)|Varsa, kaynak kodundaki tür veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa, kaynak kodundaki tür veya üyenin tanımını görüntüler.|
|**Başvuruya git**|Varsa, kaynak kodundaki tür veya üyenin başvurusunu görüntüler.|
|**Çağrı hiyerarşisini görüntüle**|Seçilen yöntemi **çağrı hiyerarşisi** penceresinde görüntüler.|

## <a name="code-definition-window-c"></a>Kod Tanım penceresi (C++)

**Kod tanımı** penceresi, etkin projedeki seçili C++ bir türün veya üyenin tanımını görüntüler. Tür veya üye kod düzenleyicisinde veya bir kod görünümü penceresinde seçilebilir.

Bu pencere salt okunurdur, ancak içinde kesme noktaları veya yer işaretleri ayarlayabilirsiniz. Görüntülenmiş tanımı değiştirmek için kısayol menüsünde **tanımı Düzenle** ' yi seçin. Bu, kaynak dosyayı kod düzenleyicisinde açar ve ekleme noktasını tanımın başladığı satıra taşıdır.

> [!NOTE]
> Visual Studio 2015 ' den başlayarak, **kod tanımı** penceresi yalnızca kodla birlikte C++ kullanılabilir.

### <a name="code-definition-shortcut-menu"></a>Kod tanımı kısayol menüsü

**Kod tanımı** penceresindeki kısayol (veya sağ tıklama) menüsünde aşağıdaki komutlar bulunabilir:

|||
|-|-|
|**Hızlı Eylemler ve yeniden düzenlemeler**||
|**Yeniden Adlandır**||
|**Ekleme dosyalarının grafiğini oluştur**||
|**Açıklama Özeti**||
|**Tanıma Git**|Tanımı (veya kısmi sınıflar için tanımları) bulur ve **sonuçları bul** penceresinde görüntüler.|
|**Bildirime git**||
|**Tüm başvuruları bul**|Çözümdeki türe veya üyeye başvuruları bulur.|
|**Çağrı hiyerarşisini görüntüle**|Yöntemi **çağrı hiyerarşisi** penceresinde görüntüler.|
|**Üst bilgi/kod dosyası değiştirme**||
|**Testleri Çalıştır**|Projede birim testleri varsa, seçilen kod için testleri çalıştırır.|
|**Hata ayıklama testleri**||
|**Ilı**|Bir kesme noktası (veya izleme noktası) ekler.|
|**Imlece kadar Çalıştır**|Programı hata ayıklama modunda imleç konumuna çalıştırır.|
|**Gösterildiği**||
|**Kes**, **Kopyala**, **Yapıştır**||
|**Ek Açıklama**||
|**Anahat Oluşturma**|Standart ana hat komutları.|
|**İşlemini**||
|**Tanımı Düzenle**|Ekleme noktasını kod penceresindeki tanıma gider.|
|**Kodlama seçin**|Dosya için bir kodlama ayarlayabilmeniz için **kodlama** penceresini açar.|

## <a name="document-outline-window"></a>Belge Anahattı penceresi

**Belge Anahattı** penceresini, bir XAML sayfası veya bir Windows form TASARıMCıSı veya HTML sayfaları gibi tasarımcı görünümleriyle birlikte kullanabilirsiniz. Bu pencere, öğeleri ağaç görünümünde görüntüler, böylece formun veya sayfanın mantıksal yapısını görüntüleyebilir ve derin gömülü veya gizli denetimleri bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıf Görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md)
