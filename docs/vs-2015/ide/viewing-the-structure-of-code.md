---
title: Kod yapısını görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.documentoutline.window
- vs.objectbrowser
- vs.classview
- VS.CodeDefinitionView
- VS.CodeDefinitionWindow
- vs.componentpicker
- vs.callbrowser
helpviewer_keywords:
- document outline window.
- Visual Studio, object browser
- Visual Studio, code definition window
- call hierarchy
- Visual Studio, document outline window
- code definition window
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
ms.assetid: e6064f58-5ad9-4f05-8c3f-12e994b6583f
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a860fbb88bb15786fad5fdf277f8f65b245056b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545021"
---
# <a name="viewing-the-structure-of-code"></a>Kod Yapısını Görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio projelerindeki nesneleri ve üyeleri ve .NET Framework bileşenleri, COM bileşenleri, dinamik bağlantı kitaplıkları (DLL) ve tür kitaplıkları (TLB) içindeki nesneleri ve üyeleri inceleyebilirsiniz.

 Bu belgenin aşağıdaki bölümleri, farklı kod yapısı pencerelerini anlatmaktadır.

 [Sınıf Görünümü (Visual Basic, C#, C++)](#BKMK_ClassView)

 [Çağrı hiyerarşisi (Visual Basic, C#, C++)](#BKMK_CallHierarchy)

 [Nesne Tarayıcısı](#BKMK_ObjectBrowser)

 [Kod tanımı penceresi (C#, C++)](#BKMK_CodeDefinition)

 Ayrıca, projelerinizdeki türlere ve üyelere gözatıp, sembolleri aramak, yöntemin Çağrı hiyerarşisini görüntülemek, sembol başvurularını bulmak ve daha fazlasını yapmak için, daha önce listelenen birden çok araç penceresi arasında geçiş yapmak zorunda kalmadan **Çözüm Gezgini** de kullanabilirsiniz.

 Visual Studio Enterprise sahipseniz, kodunuzun yapısını ve onun tüm çözüm genelinde bağımlılıklarını görselleştirmek için kod eşlemelerini kullanabilir ve ilgilendiğiniz kodun bölümlerine gidebilirsiniz. Daha fazla bilgi için bkz. [çözümlerinizin genelinde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

> [!NOTE]
> Visual Studio sürümü ve kullandığınız ayarlar IDE 'deki özellikleri etkileyebilir. Bu konu başlığı altında açıklananlardan farklı olabilirler.

## <a name="class-view-visual-basic-c-c"></a><a name="BKMK_ClassView"></a> Sınıf Görünümü (Visual Basic, C#, C++)
 **Sınıf görünümü** , **Çözüm Gezgini** bir parçası olarak ve ayrı bir pencerede gösterilir. **Sınıf görünümü** pencere, bir uygulamanın öğelerini görüntüler. Üstteki bölmede ad alanları, türler, arabirimler, numaralandırmalar ve sınıflar görüntülenir ve alt bölmede üst bölmede seçilen türe ait Üyeler görüntülenir. Bu pencereyi kullanarak, kaynak kodundaki üye tanımlarına (veya öğe çözümünüz dışında tanımlanmışsa **nesne tarayıcısı** taşıyabilirsiniz) geçebilirsiniz.

 **Sınıf görünümü**öğelerini görüntülemek için bir proje derlemek zorunda değilsiniz. Projenizdeki kodu değiştirirken pencere yenilenir.

 Proje düğümünü seçerek ve **Ekle** düğmesini seçerek **Yeni öğe Ekle** iletişim kutusunu açmak için projenize kod ekleyebilirsiniz. Kod ayrı bir dosyaya eklenir.

 Projeniz kaynak kodu denetimine iade edildiğinde, her **sınıf görünümü** öğesi dosyanın kaynak kodu durumunu gösteren bir simge görüntüler. **Kullanıma alma,** **Iade**etme ve **en son sürümü Al** gibi ortak kaynak kodu denetim komutları, öğesi için kısayol menüsünde de mevcuttur.

### <a name="class-view-toolbar"></a>Sınıf Görünümü araç çubuğu
 Sınıf Görünümü araç çubuğu aşağıdaki komutları içerir.

|Komut|Açıklama|
|-|-|
|**Yeni klasör**|Sık kullanılan öğeleri düzenleyebileceğiniz bir sanal klasör veya alt klasör oluşturur. Bunlar, etkin çözüm (. suo) dosyasına kaydedilir. Kodunuzda bir öğeyi yeniden adlandırdıktan veya sildikten sonra, bir sanal klasörde hata düğümü olarak görünebilir. Bu sorunu düzeltmek için, hata düğümünü silin. Bir öğeyi yeniden adlandırdıysanız proje hiyerarşisinden klasörü yeniden klasöre taşıyabilirsiniz.|
|**Geri**|Daha önce seçilen öğeye gider.|
|**İleri**|Sonraki seçili öğeye gider.|
|**Sınıf diyagramını görüntüle** (yalnızca yönetilen kod projeleri)|**Sınıf görünümü**bir ad alanı veya tür seçtiğinizde kullanılabilir hale gelir. Bir ad alanı seçildiğinde, sınıf diyagramı içindeki tüm türleri gösterir. Bir tür seçildiğinde, sınıf diyagramı yalnızca bu türü gösterir.|

### <a name="class-view-settings"></a>Sınıf Görünümü ayarları
 Araç çubuğundaki **Sınıf Görünümü ayarları** düğmesi aşağıdaki ayarlara sahiptir.

|Ad|Açıklama|
|-|-|
|**Temel türleri göster**|Temel türler görüntülenir.|
|**Türetilmiş türleri göster**|Türetilmiş türler görüntülenir.|
|**Gizli türleri ve üyeleri göster**|Gizli türler ve Üyeler (istemciler tarafından kullanılmak üzere tasarlanmamıştır) açık gri metinde görüntülenir.|
|**Ortak üyeleri göster**|Ortak Üyeler görüntülenir.|
|**Korumalı üyeleri göster**|Korunan Üyeler görüntülenir.|
|**Özel üyeleri göster**|Özel Üyeler görüntülenir.|
|**Diğer üyeleri göster**|İç (veya Visual Basic arkadaş) Üyeler dahil diğer üye türleri görüntülenir.|
|**Devralınan üyeleri göster**|Devralınan Üyeler görüntülenir.|
|**Uzantı yöntemlerini göster**|Uzantı metotları görüntülenir.|

### <a name="class-view-shortcut-menu"></a>Sınıf Görünümü kısayol menüsü
 **Sınıf görünümü** kısayol menüsü, seçilen proje türüne bağlı olarak aşağıdaki komutları içerebilir.

|Komut|Açıklama|
|-|-|
|**Tanıma Git**|Öğe açık projede tanımlanmamışsa, kaynak kodundaki veya **nesne tarayıcısı**içindeki öğenin tanımını bulur.|
|**Tanıma gözatatıon**|**Nesne tarayıcısı**seçili öğeyi görüntüler.|
|**Tüm Başvuruları Bul**|Şu anda seçili olan nesne öğesini bulur ve sonuçları **Bul sonuçları** penceresinde görüntüler.|
|**Türe Filtre Uygula** (yalnızca yönetilen kod)|Yalnızca seçilen türü veya ad alanını görüntüler. **Bul** kutusunun yanında bulunan **bul** (X) düğmesini seçerek filtreyi kaldırabilirsiniz.|
|**Kopyala**|Öğenin tam adını kopyalar.|
|**Alfabetik olarak Sırala**|Türleri ve üyeleri ada göre alfabetik olarak listeler.|
|**Üye türüne göre sırala**|Türlerine göre sırasıyla türler ve üyeleri listeler (Bu tür sınıfların önüne ve arabirimlerin önüne arabirimler ve yöntemlerin önündeki Yöntemler).|
|**Üye erişimine göre sırala**|Türleri ve üyeleri, genel veya özel gibi erişim türüne göre sıralar.|
|**Üye türüne göre grupla**|Türleri ve üyeleri nesne türüne göre gruplar halinde sıralar.|
|**Bildirime git** (yalnızca C++ kod)|Varsa, kaynak kodundaki tür veya üyenin bildirimini görüntüler.|
|**Tanıma Git**|Varsa, kaynak kodundaki tür veya üyenin tanımını görüntüler.|
|**Başvuruya git**|Varsa, kaynak kodundaki tür veya üyenin başvurusunu görüntüler.|
|**Çağrı hiyerarşisini görüntüle**|Seçilen yöntemi **çağrı hiyerarşisi** penceresinde görüntüler.|

## <a name="call-hierarchy-visual-basic-c-c"></a><a name="BKMK_CallHierarchy"></a> Çağrı hiyerarşisi (Visual Basic, C#, C++)
 **Çağrı hiyerarşisi** penceresi, belirli bir yöntemin (veya özelliğin veya oluşturucunun) nerede çağrıldığını gösterir ve bu yöntemden çağrılan yöntemleri listeler. Belirli bir kapsamdaki Yöntemler arasında arayan/çağrılan ilişkilerini gösteren çağrı grafiğinin birden çok düzeyini görüntüleyebilirsiniz.

 **Çağrı hiyerarşisi** penceresini bir Yöntem (veya özellik veya Oluşturucu) seçerek ve ardından kısayol menüsünde **sınıf hiyerarşisini görüntüle** ' yi seçerek görüntüleyebilirsiniz. Ekran aşağıdaki resme benzemelidir.

 ![Çağrı hiyerarşisi birden çok düğüm açık](../ide/media/multiplenodes.png "MultipleNodes") Çağrı hiyerarşisi penceresi

 Araç çubuğundaki açılan listeyi kullanarak hiyerarşinin kapsamını belirtebilirsiniz: çözüm, geçerli proje veya geçerli belge.

 Ana bölmede, yöntemine ve yönteminden yapılan çağrılar görüntülenir ve **siteleri çağır** bölmesi seçilen çağrının konumunu görüntüler. Sanal veya soyut olan üyeler için bir **geçersiz kılma yöntemi adı** düğümü görüntülenir. Arabirim üyeleri için bir **Implements Yöntem adı** düğümü görüntülenir.

 **Çağrı hiyerarşisi** penceresi, bir yöntemin olay işleyicisi olarak eklendiği veya bir temsilciye atandığı yerleri dahil olmak üzere metot grubu başvurularını bulmaz. Bu başvuruları bulmak için, **tüm başvuruları bul** komutunu kullanın.

 **Çağrı hiyerarşisi** penceresindeki kısayol menüsü aşağıdaki komutları içerir.

|Komut|Açıklama|
|-|-|
|**Yeni kök olarak ekle**|Seçili düğümü yeni bir kök düğüm olarak ekler.|
|**Kökü Kaldır**|Seçili kök düğümü ağaç görünümü bölmesinden kaldırır.|
|**Tanıma Git**|Bir yöntemin orijinal tanımına gider.|
|**Tüm Başvuruları Bul**|Seçili yönteme ait tüm başvuruları projede bulur.|
|**Kopyala**|Seçili düğümü kopyalar (alt düğümlerini değil).|
|**Yenile**|Bilgileri yeniler.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a> Nesne Tarayıcısı
 **Nesne tarayıcısı** , projelerinizdeki kodun açıklamalarını görüntüler.

 **Nesne tarayıcısı**görüntülemek istediklerinizi filtreleyebilirsiniz. Pencerenin üst kısmındaki aşağı açılan listeyi kullanarak aşağıdaki seçenekler arasından seçim yapabilirsiniz:

- Herhangi bir .NET Framework

- Silverlight

- Etkin çözüm

- Özel bir bileşen kümesi

  Özel bileşenler, yönetilen kod yürütülebilir dosyaları, kitaplık derlemeleri, tür kitaplıkları ve. ocx dosyalarını içerebilir. C++ özel bileşenleri eklemek mümkün değildir. Özel ayarlar Visual Studio Kullanıcı uygulaması dizinine kaydedilir,%APPDATA%\Roaming\Microsoft\VisualStudio\11.0\ObjBrowEX.dat.

  **Nesne tarayıcısı** sol bölmesinde .NET Framework ve com bileşenleri gibi fiziksel kapsayıcılar gösterilmektedir. Kapsayıcı düğümlerini içerdikleri ad alanlarını görüntüleyecek şekilde genişletebilir ve ardından içerdikleri türleri göstermek için ad alanlarını genişletebilirsiniz. Bir tür seçtiğinizde, üyeleri (Özellikler ve yöntemler gibi) sağ bölmede listelenir. Sağ alt bölmede seçili öğeyle ilgili ayrıntılı bilgiler görüntülenir.

  Pencerenin üst kısmındaki **arama** kutusunu kullanarak belirli bir öğe için arama yapabilirsiniz. Aramalar büyük/küçük harfe duyarlıdır. Arama sonuçları sol bölmede görüntülenir. Bir aramayı temizlemek için **arama** kutusunun yanındaki **Aramayı Temizle** (X) düğmesini seçin.

  **Nesne tarayıcısı** yaptığınız seçimleri izler ve araç çubuğundaki **İleri** ve **geri** düğmelerini kullanarak seçimleriniz arasında gezinebilirsiniz.

  Bir öğeyi (derleme, ad alanı, tür veya üye) seçerek ve araç çubuğundaki **Başvuru Ekle** düğmesini seçerek açık bir çözüme derleme başvurusu eklemek için **nesne tarayıcısı** kullanabilirsiniz.

### <a name="object-browser-settings"></a>Nesne Tarayıcısı ayarları
 Araç çubuğundaki **nesne tarayıcısı ayarları** düğmesini kullanarak, aşağıdaki görünümlerden birini belirtebilirsiniz.

|Ad|Açıklama|
|-|-|
|**Ad alanlarını görüntüle**|Sol bölmedeki fiziksel kapsayıcılar yerine ad alanlarını görüntüler. Birden fazla fiziksel kapsayıcıda depolanan ad alanları birleştirilir.|
|**Kapsayıcıları görüntüle**|Sol bölmedeki ad alanları yerine fiziksel kapsayıcıları görüntüler. **Ad alanlarını** ve **Görünüm kapsayıcılarını** görüntüleme birbirini dışlamalı ayarlar.|
|**Temel türleri göster**|Temel türleri görüntüler.|
|**Türetilmiş türleri göster**|Türetilmiş türleri görüntüler.|
|**Gizli türleri ve üyeleri göster**|Açık gri metinde gizli türleri ve üyeleri (istemciler tarafından kullanılmak üzere tasarlanmamıştır) görüntüler.|
|**Ortak üyeleri göster**|Ortak üyeleri görüntüler.|
|**Korumalı üyeleri göster**|Korumalı üyeleri görüntüler.|
|**Özel üyeleri göster**|Özel üyeleri görüntüler.|
|**Diğer üyeleri göster**|İç (veya arkadaş Visual Basic) Üyeler dahil diğer üye türlerini görüntüler.|
|**Devralınan üyeleri göster**|Devralınan üyeleri görüntüler.|
|**Uzantı yöntemlerini göster**|Uzantı yöntemlerini görüntüler.|

### <a name="object-browser-shortcut-menu-commands"></a>Nesne Tarayıcısı kısayol menü komutları
 **Nesne tarayıcısı** kısayol menüsünde, seçilen öğenin türüne bağlı olarak aşağıdaki komutlar bulunabilir.

|Komut|Açıklama|
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

## <a name="code-definition-window-c-c"></a><a name="BKMK_CodeDefinition"></a> Kod tanımı penceresi (C#, C++)
 **Kod tanımı** penceresi, etkin projedeki seçili bir türün veya üyenin tanımını görüntüler. Tür veya üye kod düzenleyicisinde veya bir kod görünümü penceresinde seçilebilir.

 Bu pencere salt okunurdur, ancak içinde kesme noktaları veya yer işaretleri ayarlayabilirsiniz. Görüntülenmiş tanımı değiştirmek için kısayol menüsünde **tanımı Düzenle** ' yi seçin. Bu, kaynak dosyayı kod düzenleyicisinde açar ve ekleme noktasını tanımın başladığı satıra taşıdır.

### <a name="code-definition-shortcut-menu"></a>Kod tanımı kısayol menüsü
 **Kod tanımı** penceresindeki kısayol menüsü, programlama diline bağlı olarak aşağıdaki komutları içerebilir.

|Komut|Açıklama|
|-|-|
|**Birim testleri oluşturma**|Seçili öğe için birim testleri oluşturur.|
|**Sıralı diyagram oluştur**|Bir yöntem seçildiğinde, bir sıralı diyagram oluşturur.|
|**Özel erişimci oluştur**|Çözümde bir birim testi varsa, testin koda erişmek için kullandığı bir yöntem oluşturur.|
|**Tanıma Git**|Tanımı (veya kısmi sınıflar için tanımları) bulur ve **sonuçları bul** penceresinde görüntüler.|
|**Tüm Başvuruları Bul**|Çözümdeki türe veya üyeye başvuruları bulur.|
|**Çağrı hiyerarşisini görüntüle**|Yöntemi **çağrı hiyerarşisi** penceresinde görüntüler.|
|**Çağırma testlerini göster**|Projede birim testleri varsa, seçilen kodu çağıran testleri gösterir.|
|**Çağırma testleri çalıştırma**|Projede birim testleri varsa, seçilen kod için testleri çalıştırır.|
|**Ilı**|Bir kesme noktası (veya izleme noktası) ekler.|
|**Imlece kadar Çalıştır**|Programı hata ayıklama modunda imleç konumuna çalıştırır.|
|**Kopyala**|Seçili satırı kopyalar.|
|**Anahat Oluşturma**|Standart ana hat komutları.|
|**Tanımı Düzenle**|Ekleme noktasını kod penceresindeki tanıma gider.|
|**Kodlama seçin**|Dosya için bir kodlama ayarlayabilmeniz için **kodlama** penceresini açar.|

### <a name="document-outline-window"></a>Belge Anahattı penceresi
 **Belge Anahattı** penceresini, bir XAML sayfası veya bir Windows form TASARıMCıSı veya HTML sayfaları gibi tasarımcı görünümleriyle birlikte kullanabilirsiniz. Bu pencere, form veya sayfanın mantıksal yapısını görüntüleyebilmeniz ve derin gömülü veya gizli denetimleri bulabilmeniz için öğeleri bir ağaç görünümünde görüntüler.

## <a name="see-also"></a>Ayrıca Bkz.
 [Sınıf Görünümü ve Nesne Tarayıcısı simgeleri](../ide/class-view-and-object-browser-icons.md)
