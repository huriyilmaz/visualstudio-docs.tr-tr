---
title: Kod yapısını görüntülemek için Araçlar pencerelerini kullanın
description: Sınıfları ve Visual Studio üyelerini incelemek için Sınıf Görünümü, çağrı hiyerarşisi, Nesne Tarayıcısı ve kod tanımı (yalnızca C++) araç pencerelerini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/19/2019
ms.topic: reference
f1_keywords:
- vs.documentoutline.window
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3d37766aa3ac8dcb72ee4f7dc2e3dd79fd37df38c36dc5a9e159dfbf848acde9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231931"
---
# <a name="view-the-structure-of-code-by-using-different-tool-windows"></a>Farklı araç pencerelerini kullanarak kodun yapısını görüntüleme

**Sınıf Görünümü**, **çağrı hiyerarşisi**, **Nesne Tarayıcısı** ve **kod tanımı** (yalnızca C++) gibi çeşitli araç pencerelerini kullanarak Visual Studio sınıfları ve üyelerini inceleyebilirsiniz. bu araç pencereleri Visual Studio projeler, .net bileşenleri, COM bileşenleri, dinamik bağlantı kitaplıkları (DLL) ve tür kitaplıkları (TLB) içinde kodu inceleyebilir.

Ayrıca, projelerinizdeki türlere ve üyelere gözatıp, sembolleri aramak, bir yöntemin Çağrı hiyerarşisini görüntülemek, sembol başvurularını bulmak ve birden çok araç penceresi arasında geçiş yapmak zorunda kalmadan, **Çözüm Gezgini** de kullanabilirsiniz.

