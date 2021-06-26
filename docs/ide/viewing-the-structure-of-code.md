---
title: Kod yapısını görüntülemek için araç pencerelerini kullanma
description: Sınıf Görünümü, Çağrı Hiyerarşisi, Nesne Tarayıcısı ve Kod Tanımı (yalnızca C++) araç pencerelerini kullanarak Visual Studio.
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
ms.workload:
- multiple
ms.openlocfilehash: 41c11025e22c1288387862fa138b35efbbca8557
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924961"
---
# <a name="view-the-structure-of-code-by-using-different-tool-windows"></a>Farklı araç pencerelerini kullanarak kodun yapısını görüntüleme

sınıflarını ve üyelerini Visual Studio , Çağrı Hiyerarşisi, Nesne Tarayıcısı ve Sınıf Görünümü Kod Tanımı  **(yalnızca C++)** gibi çeşitli araç pencerelerini kullanarak sınıflarını ve üyelerini inceleyebilirsiniz. Bu araç pencereleri projelerde, .NET Visual Studio, COM bileşenlerinde, dinamik bağlantı kitaplıklarında (DLL) ve tür kitaplıklarında (TLB) kodu inceler.

Ayrıca, **Çözüm Gezgini** türlerine ve üyelerine göz atmak, semboller aramak, bir yöntemin çağrı hiyerarşisini görüntülemek, sembol başvurularını bulmak ve daha fazlasını birden çok araç pencereleri arasında geçiş yapmak zorunda kalmadan kullanabilirsiniz.

Visual Studio Enterprise sürümünüz varsa, kod *haritalarını* kullanarak kodunuzun yapısını ve bağımlılıklarını çözümün tamamına görselleştirebilirsiniz. Daha fazla bilgi için [bkz. Kod eşlemeleri ile bağımlılıkları eşleme.](../modeling/map-dependencies-across-your-solutions.md)

## <a name="class-view-visual-basic-c-c"></a>Sınıf Görünümü (Visual Basic, C#, C++)

