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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: cce4607a1721927681be35b984d08b74aa16f581
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094002"
---
# <a name="view-the-structure-of-code-by-using-different-tool-windows"></a>Farklı araç pencerelerini kullanarak kodun yapısını görüntüleme

sınıflarını ve üyelerini Visual Studio , Çağrı Hiyerarşisi, Nesne Tarayıcısı ve Sınıf Görünümü Kod Tanımı  **(yalnızca C++)** gibi çeşitli araç pencerelerini kullanarak sınıflarını ve üyelerini inceleyebilirsiniz. Bu araç pencereleri projelerde, .NET Visual Studio, COM bileşenlerinde, dinamik bağlantı kitaplıklarında (DLL) ve tür kitaplıklarında (TLB) kodu inceler.

Ayrıca, **Çözüm Gezgini** türlerine ve üyelerine göz atmak, semboller aramak, bir yöntemin çağrı hiyerarşisini görüntülemek, sembol başvurularını bulmak ve daha fazlasını birden çok araç pencereleri arasında geçiş yapmak zorunda kalmadan kullanabilirsiniz.

Visual Studio Enterprise sürümünüz varsa, kod haritalarını  kullanarak kodunuzun yapısını ve bağımlılıklarını çözümün tamamına görselleştirebilirsiniz. Daha fazla bilgi için [bkz. Kod eşlemeleri ile bağımlılıkları eşleme.](../modeling/map-dependencies-across-your-solutions.md)

## <a name="class-view-visual-basic-c-c"></a>Sınıf Görünümü (Visual Basic, C#, C++)