Visual Studio Enterprise sürümüne sahipseniz, kodunuzun yapısını ve tüm çözüm içindeki bağımlılıklarını görselleştirmek için *kod eşlemelerini* kullanabilirsiniz. Daha fazla bilgi için bkz. [kod eşlemeleriyle harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Sınıf Görünümü (Visual Basic, C#, C++)

**Sınıf görünümü** , **Çözüm Gezgini** bir parçası olarak ve ayrı bir pencere olarak gösterilir. **Sınıf görünümü** bir uygulamanın öğelerini görüntüler. Üstteki bölmede ad alanları, türler, arabirimler, numaralandırmalar ve sınıflar görüntülenir ve alt bölmede üst bölmede seçilen türe ait Üyeler görüntülenir. Bu pencereyi kullanarak, kaynak kodundaki üye tanımlarına (veya öğe çözümünüz dışında tanımlanmışsa **nesne tarayıcısı** taşıyabilirsiniz) geçebilirsiniz.

**Sınıf görünümü** öğelerini görüntülemek için bir proje derlemek zorunda değilsiniz. Projenizdeki kodu değiştirirken pencere yenilenir.

Proje düğümünü seçerek ve **Ekle** düğmesini seçerek **Yeni öğe Ekle** iletişim kutusunu açmak için projenize kod ekleyebilirsiniz. Kod ayrı bir dosyaya eklenir.

Projeniz kaynak kodu denetimine iade edildiğinde, her **sınıf görünümü** öğesi dosyanın kaynak kodu durumunu gösteren bir simge görüntüler. **Kullanıma alma,** **Iade** etme ve **en son sürümü Al** gibi ortak kaynak kodu denetim komutları, öğesi için kısayol menüsünde de mevcuttur.

### <a name="class-view-toolbar"></a>Sınıf Görünümü araç çubuğu

**Sınıf görünümü** araç çubuğu aşağıdaki komutları içerir:

|Ad|Açıklama|
|-|-|
|**Yeni klasör**|Sık kullanılan öğeleri düzenleyebileceğiniz bir sanal klasör veya alt klasör oluşturur. Bunlar, etkin çözüm (*. suo*) dosyasına kaydedilir. Kodunuzda bir öğeyi yeniden adlandırdıktan veya sildikten sonra, bir sanal klasörde hata düğümü olarak görünebilir. Bu sorunu düzeltmek için, hata düğümünü silin. Bir öğeyi yeniden adlandırdıysanız proje hiyerarşisinden klasörü yeniden klasöre taşıyabilirsiniz.|
|**Geri**|Daha önce seçilen öğeye gider.|
|**İleri**|Sonraki seçili öğeye gider.|
|**Sınıf diyagramını görüntüle** (yalnızca yönetilen kod projeleri)|**Sınıf görünümü** bir ad alanı veya tür seçtiğinizde kullanılabilir hale gelir. Bir ad alanı seçildiğinde, sınıf diyagramı içindeki tüm türleri gösterir. Bir tür seçildiğinde, sınıf diyagramı yalnızca bu türü gösterir.|

### <a name="class-view-settings"></a>Sınıf Görünümü ayarları

araç çubuğundaki **Sınıf Görünümü Ayarlar** düğmesi aşağıdaki ayarlara sahiptir:

|Ad|Açıklama|
|-|-|
|**Temel türleri göster**|Temel türler görüntülenir.|
|**Project başvurularını göster**|Project başvurular görüntülenir.|
|**Gizli türleri ve üyeleri göster**|Gizli türler ve Üyeler (istemciler tarafından kullanılmak üzere tasarlanmamıştır) açık gri metinde görüntülenir.|
|**Ortak üyeleri göster**|Ortak Üyeler görüntülenir.|
|**Korumalı üyeleri göster**|Korunan Üyeler görüntülenir.|
|**Özel üyeleri göster**|Özel Üyeler görüntülenir.|
|**Diğer üyeleri göster**|iç (veya Visual Basic arkadaş) üyeler dahil diğer üye türleri görüntülenir.|
|**Devralınan üyeleri göster**|Devralınan Üyeler görüntülenir.|

### <a name="class-view-shortcut-menu"></a>Sınıf Görünümü kısayol menüsü

**Sınıf görünümü** ' deki kısayol (veya sağ tıklama) menüsünde, seçilen proje türüne bağlı olarak aşağıdaki komutlar bulunabilir:

|Ad|Açıklama|
|-|-|
|**Tanıma Git**|Öğe açık projede tanımlanmamışsa, kaynak kodundaki veya **nesne tarayıcısı** içindeki öğenin tanımını bulur.|
|**Tanıma gözatatıon**|**Nesne tarayıcısı** seçili öğeyi görüntüler.|
|**Tüm Başvuruları Bul**|Şu anda seçili olan nesne öğesini bulur ve sonuçları **Bul sonuçları** penceresinde görüntüler.|
|**Türe Filtre Uygula** (yalnızca yönetilen kod)|Yalnızca seçilen türü veya ad alanını görüntüler. **Bul** kutusunun yanında bulunan **bul** (**X**) düğmesini seçerek filtreyi kaldırabilirsiniz.|
|**Kopyala**|Öğenin tam adını kopyalar.|
|**Alfabetik olarak Sırala**|Türleri ve üyeleri ada göre alfabetik olarak listeler.|
|**Üye türüne göre sırala**|Türlerine göre sırasıyla türler ve üyeleri listeler (Bu tür sınıfların önüne ve arabirimlerin önüne arabirimler ve yöntemlerin önündeki Yöntemler).|
|**Üye erişimine göre sırala**|Türleri ve üyeleri, genel veya özel gibi erişim türüne göre sıralar.|
|**Üye türüne göre grupla**|Türleri ve üyeleri nesne türüne göre gruplar halinde sıralar.|
|**Bildirime git** (yalnızca C++ kod)|Varsa, kaynak kodundaki tür veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa, kaynak kodundaki tür veya üyenin tanımını görüntüler.|
|**Başvuruya git**|Varsa, kaynak kodundaki tür veya üyenin başvurusunu görüntüler.|
|**Çağrı hiyerarşisini görüntüle**|Seçilen yöntemi **çağrı hiyerarşisi** penceresinde görüntüler.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Çağrı hiyerarşisi penceresi (Visual Basic, C#, C++)

**Çağrı hiyerarşisi** penceresi, belirli bir yöntemin veya özelliğin nerede çağrıldığını gösterir. Ayrıca, bu yöntemden çağrılan yöntemleri de listeler. Çağrı grafiğinin birden çok düzeyini, belirli bir kapsamdaki Yöntemler arasında arayan-çağrılan ilişkilerini gösteren bir şekilde görüntüleyebilirsiniz.

Düzenleyicide bir Yöntem (veya özellik veya Oluşturucu) seçerek **çağrı hiyerarşisi** penceresini görüntüleyebilir ve ardından kısayol menüsünde **Çağrı hiyerarşisini görüntüle** ' yi seçebilirsiniz. Ekran aşağıdaki görüntüye benzemelidir:

![Visual Studio 'de çağrı hiyerarşisi penceresi](../ide/media/multiplenodes.png)

Araç çubuğundaki açılan listeyi kullanarak hiyerarşinin kapsamını belirtebilirsiniz: çözüm, geçerli proje veya geçerli belge.

Ana bölmede, yöntemine ve yönteminden yapılan çağrılar görüntülenir ve **siteleri çağır** bölmesi seçilen çağrının konumunu görüntüler. Sanal veya soyut olan üyeler için bir **geçersiz kılma yöntemi adı** düğümü görüntülenir. Arabirim üyeleri için bir **Implements Yöntem adı** düğümü görüntülenir.

**Çağrı hiyerarşisi** penceresi, bir yöntemin olay işleyicisi olarak eklendiği veya bir temsilciye atandığı yerleri dahil olmak üzere metot grubu başvurularını bulmaz. Bu başvuruları bulmak için Tüm Başvuruları **Bul komutunu** kullanın.

Çağrı Hiyerarşisi **penceresindeki kısayol** menüsü aşağıdaki komutları içerir:

|Ad|Açıklama|
|-|-|
|**Yeni Kök Olarak Ekle**|Seçilen düğümü yeni bir kök düğüm olarak ekler.|
|**Kök Kaldır**|Seçili kök düğümü ağaç görünümü bölmesinden kaldırır.|
|**Tanıma Git**|Bir yöntemin özgün tanımına gidin.|
|**Tüm Başvuruları Bul**|Projede, seçilen yönteme yapılan tüm başvuruları bulur.|
|**Kopyala**|Seçilen düğümü kopyalar (ancak alt düğümlerini kopyalar).|
|**Yenile**|Bilgileri yeniler.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a> Nesne Tarayıcısı

Nesne **Tarayıcısı** penceresi, projeleriniz içinde kodun açıklamalarını görüntüler.

Pencerenin en üstünde yer alan açılan listeyi kullanarak görüntülemek istediğiniz bileşenleri filtreleebilirsiniz. Özel bileşenler yönetilen kod yürütülebilir dosyalarını, kitaplık derlemelerini, tür kitaplıklarını ve *.ocx dosyalarını* içerebilir. C++ özel bileşenleri eklemek mümkün değildir.

::: moniker range="vs-2017"

Özel ayarlar% *APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat* Visual Studio kullanıcı uygulaması dizinine kaydedilir.

::: moniker-end

::: moniker range=">=vs-2019"

Özel ayarlar% *APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat* Visual Studio kullanıcı uygulaması dizinine kaydedilir.

::: moniker-end

Object Browser'ın sol **bölmesinde derlemeler** gösterilir. Derlemeleri içerilen ad alanlarını görüntülemek için genişletebilirsiniz ve ardından ad alanlarını, içerecekleri türleri görüntüleyecek şekilde genişletebilirsiniz. Bir tür seçerek sağ bölmede üyeleri (özellikler ve yöntemler gibi) listelenir. Sağ alt bölmede seçili öğe hakkında ayrıntılı bilgiler görüntülenir.

Pencerenin üst kısmında yer alan Arama kutusunu **kullanarak belirli** bir öğeyi arayabilirsiniz. Aramalar büyük/büyük/büyük harfe duyarlı değildir. Arama sonuçları sol bölmede görüntülenir. Bir aramanın temizlemek için Arama **kutusunun yanındaki** AramaYı Temizle (**X**) **düğmesini** seçin.

Object **Browser,** yapmış olduğu seçimleri takip eder ve araç çubuğundaki İleri  ve Geri düğmelerini kullanarak **seçimleriniz arasında** gezinebilirsiniz.

Bir öğeyi **(derleme,** ad alanı, tür veya üye) seçerek ve araç çubuğunda Başvuru Ekle  düğmesini seçerek açık bir çözüme derleme başvurusu eklemek için Object Browser'ı kullanabilirsiniz.

### <a name="object-browser-settings"></a>Nesne Tarayıcısı ayarları

Araç **çubuğundaki Object Browser Ayarlar** düğmesini kullanarak aşağıdaki görünümlerden birini belirtebilirsiniz:

|Ad|Açıklama|
|-|-|
|**Ad Alanlarını Görüntüleme**|Sol bölmede fiziksel kapsayıcılar yerine ad alanlarını görüntüler. Birden çok fiziksel kapsayıcıda depolanan ad alanları birleştirilir.|
|**Kapsayıcıları Görüntüleme**|Sol bölmede ad alanları yerine fiziksel kapsayıcıları görüntüler. **Ad Alanlarını Görüntüle ve** **Kapsayıcıları Görüntüle,** birbirini dışlar.|
|**Temel Türleri Göster**|Temel türleri görüntüler.|
|**Gizli Türleri ve Üyeleri Gösterme**|Gizli türleri ve üyeleri (istemciler tarafından kullanılmak üzere değil) açık gri metin olarak görüntüler.|
|**Genel Üyeleri Göster**|Genel üyeleri görüntüler.|
|**Korumalı Üyeleri Göster**|Korumalı üyeleri görüntüler.|
|**Özel Üyeleri Göster**|Özel üyeleri görüntüler.|
|**Diğer Üyeleri Göster**|dahili (veya şirket içi arkadaş) üyeler de dahil olmak üzere diğer üye Visual Basic görüntüler.|
|**Devralınan Üyeleri Göster**|Devralınan üyeleri görüntüler.|
|**Uzantı Yöntemlerini Göster**|Uzantı yöntemlerini görüntüler.|

### <a name="object-browser-shortcut-menu-commands"></a>Nesne Tarayıcısı kısayol menü komutları

Object **Browser'daki** kısayol (veya sağ tıklama) menüsü, seçilen öğenin türüne bağlı olarak aşağıdaki komutları içerebilir:

|Ad|Açıklama|
|-|-|
|**Tanıma Gözat**|Seçilen öğenin birincil düğümünü gösterir.|
|**Tüm Başvuruları Bul**|Seçili olan nesne öğesini bulur ve sonuçları Sonuçları Bul **penceresinde** görüntüler.|
|**Türe Göre Filtrele**|Yalnızca seçilen türü veya ad alanını görüntüler. Arama Temizle düğmesini seçerek **filtreyi kaldırabilirsiniz.**|
|**Kopyala**|Öğenin tam adını kopyalar.|
|**Kaldır**|Kapsam bir özel bileşen kümesiyse, seçilen bileşeni kapsamdan kaldırır.|
|**Alfabetik Olarak Sırala**|Türleri ve üyeleri adlarına göre alfabetik olarak listeler.|
|**Nesne Türüne Göre Sırala**|Türleri ve üyeleri türe göre sırasıyla listeler (sınıflar arabirimlerden önce, arabirimler temsilcilerden önce ve yöntemler özelliklerden önce gelecek şekilde).|
|**Nesne Erişimine Göre Sırala**|Genel veya özel gibi erişim türüne göre türleri ve üyeleri listeler.|
|**Nesne Türüne Göre Grupla**|Türleri ve üyeleri nesne türüne göre gruplara sıralar.|
|**Bildirime Git** (yalnızca C++ projeleri)|Varsa kaynak kodda türün veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa kaynak kodda türün veya üyenin tanımını görüntüler.|
|**Başvuruya Git**|Varsa kaynak kodda türe veya üyeye bir başvuru görüntüler.|
|**Çağrı Hiyerarşisini Görüntüleme**|Seçilen yöntemi Çağrı **Hiyerarşisi penceresinde** görüntüler.|

## <a name="code-definition-window-c"></a>Kod Tanım penceresi (C++)

Kod **Tanımı penceresi,** etkin projede seçili bir C++ türünün veya üyesinin tanımını görüntüler. Tür veya üye, kod düzenleyicisinde veya bir kod görünümü penceresinde seçilebilir.

Bu pencere salt okunur olsa da, içinde kesme noktaları veya yer işaretleri ayarlayın. Görüntülenen tanımı değiştirmek için kısayol **menüsünde Tanımı Düzenle'yi** seçin. Bu işlem kaynak dosyayı kod düzenleyicisinde açar ve ekleme noktasını tanımın başladığı satıra taşır.

> [!NOTE]
> 2015'Visual Studio başlayarak, Kod **Tanımı** penceresi yalnızca C++ koduyla kullanılabilir.

### <a name="code-definition-shortcut-menu"></a>Kod Tanımı kısayol menüsü

Kod Tanımı penceresindeki kısayol (veya sağ **tıklama)** menüsü aşağıdaki komutları içerebilir:

|Ad|Açıklama|
|-|-|
|**Hızlı Eylemler ve Yeniden Düzenlemeler**||
|**Yeniden Adlandır**||
|**içerme dosyaları Graph oluştur**||
|**Tanıma Göz At**||
|**Tanıma Git**|Tanımı (veya kısmi sınıflar için tanımları) bulur ve **sonuçları bul** penceresinde görüntüler.|
|**Bildirime git**||
|**Tüm Başvuruları Bul**|Çözümdeki türe veya üyeye başvuruları bulur.|
|**Çağrı hiyerarşisini görüntüle**|Yöntemi **çağrı hiyerarşisi** penceresinde görüntüler.|
|**Üst bilgi/kod dosyası değiştirme**||
|**Testleri Çalıştır**|Projede birim testleri varsa, seçilen kod için testleri çalıştırır.|
|**Hata ayıklama testleri**||
|**Ilı**|Bir kesme noktası (veya izleme noktası) ekler.|
|**Imlece kadar Çalıştır**|Programı hata ayıklama modunda imleç konumuna çalıştırır.|
|**Kod Parçacığı**||
|**Kes**, **Kopyala**, **Yapıştır**||
|**Ek Açıklama**||
|**Anahat Oluşturma**|Standart ana hat komutları.|
|**İşlemini**||
|**Tanımı Düzenle**|Ekleme noktasını kod penceresindeki tanıma gider.|
|**Kodlama seçin**|Dosya için bir kodlama ayarlayabilmeniz için **kodlama** penceresini açar.|

## <a name="document-outline-window"></a>Belge Anahattı penceresi

**belge anahattı** penceresini, bir XAML sayfası veya Windows Form tasarımcısı gibi tasarımcı görünümleri ile veya HTML sayfalarıyla birlikte kullanabilirsiniz. Bu pencere, öğeleri ağaç görünümünde görüntüler, böylece formun veya sayfanın mantıksal yapısını görüntüleyebilir ve derin gömülü veya gizli denetimleri bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıf Görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md)