**Sınıf Görünümü** ayrı bir pencere **Çözüm Gezgini** olarak gösterilir. **Sınıf Görünümü** uygulamanın öğelerini görüntüler. Üst bölmede ad alanları, türler, arabirimler, numaralar ve sınıflar, alt bölme ise üst bölmede seçilen türe ait olan üyeleri görüntüler. Bu pencereyi kullanarak kaynak kodda (veya öğe çözüm dışında tanımlanmışsa **Nesne** Tarayıcısı'nın içinde) üye tanımları'ne geçebilirsiniz.

Bir projeyi derlemek için proje öğelerini **Sınıf Görünümü.** Projenizin kodunu değiştirerek pencere yenilenir.

Proje düğümünü ve Ekle düğmesini seçerek projenize kod ekleyebilir **ve** Yeni Öğe Ekle **iletişim kutusunu** açabilirsiniz. Kod ayrı bir dosyaya eklenir.

Projeniz kaynak kodu denetimine iade edilirse, **her Sınıf Görünümü** öğesi dosyanın kaynak kodu durumunu gösteren bir simge görüntüler. Öğenin kısayol menüsünde **Check Out**, **Check In** ve Get **Latest Version** gibi yaygın kaynak kodu denetimi komutları da kullanılabilir.

### <a name="class-view-toolbar"></a>Sınıf Görünümü araç çubuğu

Araç **Sınıf Görünümü** aşağıdaki komutları içerir:

|Ad|Açıklama|
|-|-|
|**Yeni Klasör**|Sık kullanılan öğeleri düzenleyecek bir sanal klasör veya alt klasör oluşturur. Bunlar etkin çözüm (*.suo*) dosyasına kaydedilir. Kodundaki bir öğeyi yeniden adlandırdıktan veya sildikten sonra, bu öğe bir sanal klasörde hata düğümü olarak görünebilir. Bu sorunu düzeltmek için hata düğümünü silin. Bir öğeyi yeniden adlandırdıysanız, öğeyi proje hiyerarşisinde klasöre yeniden taşıyabilirsiniz.|
|**Geri**|Daha önce seçilen öğeye gidin.|
|**İleri**|Bir sonraki seçilen öğeye gidin.|
|**Sınıf Diyagramını Görüntüle** (yalnızca yönetilen kod projeleri)|bir ad alanı seçerek veya içinde bir ad alanı **Sınıf Görünümü.** Bir ad alanı seçildiğinde, sınıf diyagramı bu ad alanının tüm türlerini gösterir. Bir tür seçildiğinde, sınıf diyagramı yalnızca bu türü gösterir.|

### <a name="class-view-settings"></a>Sınıf Görünümü ayarları

Araç **Sınıf Görünümü Ayarlar** düğmesi aşağıdaki ayarlara sahip:

|Ad|Açıklama|
|-|-|
|**Temel Türleri Göster**|Temel türler görüntülenir.|
|**Proje Başvurularını Göster**|Proje başvuruları görüntülenir.|
|**Gizli Türleri ve Üyeleri Gösterme**|Gizli türler ve üyeler (istemciler tarafından kullanılmak üzere değildir) açık gri metinlerde görüntülenir.|
|**Genel Üyeleri Göster**|Genel üyeler görüntülenir.|
|**Korumalı Üyeleri Göster**|Korumalı üyeler görüntülenir.|
|**Özel Üyeleri Göster**|Özel üyeler görüntülenir.|
|**Diğer Üyeleri Göster**|Dahili (veya Şirket içi Arkadaş) üyeler de dahil olmak üzere diğer üye Visual Basic görüntülenir.|
|**Devralınan Üyeleri Göster**|Devralınan üyeler görüntülenir.|

### <a name="class-view-shortcut-menu"></a>Sınıf Görünümü kısayol menüsü

Seçilen projenin türüne bağlı olarak, **Sınıf Görünümü** kısayol (veya sağ tıklama) menüsü aşağıdaki komutları içerebilir:

|Ad|Açıklama|
|-|-|
|**Tanıma Git**|Öğesi açık projede tanımlanmamışsa kaynak kodda veya **Object Browser'da** öğesinin tanımını bulur.|
|**Tanıma Gözat**|Object Browser'da seçili **öğeyi görüntüler.**|
|**Tüm Başvuruları Bul**|Seçili olan nesne öğesini bulur ve sonuçları Sonuçları Bul **penceresinde** görüntüler.|
|**Türe Göre Filtrele** (yalnızca yönetilen kod)|Yalnızca seçilen türü veya ad alanını görüntüler. Bul kutusunun yanındaki Bul (**X**) **düğmesini** seçerek filtreyi **kaldırabilirsiniz.**|
|**Kopyala**|Öğenin tam adını kopyalar.|
|**Alfabetik Olarak Sırala**|Türleri ve üyeleri adlarına göre alfabetik olarak listeler.|
|**Üye Türüne Göre Sırala**|Türleri ve üyeleri türe göre sırasıyla listeler (sınıflar arabirimlerden önce, arabirimler temsilcilerden önce ve yöntemler özelliklerden önce gelecek şekilde).|
|**Üye Erişimine Göre Sırala**|Genel veya özel gibi erişim türüne göre türleri ve üyeleri listeler.|
|**Üye Türüne Göre Grupla**|Türleri ve üyeleri nesne türüne göre gruplara sıralar.|
|**Bildirime Git** (yalnızca C++ kodu)|Varsa kaynak kodda türün veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa kaynak kodda türün veya üyenin tanımını görüntüler.|
|**Başvuruya Git**|Varsa kaynak kodda türe veya üyeye bir başvuru görüntüler.|
|**Çağrı Hiyerarşisini Görüntüleme**|Seçilen yöntemi Çağrı **Hiyerarşisi penceresinde** görüntüler.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Çağrı Hiyerarşisi penceresi (Visual Basic, C#, C++)

Çağrı **Hiyerarşisi** penceresi, belirli bir yöntemin veya özelliğin çağrıldı olduğu yeri gösterir. Ayrıca, bu yöntemden çağrılan yöntemleri listeler. Belirtilen kapsamda yöntemler arasındaki çağıran-çağrılan ilişkilerini gösteren birden çok çağrı grafı düzeyi görüntüebilirsiniz.

Düzenleyicide **bir** yöntem (veya özellik veya oluşturucu) ve ardından kısayol menüsünde Çağrı Hiyerarşisini Görüntüle'yi seçerek Çağrı Hiyerarşisi **penceresini** görüntüebilirsiniz. Ekran aşağıdaki görüntüye benzer:

![Visual Studio'de Hiyerarşiyi Çağırma penceresi](../ide/media/multiplenodes.png)

Araç çubuğundaki açılan listeyi kullanarak hiyerarşinin kapsamını belirtebilirsiniz: çözüm, geçerli proje veya geçerli belge.

Ana bölmede yöntemine gelen ve yöntemden yapılan çağrılar, **Çağrı Siteleri** bölmesi ise seçilen çağrının konumunu görüntüler. Sanal veya soyut üyeler için bir **Overrides yöntem adı** düğümü görünür. Arabirim üyeleri için **Implements yöntem adı düğümü** görünür.

Çağrı **Hiyerarşisi** penceresi, bir yöntemin olay işleyicisi olarak ekli olduğu veya bir temsilciye atandığı yerleri içeren yöntem grubu başvurularını bulmaz. Bu başvuruları bulmak için, **tüm başvuruları bul** komutunu kullanın.

**Çağrı hiyerarşisi** penceresindeki kısayol menüsü aşağıdaki komutları içerir:

|Ad|Açıklama|
|-|-|
|**Yeni kök olarak ekle**|Seçili düğümü yeni bir kök düğüm olarak ekler.|
|**Kökü Kaldır**|Seçili kök düğümü ağaç görünümü bölmesinden kaldırır.|
|**Tanıma Git**|Bir yöntemin orijinal tanımına gider.|
|**Tüm Başvuruları Bul**|Seçili yönteme ait tüm başvuruları projede bulur.|
|**Kopyala**|Seçili düğümü kopyalar (alt düğümleri değil).|
|**Yenile**|Bilgileri yeniler.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a> Nesne Tarayıcısı

**Nesne tarayıcısı** penceresinde, projelerinizdeki kodun açıklamaları görüntülenir.

Pencerenin üst kısmındaki açılan listeyi kullanarak görüntülemek istediğiniz bileşenlere filtre uygulayabilirsiniz. Özel bileşenler, yönetilen kod yürütülebilir dosyaları, kitaplık derlemeleri, tür kitaplıkları ve *. ocx* dosyalarını içerebilir. C++ özel bileşenleri eklemek mümkün değildir.

::: moniker range="vs-2017"

Özel ayarlar, Visual Studio Kullanıcı uygulama dizininde, *%AppData%\microsoft\visualstudio\15.0\ObjBrowEX.dat* dizinine kaydedilir.

::: moniker-end

::: moniker range=">=vs-2019"

Özel ayarlar, Visual Studio Kullanıcı uygulama dizininde, *%AppData%\microsoft\visualstudio\16.0\ObjBrowEX.dat* dizinine kaydedilir.

::: moniker-end

**Nesne tarayıcısı** sol bölmesi derlemeleri gösterir. Derlemeleri içerdikleri ad alanlarını görüntüleyecek şekilde genişletebilir ve ardından içerdikleri türleri göstermek için ad alanlarını genişletebilirsiniz. Bir tür seçtiğinizde, üyeleri (Özellikler ve yöntemler gibi) sağ bölmede listelenir. Sağ alt bölmede seçili öğeyle ilgili ayrıntılı bilgiler görüntülenir.

Pencerenin üst kısmındaki **arama** kutusunu kullanarak belirli bir öğe için arama yapabilirsiniz. Aramalar büyük/küçük harfe duyarlıdır. Arama sonuçları sol bölmede görüntülenir. Bir aramayı temizlemek için **arama** kutusunun yanındaki **Aramayı Temizle** (**X**) düğmesini seçin.

**Nesne tarayıcısı** yaptığınız seçimleri izler ve araç çubuğundaki **İleri** ve **geri** düğmelerini kullanarak seçimleriniz arasında gezinebilirsiniz.

Bir öğeyi (derleme, ad alanı, tür veya üye) seçerek ve araç çubuğundaki **Başvuru Ekle** düğmesini seçerek açık bir çözüme derleme başvurusu eklemek için **nesne tarayıcısı** kullanabilirsiniz.

### <a name="object-browser-settings"></a>Nesne Tarayıcısı ayarları

Araç çubuğundaki **nesne tarayıcısı ayarları** düğmesini kullanarak, aşağıdaki görünümlerden birini belirtebilirsiniz:

|Ad|Açıklama|
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

|Ad|Açıklama|
|-|-|
|**Tanıma gözatatıon**|Seçili öğenin birincil düğümünü gösterir.|
|**Tüm Başvuruları Bul**|Şu anda seçili olan nesne öğesini bulur ve sonuçları **Bul sonuçları** penceresinde görüntüler.|
|**Türe göre filtrele**|Yalnızca seçilen türü veya ad alanını görüntüler. **Aramayı Temizle** düğmesini seçerek filtreyi kaldırabilirsiniz.|
|**Kopyala**|Öğenin tam adını kopyalar.|
|**Kaldır**|Kapsam özel bir bileşen kümesi ise, seçili bileşeni kapsamdan kaldırır.|
|**Alfabetik olarak Sırala**|Türleri ve üyeleri ada göre alfabetik olarak listeler.|
|**Nesne türüne göre sırala**|Türlerine göre sırasıyla türler ve üyeleri listeler (Bu tür sınıfların önüne ve arabirimlerin önüne arabirimler ve yöntemlerin önündeki Yöntemler).|
|**Nesne erişimine göre sırala**|Türleri ve üyeleri, genel veya özel gibi erişim türüne göre sıralar.|
|**Nesne türüne göre Gruplandır**|Türleri ve üyeleri nesne türüne göre gruplar halinde sıralar.|
|**Bildirime git** (yalnızca C++ projeleri)|Varsa, kaynak kodundaki tür veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa, kaynak kodundaki tür veya üyenin tanımını görüntüler.|
|**Başvuruya git**|Varsa, kaynak kodundaki tür veya üyenin başvurusunu görüntüler.|
|**Çağrı hiyerarşisini görüntüle**|Seçilen yöntemi **çağrı hiyerarşisi** penceresinde görüntüler.|

## <a name="code-definition-window-c"></a>Kod Tanım penceresi (C++)

**Kod tanımı** penceresi, etkin projedeki seçili bir C++ türünün veya üyesinin tanımını görüntüler. Tür veya üye kod düzenleyicisinde veya bir kod görünümü penceresinde seçilebilir.

Bu pencere salt okunurdur, ancak içinde kesme noktaları veya yer işaretleri ayarlayabilirsiniz. Görüntülenmiş tanımı değiştirmek için kısayol menüsünde **tanımı Düzenle** ' yi seçin. Bu, kaynak dosyayı kod düzenleyicisinde açar ve ekleme noktasını tanımın başladığı satıra taşıdır.

> [!NOTE]
> Visual Studio 2015 ' den başlayarak, **kod tanımı** penceresi yalnızca C++ kodu ile kullanılabilir.

### <a name="code-definition-shortcut-menu"></a>Kod tanımı kısayol menüsü

**Kod tanımı** penceresindeki kısayol (veya sağ tıklama) menüsünde aşağıdaki komutlar bulunabilir:

|Ad|Açıklama|
|-|-|
|**Hızlı Eylemler ve Yeniden Düzenlemeler**||
|**Yeniden Adlandır**||
|**Ekleme dosyalarının grafiğini oluştur**||
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

**Belge Anahattı** penceresini, bir XAML sayfası veya bir Windows form TASARıMCıSı veya HTML sayfaları gibi tasarımcı görünümleriyle birlikte kullanabilirsiniz. Bu pencere, öğeleri ağaç görünümünde görüntüler, böylece formun veya sayfanın mantıksal yapısını görüntüleyebilir ve derin gömülü veya gizli denetimleri bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıf Görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md)
