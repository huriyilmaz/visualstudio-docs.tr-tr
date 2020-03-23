---
title: Görüntüler ve Simgeler
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 843829c56fcbd2f5c558d7c4a8b14a660a431eac
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302422"
---
# <a name="images-and-icons-for-visual-studio"></a>Visual Studio İçin Görüntüler ve Simgeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Visual Studio'da görüntü kullanımı
 Resim oluşturmadan önce Visual [Studio Image Library'deki](https://www.microsoft.com/download/details.aspx?id=35825)1.000'den fazla resimden yararlanmayı düşünün.

### <a name="types-of-images"></a>Resim türleri

- **Simgeler**. Komutlarda, hiyerarşilerde, şablonlarda ve benzerlerinde görünen küçük görüntüler. Visual Studio'da kullanılan varsayılan simge boyutu 16x16 PNG'dir. Görüntü hizmeti tarafından üretilen simgeler, HDPI desteği için otomatik olarak XAML biçimini oluşturur.

     **NOT:** Menü sisteminde görüntüler kullanılırken, her komut için bir simge oluşturmamalısınız. Komutunuzun bir simge alıp almaması gerektiğini görmek [için Visual Studio için Menülere ve Komutlara](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) başvurun.

- **Küçük.** Yeni Proje iletişim kutusu gibi bir iletişim kutusunun önizleme alanında kullanılan görüntüler.

- **İletişim görüntüleri.** Açıklayıcı grafik veya ileti göstergeleri olarak iletişim veya sihirbazlarda görünen görüntüler. Zor bir kavramı göstermek veya kullanıcının dikkatini çekmek için seyrek ve yalnızca gerektiğinde kullanın (uyarı, uyarı).

- **Animasyonlu görüntüler.** İlerleme göstergelerinde, durum çubuklarında ve işlem iletişim lerinde kullanılır.

- **Imleç.** Fareyi kullanarak bir işlemin izin verilip verilmediğini, bir nesnenin bırakılabileceği ve benzeri bir işlemin izin verilip verilmediğini belirtmek için kullanılır.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Simge tasarımı

### <a name="overview"></a>Genel Bakış
 Visual Studio, temiz geometriye ve pozitif/negatif (açık/koyu) 50/50 dengesine sahip modern tarzda simgeler kullanır ve doğrudan, anlaşılabilir metaforlar kullanır. Önemli simge tasarım noktaları netlik, basitleştirme ve bağlam etrafında merkezi.

- **Netlik:** bir simgeye anlamını ve bireyselliğini veren temel metafora odaklanın.

- **Basitleştirme:** simgeyi temel anlamı ile azaltın – temayı sadece gerekli öğe(ler) ve fırfırsız ile karşıya geçirin.

- **Bağlam:** Hangi öğelerin simgenin temel metaforu oluşturduğuna karar verirken çok önemli olan kavram geliştirme sırasında bir simgenin rolünün tüm yönlerini göz önünde bulundurun.

  Simgelerle, kaçınılması gereken bir dizi tasarım noktası vardır:

- Uygun olmadıklarında UI öğelerini simgeleyen simgeler kullanmayın. UI öğesi ne yaygın, belirgin ne de benzersiz olduğunda daha soyut veya sembolik bir yaklaşım seçin.

- Belgeler, klasörler, oklar ve büyüteç gibi yaygın öğeleri aşırı kullanmayın. Bu tür öğeleri yalnızca simgenin anlamı için gerekli olduğunda kullanın. Örneğin, sağa bakan büyüteç yalnızca Arama, Gözat ve Bul'u belirtmelidir.

- Bazı eski simge öğeleri perspektif kullanımını korusa da, öğe onsuz netlik olmadığı sürece perspektifle yeni simgeler oluşturmayın.

- Bir simgeye çok fazla bilgi sığdırmayın. Kolayca tanınabilir bir sembol olarak tanınabilir veya öğrenilebilen basit bir görüntü, aşırı karmaşık bir görüntüden çok daha yararlıdır. Bir simge tüm hikayeyi anlatamaz.

### <a name="icon-creation"></a>Simge oluşturma

#### <a name="concept-development"></a>Kavram geliştirme
 Visual Studio kendi ui içinde simge türleri geniş bir yelpazede vardır. Geliştirme sırasında simge türünü dikkatlice düşünün. Simge öğeleriniz için belirsiz veya nadir UI nesneleri kullanmayın. Smart Tag simgesi gibi bu gibi durumlarda sembolik tercih edin. Soldaki soyut etiketin anlamının sağdaki belirsiz, UI tabanlı sürümden daha açık olduğunu unutmayın:

|||
|-|-|
|**Sembolik imgelerin doğru kullanımı**|**Sembolik imgelerin yanlış kullanımı**|
|![Akıllı Etiket simgesini düzelt](../../extensibility/ux-guidelines/media/0404-01-smarttagcorrect.png "0404-01_SmartTagCorrect")|![Yanlış Akıllı Etiket simgesi](../../extensibility/ux-guidelines/media/0404-02-smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Standart, kolayca tanınabilir UI öğelerisimgeleri için iyi çalışması örnekleri vardır. Pencere Ekle şu şekilde bir örnektir:

|||
|-|-|
|**Simgedeki UI öğesini düzeltme**|**Simgedeki yanlış UI öğesi**|
|![Pencere Ekle simgesini düzelt](../../extensibility/ux-guidelines/media/0404-03-addwindowcorrect.png "0404-03_AddWindowCorrect")|![Pencere Ekle simgesini yanlış ekleyin](../../extensibility/ux-guidelines/media/0404-04-addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Simgenin anlamı için gerekli olmadıkça belgeyi temel öğe olarak kullanmayın. Belge Ekle'deki belge öğesi olmadan (aşağıda) anlam kaybolur, Yenileme ile belge öğesi anlamı ile ifade etmek gereksizdir.

|||
|-|-|
|**Belge simgesinin doğru kullanımı**|**Belge simgesinin yanlış kullanımı**|
|![Belge simgesini düzelt](../../extensibility/ux-guidelines/media/0404-05-documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Yanlış Belge simgesi](../../extensibility/ux-guidelines/media/0404-06-documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 "Göster" kavramı, Tüm Dosyaları Göster örneğinde olduğu gibi, gösterileni en iyi gösteren simgeyle temsil edilmelidir. Kaynak Görünümü örneğinde olduğu gibi gerekirse "görünüm" kavramını belirtmek için bir lens metaforu kullanılabilir.

|||
|-|-|
|**"Göster"**|**"Görünüm"**|
|![Simgeyi göster](../../extensibility/ux-guidelines/media/0404-07-show.png "0404-07_Show")|![Simgeyi görüntüle](../../extensibility/ux-guidelines/media/0404-08-view.png "0404-08_View")|

 Sağa bakan büyüteç simgesi yalnızca Arama, Bul ve Gözat'ı temsil etmelidir. Artı işareti veya eksi işareti olan sola bakan varyant yalnızca yakınlaştırma/uzaklaştırma anlamına etmelidir.

|||
|-|-|
|**"Arama"**|**"Yakınlaştırma"**|
|![Arama simgesi](../../extensibility/ux-guidelines/media/0404-09-search.png "0404-09_Search")|![Yakınlaştırma simgesi](../../extensibility/ux-guidelines/media/0404-10-zoom.png "0404-10_Zoom")|

 Ağaç görünümlerinde hem klasör simgesini hem de değiştiriciyi kullanmayın. Kullanılabilir olduğunda, yalnızca değiştirici kullanın.

|||
|-|-|
|**Ağaç görünümü simgelerini düzelt**|**Yanlış ağaç görünümü simgeleri**|
|![Ağaç görünümü simgesini düzeltme &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11-treeviewcorrect1.png "0404-11_TreeViewCorrect1") Ağaç görünümü ![simgesini düzelt&#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12-treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Yanlış ağaç görünümü simgesi &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13-treeviewincorrect1.png "0404-13_TreeViewIncorrect1") Yanlış ağaç görünümü simgesi &#40;2 ![&#41;](../../extensibility/ux-guidelines/media/0404-14-treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Stil ayrıntıları

#### <a name="layout"></a>Düzen
 Standart 16x16 simgeleri için gösterildiği gibi yığın öğeleri:

 ![16x16 simgeleri için düzen yığını](../../extensibility/ux-guidelines/media/0404-15-layoutstack.png "0404-15_LayoutStack")

 **16x16 simgeleri için düzen yığını**

 Durum bildirim öğeleri bağımsız simgeler olarak daha iyi kullanılır. Ancak, görev tamamlandı simgesinde olduğu gibi temel öğeye bir bildirimin üst üste yığılması gereken bağlamlar vardır:

 ![Visual Studio'da bağımsız bildirimler](../../extensibility/ux-guidelines/media/0404-16-standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")

 **Bağımsız bildirim simgeleri**

 ![Görev tam simgesi](../../extensibility/ux-guidelines/media/0404-17-taskcomplete.png "0404-17_TaskComplete")

 **Görev Tamamlama simgesi**

 Proje simgeleri genellikle birden çok boyut içeren .ico dosyalarıdır. Çoğu 16x16 simgeleri aynı öğeleri içerir. 32x32 sürümleri, gerektiğinde proje türü de dahil olmak üzere daha fazla ayrıntıya sahiptir.

 ![Visual Studio'da proje simgeleri](../../extensibility/ux-guidelines/media/0404-18-iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")

 **VB Windows Control Library Proje simgeleri, 16x16 ve 32x32**

 Simgeyi piksel çerçevesi içinde ortala. Bu mümkün değilse, simgeyi çerçevenin üst ve/veya sağına hizalayın.

 ![Piksel çerçevesi içinde ortalanmış simge](../../extensibility/ux-guidelines/media/0404-19-iconcentered.png "0404-19_IconCentered")

 **Piksel çerçevesi içinde ortalanmış simge**

 ![Piksel çerçevesinin sağ üst kısmında hizalanmış simge](../../extensibility/ux-guidelines/media/0404-20-icontopright.png "0404-20_IconTopRight")

 **Çerçevenin sağ üst kısmında hizalanmış simge**

 ![Simge ortalanmış ve piksel çerçevesinin üst üstüne hizalanmış](../../extensibility/ux-guidelines/media/0404-21-icontopalign.png "0404-21_IconTopAlign")

 **Simge ortalanmış ve çerçevenin üst hizalanmış**

 İdeal hizalama ve dengeyi sağlamak için, simgenin temel öğesini eylem glifleri ile engellemekten kaçının. Glifleri temel öğenin sol üst yerine yerleştirin. Ek bir öğe eklerken, simgenin hizalanmasını ve dengesini göz önünde bulundurun.

|||
|-|-|
|**Doğru hizalama ve denge**|**Yanlış hizalama ve denge**|
|![Simge dengesini ve hizalamayı düzeltin](../../extensibility/ux-guidelines/media/0404-22-alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Yanlış simge dengesi ve hizalama](../../extensibility/ux-guidelines/media/0404-23-alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Öğeleri paylaşan ve kümeler halinde kullanılan simgeler için boyut eşitliği sağlayın. Yanlış eşleştirmede daire ve ok büyük boy olduğunu ve eşleşmediğini unutmayın.

|||
|-|-|
|**Doğru boyut paritesi**|**Yanlış boyut paritesi**|
|![Simge boyutunu ve pariteyi düzeltin](../../extensibility/ux-guidelines/media/0404-24-sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Yanlış simge boyutu ve eşlik](../../extensibility/ux-guidelines/media/0404-25-sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Tutarlı çizgi ve görsel ağırlıklar kullanın. Yan yana karşılaştırma yaparak, oluşturduğun simgenin diğer simgelerle karşılaştırıldığında nasıl olduğunu değerlendirin. 16x16 çerçevenin tamamını asla kullanmayın, 15x15 veya daha küçük kullanın. Negatif-pozitif (koyu-ışığa) oranı 50/50 olmalıdır.

|||
|-|-|
|**Doğru negatif-pozitif oranı**|**Yanlış negatif-pozitif oranı**|
|![1&#41;&#40;simgeler için doğru görsel ağırlık](../../extensibility/ux-guidelines/media/0404-26-visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![2&#41;&#40;simgeler için doğru görsel ağırlık](../../extensibility/ux-guidelines/media/0404-27-visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![3&#41;&#40;simgeler için doğru görsel ağırlık](../../extensibility/ux-guidelines/media/0404-28-visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Simgeler için yanlış görsel ağırlık](../../extensibility/ux-guidelines/media/0404-29-visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Eleman bütünlüğünden ödün vermeden öğelerinizi oluşturmak için basit, karşılaştırılabilir şekiller ve tamamlayıcı açılar kullanın. Mümkünse 45° veya 90° açıkullanın.

 ![Doğru simge açıları](../../extensibility/ux-guidelines/media/0404-30-iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektif
 Simgeyi açık ve anlaşılır tutun. Perspektifi ve ışık kaynağını yalnızca gerektiğinde kullanın. Simge öğeleri üzerinde perspektif kullanmaktan kaçınılması gerekirken, bazı öğeler onsuz tanınmaz. Bu gibi durumlarda, stilize bir perspektif öğenin netliğini iletir.

 ![3&#45;noktası perspektifi](../../extensibility/ux-guidelines/media/0404-31-3pointperspective.png "0404-31_3PointPerspective")

 **3 puanlık perspektif**

 ![1&#45;noktası perspektifi](../../extensibility/ux-guidelines/media/0404-32-1pointperspective.png "0404-32_1PointPerspective")

 **1 puanlık perspektif**

 Çoğu öğe sağa dönük veya açılı olmalıdır.

 ![Simgeler sağa açılı](../../extensibility/ux-guidelines/media/0404-33-angledright.png "0404-33_AngledRight")

 Işık kaynaklarını yalnızca bir nesneye gerekli netlik eklerken kullanın.

|||
|-|-|
|**Doğru ışık kaynağı**|**Yanlış ışık kaynağı**|
|![Simgeler için doğru ışık kaynakları](../../extensibility/ux-guidelines/media/0404-34-lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Simgeler için yanlış ışık kaynakları](../../extensibility/ux-guidelines/media/0404-35-lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Anahatları yalnızca okunabilirliği artırmak veya metaforu daha iyi iletişim kurmak için kullanın. Negatif-pozitif (koyu-ışık) dengesi 50/50 olmalıdır.

|||
|-|-|
|**Anahatların doğru kullanımı**|**Anahatların yanlış kullanımı**|
|![Anahatları düzelt](../../extensibility/ux-guidelines/media/0404-36-outlinescorrect.png "0404-36_OutlinesCorrect")|![Yanlış anahatlar](../../extensibility/ux-guidelines/media/0404-37-outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Simge türleri
 **Kabuk ve komut çubuğu** simgeleri aşağıdaki öğelerden en fazla üçinden oluşur: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Kabuk ve komut çubuğu simgeleri](../../extensibility/ux-guidelines/media/0404-38-shellicons.png "0404-38_ShellIcons")

 **Kabuk ve komut çubuğu simgelerine örnekler**

 **Araç penceresi komut çubuğu** simgeleri aşağıdaki öğelerden en fazla üçinden oluşur: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Araç penceresi komut çubuğu simgeleri](../../extensibility/ux-guidelines/media/0404-39-toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")

 **Araç penceresi komut çubuğu simgelerine örnekler**

 **Ağaç görünümü disambiguator** simgeleri en fazla üç aşağıdaki öğelerden oluşur: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Ağaç görünümü disambiguator simgeleri](../../extensibility/ux-guidelines/media/0404-40-treeviewicons.png "0404-40_TreeViewIcons")

 **Ağaç görünümü disambiguator simgelerine örnekler**

 **Devlet tabanlı değer taksonomi** simgeleri aşağıdaki durumlarda vardır: etkin, etkin devre dışı ve etkin olmayan devre dışı.

 ![Devlet&#45;tabanlı taksonomi değer simgeleri](../../extensibility/ux-guidelines/media/0404-41-statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")

 **Devlet tabanlı değer taksonomi simgelerine örnekler**

 **IntelliSense** simgeleri aşağıdaki öğelerden en fazla üçinden oluşur: bir temel, bir değiştirici ve bir durum.

 ![IntelliSense simgeleri](../../extensibility/ux-guidelines/media/0404-42-intellisenseicons.png "0404-42_IntelliSenseIcons")

 **IntelliSense simgelerine örnekler**

 **Küçük (16x16) proje** simgeleri en fazla iki öğeolmalıdır: bir temel ve bir değiştirici.

 ![16x16 proje simgesi &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-43-16x16project1.png "0404-43_16x16Project1") ![16x16 proje simgesi &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44-16x16project2.png "0404-44_16x16Project2") ![16x16 proje simgesi &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45-16x16project3.png "0404-45_16x16Project3")

 **Küçük (16x16) proje simgelerine örnekler**

 **Büyük (32x32) proje** simgeleri aşağıdaki öğelerden en fazla dörtten oluşur: bir temel, bir ila iki değiştirici ve bir dil bindirme.

 ![32x32 proje simgeleri](../../extensibility/ux-guidelines/media/0404-46-32x32project.png "0404-46_32x32Project")

 **Büyük (32x32) proje simgelerine örnekler**

### <a name="production-details"></a>Üretim detayları
 Tüm yeni Ara bilgi arabirimi öğeleri Windows Presentation Foundation (WPF) kullanılarak oluşturulmalı ve WPF için tüm yeni simgeler 32 bit PNG biçiminde olmalıdır. 24 bit PNG saydamlığı desteklemeyen eski bir biçimdir ve bu nedenle simgeler için önerilmez.

 Çözünürlüğü 96 DPI'dan kaydedin.

#### <a name="file-types"></a>Dosya türleri

- **32-bit PNG:** simgeler için tercih edilen biçim. Tek bir raster (piksel) görüntü depolayabilir bir kayıpsız veri sıkıştırma dosya biçimi. 32-bit PNG dosyaları alfa-kanal saydamlığı, gama düzeltme ve iç içe destek.

- **32 bit BMP:** WPF olmayan denetimler için. XP veya yüksek renk olarak da adlandırılan 32 bit BMP, alfa kanalı saydamlığı olan gerçek renkli bir görüntü olan RGB/A görüntü biçimidir. Alfa kanalı, Adobe Photoshop'ta atanmış ve bit eşlemi içinde ek (dördüncü) renk kanalı olarak kaydedilen saydamlık katmanıdır. Renk derinliği hakkında hızlı bir görsel ipucu sağlamak için tüm 32 bit BMP dosyalarına resim üretimi sırasında siyah bir arka plan eklenir. Bu siyah arka plan, UI'de maskelenecek alanı temsil eder.

- **32 bit ICO:** Proje simgeleri ve Öğe Ekle için. Tüm ICO dosyaları alfa-kanal saydamlığı (RGB/A) ile 32 bit gerçek renktir. ICO dosyaları birden çok boyutu ve renk derinliklerini depolayabildiği için, Vista simgeleri genellikle 16x16, 32x32, 48x48 ve 256x256 görüntü boyutları içeren bir ICO biçimindedir. Windows Gezgini'nde düzgün görüntülenebilmek için ICO dosyalarının her görüntü boyutu için 24 bit ve 8 bit renk derinliklerine kaydedilmesi gerekir.

- **XAML:** tasarım yüzeyleri ve Windows süsleyiciler için. XAML simgeleri, ölçekleme, döndürme, dosyalama ve saydamlığı destekleyen vektör tabanlı görüntü dosyalarıdır. Onlar Visual Studio bugün yaygın değildir ama esneklik nedeniyle daha popüler hale gelmektedir.

- **Svg**

- **24 bit BMP:** Visual Studio komut çubuğu için. Gerçek renkli RGB görüntü biçimi olan 24 bit BMP, eleme saydamlık katmanı için renk anahtarı olarak macenta (R=255, G=0, B=255) kullanarak bir saydamlık katmanı oluşturan bir simge kuralıdır. 24 bit BMP'de, tüm macenta yüzeyleri arka plan rengi kullanılarak görüntülenir.

- **24-bit GIF:** Visual Studio komut çubuğu için. Saydamlığı destekleyen gerçek renkli RGB görüntü biçimi. GIF dosyaları genellikle Sihirbaz resmi ve GIF animasyonlarında kullanılır.

### <a name="icon-construction"></a>Simge yapısı
 Visual Studio'daki en küçük simge boyutu 16x16'dır. Ortak kullanımda en büyük 32x32'dir. Bir simge tasarlarken 16x16, 24x24 veya 32x32 çerçevenin tamamını doldurmamayı unutmayın. Okunaklı, tek tip simge yapısı kullanıcı tanıma için gereklidir. Simgeler inşa ederken aşağıdaki noktalara bağlı kalarak.

- Simgeler açık, anlaşılır ve tutarlı olmalıdır.

- Durum bildirim öğelerini tek simgeler olarak kullanmak ve simge tabanı öğesinin üstüne yığmamak daha iyidir. Belirli bağlamlarda, UI durum öğesi nin bir temel öğeyle eşlenemasını gerektirebilir.

- Proje simgeleri genellikle çeşitli boyutlarda içeren .ico dosyalarıdır. Yalnızca 16x16, 24x24 ve 32x32 simgeleri güncellenmektedir. Çoğu 16x16 ve 24x24 simgeleri aynı öğeleri içerecektir. 32x32 simgeleri, gerektiğinde proje dil türü de dahil olmak üzere daha fazla ayrıntı içerir.

- 32x32 simgeleri için temel öğeler genellikle 2 piksellik bir çizgi ağırlığına sahiptir. Ayrıntı öğeleri için 1 veya 2 piksellik çizgi ağırlığı kullanılabilir. Hangisinin daha uygun olduğunu belirlemek için en iyi kararınızı kullanın.

- 16x16 ve 24x24 simgeleri için öğeler arasında en az 1 piksel lik bir boşluk var. 32x32 simgeleri için, öğeler arasında ve değiştirici ve temel öğe arasında 2 piksel aralığı kullanın.

  ![16x16, 24x24 ve 32x32 simgeleri için eleman aralığı](../../extensibility/ux-guidelines/media/0404-47-elementspacing.png "0404-47_ElementSpacing")

  **16x16, 24x24 ve 32x32 boyutlarındaki simgeler için eleman aralığı**

#### <a name="color-and-accessibility"></a>Renk ve erişilebilirlik
 Visual Studio uyumluluk yönergeleri, üründeki tüm simgelerin renk ve kontrast için erişilebilirlik gereksinimlerini geçirmesini gerektirir. Bu simge ters yoluyla elde edilir ve tasarlarken, onlar üründe programlı ters olacak farkında olmalıdır.

 Visual Studio simgelerinde renk kullanma hakkında daha fazla bilgi için [bkz.](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Görüntülerde renk kullanma

### <a name="overview"></a>Genel Bakış
 Visual Studio'daki simgeler öncelikle monokromatiktir. Renk belirli bilgileri iletmek için ayrılmıştır ve dekorasyon için asla. Renk kullanılır:

- bir eylemi belirtmek için

- kullanıcıyı durum bildirimi konusunda uyarmak için

- dil bağlantısını belirlemek için

- IntelliSense içindeki öğeleri ayırt etmek için

### <a name="accessibility"></a>Erişilebilirlik
 Visual Studio uyumluluk yönergeleri, üründe iade edilen tüm simgelerin renk ve kontrast için erişilebilirlik gereksinimlerini geçirmesini gerektirir. Görsel dil paletindeki renkler test edilmiştir ve bu gereksinimleri karşılar.

#### <a name="color-inversion-for-dark-themes"></a>Koyu temalar için renk ters çevirme
 Visual Studio karanlık temasında simgelerin doğru kontrast oranıyla görünmesini sağlamak için programlı bir ters uygulama uygulanır. Bu kılavuzdaki renkler kısmen, doğru şekilde ters çevirmeleri için seçilmiştir. Renk kullanımınızı bu paletle sınırlandırın, yoksa ters çevirme uygulandığında öngörülemeyen sonuçlar alırsınız.

 ![Renkleri ters çevrilmiş simgeörnekleri](../../extensibility/ux-guidelines/media/0405-01-darkthemeinversion.png "0405-01_DarkThemeInversion")

 **Renklerini ters çevrilmiş simgeler örnekleri**

### <a name="base-palette"></a>Taban paleti
 Tüm standart simgeler üç temel renk içerir. Simgeler, 3B araç simgeleri için bir veya iki özel durum la birlikte hiçbir degrade veya damla gölge içermez.

|Kullanım|Adı|Değer (Işık teması)|Swatch|Örnek|
|-----------|----------|---------------------------|------------|-------------|
|Arka Plan/Karanlık|VS BG|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|![Temel palet örneği](../../extensibility/ux-guidelines/media/0405-02-basepaletteexample.png "0405-02_BasePaletteExample")|
|Ön Plan/Işık|VS FG|F0EFF1 / 240.239.241|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405-f0eff1.png "0405_F0EFF1")||
|Anahat|VS Çıkış|F6F6F6 / 246.246.246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")||

 Temel renklere ek olarak, her simge genişletilmiş paletten bir ek renk içerebilir.

### <a name="extended-palette"></a>Genişletilmiş palet

#### <a name="action-modifiers"></a>Eylem değiştiriciler
 Aşağıdaki dört renk, eylem değiştiriciler tarafından gerekli eylem türlerini gösterir:

|Kullanım|Adı|Değer (tüm temalar)|Swatch|
|-----------|----------|--------------------------|------------|
|Pozitif|VS Eylem Yeşil|388A34 / 56.138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Negatif|VS Eylem Kırmızı|A1260D / 161,38,13|![Swatch A1260D](../../extensibility/ux-guidelines/media/0405-a1260d.png "0405_A1260D")|
|Nötr|VS Eylem Mavi|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Oluştur/Yeni|VS Eylem Turuncu|C27D1A / 194.156,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Örnekler
 Yeşil, "Ekle", "Çalıştır", "Oynat" ve "Doğrula" gibi pozitif eylem değiştiriciler için kullanılır.

|||||
|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **Çalıştır**|![Sorgu simgesini yürüt](../../extensibility/ux-guidelines/media/0405-04-executequery.png "0405-04_ExecuteQuery") **Execute Query**|![Tüm adımları oyna simgesi](../../extensibility/ux-guidelines/media/0405-05-playallsteps.png "0405-05_PlayAllSteps") **Tüm Adımları Oyna**|![Denetim simgesi ekle](../../extensibility/ux-guidelines/media/0405-06-addcontrol.png "0405-06_AddControl") **Denetim Ekle**|

 Kırmızı, "Sil", "Durdur", "İptal Et" ve "Kapat" gibi olumsuz eylem değiştiriciler için kullanılır.

|||||
|-|-|-|-|
|![İlişki simgesini silme](../../extensibility/ux-guidelines/media/0405-07-deleterelationship.png "0405-07_DeleteRelationship") **İlişkisi silme**|![Sütun simgesini silme](../../extensibility/ux-guidelines/media/0405-08-deletecolumn.png "0405-08_DeleteColumn") **Sütunu Silme**|![Sorgu simgesini durdur](../../extensibility/ux-guidelines/media/0405-09-stopquery.png "0405-09_StopQuery") **Sorgu'u Durdur**|![Bağlantı çevrimdışı simge](../../extensibility/ux-guidelines/media/0405-10-connectionoffline.png "0405-10_ConnectionOffline") **Bağlantı Çevrimdışı**|

 Mavi, "Aç", "Sonraki", "Önceki", "İçe Aktarma" ve "Dışa Aktarma" gibi oklar olarak en sık temsil edilen nötr eylem değiştiricilere uygulanır.

|||||
|-|-|-|-|
|![Alan simgesine git](../../extensibility/ux-guidelines/media/0405-11-gotofield.png "0405-11_GoToField") **Alana git**|![Toplu denetim&#45;simgesi](../../extensibility/ux-guidelines/media/0405-12-batchedcheckin.png "0405-12_BatchedCheckIn") **Toplu Check-In**|![Adres düzenleyicisimgesi Adres Düzenleyicisi](../../extensibility/ux-guidelines/media/0405-13-addresseditor.png "0405-13_AddressEditor") **Address Editor**|Dernek editörü simgesi Dernek ![Düzenleyicisi](../../extensibility/ux-guidelines/media/0405-14-associationeditor.png "0405-14_AssociationEditor") **Association Editor**|

 Koyu altın öncelikle "Yeni" değiştirici için kullanılır.

|||||
|-|-|-|-|
|![Yeni proje simgesi](../../extensibility/ux-guidelines/media/0405-15-newproject.png "0405-15_NewProject") **Yeni Proje**|![Yeni grafik simgesi oluşturma](../../extensibility/ux-guidelines/media/0405-16-createnewgraph.png "0405-16_CreateNewGraph") **Yeni Grafik Oluştur**|![Yeni ünite test simgesi](../../extensibility/ux-guidelines/media/0405-17-newunittest.png "0405-17_NewUnitTest") **Yeni Ünite Testi**|![Yeni liste öğesi simgesi](../../extensibility/ux-guidelines/media/0405-18-newlistitem.png "0405-18_NewListItem") **Yeni Liste Öğesi**|

#### <a name="special-cases"></a>Özel durumlar
 Özel durumlarda, renkli eylem değiştirici bağımsız bir simge olarak kullanılabilir. Simge için kullanılan renk, simgenin ilişkili olduğu eylemleri yansıtır. Bu kullanım, aşağıdakiler de dahil olmak üzere küçük bir simge alt kümesiyle sınırlıdır:

||||||
|-|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03-actionmodifierrun.png "0405-03_ActionModifierRun") **Çalıştır**|![Simgeyi](../../extensibility/ux-guidelines/media/0405-19-stop.png "0405-19_Stop") **Durdur**|![Simgeyi sil](../../extensibility/ux-guidelines/media/0405-20-delete.png "0405-20_Delete") **Silme**|![Simgeyi Kaydet](../../extensibility/ux-guidelines/media/0405-21-save.png "0405-21_Save") **Save**|![Geri dön simgesine git](../../extensibility/ux-guidelines/media/0405-22-navigateback.png "0405-22_NavigateBack") **Geri Git**|

### <a name="code-hierarchy-palette"></a>Kod hiyerarşisi paleti

#### <a name="folder"></a>Klasör

|Kullanım|Adı|Değer (tüm temalar)|Swatch|Örnek|
|-----------|----------|--------------------------|------------|-------------|
|Klasörler|Klasör|DCB67A / 220.182.122|![Swatch DCB67A](../../extensibility/ux-guidelines/media/0405-dcb67a.png "0405_DCB67A")|![Klasör renk simgesi](../../extensibility/ux-guidelines/media/0405-23-foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio dilleri
 Visual Studio'da bulunan ortak dillerin veya platformların her birinin ilişkili bir rengi vardır. Bu renkler temel simgede veya bileşik simgelerin sağ üst köşesinde görünen dil değiştiriciler kullanılır.

|Kullanım|Adı|Değer (tüm temalar)|Swatch|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Mavi|0095D7 / 0,149,215|![Swatch 0095D7](../../extensibility/ux-guidelines/media/0405-0096d7.png "0405_0096D7")|
|C++|CPP Mor|9B4F96 / 155.79.150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|C#|CS Yeşil (VS Eylem Yeşil)|388A34 / 56.138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|CSS|CSS Kırmızı|BD1E2D / 189,30,45|![Swatch BD1E2D](../../extensibility/ux-guidelines/media/0405-bd1e2d.png "0405_BD1E2D")|
|F#|FS Mor|672878 / 103,40,120|![Swatch 672878](../../extensibility/ux-guidelines/media/0405-672878.png "0405_672878")|
|JavaScript|JS Turuncu|F16421 / 241.100,33|![Swatch F16421](../../extensibility/ux-guidelines/media/0405-f16421.png "0405_F16421")|
|VB|VB Mavi (VS Eylem Mavi)|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|TypeScript|TS Turuncu|E04C06 / 224,76,6|![Swatch E04C06](../../extensibility/ux-guidelines/media/0405-e04c06.png "0405_E04C06")|
|Python|PY Yeşil|879636 / 135,150,54|![Swatch 879636](../../extensibility/ux-guidelines/media/0405-879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Dil değiştiricili simge örnekleri

|||||||
|-|-|-|-|-|-|
|![Visual Basic simgesi](../../extensibility/ux-guidelines/media/0405-25-vb.png "0405-25_VB") **VB**|![C&#35; simgesi](../../extensibility/ux-guidelines/media/0405-26-csharp.png "0405-26_CSharp") **C#**|![C&#43;&#43; simgesi](../../extensibility/ux-guidelines/media/0405-27-cplusplus.png "0405-27_CPlusPlus") **C++**|![F&#35; simgesi](../../extensibility/ux-guidelines/media/0405-28-fsharp.png "0405-28_FSharp") **F#**|![JavaScript simgesi](../../extensibility/ux-guidelines/media/0405-29-javascript.png "0405-29_JavaScript") **JavaScript**|![Python simgesi](../../extensibility/ux-guidelines/media/0405-30-python.png "0405-30_Python") **Python**|
|![HTML simgesi](../../extensibility/ux-guidelines/media/0405-31-html.png "0405-31_HTML") **HTML**|![WPF simgesi](../../extensibility/ux-guidelines/media/0405-32-wpf.png "0405-32_WPF") **WPF**|![ASP simgesi](../../extensibility/ux-guidelines/media/0405-33-asp.png "0405-33_ASP") **ASP**|![CSS simgesi](../../extensibility/ux-guidelines/media/0405-34-css.png "0405-34_CSS") **CSS**|![TypeScript simgesi](../../extensibility/ux-guidelines/media/0405-35-typescript.png "0405-35_TypeScript") **TypeScript**||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense simgeleri özel bir renk paleti kullanır. Bu renkler, kullanıcıların IntelliSense açılır listesindeki farklı öğeleri hızlı bir şekilde ayırt etmelerine yardımcı olmak için kullanılır.

|Kullanım|Adı|Değer (tüm temalar)|Swatch|
|-----------|----------|--------------------------|------------|
|Sınıf, Etkinlik|VS Eylem Turuncu|C27D1A / 194.125,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405-c27d1a.png "0405_C27D1A")|
|Uzatma Yöntemi, Yöntem, Modül, Temsilci|VS Eylem Mor|652D90 / 101,45,144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405-652d90.png "0405_652D90")|
|Alan, Enum Öğesi, Makro, Yapı, Birlik Değer Türü, Operatör, Arayüz|VS Eylem Mavi|00539C / 0,83,156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405-00539c.png "0405_00539C")|
|Nesne|VS Eylem Yeşil|388A34 / 56.138,52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405-388a34.png "0405_388A34")|
|Sabit, Özel Durum, Enum Öğesi, Harita, Harita Öğesi, Ad Alanı, Şablon, Tür Tanımı|Arka Plan (VS BG)|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405-424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense simgelerine örnekler

||||||
|-|-|-|-|-|
|![IntelliSense sınıf simgesi](../../extensibility/ux-guidelines/media/0405-36-intellisenseclass.png "0405-36_IntelliSenseClass") **Sınıf**|![IntelliSense özel etkinlik simgesi](../../extensibility/ux-guidelines/media/0405-37-intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent") **Özel Etkinlik**|![IntelliSense temsilci simgesi](../../extensibility/ux-guidelines/media/0405-38-intellisensedelegate.png "0405-38_IntelliSenseDelegate") **Temsilci**|![IntelliSense yöntemi arkadaş simgesi](../../extensibility/ux-guidelines/media/0405-39-intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") **Yöntem Arkadaş**|![Alan simgesi](../../extensibility/ux-guidelines/media/0405-40-field.png "0405-40_Field") **Alan**|
|![IntelliSense korumalı enum item simgesi](../../extensibility/ux-guidelines/media/0405-41-intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem") **Korumalı Enum Öğesi**|![IntelliSense nesne simgesi](../../extensibility/ux-guidelines/media/0405-42-intellisenseobject.png "0405-42_IntelliSenseObject") **Nesne**|![IntelliSense şablon simgesi](../../extensibility/ux-guidelines/media/0405-43-intellisensetemplate.png "0405-43_IntelliSenseTemplate") **Şablon**|![IntelliSense özel durum kısayol simgesi](../../extensibility/ux-guidelines/media/0405-44-intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut") **Özel Durum Kısayolu**||

### <a name="notifications"></a>Bildirimler
 Visual Studio'daki bildirimler durumu belirtmek için kullanılır. Bildirim paleti, aşağıdaki durum düzeylerine sahip bildirimleri tanımlamak için aşağıdaki dört rengin yanı sıra siyah veya beyaz ön plan doldurma seçeneklerini kullanır.

|Kullanım|Adı|Değer (tüm temalar)|Swatch|
|-----------|----------|--------------------------|------------|
|Durum: nötr|Bildirim Mavisi (VS Mavi)|1BA1E2 / 27.161.226|![Swatch 1BA1E2](../../extensibility/ux-guidelines/media/0405-1ba1e2.png "0405_1BA1E2")|
|Durum: pozitif|Bildirim Yeşili (VS Yeşil)|339933 / 51,153,51|![Swatch 339933](../../extensibility/ux-guidelines/media/0405-339933.png "0405_339933")|
|Durum: negatif|Bildirim Kırmızı (VS Kırmızı)|E51400 / 229,20,0|![Swatch E51400](../../extensibility/ux-guidelines/media/0405-e51400.png "0405_E51400")|
|Durum: uyarı|Bildirim Sarı (VS Turuncu)|FFCC00 / 255.204,0|![Swatch FFCC00](../../extensibility/ux-guidelines/media/0405-ffcc00.png "0405_FFCC00")|
|Ön plan dolgusu|Bildirim Siyahı (Siyah)|000000 / 0,0,0|![Swatch &#35;000000](../../extensibility/ux-guidelines/media/0405-000000.png "0405_000000")|
|Ön plan dolgusu|Bildirim Beyaz (Beyaz)|FFFFFF / 255.255.255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Bildirim simgelerine örnekler

|||||
|-|-|-|-|
|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-45-alert.png "0405-45_Alert") **Uyarı**|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-48-warning.png "0405-48_Warning") **Uyarı**|![Tam simge](../../extensibility/ux-guidelines/media/0405-46-complete.png "0405-46_Complete") **Tamamla**|![Simgeyi](../../extensibility/ux-guidelines/media/0405-47-stop.png "0405-47_Stop") **Durdur**|

### <a name="visual-studio-online"></a>Visual Studio Team Services
 Genel olarak, Visual Studio Online bir tarayıcıda barındırılan özelliklerden oluşur. Renk farklı ortamlarda değişir, ancak stil aynı kalır.

|Grup|Kullanım|Adı|Değer (tüm temalar)|Swatch|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Arka plan|TFSO BG|656565/ 101, 101, 101|![Swatch 656565](../../extensibility/ux-guidelines/media/0405-656565.png "0405_656565")|
|TFS|Anahat|TFSO OUT|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Napa|Arka plan|Beyaz|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|Monako|Arka plan|Beyaz|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Arka plan|Beyaz|FFFFFF / 255, 255, 255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405-ffffff.png "0405_FFFFFF")|
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Swatch 555555](../../extensibility/ux-guidelines/media/0405-555555.png "0405_555555")|
|F12|Hover|F12 Blue_Hover|2279BF / 34.121.191|![Swatch 2279BF](../../extensibility/ux-guidelines/media/0405-2279bf.png "0405_2279BF")|
|F12|Devre dışı|F12 LtGrey_Disabled|ABABAC / 171.171.172|![Swatch ABABAC](../../extensibility/ux-guidelines/media/0405-ababac.png "0405_ABABAC")|
|F12|Hover arka plan|Hover bg|D9EBF7 / 217.235.247|![Swatch D9EBF7](../../extensibility/ux-guidelines/media/0405-d9ebf7.png "0405_D9EBF7")|
|F12|Basılı arka plan|Basılı bg|B2D7F0 / 178.215.240|![Swatch B2D7F0](../../extensibility/ux-guidelines/media/0405-b2d7f0.png "0405_B2D7F0")|
|F12|Anahat|VS OUT|F6F6F6 / 246.246.246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405-f6f6f6.png "0405_F6F6F6")|
|F12|Bilgi|Bilgi|00BCF2 / 0,188,242|![Swatch 00BCF2](../../extensibility/ux-guidelines/media/0405-00bcf2.png "0405_00BCF2")|
|F12|Uyarı|Uyarı|F28300 / 242.131,0|![Swatch F28300](../../extensibility/ux-guidelines/media/0405-f28300.png "0405_F28300")|
|F12|Hata / Negatif|Error_Negative|E81123 / 232,17,35|![Swatch E81123](../../extensibility/ux-guidelines/media/0405-e81123.png "0405_E81123")|
|F12|Başlangıç / Pozitif|Start_Positive|009E49 / 0,158,73|![Swatch 009E49](../../extensibility/ux-guidelines/media/0405-009e49.png "0405_009E49")|
|F12|Kesme türü|Kesme türü|9B4F96 / 155.79.150|![Swatch 9B4F96](../../extensibility/ux-guidelines/media/0405-9b4f96.png "0405_9B4F96")|
|F12|Etkinlik İşareti|Etkinlik İşareti|A51F00 / 165,31,0|![Swatch A51F00](../../extensibility/ux-guidelines/media/0405-a51f00.png "0405_A51F00")|
|F12|Kullanıcı İşareti|Kullanıcı İşareti|F16220 / 241,98,32|![Swatch F16220](../../extensibility/ux-guidelines/media/0405-f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Visual Studio Online simgelerine örnekler

|TFS Online||||
|----------------|-|-|-|
|![TFS Online takım simgesi](../../extensibility/ux-guidelines/media/0405-49-tfsonlineteam.png "0405-49_TFSOnlineTeam") **Online Takım**|![TFS bilgi simgesi](../../extensibility/ux-guidelines/media/0405-50-tfsinformation.png "0405-50_TFSInformation") **Bilgi**|![TFS tarih simgesi](../../extensibility/ux-guidelines/media/0405-51-tfshistory.png "0405-51_TFSHistory") **Tarihçe**|![TFS şube simgesi](../../extensibility/ux-guidelines/media/0405-52-tfsbranch.png "0405-52_TFSBranch") **Şube**|

|Napa||||
|----------|-|-|-|
|![Napa içerik simgesi](../../extensibility/ux-guidelines/media/0405-53-napacontent.png "0405-53_NapaContent") **İçerik**|![Napa ofis posta simgesi](../../extensibility/ux-guidelines/media/0405-54-napaofficemail.png "0405-54_NapaOfficeMail") **Office Mail**|![Napa SharePoint simgesi](../../extensibility/ux-guidelines/media/0405-55-napasharepoint.png "0405-55_NapaSharePoint") **SharePoint**|![Napa görev bölmesi simgesi](../../extensibility/ux-guidelines/media/0405-56-napataskpane.png "0405-56_NapaTaskPane") **Görev Bölmesi**|

|Monako||||
|------------|-|-|-|
|![Monako dosyaları simgesi](../../extensibility/ux-guidelines/media/0405-57-monacofiles.png "0405-57_MonacoFiles") **Dosyalar**|![Monako Git simgesi](../../extensibility/ux-guidelines/media/0405-58-monacogit.png "0405-58_MonacoGit") **Git**|![Monako arama simgesi](../../extensibility/ux-guidelines/media/0405-59-monacosearch.png "0405-59_MonacoSearch") **Arama**|![Monako metin simgesi](../../extensibility/ux-guidelines/media/0405-60-monacotext.png "0405-60_MonacoText") **Metin**|

|F12||||
|---------|-|-|-|
|![F12 güzel kod simgesi](../../extensibility/ux-guidelines/media/0405-61-f12prettycode.png "0405-61_F12PrettyCode") **Pretty Code**|![F12 Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-62-f12warning.png "0405-62_F12Warning") **Uyarı**|![F12 Öykünme simgesi](../../extensibility/ux-guidelines/media/0405-63-f12emulate.png "0405-63_F12Emulate") **Öykün**|