**Sınıf Görünümü** ayrı bir pencere **Çözüm Gezgini** olarak gösterilir. **Sınıf Görünümü** uygulamanın öğelerini görüntüler. Üst bölmede ad alanları, türler, arabirimler, numaralar ve sınıflar, alt bölme ise üst bölmede seçilen türe ait olan üyeleri görüntüler. Bu pencereyi kullanarak, kaynak kodda (veya öğe çözüm dışında tanımlanmışsa **Nesne** Tarayıcısı'nın içinde) üye tanımları'ne geçebilirsiniz.

bir projeyi derlemeniz, proje öğelerini içinde görüntülemek için **Sınıf Görünümü.** Projenizin kodunu değiştirerek pencere yenilenir.

Proje düğümünü ve Ekle düğmesini seçerek projenize kod ekleyebilir **ve** Yeni Öğe Ekle **iletişim kutusunu** açabilirsiniz. Kod ayrı bir dosyaya eklenir.

Projeniz kaynak kodu denetimine iade edilirse, **her Sınıf Görünümü** öğesi dosyanın kaynak kodu durumunu gösteren bir simge görüntüler. Öğenin kısayol menüsünde **Check Out**, **Check In** ve Get **Latest Version** gibi yaygın kaynak kodu denetimi komutları da kullanılabilir.

### <a name="class-view-toolbar"></a>Sınıf Görünümü araç çubuğu

Araç **Sınıf Görünümü** aşağıdaki komutları içerir:

|Ad|Açıklama|
|-|-|
|**Yeni Klasör**|Sık kullanılan öğeleri düzenleyecek bir sanal klasör veya alt klasör oluşturur. Bunlar etkin çözüm (*.suo*) dosyasına kaydedilir. Kodundaki bir öğeyi yeniden adlandırdıktan veya sildikten sonra, bu öğe bir sanal klasörde hata düğümü olarak görünebilir. Bu sorunu düzeltmek için hata düğümünü silin. Bir öğeyi yeniden adlandırdıysanız, öğeyi proje hiyerarşisinde klasöre yeniden taşıyabilirsiniz.|
|**Geri**|Daha önce seçilen öğeye gidin.|
|**İleri**|Bir sonraki seçilen öğeye gidin.|
|**Sınıf Diyagramını Görüntüle** (yalnızca yönetilen kod projeleri)|bir ad alanı seçerek veya bir ad alanına yazarak **Sınıf Görünümü.** Bir ad alanı seçildiğinde, sınıf diyagramı bu ad alanının tüm türlerini gösterir. Bir tür seçildiğinde, sınıf diyagramı yalnızca bu türü gösterir.|

### <a name="class-view-settings"></a>Sınıf Görünümü ayarları

Araç **Sınıf Görünümü Ayarlar** düğmesi aşağıdaki ayarlara sahip:

|Ad|Açıklama|
|-|-|
|**Temel Türleri Göster**|Temel türler görüntülenir.|
|**Project Başvurularını Göster**|Project başvurular görüntülenir.|
|**Gizli Türleri ve Üyeleri Gösterme**|Gizli türler ve üyeler (istemciler tarafından kullanılmak üzere değildir) açık gri metinlerde görüntülenir.|
|**Genel Üyeleri Göster**|Genel üyeler görüntülenir.|
|**Korumalı Üyeleri Göster**|Korumalı üyeler görüntülenir.|
|**Özel Üyeleri Göster**|Özel üyeler görüntülenir.|
|**Diğer Üyeleri Göster**|Dahili (veya Şirket içi arkadaş) üyeler de dahil olmak üzere Visual Basic görüntülenir.|
|**Devralınan Üyeleri Göster**|Devralınan üyeler görüntülenir.|

### <a name="class-view-shortcut-menu"></a>Sınıf Görünümü kısayol menüsü

Sınıf Görünümü kısayolu (veya sağ  tıklama) menüsü, seçilen projenin türüne bağlı olarak aşağıdaki komutları içerebilir:

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
|**Üye Türüne Göre Grupla**|Türleri ve üyeleri nesne türüne göre gruplar halinde sıralar.|
|**Bildirime Git** (yalnızca C++ kodu)|Varsa kaynak kodda türün veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa kaynak kodda türün veya üyenin tanımını görüntüler.|
|**Başvuruya Git**|Varsa kaynak kodda türe veya üyeye bir başvuru görüntüler.|
|**Çağrı Hiyerarşisini Görüntüleme**|Seçilen yöntemi Çağrı **Hiyerarşisi penceresinde** görüntüler.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Çağrı Hiyerarşisi penceresi (Visual Basic, C#, C++)

Çağrı **Hiyerarşisi** penceresi, belirli bir yöntemin veya özelliğin çağrıldı olduğu yeri gösterir. Ayrıca, bu yöntemden çağrılan yöntemleri listeler. Belirtilen kapsamda yöntemler arasındaki çağıran-çağrılan ilişkilerini gösteren birden çok çağrı grafı düzeyi görüntüebilirsiniz.

Düzenleyicide bir **yöntem** (veya özellik veya oluşturucu) seçerek ve ardından kısayol menüsünde Çağrı Hiyerarşisini Görüntüle'yi seçerek Çağrı Hiyerarşisi **penceresini** görüntüebilirsiniz. Ekran aşağıdaki görüntüye benzer:

![Visual Studio'de Hiyerarşiyi Çağırma penceresi](../ide/media/multiplenodes.png)

Araç çubuğundaki açılan listeyi kullanarak hiyerarşinin kapsamını belirtebilirsiniz: çözüm, geçerli proje veya geçerli belge.

Ana bölmede yöntemine gelen ve yöntemden yapılan çağrılar, **Çağrı Siteleri** bölmesi ise seçilen çağrının konumunu görüntüler. Sanal veya soyut üyeler için bir **Overrides yöntem adı** düğümü görünür. Arabirim üyeleri için **Implements yöntem adı düğümü** görünür.

Çağrı **Hiyerarşisi** penceresi, bir yöntemin olay işleyicisi olarak ekli olduğu veya bir temsilciye atandığı yerleri içeren yöntem grubu başvurularını bulmaz. Bu başvuruları bulmak için Tüm Başvuruları **Bul komutunu** kullanın.

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

Özel ayarlar% *APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat* kullanıcı Visual Studio dizinine kaydedilir.

::: moniker-end

Object Browser'ın sol **bölmesinde derlemeler** gösterilir. Derlemeleri içerilen ad alanlarını görüntülemek için genişletebilirsiniz ve ardından içerilen türleri görüntülemek için ad alanlarını genişletebilirsiniz. Bir tür seçerek sağ bölmede üyeleri (özellikler ve yöntemler gibi) listelenir. Sağ alt bölmede seçili öğe hakkında ayrıntılı bilgiler görüntülenir.

Pencerenin üst kısmında yer alan Arama kutusunu **kullanarak belirli** bir öğeyi arayabilirsiniz. Aramalar büyük/büyük/büyük harfe duyarlı değildir. Arama sonuçları sol bölmede görüntülenir. Bir aramanın temizlemek için Arama **kutusunun yanındaki** AramaYı Temizle (**X**) **düğmesini** seçin.

Object **Browser,** yapmış olduğu seçimleri takip eder ve araç çubuğundaki İleri  ve Geri düğmelerini kullanarak **seçimleriniz arasında** gezinebilirsiniz.

Bir öğe **(derleme,** ad alanı, tür veya üye) seçerek ve araç çubuğunda Başvuru Ekle  düğmesini seçerek açık bir çözüme derleme başvurusu eklemek için Object Browser'ı kullanabilirsiniz.

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
|**Diğer Üyeleri Göster**|Dahili (veya şirket içi arkadaş) üyeler de dahil olmak üzere diğer üye Visual Basic görüntüler.|
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
