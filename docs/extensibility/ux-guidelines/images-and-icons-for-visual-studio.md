---
title: Visual Studio için görüntüler ve simgeler | Microsoft Docs
description: Visual Studio görüntülerini ve simgelerini oluşturmak için kullanılan tasarım kavramları hakkında bilgi edinin.
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ca7eea3b88b6cfe38bd0d1be568b9aeaf5e329ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028936"
---
# <a name="images-and-icons-for-visual-studio"></a>Visual Studio İçin Görüntüler ve Simgeler
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Visual Studio görüntü kullanımı
 resim oluşturmadan önce [Visual Studio görüntü kitaplığındaki](https://www.microsoft.com/download/details.aspx?id=35825)1000 + görüntüden birini kullanmayı düşünün.

### <a name="types-of-images"></a>Görüntü türleri

- **Simgeler**. Komutlarda, hiyerarşilerde, şablonlarda ve benzeri görünen küçük görüntüler. Visual Studio için kullanılan varsayılan simge boyutu 16x16 PNG 'dir. Görüntü hizmeti tarafından üretilen simgeler otomatik olarak HDPı desteği için XAML biçimini oluşturur.

    > [!NOTE]
    > Görüntüler menü sisteminde kullanıldığında, her komut için bir simge oluşturmamalıdır. komutlarınızın bir simge alması gerekip gerekmediğini görmek için [Visual Studio menülere ve komutlara](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) danışın.

- **Küçük resimleri.** yeni Project iletişim kutusu gibi bir iletişim kutusunun önizleme alanında kullanılan görüntüler.

- **İletişim kutusu görüntüleri.** Açıklayıcı grafikler veya ileti göstergeleri olarak iletişim kutularında ya da sihirbazlarda görünen görüntüler. Yalnızca zor bir kavram göstermek veya kullanıcının dikkatini çekmek (uyarı, uyarı) için gerekli olduğunda seyrek ve yalnızca kullanın.

- **Animasyonlu görüntüler.** Devam eden göstergeler, durum çubukları ve işlem iletişim kutularında kullanılır.

- **İmleçler.** Bir işlemin fare kullanarak izin verilip verilmeyeceğini belirtmek için kullanılır, burada bir nesne bırakılabilir ve bu şekilde devam eder.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a> Simge tasarımı

### <a name="overview"></a>Genel Bakış
 Visual Studio, temiz geometri ve 50/50 bir pozitif/negatif (açık/koyu) bakiyesi olan modern stil simgeleri kullanır ve doğrudan, anlaşılabilir metaphiler kullanır. Netme, basitleştirme ve bağlam etrafında önemli simge tasarım noktaları merkezi.

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
 Visual Studio, kullanıcı arabirimi içinde çok çeşitli simge türleri içeriyor. Geliştirme sırasında simge türünü dikkatle düşünün. Simge öğeleriniz için belirsiz veya seyrek olmayan UI nesneleri kullanmayın. Akıllı etiket simgesiyle birlikte bu durumlarda sembolik için kabul edin. Soldaki soyut etiketin anlamı, sağdaki Kullanıcı arabirimi tabanlı sürümden daha belirgin olduğunu unutmayın:

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

 ![Visual Studio bağımsız bildirimler](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Tek başına bildirim simgeleri

 ![Görev tamamlanma simgesi](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Görev tamamlanma simgesi

 Project simgeler genellikle birden çok boyut içeren. ico dosyalarıdır. En çok 16x16 simgesi aynı öğeleri içerir. 32x32 sürümlerinde, uygun olduğunda proje türü de dahil olmak üzere daha fazla ayrıntı vardır.

 ![Visual Studio simgeleri Project](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />VB Windows denetim kitaplığı Project simgeleri, 16x16 ve 32x32

 Bir simgeyi piksel çerçevesi içinde ortalayın. Bu mümkün değilse, simgeyi çerçevenin üst ve/veya sağına hizalayın.

 ![Piksel çerçevesi içinde ortalanmış simge](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Piksel çerçevesi içinde ortalanmış simge

 ![Piksel çerçevesinin sağ üst kısmına hizalanmış simge](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Çerçevenin sağ üst köşesindeki simge

 ![Ortalanmış ve piksel çerçevesinin üstüne hizalanmış simge](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Ortalanmış ve çerçevenin en üstüne hizalanmış simge

 İdeal hizalama ve denge elde etmek için simgenin temel öğesini eylem klifleriyle tıkamaktan kaçının. Glyph'i temel öğenin sol üst yanına yakın bir yere yer. Ek öğe eklerken simgenin hizalamasını ve dengelerini göz önünde bulundurabilirsiniz.

|**Hizalamayı ve dengeyi düzeltme**|**Yanlış hizalama ve bakiye**|
|-|-|
|![Doğru simge bakiyesi ve hizalaması](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Yanlış simge bakiyesi ve hizalaması](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Öğeleri ve kümelerde kullanılan simgelerin boyut eşlikli olduğundan emin olur. Yanlış eşleştirmede dairenin ve okun fazla büyük olduğunu ve eşleşme olmadığını unutmayın.

|**Doğru boyut eşlik**|**Yanlış boyut eşlik**|
|-|-|
|![Doğru simge boyutu ve eşlik](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Yanlış simge boyutu ve eşlik](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Tutarlı çizgi ve görsel ağırlıklar kullanın. Yan yana karşılaştırma kullanarak, bina simgenin diğer simgelerle karşılaştırılmasını değerlendirin. Hiçbir zaman 16x16 çerçevenin tamamını, 15x15 veya daha küçük bir çerçeveyi kullanmayın. Negatif-pozitif (koyu-açık) oranı 50/50 olmalıdır.

|**Negatif-pozitif oranını düzeltme**|**Hatalı negatif-pozitif oranı**|
|-|-|
|![Simgeler için görsel ağırlığı &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Simgeler için görsel ağırlığı &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Simgeler için görsel ağırlığı &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Simgeler için yanlış görsel ağırlığı](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Öğe bütünlüğünden ödün vermeden öğelerinizi oluşturmak için basit, karşılaştırılabilir şekiller ve tamamlayıcı açılar kullanın. Mümkün olduğunca 45° veya 90° açı kullanın.

 ![Simge açılarını düzeltme](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektif
 Simgeyi net ve anlaşılır bir şekilde tutma. Perspektifi ve açık kaynağı yalnızca gerekli olduğunda kullanın. Simge öğelerinde perspektif kullanmaktan kaçınılmalıdır, ancak bazı öğeler bu olmadan tanınamaz. Böyle durumlarda, stilize edilmiş bir perspektif öğenin netliğini iletir.

 ![3 noktalı perspektif](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3 noktalı perspektif

 ![1 nokta perspektifi](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1 nokta perspektifi

 Çoğu öğenin sağa dönük veya açılı olması gerekir:

 ![Sağa açılı simgeler](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Yalnızca bir nesneye gerekli netliği eklerken açık kaynakları kullanın.

|**Doğru açık kaynak**|**Yanlış açık kaynak**|
|-|-|
|![Simgeler için açık kaynakları düzeltme](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Simgeler için yanlış açık kaynaklar](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Ana hatları yalnızca okunaklılığı geliştirmek veya benzetmeyle daha iyi iletişim kurmak için kullanın. Negatif-pozitif (koyu-açık) bakiye 50/50 olmalıdır.

|**Ana hatların doğru kullanımı**|**Ana hatların yanlış kullanımı**|
|-|-|
|![Ana hatları düzeltme](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Yanlış ana hatlar](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Simge türleri
 **Kabuk ve komut çubuğu** simgeleri şu öğelerden en fazla üçten oluşur: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Kabuk ve komut çubuğu simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Kabuk ve komut çubuğu simgeleri örnekleri

 **Araç penceresi komut çubuğu** simgeleri şu öğelerden en fazla üçten oluşur: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Araç penceresi komut çubuğu simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Araç penceresi komut çubuğu simgeleri örnekleri

 **Ağaç görünümü disambiguator** simgeleri şu öğelerden en fazla üçten oluşur: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Ağaç görünümü disambiguator simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Ağaç görünümü disambiguator simgeleri örnekleri

 **Durum tabanlı değer sınıflandırma simgeleri şu** durumlarda mevcuttur: etkin, etkin devre dışı ve devre dışı.

 ![Durum tabanlı değer sınıflandırma simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Durum tabanlı değer sınıflandırma simgeleri örnekleri

 **IntelliSense** simgeleri şu öğelerden en fazla üçten oluşur: bir temel, bir değiştirici ve bir durum.

 ![IntelliSense simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />IntelliSense simgeleri örnekleri

 **Küçük (16x16)** proje simgelerinin en fazla iki öğeye sahip olması gerekir: bir temel ve bir değiştirici.

 ![Küçük (16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![proje simgelerinin örnekleri 16x16 proje simgesi &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3") proje simgesi &#40;3&#41;<br />Küçük (16x16) proje simgeleri örnekleri

 **Büyük (32x32)** proje simgeleri şu öğelerden en fazla dört taneden oluşur: bir temel, bire iki değiştirici ve bir dil katman.

 ![Büyük (32x32) proje simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Büyük (32x32) proje simgeleri örnekleri

### <a name="production-details"></a>Üretim ayrıntıları
 Tüm yeni kullanıcı arabirimi öğeleri Windows Presentation Foundation (WPF) kullanılarak oluşturulmalı ve WPF için tüm yeni simgeler 32 bit PNG biçiminde olmalıdır. 24 bit PNG, saydamlığı desteklemez ve bu nedenle simgeler için önerilmez.

 Çözünürlüğü 96 DPI olarak kaydedin.

#### <a name="file-types"></a>Dosya türleri

- **32 bit PNG: Simgeler** için tercih edilen biçim. Tek bir tarama (piksel) görüntüsünü depolayabilirsiniz kayıpsız veri sıkıştırma dosyası biçimi. 32 bit PNG dosyaları alfa kanal saydamlığını, düzeltmeyi ve ara özelliği destekler.

- **32 bit BMP:** WPF olmayan denetimler için. XP veya yüksek renk olarak da adlandırılan 32 bit BMP, bir RGB/A görüntü biçimidir ve alfa kanalı saydamlığı olan gerçek renkli bir resimdir. Alfa kanal, Adobe Adobe Adobe'de belirlenen ve ardından bit eşlem içinde ek (dördüncü) renk kanalı olarak kaydedilen bir saydamlık katmanıdır. Renk derinliği hakkında hızlı bir görsel ipucu sağlamak için 32 bitlik tüm BMP dosyalarına sanat çalışmaları sırasında siyah bir arka plan eklenir. Bu siyah arka plan, kullanıcı arabiriminde maskelenmiş alanı temsil eder.

- **32 bit ICO:** Project ve Öğe Ekle için. Tüm ICO dosyaları, alfa kanal saydamlığı (RGB/A) ile 32 bit gerçek renktir. ICO dosyaları birden çok boyut ve renk derinliği depolayana kadar Vista simgeleri genellikle 16x16, 32x32, 48x48 ve 256x256 görüntü boyutlarını içeren bir ICO biçimindedir. Windows Gezgini'nde düzgün bir şekilde görüntülemek için ICO dosyalarının her görüntü boyutu için 24 bit ve 8 bit renk derinliklerine indirgenmiş olması gerekir.

- **XAML:** Tasarım yüzeyleri ve Windows için. XAML simgeleri ölçeklendirme, döndürme, dosyalama ve saydamlığı destekleyen vektör tabanlı görüntü dosyalarıdır. Günümüzde bu Visual Studio yaygın değildir, ancak esneklikleri nedeniyle daha popüler hale geliyor.

- **Svg**

- **24 bit BMP:** Visual Studio çubuğu için. Gerçek renkli RGB görüntü biçimi olan 24 bit BMP, saydam saydamlık katmanı için renk anahtarı olarak magenta (R=255, G=0, B=255) kullanarak bir saydamlık katmanı oluşturan simge kuralıdır. 24 bit BMP'de tüm magenta yüzeyleri arka plan rengi kullanılarak görüntülenir.

- **24 bit GIF:** Visual Studio çubuğu için. Saydamlığı destekleyen bir gerçek renk RGB görüntü biçimi. GIF dosyaları genellikle Sihirbaz resmi ve GIF animasyonlarında kullanılır.

### <a name="icon-construction"></a>Simge yapısı
 Uygulamanın en küçük simge boyutu Visual Studio 16x16'dır. Yaygın olarak kullanılan en büyük kullanım 32x32'dir. Simge tasarlarken 16x16, 24x24 veya 32x32 çerçevenin tamamını doldurmamalarını unutmayın. Okunaklı, tekdüze simge yapısı, kullanıcı tanıma için önemlidir. Simgeleri inşa etmek için aşağıdaki noktalara uyun.

- Simgeler net, anlaşılır ve tutarlı olmalıdır.

- Durum bildirimi öğelerini tek simge olarak kullanmak ve bunları bir simge temel öğesinin üzerine yığmamak daha iyidir. Belirli bağlamlarda, kullanıcı arabirimi durum öğesinin bir temel öğe ile eşleştirilmiş olması gerektirebilir.

- Project simgeleri genellikle çeşitli boyutlara sahip .ico dosyalarıdır. Yalnızca 16x16, 24x24 ve 32x32 simgeleri güncelleştiriliyor. Çoğu 16x16 ve 24x24 simgeleri aynı öğeleri içerir. 32x32 simgeleri, uygun olduğunda proje dil türü de dahil olmak üzere daha fazla ayrıntı içerir.

- 32x32 simgeleri için temel öğeler genellikle 2 piksel çizgi ağırlığına sahiptir. Ayrıntı öğeleri için 1 veya 2 piksel çizgi ağırlığı kullanılabilir. Hangisinin daha uygun olduğunu belirlemek için en iyi kararınızı kullanın.

- 16x16 ve 24x24 simgeleri için öğeler arasında en az 1 piksel boşluk içerir. 32x32 simgeleri için öğeler arasında ve değiştirici ile temel öğe arasında 2 piksellik boşluk kullanın.

  ![16x16, 24x24 ve 32x32 boyutlu simgeler için öğe aralığı](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />16x16, 24x24 ve 32x32 boyutlu simgeler için öğe aralığı

#### <a name="color-and-accessibility"></a>Renk ve erişilebilirlik
 Visual Studio uyumluluk yönergeleri, üründe yer alan tüm simgelerin renk ve karşıtlık için erişilebilirlik gereksinimlerini geçmelerini gerektirir. Bu, simge ters çevirme yoluyla lenir ve tasarımını tamamlarsanız, bunların üründe program aracılığıyla ters çevireceklerini fark ediyorsanız.

 Simgelerde renk kullanma hakkında daha fazla Visual Studio için [bkz. Görüntülerde renk kullanma.](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages)

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Görüntülerde renk kullanma

### <a name="overview"></a>Genel Bakış
 Visual Studio simgeler öncelikli olarak monokromatiktir. Renk, belirli bilgileri iletmek için ayrılmıştır ve hiçbir zaman süsleme için ayrılmıştır. Renk kullanılır:

- bir eylemi göstermek için

- bir durum bildirimi için kullanıcıya uyarı

- dil ilişkilerini atama

- IntelliSense içindeki öğeleri ayırt etmek için

### <a name="accessibility"></a>Erişilebilirlik
 Visual Studio uyumluluk yönergeleri, ürüne iade olan tüm simgelerin renk ve karşıtlık için erişilebilirlik gereksinimlerini geçmelerini gerektirir. Görsel dil paletinde renkler test edilmiştir ve bu gereksinimleri karşılar.

#### <a name="color-inversion-for-dark-themes"></a>Koyu temalar için renk ters çevirme
 Simgelerin koyu temada doğru karşıtlık oranıyla Visual Studio için program aracılığıyla bir ters çevirme uygulanır. Bu kılavuzda yer alan renkler kısmen seçilmiştir ve doğru şekilde ters çevirilmelidir. Renk kullanımınızı bu paletle kısıtlar veya ters çevirme uygulandığında öngörülemeyen sonuçlar elde edilir.

 ![Renkleri ters çeviren simge örnekleri](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Renkleri ters çeviren simge örnekleri

### <a name="base-palette"></a>Temel palet
 Tüm standart simgeler üç temel renk içerir. Simgeler, 3D araç simgeleri için bir veya iki özel durum dışında hiçbir gradyan veya bırakma gölgesi içermez.

|Kullanım|Name|Değer (Açık tema)|Swatch|Örnek|
|-----------|----------|---------------------------|------------|-------------|
|Arka Plan/Koyu|VS BG|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Temel palet örneği](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Ön Plan/Açık|VS FG|F0EFF1 / 240.239.241|![Swatch F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Ana hat|VS Out|F6F6F6 / 246,246,246|![Swatch F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Temel renklere ek olarak, her simge genişletilmiş paletden bir tane daha renk içerebilir.

### <a name="extended-palette"></a>Genişletilmiş palet

#### <a name="action-modifiers"></a>Eylem değiştiricileri
 Aşağıdaki dört renk, eylem değiştiricileri için gereken eylem türlerini gösterir:

|Kullanım|Name|Değer (tüm temalar)|Swatch|
|-----------|----------|--------------------------|------------|
|Pozitif|VS Action Green|388A34 / 56.138.52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negatif|VS Action Red|A1260D / 161,38,13|![Swatch A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Nötr|VS Action Blue|00539C / 0,83.156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Oluştur/Yeni|VS Action Orange|C27D1A / 194,156,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Örnekler
 Yeşil, "Ekle", "Çalıştır", "Oynat" ve "Doğrula" gibi pozitif eylem değiştiricileri için kullanılır.

|Çalıştır|Sorguyu yürütme|Tüm adımları oynatma|Denetim Ekle|
|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Sorguyu yürüt simgesi](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Tüm adımları oynat simgesi](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Denetim ekle simgesi](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Kırmızı, "Sil", "Durdur", "İptal" ve "Kapat" gibi negatif eylem değiştiricileri için kullanılır.

|İlişkiyi Sil|Sütunu Sil|Sorguyu durdur|Çevrimdışı bağlantı|
|-|-|-|-|
|![İlişki Sil simgesi](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Sütun Sil simgesi](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Sorgu simgesini durdur](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Çevrimdışı bağlantı simgesi](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Mavi, "Aç", "Next," "Previous," "Import," ve "Export" gibi en yaygın olarak oklar olarak temsil edilen bağımsız eylem değiştiricilerine uygulanır.

|Alana git|Toplu Check-In|Adres Düzenleyicisi|İlişkilendirme Düzenleyicisi|
|-|-|-|-|
|![Alan simgesine git](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Toplu denetim&#45;simgesi](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Adres Düzenleyicisi simgesi](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![İlişkilendirme düzenleyici simgesi](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 Koyu altın öncelikle "yeni" değiştiricisi için kullanılır.

|Yeni Proje|Yeni Graph oluştur|Yeni birim testi|Yeni liste öğesi|
|-|-|-|-|
|![Yeni proje simgesi](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Yeni grafik simgesi oluştur](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Yeni birim testi simgesi](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Yeni liste öğesi simgesi](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Özel durumlar
 Özel durumlarda, renkli bir eylem değiştiricisi bağımsız bir simge olarak bağımsız olarak kullanılabilir. Simge için kullanılan renk, simgenin ilişkilendirildiği eylemleri yansıtır. Bu kullanım aşağıdakiler de dahil olmak üzere küçük bir simge alt kümesiyle sınırlandırılmıştır:

|Çalıştır|Durdur|Sil|Kaydet|Geri git|
|-|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Durdur simgesi-düz kırmızı kare.](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Simgeyi Sil](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Kaydet simgesi](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Geri git simgesi](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Kod hiyerarşisi paleti

#### <a name="folder"></a>Klasör

|Kullanım|Name|Değer (tüm temalar)|Basılı|Örnek|
|-----------|----------|--------------------------|------------|-------------|
|Klasörler|Klasör|DCB67A/220.182.122|![DCB67A örneği](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Klasör rengi simgesi](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio dilleri
 Visual Studio bulunan ortak dillerin veya platformların her biri ilişkili bir renge sahiptir. Bu renkler temel simgenin üzerinde veya bileşik simgelerin sağ üst köşesinde görünen dil değiştiricilerinde kullanılır.

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

|VB|C#|C++|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Visual Basic simgesi](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![C&#35; simgesi](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![C&#43;&#43; simgesi](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![F&#35; simgesi](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![JavaScript simgesi](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Python simgesi](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|
|![HTML simgesi](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF simgesi](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP simgesi](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS simgesi](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript simgesi](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript|

#### <a name="intellisense"></a>IntelliSense
 IntelliSense simgeleri özel bir renk paleti kullanır. Bu renkler, kullanıcıların IntelliSense açılan listesinde yer alan farklı öğeler arasında hızla ayrım yapmak için kullanılır.

|Kullanım|Name|Değer (tüm temalar)|Swatch|
|-----------|----------|--------------------------|------------|
|Sınıf, Olay|VS Action Orange|C27D1A / 194,125,26|![Swatch C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Uzantı Yöntemi, Yöntem, Modül, Temsilci|VS Action Purple|652D90 / 101,45,144|![Swatch 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Alan, Enum Öğesi, Makro, Yapı, Union Değer Türü, İşleç, Arabirim|VS Action Blue|00539C / 0,83.156|![Swatch 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Nesne|VS Action Green|388A34 / 56.138.52|![Swatch 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Sabit, Özel Durum, Sabit Öğe, Eşleme, Eşleme Öğesi, Ad Alanı, Şablon, Tür Tanımı|Arka Plan (VS BG)|424242 / 66,66,66|![Swatch 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense simgeleri örnekleri

|Sınıf|Özel Olay|Temsilci|Yöntem Arkadaşı|Alan|
|-|-|-|-|-|
|![IntelliSense sınıf simgesi](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![IntelliSense özel olay simgesi](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![IntelliSense temsilci simgesi](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![IntelliSense yöntemi arkadaş simgesi](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Alan simgesi](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Korumalı Enum Öğesi|Nesne|Şablon|Özel Durum Kısayolu|
|-|-|-|-|
|![IntelliSense korumalı enum öğesi simgesi](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![IntelliSense nesne simgesi](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![IntelliSense şablon simgesi](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![IntelliSense özel durum kısayol simgesi](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Bildirimler
 Bildirim Visual Studio durumu belirtmek için kullanılır. Bildirim paleti, bildirimleri aşağıdaki durum düzeyleriyle tanımlamak için siyah veya beyaz ön plan dolgu seçeneklerinin yanı sıra aşağıdaki dört rengi kullanır.

|Kullanım|Name|Değer (tüm temalar)|Swatch|
|-----------|----------|--------------------------|------------|
|Durum: nötr|Bildirim Mavisi (VS Blue)|1BA1E2 / 27.161.226|![Swatch 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Durum: pozitif|Bildirim Yeşili (VS Green)|339933 / 51,153,51|![Swatch 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Durum: negatif|Bildirim Kırmızısı (VS Red)|E51400 / 229,20,0|![Swatch E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Durum: uyarı|Bildirim Sarısı (VS Orange)|FFCC00 / 255.204,0|![Swatch FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Ön plan dolgusu|Bildirim Siyah (Siyah)|000000 / 0,0,0|![Swatch &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Ön plan dolgusu|Beyaz Bildirim (Beyaz)|FFFFFF / 255.255.255|![Swatch FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Bildirim simgeleri örnekleri

|Uyarı|Uyarı|Tamamla|Durdur|
|-|-|-|-|
|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Tamam simgesi](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Ortadaki beyaz kareyle düz kırmızı daire simgesini durdur.](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|