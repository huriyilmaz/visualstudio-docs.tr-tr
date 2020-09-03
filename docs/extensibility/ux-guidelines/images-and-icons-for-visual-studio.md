---
title: Visual Studio için görüntüler ve simgeler | Microsoft Docs
ms.date: 04/26/2017
ms.topic: overview
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edbf1542277189f37565e7ff415a52025094e595
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85906116"
---
# <a name="images-and-icons-for-visual-studio"></a>Visual Studio İçin Görüntüler ve Simgeler
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Visual Studio 'da görüntü kullanımı
 Resim oluşturmadan önce, [Visual Studio Görüntü Kitaplığı](https://www.microsoft.com/download/details.aspx?id=35825)'nda 1000 + görüntüden birini kullanmayı düşünün.

### <a name="types-of-images"></a>Görüntü türleri

- **Simgeler**. Komutlarda, hiyerarşilerde, şablonlarda ve benzeri görünen küçük görüntüler. Visual Studio 'da kullanılan varsayılan simge boyutu 16x16 PNG 'dir. Görüntü hizmeti tarafından üretilen simgeler otomatik olarak HDPı desteği için XAML biçimini oluşturur.

    > [!NOTE]
    > Görüntüler menü sisteminde kullanıldığında, her komut için bir simge oluşturmamalıdır. Komutlarınızın bir simge alması gerekip gerekmediğini görmek için [Visual Studio Için menülere ve komutlara](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) danışın.

- **Küçük resimleri.** Yeni proje iletişim kutusu gibi bir iletişim kutusunun Önizleme alanında kullanılan görüntüler.

- **İletişim kutusu görüntüleri.** Açıklayıcı grafikler veya ileti göstergeleri olarak iletişim kutularında ya da sihirbazlarda görünen görüntüler. Yalnızca zor bir kavram göstermek veya kullanıcının dikkatini çekmek (uyarı, uyarı) için gerekli olduğunda seyrek ve yalnızca kullanın.

- **Animasyonlu görüntüler.** Devam eden göstergeler, durum çubukları ve işlem iletişim kutularında kullanılır.

- **İmleçler.** Bir işlemin fare kullanarak izin verilip verilmeyeceğini belirtmek için kullanılır, burada bir nesne bırakılabilir ve bu şekilde devam eder.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> Simge tasarımı

### <a name="overview"></a>Genel Bakış
 Visual Studio, temizleme geometrisi ve 50/50 bir pozitif/negatif (Açık/Koyu) olan modern stil simgeleri kullanır ve doğrudan, anlaşılır olmayan metaphiler kullanır. Netme, basitleştirme ve bağlam etrafında önemli simge tasarım noktaları merkezi.

- **Netlik:** bir simgenin anlamı ve kişiselleştirme durumunu gösteren çekirdek benzetimini 'a odaklanın.

- Basitlik **:** simgeyi çekirdek anlamı azaltır-yalnızca gerekli öğe (ler) i ve frills olmadan temayı alın.

- **Bağlam:** bir simgenin, temel metaphor 'ın hangi öğelerin oluşturduğunu seçerken çok önemli olan kavram geliştirme sırasında bir simgenin rolünün tüm yönlerini göz önünde bulundurun.

  Simgelerle karşılaşmamak için çeşitli tasarım noktaları vardır:

- Uygun olduğu durumlar dışında UI öğelerini işaret eden simgeler kullanmayın. UI öğesi ortak, önne veya benzersiz olmadığında daha soyut veya sembolik bir yaklaşım seçin.

- Belgeler, klasörler, oklar ve Büyüteç Camı gibi yaygın öğeleri aşırı kullanmayın. Bu gibi öğeleri yalnızca simgenin anlamı için gerekli olduğunda kullanın. Örneğin, sağa bakan Büyüteç Camı yalnızca arama, gezinme ve bulma seçeneğini göstermelidir.

- Bazı eski simge öğeleri perspektif kullanımını korumakla birlikte, öğe bu olmadan anlaşıbulunmadığı için perspektifle yeni simgeler oluşturmayın.

- Bir simgeye çok fazla bilgi vermez. Tanınabilir bir sembol olarak kolayca tanınan veya öğrenilebilecek basit bir görüntü, aşırı karmaşık bir görüntüden çok daha yararlıdır. Bir simge bütün hikayeyi söyleyebilir.

### <a name="icon-creation"></a>Simge oluşturma

#### <a name="concept-development"></a>Kavram geliştirme
 Visual Studio Kullanıcı arabirimi içinde çok çeşitli simge türlerini içerir. Geliştirme sırasında simge türünü dikkatle düşünün. Simge öğeleriniz için belirsiz veya seyrek olmayan UI nesneleri kullanmayın. Akıllı etiket simgesiyle birlikte bu durumlarda sembolik için kabul edin. Soldaki soyut etiketin anlamı, sağdaki Kullanıcı arabirimi tabanlı sürümden daha belirgin olduğunu unutmayın:

|**Sembolik canlandırın 'nin doğru kullanımı**|**Sembolik Imagery 'nin yanlış kullanımı**|
|-|-|
|![Doğru akıllı etiket simgesi](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Hatalı akıllı etiket simgesi](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Standart, kolayca tanınabilir Kullanıcı arabirimi öğelerinin simgeler için iyi bir şekilde çalıştığını örnekler vardır. Bu tür bir örnek pencere ekleyin:

|**Bir simgenin içinde doğru Kullanıcı arabirimi öğesi**|**Bir simgede hatalı UI öğesi**|
|-|-|
|![Pencereyi doğru Ekle simgesi](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Yanlış pencere Ekle simgesi](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Simgenin anlamı için önemli olmadığı sürece belgeyi temel öğe olarak kullanmayın. Belge Ekle (aşağıdaki) sayfasında belge öğesi olmadan anlamı kaybolur, ancak bu anlamı yenilemek için belge öğesini yenileme işlemi gereksizdir.

|**Belge simgesinin doğru kullanımı**|**Belge simgesinin yanlış kullanımı**|
|-|-|
|![Doğru belge simgesi](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Belge simgesi yanlış](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 "Göster" kavramı, gösterilmekte olan tüm dosyaları göster örneğinde olduğu gibi en iyi şekilde gösterilen simgeyle temsil edilmelidir. Kaynak görünümü örneğinde olduğu gibi, gerekirse "görüntüleme" kavramını göstermek için bir lens benzetimini kullanılabilir.

|**Göster**|**Görünümü**|
|-|-|
|![Simgeyi göster](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Görünüm simgesi](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Sağa bakan Büyüteç simgesi yalnızca arama, bulma ve gözatmayı temsil etmelidir. Artı işareti veya eksi işareti ile sola bakan varyant yalnızca Yakınlaştır/Büyüt ' i temsil etmelidir.

|**Aramanız**|**Yakınlaştırma**|
|-|-|
|![Arama simgesi](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Yakınlaştır simgesi](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Ağaç görünümlerinde, hem klasör simgesini hem de değiştiricisini kullanmayın. Kullanılabilir olduğunda yalnızca değiştirici kullanın.

|**Doğru ağaç görünümü simgeleri**|**Ağaç görünümü simgeleri yanlış**|
|-|-|
|Doğru ağaç görünümü simgesi ![&#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![ağaç görünümü simgesini &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Hatalı ağaç görünümü simgesi &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![ağaç görünümü simgesi &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Stil ayrıntıları

#### <a name="layout"></a>Layout
 Standart 16x16 simgeleri için gösterilen yığın öğeleri:

 ![16x16 simgeleri için Düzen yığını](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />16x16 simgeleri için Düzen yığını

 Durum bildirim öğeleri, tek başına simgeler olarak daha iyi kullanılır. Bununla birlikte, bir bildirimin temel öğede (örneğin, görev tamamlanma simgesiyle) yığın olarak oluşturulması gereken bağlamlar vardır:

 ![Visual Studio 'da tek başına bildirimler](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Tek başına bildirim simgeleri

 ![Görev tamamlanma simgesi](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Görev tamamlanma simgesi

 Proje simgeleri genellikle birden çok boyut içeren. ico dosyalarıdır. En çok 16x16 simgesi aynı öğeleri içerir. 32x32 sürümlerinde, uygun olduğunda proje türü de dahil olmak üzere daha fazla ayrıntı vardır.

 ![Visual Studio 'da proje simgeleri](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />VB Windows Denetim Kitaplığı proje simgeleri, 16x16 ve 32x32

 Bir simgeyi piksel çerçevesi içinde ortalayın. Bu mümkün değilse, simgeyi çerçevenin üst ve/veya sağına hizalayın.

 ![Piksel çerçevesi içinde ortalanmış simge](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Piksel çerçevesi içinde ortalanmış simge

 ![Piksel çerçevesinin sağ üst kısmına hizalanmış simge](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Çerçevenin sağ üst kısmına hizalanmış simge

 ![Ortalanmış ve piksel çerçevesinin üstüne hizalanmış simge](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Simge ortalanmış ve çerçevenin üst kısmına hizalanır

 İdeal hizalama ve dengeyi elde etmek için simgenin temel öğesini eylem glifleri ile engellemeyi önleyin. Glifi Taban öğesinin sol üst kısmına yerleştirin. Ek bir öğe eklerken, simgenin hizalamasını ve dengesini göz önünde bulundurun.

|**Hizalama ve dengeyi doğru**|**Hizalama ve bakiye yanlış**|
|-|-|
|![Simge dengesini ve hizalamayı Düzeltme](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Yanlış simge dengesi ve hizalaması](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Öğeleri paylaşan ve kümeler halinde kullanılan simgeler için boyut eşliği sağlayın. Yanlış eşleştirmeden, dairenin ve okun büyük boyutlu olduğunu ve eşleşmediğini unutmayın.

|**Doğru boyut eşliği**|**Yanlış boyut eşliği**|
|-|-|
|![Doğru simge boyutu ve eşliği](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Yanlış simge boyutu ve eşlik](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Tutarlı çizgi ve görsel ağırlıklar kullanın. Oluşturduğunuz simgenin yan yana karşılaştırma kullanarak diğer simgelere nasıl Karşılaştırıldığı değerlendirin. Tüm 16x16 çerçevesini hiçbir şekilde kullanmayın, 15x15 veya daha küçük kullanın. Negatif-pozitif (koyu-hafif) oran 50/50 olmalıdır.

|**Sıfırdan olumlu oranı doğru yapın**|**Negatif-pozitif oranına yanlış**|
|-|-|
|![Simgeler &#40;1&#41;için görsel ağırlığı düzeltin ](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Simgeler &#40;2&#41;için görsel ağırlığı düzeltin ](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Simgeler &#40;3&#41;için doğru görsel ağırlığı ](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Simgeler için yanlış görsel ağırlık](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Öğeleri öğe bütünlüğünden ödün vermeden derlemek için basit, karşılaştırılabilir şekiller ve tamamlayıcı açıları kullanın. Mümkün olduğunda 45 ° veya 90 ° açı kullanın.

 ![Simge açılarla doğru](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektif
 Simgenin işaretini kaldırın ve anlaşılır durumda tutun. Yalnızca gerektiğinde perspektif ve hafif kaynak kullanın. Simge öğelerinde perspektif kullanılması önlenebilir olsa da, bazı öğeler bu olmadan tanınmıyor. Bu gibi durumlarda, stilize bir perspektif öğenin netliğini iletişim kurar.

 ![3 noktalı perspektif](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3 noktalı perspektif

 ![1 noktalı perspektif](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1 noktalı perspektif

 Çoğu öğe doğru veya sağa açılı olmalıdır:

 ![Simgeler açılı sağ](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Hafif kaynakları yalnızca bir nesneye gerekli açıklık eklerken kullanın.

|**Doğru ışık kaynağı**|**Hatalı ışık kaynağı**|
|-|-|
|![Simgeler için ışık kaynaklarını düzeltin](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Simgeler için hatalı açık kaynaklar](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Yalnızca okunabilirliği geliştirmek veya metaphor ile daha iyi iletişim kurmak için anahatları kullanın. Negatif pozitif (koyu-hafif) bakiye 50/50 olmalıdır.

|**Ana hatlarıyla doğru kullanımı**|**Anahatların yanlış kullanımı**|
|-|-|
|![Doğru anahatlar](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Yanlış anahatlar](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Simge türleri
 **Kabuk ve komut çubuğu** simgeleri şu öğelerden üçten fazla değil: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Kabuk ve komut çubuğu simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Kabuk ve komut çubuğu simgeleri örnekleri

 **Araç penceresi komut çubuğu** simgeleri şu öğelerden üçten fazla değil: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Araç penceresi komut çubuğu simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Araç penceresi komut çubuğu simgeleri örnekleri

 **Ağaç görünümü Kesinleştirme** simgeleri şu öğelerden üçten fazla değil: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Ağaç görünümü Kesinleştirme simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Ağaç görünümü Kesinleştirme simgeleri örnekleri

 Şu durumlarda **durum tabanlı değer taksonomi** simgeleri var: etkin, etkin devre dışı ve etkin olmayan devre dışı.

 ![Durum tabanlı değer taksonomi simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Durum tabanlı değer taksonomi simgeleri örnekleri

 **IntelliSense** simgeleri şu öğelerden üçten fazla değil: bir temel, bir değiştirici ve bir durum.

 ![IntelliSense simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />IntelliSense simgeleri örnekleri

 **Küçük (16x16) proje** simgelerinin ikiden fazla öğe olmaması gerekir: bir temel ve bir değiştirici.

 ![Küçük (16x16) proje simgeleri](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16X16 proje simgesine örnek &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 proje simgesi &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Küçük (16x16) proje simgeleri örnekleri

 **Büyük (32x32) proje** simgeleri aşağıdaki öğelerin dörtten fazla değil: bir temel, biri iki değiştiricinin ve bir dil kaplaması.

 ![Büyük (32x32) proje simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Büyük (32x32) proje simgeleri örnekleri

### <a name="production-details"></a>Üretim ayrıntıları
 Tüm yeni kullanıcı arabirimi öğeleri Windows Presentation Foundation (WPF) kullanılarak oluşturulmalıdır ve WPF için tüm yeni simgeler 32 bit PNG biçiminde olmalıdır. 24 bit PNG, saydamlığı desteklemeyen eski bir biçimdir ve bu nedenle simgeler için önerilmez.

 Çözünürlüğü 96 DPI adresinden tasarruf edin.

#### <a name="file-types"></a>Dosya türleri

- **32-BIT png:** simgeler için tercih edilen biçim. Tek bir raster (piksel) görüntüsünü depolayabilen kayıpsız bir veri sıkıştırma dosyası biçimi. 32-bit PNG dosyaları alfa kanalı saydamlığını, Gamma düzeltmesini ve taramayı destekler.

- **32-BIT BMP:** WPF olmayan denetimler için. Ayrıca, XP veya yüksek renk olarak da bilinen 32-bit BMP, alfa kanalı saydamlığı olan gerçek renkli bir resim olan bir RGB/A görüntü biçimidir. Alfa kanalı, Adobe Photoshop 'ta belirlenmiş bir saydamlık katmanıdır ve daha sonra bit eşlem içinde ek (dördüncü) renk kanalı olarak kaydedilir. Renk derinliği hakkında hızlı bir görsel ipucu sağlamak için tüm 32-bit BMP dosyalarına resim üretimi sırasında siyah bir arka plan eklenir. Bu siyah arka plan, Kullanıcı arabiriminde maskelenecek alanı temsil eder.

- **32-BIT ICO:** proje simgeleri Için ve öğe Ekle. Tüm ICO dosyaları alfa kanalı saydamlığı (RGB/A) ile 32 bitlik gerçek renktedir. ICO dosyaları birden çok boyut ve renk derinlikleri depolayabildiğinden, Vista simgeleri genellikle 16x16, 32x32, 48x48 ve 256x256 görüntü boyutlarını içeren bir ICO biçimindedir. Windows Gezgini 'nde düzgün şekilde görüntülenebilmesi için, ICO dosyalarının her görüntü boyutu için 24 bit ve 8 bit renk derinlikleri ile kaydedilmesi gerekir.

- **XAML:** tasarım yüzeyleri ve Windows donatıcıları için. XAML simgeleri ölçekleme, döndürme, dosyalama ve saydamlığı destekleyen vektör tabanlı görüntü dosyalarıdır. Bunlar, Visual Studio 'da bugün yaygın değildir ancak esnekliği nedeniyle daha popüler hale gelmektedir.

- **SVG**

- **24 BIT BMP:** Visual Studio komut çubuğu için. Doğru renkli bir RGB görüntü biçimi olan 24 bit BMP, bir gizleme saydamlık katmanı için bir renk tuşu olarak macenta (R = 255, G = 0, B = 255) kullanarak saydamlık katmanı oluşturan bir simge kuralıdır. 24 bit BMP 'de, tüm Macenta yüzeyler arka plan rengi kullanılarak görüntülenir.

- **24 BIT GIF:** Visual Studio komut çubuğu için. Saydamlığı destekleyen gerçek renkli bir RGB resim biçimi. GIF dosyaları genellikle sihirbaz resminde ve GIF animasyonlarında kullanılır.

### <a name="icon-construction"></a>Simge oluşturma
 Visual Studio 'da en küçük simge boyutu 16x16 'dir. Yaygın kullanımda olan en büyük değer 32x32 ' dir. Bir simge tasarlarken 16x16, 24x24 veya 32x32 çerçevesinin tamamını doldurmayacağınızı unutmayın. Okunaklı bir simge oluşturma, Kullanıcı tanıma için önemlidir. Simge oluştururken aşağıdaki noktalara uyar.

- Simgeler net, anlaşılır ve tutarlı olmalıdır.

- Durum bildirim öğelerini bir simge temel öğesinin üzerine yığmak için tek simgeler olarak kullanmak daha iyidir. Bazı bağlamlarda, Kullanıcı Arabirimi durum öğesinin bir temel öğeyle eşlenmesini gerektirebilir.

- Proje simgeleri genellikle birkaç boyut içeren. ico dosyalarıdır. Yalnızca 16x16, 24x24 ve 32x32 simgeleri güncelleştiriliyor. Çoğu 16x16 ve 24x24 simge aynı öğeleri içerir. 32x32 simgeleri, uygunsa proje dili türü de dahil olmak üzere daha fazla ayrıntı içerir.

- 32x32 simgeleri için, temel öğelerin genellikle 2 piksellik bir çizgi ağırlığı vardır. Ayrıntı öğeleri için 1 veya 2 piksellik çizgi kalınlığı kullanılabilir. Hangisinin daha uygun olduğunu öğrenmek için en iyi kararlarınızı kullanın.

- 16x16 ve 24x24 simgelerinin öğeleri arasında en az 1 piksellik bir boşluk vardır. 32x32 simgeleri için, öğeler arasında ve değiştirici ile temel öğe arasında 2 piksellik boşluk kullanın.

  ![Boyut 16x16, 24x24 ve 32x32 simgeleri için öğe boşluğu](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Boyut 16x16, 24x24 ve 32x32 simgeleri için öğe boşluğu

#### <a name="color-and-accessibility"></a>Renk ve erişilebilirlik
 Visual Studio uyumluluk yönergeleri, üründeki tüm simgelerin renk ve kontrast için erişilebilirlik gereksinimlerini geçmesini gerektirir. Bu, Icon Inversion aracılığıyla elde edilir ve tasarım yaparken, ürünün programlamayla program aracılığıyla tersine çevrilecektir.

 Visual Studio simgelerinde renk kullanma hakkında daha fazla bilgi için bkz. [görüntülerde renk kullanma](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Görüntülerde renk kullanma

### <a name="overview"></a>Genel Bakış
 Visual Studio 'daki simgeler temelde tek bir görseldir. Renk, belirli bilgileri iletmek ve hiçbir şekilde süslemesi için ayrılmıştır. Renk kullanılır:

- bir eylemi belirtmek için

- kullanıcıyı bir durum bildirimine uyarma

- Dil ilişkisini belirlemek için

- IntelliSense içindeki öğeleri ayırt etmek için

### <a name="accessibility"></a>Erişilebilirlik
 Visual Studio uyumluluk yönergeleri, ürüne işaretlenmiş tüm simgelerin renk ve kontrast için erişilebilirlik gereksinimlerini geçirmesini gerektirir. Görsel dil paletindeki renkler test edilmiştir ve bu gereksinimleri karşılar.

#### <a name="color-inversion-for-dark-themes"></a>Koyu Temalar için Color Inversion
 Simgelerin, Visual Studio koyu temasının doğru kontrast oranıyla görünmesi için bir Inversion programlı olarak uygulanır. Bu kılavuzdaki renkler, doğru şekilde ters çevirmeleri için bölümünde seçilmiştir. Renk kullanımını Bu palete sınırlayın veya Inversion uygulandığında öngörülemeyen sonuçlara sahip olursunuz.

 ![Renkleri tersine çevrilmiş simgelere örnek olarak](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Renkleri tersine çevrilmiş simgelere örnek olarak

### <a name="base-palette"></a>Temel palet
 Tüm standart simgeler üç temel renk içerir. Simgeler, 3B araç simgeleri için bir veya iki özel durum ile degradeler veya bırakma gölgeleri içermez.

|Kullanım|Name|Değer (açık Tema)|Basılı|Örnek|
|-----------|----------|---------------------------|------------|-------------|
|Arka plan/koyu|VS BG|424242/66, 66, 66|![Renk örneği 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Temel palet örneği](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Ön plan/açık|VS FG|F0EFF1/240.239.241|![F0EFF1 örneği](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Ana hat|KARŞı|F6F6F6/246.246.246|![F6F6F6 örneği](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Taban renklere ek olarak, her simge genişletilmiş paletten bir ek renk içerebilir.

### <a name="extended-palette"></a>Genişletilmiş palet

#### <a name="action-modifiers"></a>Eylem değiştiricileri
 Aşağıdaki dört renk, eylem değiştiricilerine gereken eylem türlerini gösterir:

|Kullanım|Name|Değer (tüm temalar)|Basılı|
|-----------|----------|--------------------------|------------|
|Pozitif|VS eylemi yeşil|388A34/56138, 52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negatif|VS eylemi Red|A1260D/161, 38, 13|![A1260D örneği](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Nötr|VS eylemi mavi|00539C/0, 83156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Oluştur/yeni|VS eylemi turuncu|C27D1A/194156, 26|![C27D1A örneği](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Örnekler
 Yeşil, "Ekle", "Çalıştır", "Play" ve "Validate" gibi pozitif eylem değiştiricilerinde kullanılır.

|Çalıştır|Sorguyu Yürüt|Tüm adımları Yürüt|Denetim Ekle|
|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Sorgu simgesini Yürüt](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Tüm adımları Yürüt simgesi](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Denetim simgesi ekle](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Kırmızı, "Sil", "Durdur", "Iptal" ve "Kapat" gibi negatif Eylem değiştiricileri için kullanılır.

|İlişkiyi Sil|Sütunu Sil|Sorguyu durdur|Çevrimdışı bağlantı|
|-|-|-|-|
|![İlişki Sil simgesi](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Sütun Sil simgesi](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Sorgu simgesini durdur](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Çevrimdışı bağlantı simgesi](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Mavi, "Aç", "Next," "Previous," "Import," ve "Export" gibi en yaygın olarak oklar olarak temsil edilen bağımsız eylem değiştiricilerine uygulanır.

|Alana git|Toplu Iade etme|Adres Düzenleyicisi|İlişkilendirme Düzenleyicisi|
|-|-|-|-|
|![Alan simgesine git](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Toplu denetim&#45;simgesi](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Adres Düzenleyicisi simgesi](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![İlişkilendirme düzenleyici simgesi](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 Koyu altın öncelikle "yeni" değiştiricisi için kullanılır.

|Yeni Proje|Yeni grafik oluştur|Yeni birim testi|Yeni liste öğesi|
|-|-|-|-|
|![Yeni proje simgesi](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Yeni grafik simgesi oluştur](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Yeni birim testi simgesi](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Yeni liste öğesi simgesi](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Özel durumlar
 Özel durumlarda, renkli bir eylem değiştiricisi bağımsız bir simge olarak bağımsız olarak kullanılabilir. Simge için kullanılan renk, simgenin ilişkilendirildiği eylemleri yansıtır. Bu kullanım aşağıdakiler de dahil olmak üzere küçük bir simge alt kümesiyle sınırlandırılmıştır:

|Çalıştır|Durdur|Sil|Kaydet|Geri git|
|-|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Durdur simgesi](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Simgeyi Sil](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Kaydet simgesi](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Geri git simgesi](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Kod hiyerarşisi paleti

#### <a name="folder"></a>Klasör

|Kullanım|Name|Değer (tüm temalar)|Basılı|Örnek|
|-----------|----------|--------------------------|------------|-------------|
|Klasörler|Klasör|DCB67A/220.182.122|![DCB67A örneği](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Klasör rengi simgesi](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio dilleri
 Visual Studio 'da kullanılabilen ortak dillerin veya platformların her biri ilişkili bir renge sahiptir. Bu renkler temel simgenin üzerinde veya bileşik simgelerin sağ üst köşesinde görünen dil değiştiricilerinde kullanılır.

|Kullanım|Name|Değer (tüm temalar)|Basılı|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF mavi|0095D7/0149.215|![Renk örneği 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP mor|9B4F96/155, 79150|![Renk örneği 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS yeşil (VS eylemi yeşil)|388A34/56138, 52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS Red|BD1E2D/, 30, 45|![BD1E2D örneği](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS mor|672878/103, 40120|![Renk örneği 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS turuncu|F16421/241100, 33|![F16421 örneği](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB mavi (VS eylemi mavi)|00539C/0, 83156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TH turuncu|E04C06/224, 76, 6|![E04C06 örneği](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|Yeşil Kopyala|879636/135150, 54|![Renk örneği 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Dil değiştiricilerine sahip simgeler örnekleri

|VB|C#|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Visual Basic simgesi](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![C&#35; simgesi](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![C&#43;&#43; simgesi](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![F&#35; simgesi](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![JavaScript simgesi](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Python simgesi](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|-|
|![HTML simgesi](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF simgesi](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP simgesi](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS simgesi](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript simgesi](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 IntelliSense simgeleri özel bir renk paleti kullanır. Bu renkler, kullanıcıların IntelliSense açılan listesinde farklı öğeler arasında hızlı bir şekilde ayrım yapmanıza yardımcı olmak için kullanılır.

|Kullanım|Name|Değer (tüm temalar)|Basılı|
|-----------|----------|--------------------------|------------|
|Sınıf, olay|VS eylemi turuncu|C27D1A/194125, 26|![C27D1A örneği](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Genişletme yöntemi, yöntemi, modülü, temsilci|VS eylemi mor|652D90/101, 45144|![Renk örneği 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Alan, Enum öğesi, makro, yapı, birleşim değeri türü, Işleç, arabirim|VS eylemi mavi|00539C/0, 83156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Nesne|VS eylemi yeşil|388A34/56138, 52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Sabit, özel durum, sabit listesi öğesi, eşleme, eşleme öğesi, ad alanı, şablon, tür tanımı|Arka plan (VS BG)|424242/66, 66, 66|![Renk örneği 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense simgeleri örnekleri

|Sınıf|Özel olay|Temsilci|Yöntem arkadaş|Alan|
|-|-|-|-|-|
|![IntelliSense sınıf simgesi](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![IntelliSense özel olay simgesi](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![IntelliSense temsilci simgesi](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![IntelliSense yöntemi arkadaş simgesi](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Alan simgesi](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Korumalı Enum öğesi|Nesne|Şablon|Özel durum kısayolu|
|-|-|-|-|
|![IntelliSense korumalı Enum öğesi simgesi](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![IntelliSense nesne simgesi](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![IntelliSense şablon simgesi](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![IntelliSense özel durum kısayol simgesi](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Bildirimler
 Visual Studio 'daki bildirimler, durumu göstermek için kullanılır. Bildirim paleti aşağıdaki durum düzeylerine sahip bildirimleri tanımlamak için aşağıdaki dört rengi ve siyah ya da beyaz ön plan dolgusu seçeneklerini kullanır.

|Kullanım|Name|Değer (tüm temalar)|Basılı|
|-----------|----------|--------------------------|------------|
|Durum: nötr|Uyarı mavi (VS mavi)|1BA1E2/27.161.226|![Renk örneği 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Durum: pozitif|Bildirim yeşili (VS yeşil)|339933/51153, 51|![Renk örneği 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Durum: negatif|Kırmızı bildirim (-kırmızı)|E51400/229, 20, 0|![E51400 örneği](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Durum: uyarı|Bildirim sarı (VS turuncu)|FFCC00/255204, 0|![FFCC00 örneği](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Ön plan dolgusu|Siyah bildirim (siyah)|000000 yazın/0, 0, 0|![Renk &#35;000000 yazın](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Ön plan dolgusu|Bildirim beyaz (beyaz)|FFFFFF/255.255.255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Bildirim simgeleri örnekleri

|Uyarı|Uyarı|Tamamla|Durdur|
|-|-|-|-|
|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Tamam simgesi](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Durdur simgesi](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|