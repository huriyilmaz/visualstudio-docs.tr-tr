---
title: Visual Studio için görüntüler ve simgeler | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409245"
---
# <a name="images-and-icons-for-visual-studio"></a>Görüntüler ve Visual Studio için simgeler
## <a name="BKMK_ImageUseInVisualStudio"></a>Visual Studio 'da görüntü kullanımı
 Resim oluşturmadan önce, [Visual Studio Görüntü Kitaplığı](https://www.microsoft.com/download/details.aspx?id=35825)'nda 1000 + görüntüden birini kullanmayı düşünün.

### <a name="types-of-images"></a>Görüntü türleri

- **Simgeler**. Komutlar, hiyerarşileri, şablon ve benzeri görünen küçük resimler. Visual Studio'da kullanılan varsayılan simge boyutu 16 x 16 PNG ' dir. Görüntü hizmeti tarafından otomatik olarak üretilen simgeler HDPI desteği için XAML biçiminde oluşturun.

    > [!NOTE]
    > Görüntüler menü sisteminde kullanıldığında, her komut için bir simge oluşturmamalıdır. Komutlarınızın bir simge alması gerekip gerekmediğini görmek için [Visual Studio Için menülere ve komutlara](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) danışın.

- **Küçük resimleri.** Yeni Proje iletişim kutusu gibi bir iletişim kutusu Önizleme bölümünde kullanılan görüntüler.

- **İletişim kutusu görüntüleri.** Görünen iletişim kutuları veya sihirbazlar, açıklayıcı bir grafik veya ileti göstergeleri olarak görüntüler. Seyrek ve zor bir konsepti açıklamak veya kullanıcının dikkatini (uyarı, uyarı) elde etmek için yalnızca gerekli olduğunda kullanın.

- **Animasyonlu görüntüler.** İlerleme göstergesi, durum çubukları ve işlem iletişim kutuları kullanılır.

- **İmleçler.** Burada bir nesne bırakılabilir vb. fareyi kullanarak bir işlem izin verilip verilmeyeceğini belirtmek için kullanılır.

## <a name="BKMK_IconDesign"></a>Simge tasarımı

### <a name="overview"></a>Genel Bakış
 Visual Studio temiz geometri ve olumlu/olumsuz (Açık/Koyu) 50/50 dengesi ve doğrudan, anlaşılır metaphors kullanan modern stili simgeleri kullanır. Anlaşılabilir olması adına, basitleştirme ve bağlam önemli simgesi tasarım noktaları Merkezi.

- **Netlik:** bir simgenin anlamı ve kişiselleştirme durumunu gösteren çekirdek benzetimini 'a odaklanın.

- Basitlik **:** simgeyi çekirdek anlamı azaltır-yalnızca gerekli öğe (ler) i ve frills olmadan temayı alın.

- **Bağlam:** bir simgenin, temel metaphor 'ın hangi öğelerin oluşturduğunu seçerken çok önemli olan kavram geliştirme sırasında bir simgenin rolünün tüm yönlerini göz önünde bulundurun.

  Simgeler ile birkaç önlemek için tasarım noktaları vardır:

- Uygun olduğunda kullanıcı Arabirimi öğeleri hariç geldiğiniz simgeler kullanmayın. Kullanıcı Arabirimi öğesi ne ortak, yetkisiz değiştirmeye karşı korumalı veya benzersiz değil daha soyut veya sembolik bir yaklaşım belirleyin.

- Belgeler, klasörleri, oklar ve Büyüteç gibi sık kullanılan öğeleri aşırı yok. Bu öğeler simgenin anlamı için yalnızca gerekli olduğunda kullanın. Örneğin, sağ taraftaki Büyüteç yalnızca arama belirtmelidir göz atın ve bulun.

- Bazı eski simge öğeleri perspektif kullanımını korumak olsa da, yeni simgeler olmadan netlik öğesi eksik sürece perspektif ile oluşturmayın.

- Çok fazla simge bilgileri borçlarını yok. Kolayca tanınan veya tanınabilir bir sembol öğrenilen basit bir görüntü çok daha fazla karmaşık bir görüntüden daha kullanışlıdır. Yazının tamamını bir simge bildiremez.

### <a name="icon-creation"></a>Simge oluşturma

#### <a name="concept-development"></a>Kavram geliştirme
 Visual Studio içinde kullanıcı Arabirimi çok çeşitli simge türü vardır. Dikkatli bir şekilde geliştirme sırasında simge türünü göz önünde bulundurun. Belirsiz veya seyrek UI nesneleri simgesi öğeleriniz için kullanmayın. Bu gibi durumlarda, sembolik gibi akıllı etiket simgesiyle tercih. Sol taraftaki soyut etiketin anlamını sağdaki belirsiz, kullanıcı Arabirimi tabanlı sürümden daha belirgin olduğuna dikkat edin:

|||
|-|-|
|**Sembolik canlandırın 'nin doğru kullanımı**|**Sembolik Imagery 'nin yanlış kullanımı**|
|![Doğru akıllı etiket simgesi](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Hatalı akıllı etiket simgesi](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Standart, kolayca tanınabilir kullanıcı Arabirimi öğeleri de simgelerini iş örnekler vardır. Bu tür bir örnek penceredir ekleyin:

|||
|-|-|
|**Bir simgenin içinde doğru Kullanıcı arabirimi öğesi**|**Bir simgede hatalı UI öğesi**|
|![Pencereyi doğru Ekle simgesi](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Yanlış pencere Ekle simgesi](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 Simgenin bir anlamı gerekli olmadıkça temel bir öğe bir belge kullanmayın. Belge öğesi ile yenileme anlamına iletişim kurmak gereksiz iken belge ekleme belge öğesinde (aşağıda) anlamı, kaybolur.

|||
|-|-|
|**Belge simgesinin doğru kullanımı**|**Belge simgesinin yanlış kullanımı**|
|![Doğru belge simgesi](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Belge simgesi yanlış](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 "Show" kavramını simgesiyle en iyi ne gösterilir, gibi tüm dosyaları göster örnek olarak gösterilmiştir temsil edilebilir. Bir mercek benzetme, "Görünüm" gibi gerekiyorsa, kaynak görünümü örnek kavramını göstermek için kullanılabilir.

|||
|-|-|
|**Göster**|**Görünümü**|
|![Simgeyi göster](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Görünüm simgesi](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 Sağ taraftaki temsil yalnızca arayacağı cam simgesi büyütme, bulma ve göz atma. Sol taraftaki türevi artı veya eksi işareti, yalnızca yakınlaştırma temsil / Uzaklaştır.

|||
|-|-|
|**Aramanız**|**Yakınlaştırma**|
|![Arama simgesi](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Yakınlaştır simgesi](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 Ağaç görünümleri klasör simgesini hem bir değiştiricisini kullanmayın. Kullanılabilir olduğunda, yalnızca değiştiricisini kullanın.

|||
|-|-|
|**Doğru ağaç görünümü simgeleri**|**Ağaç görünümü simgeleri yanlış**|
|![Doğru ağaç görünümü simgesi &#40;1&#41; ](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![doğru ağaç görünümü simgesi &#40;2&#41; ](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Yanlış ağaç görünümü simgesi &#40;1&#41; ](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![yanlış ağaç görünümü simgesi &#40;2&#41; ](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Stil ayrıntıları

#### <a name="layout"></a>Düzen
 Standart 16 x 16 simgelerini gösterildiği gibi yığın öğeleri:

 ![16x16 simgeleri için Düzen yığını](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />16x16 simgeleri için Düzen yığını

 Durum bildirim öğeleri daha iyi tek başına simgeler kullanılır. İçinde bir bildirim temel öğe üzerinde gibi görev tamamlanma simgesiyle Yığılmış bağlamları vardır:

 ![Visual Studio 'da tek başına bildirimler](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Tek başına bildirim simgeleri

 ![Görev tamamlanma simgesi](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Görev tamamlanma simgesi

 Proje simgeleri genellikle birden fazla boyut içeren .ico dosyalarıdır. Çoğu 16 x 16 simge aynı öğeleri içeriyor. Uygun olduğunda proje türü de dahil olmak üzere daha fazla ayrıntı 32 x 32 sürümlere sahip.

 ![Visual Studio 'da proje simgeleri](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />VB Windows Denetim Kitaplığı proje simgeleri, 16x16 ve 32x32

 Simge, piksel kare içinde ortalayın. Bu mümkün değilse, üst ve/veya çerçevenin sağında simgesi hizalayın.

 ![Piksel çerçevesi içinde ortalanmış simge](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Piksel çerçevesi içinde ortalanmış simge

 ![Piksel çerçevesinin sağ üst kısmına hizalanmış simge](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Çerçevenin sağ üst kısmına hizalanmış simge

 ![Ortalanmış ve piksel çerçevesinin üstüne hizalanmış simge](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Simge ortalanmış ve çerçevenin üst kısmına hizalanır

 İdeal hizalama ve dengeyi elde etmek için simgenin temel öğe eylem karakterleri ile engellemekte kaçının. Temel öğesinin üstüne yakın bir karakter sola yerleştir. Ek bir öğe eklerken, hizalama ve simge dengesini göz önünde bulundurun.

|||
|-|-|
|**Hizalama ve dengeyi doğru**|**Hizalama ve bakiye yanlış**|
|![Simge dengesini ve hizalamayı Düzeltme](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Yanlış simge dengesi ve hizalaması](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Öğe paylaştırmak ve kümelerinde kullanılan simge için boyut eşlik emin olun. Yanlış eşleştirme, daire ve ok büyük boyutlu olduğunu unutmayın ve eşleşmiyor.

|||
|-|-|
|**Doğru boyut eşliği**|**Yanlış boyut eşliği**|
|![Doğru simge boyutu ve eşliği](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Yanlış simge boyutu ve eşlik](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Tutarlı satır ve görsel ağırlıkları kullanın. Nasıl bir yan yana karşılaştırmayı kullanarak oluşturmakta olduğunuz simgesi diğer simgeye karşılaştırır değerlendirin. Hiçbir zaman tüm 16 x 16 çerçeveyi kullanın, 15 x 15 veya daha küçük. Negatif pozitif (Koyu ışık) oranı 50/50 olmalıdır.

|||
|-|-|
|**Sıfırdan olumlu oranı doğru yapın**|**Negatif-pozitif oranına yanlış**|
|![Simgeler &#40;1 için doğru görsel ağırlığı&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Simgeler &#40;için doğru görsel ağırlığı 2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Simgeler &#40;3 için doğru görsel ağırlığı&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Simgeler için yanlış görsel ağırlık](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Basit, karşılaştırılabilir şekiller ve Tamamlayıcı açıları öğesi bütünlüğü ödün vermeden, öğeleri oluşturmak için kullanın. 45 derecenin veya 90 ° açıları mümkün olduğunca kullanın.

 ![Simge açılarla doğru](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspektif
 Açık ve anlaşılır simgesi tutun. Perspektif ve yalnızca gerekli olduğunda bir ışık kaynağı kullanın. Simge öğelerde perspektifini kullanarak kaçınılmalıdır olsa da, bazı öğeler olmadan tanınmayan bağlıdır. Böyle durumlarda, öğenin netlik stilize perspektif iletişim kurar.

 ![3 noktalı perspektif](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />3 noktalı perspektif

 ![1 noktalı perspektif](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />1 noktalı perspektif

 Çoğu öğe doğru veya sağa açılı olmalıdır:

 ![Simgeler açılı sağ](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Işık kaynağı, yalnızca gerekli netlik nesneye eklerken kullanın.

|||
|-|-|
|**Doğru ışık kaynağı**|**Hatalı ışık kaynağı**|
|![Simgeler için ışık kaynaklarını düzeltin](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Simgeler için hatalı açık kaynaklar](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Anahatları yalnızca okunabilirliği geliştirmek veya benzetimini daha iyi iletişim kurmak için kullanın. Negatif pozitif (dark-light) Bakiye 50/50 olmalıdır.

|||
|-|-|
|**Ana hatlarıyla doğru kullanımı**|**Anahatların yanlış kullanımı**|
|![Doğru anahatlar](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Yanlış anahatlar](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Simge türü
 **Kabuk ve komut çubuğu** simgeleri şu öğelerden üçten fazla değil: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Kabuk ve komut çubuğu simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Kabuk ve komut çubuğu simgeleri örnekleri

 **Araç penceresi komut çubuğu** simgeleri şu öğelerden üçten fazla değil: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Araç penceresi komut çubuğu simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Araç penceresi komut çubuğu simgeleri örnekleri

 **Ağaç görünümü Kesinleştirme** simgeleri şu öğelerden üçten fazla değil: bir temel, bir değiştirici, bir eylem veya bir durum.

 ![Ağaç görünümü Kesinleştirme simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Ağaç görünümü Kesinleştirme simgeleri örnekleri

 Şu durumlarda **durum tabanlı değer taksonomi** simgeleri var: etkin, etkin devre dışı ve etkin olmayan devre dışı.

 ![Durum tabanlı değer taksonomi simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Durum tabanlı değer taksonomi simgeleri örnekleri

 **IntelliSense** simgeleri şu öğelerden üçten fazla değil: bir temel, bir değiştirici ve bir durum.

 ![IntelliSense simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />IntelliSense simgeler örnekleri

 **Küçük (16x16) proje** simgelerinin ikiden fazla öğe olmaması gerekir: bir temel ve bir değiştirici.

 ![Küçük (16x16) proje simgelerine örnek,](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![16x16 proje simgesi &#40;2&#41; ](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![16x16 proje simgesi &#40;3&#41; ](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Küçük (16x16) proje simgeleri örnekleri

 **Büyük (32x32) proje** simgeleri aşağıdaki öğelerin dörtten fazla değil: bir temel, biri iki değiştiricinin ve bir dil kaplaması.

 ![Büyük (32x32) proje simgeleri örnekleri](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Büyük (32x32) proje simgeleri örnekleri

### <a name="production-details"></a>Üretim ayrıntıları
 Windows Presentation Foundation (WPF) kullanarak tüm yeni kullanıcı Arabirimi öğeleri oluşturulmalı ve tüm yeni simgeleri WPF için 32-bit PNG biçiminde olmalıdır. 24 bit PNG, saydamlık desteklemiyor ve bu nedenle simgelerini önerilmez eski bir biçimidir.

 96 DPI çözünürlüğü kaydedin.

#### <a name="file-types"></a>Dosya türleri

- **32-BIT png:** simgeler için tercih edilen biçim. Bir tek tarama (piksel) görüntüsü depolayabilirsiniz kayıpsız veri sıkıştırma dosya biçimi. alfa kanalı saydamlık, gama düzeltmesi ve titreşimli 32-bit PNG dosyalarını destekler.

- **32-BIT BMP:** WPF olmayan denetimler için. Ayrıca XP ya da yüksek renk, 32-bit BMP bir alfa kanalı saydamlık rengi true görüntüsüyle bir RGB/bir görüntü biçimi çağırılır. Alfa kanalını bir bit eşlem (Dördüncü) bir ek olarak içinde kaydedildiği Adobe Photoshop belirtilen saydamlık katmanıdır renk kanalı. Siyah arka plan renk derinliği hakkında hızlı görsel bir ipucu sağlamak için tüm dosyalara 32-bit BMP resmi üretim sırasında eklenir. Bu siyah arka plan kullanıcı Arabiriminde kullanıma gizlenmeye alanını temsil eder.

- **32-BIT ICO:** proje simgeleri Için ve öğe Ekle. 32-bit gerçek renk saydam alfa kanalı ile tüm ICO dosyalardır (RGB/A). Birden çok boyut ve renk derinliği ICO dosyalarını depolayabileceğiniz için Vista simgeleri genellikle 16 x 16, 32 x 32, 48 x 48 ve 256 x 256 boyutundaki resim boyutları içeren bir ICO biçimindedir. Windows Gezgini'nde düzgün görüntülenmesi için ICO dosyaları kaydedilen her görüntü boyutu için 24-bit ve 8-bit renk derinliği için aşağı gerekir.

- **XAML:** tasarım yüzeyleri ve Windows donatıcıları için. XAML, ölçeklendirme ve döndürme, dosyalama ve saydamlık destek vektör tabanlı görüntü dosyaları simgelerdir. Bunlar, bugün Visual Studio'da ortak değildir ancak kendi esnekliğinde nedeniyle daha yaygın hale gelmektedir.

- **SVG**

- **24 BIT BMP:** Visual Studio komut çubuğu için. True-renk RGB görüntü biçimi, 24 bit BMP knock genişletme saydamlık katman için renk anahtar olarak Eflatun (R = 255, G = 0, B = 255) kullanarak bir katman saydamlığın örneklerinden biri oluşturur simgesi kuralıdır. İçinde 24 bit BMP, tüm pembe yüzey arka plan rengiyle görüntülenir.

- **24 BIT GIF:** Visual Studio komut çubuğu için. Saydamlığı destekleyen bir true renk RGB görüntü biçimi. GIF dosyaları, genellikle Sihirbazı resmi ve GIF animasyonları kullanılır.

### <a name="icon-construction"></a>Simge oluşturma
 Visual Studio'da küçük simge boyutu 16 x 16'dır. En büyük ortak 32 x 32 kullanılır. Tüm 16 x 16, 24 x 24 veya 32 x 32 çerçevesi simge tasarlarken değil doldurmaya göz önünde bulundurun. Kullanıcı tanımayı okunaklı ve Tekdüzen bir simge oluşturma gereklidir. Aşağıdaki noktalara simgeler derlerken uyar.

- Simgeler, NET, anlaşılır ve tutarlı olması gerekir.

- Durum bildirim öğeleri tek simgeler olarak kullanın ve bunları yığın üzerine bir simge temel öğe değil için iyidir. Belirli bağlamlarda Bu, temel bir öğe ile eşleştirmeye durum öğesi kullanıcı Arabirimi gerektirebilir.

- Proje simgeleri genellikle, çeşitli boyutlarda içeren .ico dosyalardır. Yalnızca 16 x 16, 24 x 24 ve 32 x 32 simgeler güncelleştiriliyor. Çoğu 16 x 16 ve 24 x 24 simgeleri aynı öğeleri içerir. 32 x 32 simgeler, uygun olduğunda proje dil türü de dahil olmak üzere daha fazla ayrıntı içerir.

- 32 x 32 simgelerini temel öğeler, genellikle 2-piksel çizgi kalınlığı sahiptir. 1 veya 2 piksel çizgi kalınlığı ayrıntı öğeler için kullanılabilir. Sağduyunuzu en iyi, daha uygun olduğunu belirlemek için kullanın.

- En az 1 piksel aralığı 24 x 24 simgeler ile öğeler için 16 x 16 arasındaki vardır. 2-piksel aralığı ve değiştiricisi ile temel öğe öğeleri arasındaki 32 x 32 simgelerini kullanın.

  ![Boyut 16x16, 24x24 ve 32x32 simgeleri için öğe boşluğu](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Boyut 16x16, 24x24 ve 32x32 simgeleri için öğe boşluğu

#### <a name="color-and-accessibility"></a>Renk ve erişilebilirlik
 Visual Studio uyumluluk yönergelerine üründeki tüm simgeleri renk ve karşıtlık erişilebilirlik gereksinimleri geçmesi gerekir. Bu simge tersine çevirme sağlanır ve tasarlarken, bunlar program aracılığıyla ürününde çevrilmemesi farkında olmalıdır.

 Visual Studio simgelerinde renk kullanma hakkında daha fazla bilgi için bkz. [görüntülerde renk kullanma](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="BKMK_UsingColorInImages"></a>Görüntülerde renk kullanma

### <a name="overview"></a>Genel Bakış
 Visual Studio'da simgeler öncelikle tek renkli. Renk belirli bilgileri iletmek için ayrılmıştır ve düzenlemesi için hiçbir zaman. Renk kullanılır:

- bir eylem belirtmek için

- durum bildirimi için kullanıcıyı uyarmak için

- Dil ilişkisi atamak için

- IntelliSense içinde öğeleri ayırmak için

### <a name="accessibility"></a>Erişilebilirlik
 Visual Studio uyumluluk kuralları, tüm simgeleri renk ve karşıtlık erişilebilirlik gereksinimleri ürün geçişinde işaretli gerektirir. Görsel dil palet renkleri edilmiş ve bu gereksinimleri karşılar.

#### <a name="color-inversion-for-dark-themes"></a>Koyu tema için renk ters çevirme
 Simgeler ile Visual Studio koyu tema doğru Karşıtlık oranı görünür yapmak için bir ters çevirmeyi program aracılığıyla uygulanır. Böylece doğru ters bu kılavuzdaki renkleri kısmen seçildi. Renk kullanımını kısıtlamak için bu paletin veya tersine çevirme uygulandığında öngörülemeyen sonuçlara alırsınız.

 ![Renkleri tersine çevrilmiş simgelere örnek olarak](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Renkleri tersine çevrilmiş simgelere örnek olarak

### <a name="base-palette"></a>Temel palet
 Tüm standart simgeleri üç temel renk içerir. Simgeleri içeren hiçbir gradyanlar veya 3B aracı simgeleri için bir veya iki özel durum ile gölgeler.

|Kullanım|Adı|Değer (açık tema)|Renk örneği|Örnek|
|-----------|----------|---------------------------|------------|-------------|
|Arka plan/koyu|VS BG|424242 / 66,66,66|![Renk örneği 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Temel palet örneği](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Ön plan/hafif|VS FG|F0EFF1 / 240,239,241|![F0EFF1 örneği](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Anahat|VS çıkış|F6F6F6 / 246,246,246|![F6F6F6 örneği](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Ek olarak temel renkler, her bir simgeyi genişletilmiş paletinden bir ek renk içerebilir.

### <a name="extended-palette"></a>Genişletilmiş paleti

#### <a name="action-modifiers"></a>Eylem Değiştiriciler
 Aşağıdaki dört renkleri tarafından eylem değiştiricileri gerekli eylemleri türlerini gösterir:

|Kullanım|Adı|Değeri (tüm tema)|Renk örneği|
|-----------|----------|--------------------------|------------|
|Pozitif|VS eylem yeşil|388A34 / 56,138,52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negatif|VS eylem kırmızı|A1260D / 161,38,13|![A1260D örneği](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Nötr|VS eylem mavi|00539C / 0,83,156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|/ Yeni Oluştur|VS eylemin turuncu|C27D1A / 194,156,26|![C27D1A örneği](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Örnekler
 Yeşil, "Ekle", "Çalıştır", "Play" ve "Validate" gibi pozitif eylem değiştiricilerinde kullanılır.

|||||
|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Çalıştırın|![Sorgu simgesini Yürüt](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />Sorguyu Yürüt|![Tüm adımları Yürüt simgesi](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />Tüm adımları Yürüt|![Denetim simgesi ekle](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />Denetim Ekle|

 Kırmızı, "Sil", "Durdur", "Iptal" ve "Kapat" gibi negatif Eylem değiştiricileri için kullanılır.

|||||
|-|-|-|-|
|![İlişki Sil simgesi](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />İlişkiyi sil|![Sütun Sil simgesi](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />Sütunu Sil|![Sorgu simgesini durdur](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />Sorguyu durdur|![Çevrimdışı bağlantı simgesi](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />Çevrimdışı bağlantı|

 Mavi, "Aç", "Next," "Previous," "Import," ve "Export" gibi en yaygın olarak oklar olarak temsil edilen bağımsız eylem değiştiricilerine uygulanır.

|||||
|-|-|-|-|
|![Alan simgesine git](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />Alana git|![Toplu iade&#45;simgesi](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />Toplu Iade etme|![Adres Düzenleyicisi simgesi](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />Adres Düzenleyicisi|![İlişkilendirme düzenleyici simgesi](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />İlişkilendirme Düzenleyicisi|

 Koyu altın öncelikle "yeni" değiştiricisi için kullanılır.

|||||
|-|-|-|-|
|![Yeni proje simgesi](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />Yeni Proje|![Yeni grafik simgesi oluştur](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />Yeni grafik oluştur|![Yeni birim testi simgesi](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />Yeni birim testi|![Yeni liste öğesi simgesi](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />Yeni liste öğesi|

#### <a name="special-cases"></a>Özel durumlar
 Özel durumlarda, renkli eylem değiştirici bağımsız olarak tek başına simgesi olarak kullanılabilir. Simge için kullanılan rengi simgesi ile ilişkili eylemler yansıtır. Bu simgeleri dahil olmak üzere, küçük bir kısmı sınırlıdır:

||||||
|-|-|-|-|-|
|![Çalıştır simgesi](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Çalıştırın|![Durdur simgesi](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Durdur|![Simgeyi Sil](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />Sil|![Kaydet simgesi](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />Kaydet|![Geri git simgesi](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />Geri git|

### <a name="code-hierarchy-palette"></a>Kod hiyerarşi paleti

#### <a name="folder"></a>Klasör

|Kullanım|Adı|Değeri (tüm tema)|Renk örneği|Örnek|
|-----------|----------|--------------------------|------------|-------------|
|Klasörler|Klasör|DCB67A / 220,182,122|![DCB67A örneği](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Klasör rengi simgesi](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Visual Studio dilleri
 Her birinin ortak dillerde veya platformlarda Visual Studio'da kullanılabilen, ilişkili bir renk olur. Bu renklerin temel simgesine veya bileşik simge sağ üst köşesinde görüntülenen dil değiştiriciler kullanılır.

|Kullanım|Adı|Değeri (tüm tema)|Renk örneği|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF mavi|0095D 7 / 0,149,215|![Renk örneği 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP mor|9B4F96 / 155,79,150|![Renk örneği 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS yeşil (VS eylem yeşil)|388A34 / 56,138,52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS kırmızı|BD1E2D / 189,30,45|![BD1E2D örneği](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS mor|672878 / 103,40,120|![Renk örneği 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS turuncu|F16421 / 241,100,33|![F16421 örneği](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB mavi (VS eylem mavi)|00539C / 0,83,156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS turuncu|E04C06 / 224,76,6|![E04C06 örneği](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|Kopyala yeşil|879636 / 135,150,54|![Renk örneği 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Dil değiştiriciler simgelerle örnekleri

|||||||
|-|-|-|-|-|-|
|![Visual Basic simgesi](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![C&#35; simgesi](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C&#43; &#43; simgesi](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![F&#35; simgesi](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![JavaScript simgesi](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Python simgesi](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![HTML simgesi](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![WPF simgesi](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![ASP simgesi](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![CSS simgesi](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![TypeScript simgesi](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Bir özel renk paletini IntelliSense simgelerini kullanın. Bu renklerin IntelliSense açılan listedeki farklı öğeleri hızlı bir şekilde ayırt kullanıcılara yardımcı olmak için kullanılır.

|Kullanım|Adı|Değeri (tüm tema)|Renk örneği|
|-----------|----------|--------------------------|------------|
|Olay sınıfı|VS eylemin turuncu|C27D1A / 194,125,26|![C27D1A örneği](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Genişletme yöntemi, yöntem, modül temsilcisi|VS eylem mor|652D 90 / 101,45,144|![Renk örneği 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Alan, sabit listesi öğesi, makrosu, yapı, birleşim değer türü işleç arabirimi|VS eylem mavi|00539C / 0,83,156|![Renk örneği 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Nesne|VS eylem yeşil|388A34 / 56,138,52|![Renk örneği 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Sabit, özel durum, sabit listesi öğesi, harita, harita öğesi, Namespace, şablonu tür tanımı|Arka plan (VS BG)|424242 / 66,66,66|![Renk örneği 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>IntelliSense simgeler örnekleri

||||||
|-|-|-|-|-|
|![IntelliSense sınıf simgesi](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />Sınıf|![IntelliSense özel olay simgesi](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />Özel olay|![IntelliSense temsilci simgesi](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />Temsilci|![IntelliSense yöntemi arkadaş simgesi](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Yöntem arkadaş|![Alan simgesi](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />Alan|
|![IntelliSense korumalı Enum öğesi simgesi](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />Korumalı Enum öğesi|![IntelliSense nesne simgesi](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Nesne|![IntelliSense şablon simgesi](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />Şablon|![IntelliSense özel durum kısayol simgesi](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />Özel durum kısayolu||

### <a name="notifications"></a>Bildirimler
 Visual Studio'da bildirimleri durumunu göstermek için kullanılır. Bildirim palet siyah veya beyaz ön plan dolgu seçeneklerini yanı sıra aşağıdaki dört renkleri bildirimleri aşağıdaki durum düzeyleri tanımlamak için kullanır.

|Kullanım|Adı|Değeri (tüm tema)|Renk örneği|
|-----------|----------|--------------------------|------------|
|Durum: nötr|Bildirim mavi (VS mavi)|1BA1E2 / 27,161,226|![Renk örneği 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Durum: pozitif|Bildirim yeşil (VS yeşil)|339933 / 51,153,51|![Renk örneği 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Durum: negatif|Bildirim kırmızı (VS kırmızı)|E51400 / 229,20,0|![E51400 örneği](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Durum: uyarı|Bildirim sarı (VS turuncu)|FFCC00 / 255,204,0|![FFCC00 örneği](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Ön plan dolgusu|Bildirim siyah (siyah)|000000 / 0,0,0|![000000 yazın &#35;örneği](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Ön plan dolgusu|Bildirim beyaz (beyaz)|FFFFFF / 255,255,255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Bildirim simgeleri örnekleri

|||||
|-|-|-|-|
|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />Uyarı|![Uyarı simgesi](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Uyarı|![Tamam simgesi](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />Complete|![Durdur simgesi](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Durdur|

### <a name="visual-studio-online"></a>Visual Studio Team Services
 Genel olarak, Visual Studio Online tarayıcıda barındırılıp özelliklerden oluşur. Farklı ortamlarda rengi değişir, ancak stil aynı kalır.

|Grup|Kullanım|Adı|Değeri (tüm tema)|Renk örneği|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Arka plan|TFSO BG|656565/ 101, 101, 101|![Renk örneği 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Anahat|ÇIKIŞ TFSO|FFFFFF / 255, 255, 255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Arka plan|Beyaz|FFFFFF / 255, 255, 255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Monako|Arka plan|Beyaz|FFFFFF / 255, 255, 255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Arka plan|Beyaz|FFFFFF / 255, 255, 255|![Renk örneği FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Renk örneği 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Vurgulu|F12 Blue_Hover|2279BF / 34,121,191|![Renk örneği 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Devre dışı|F12 LtGrey_Disabled|ABABAC / 171,171,172|![ABABAC örneği](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Üzerine gelindiğinde kullanılacak arka plan|BG getirin|D9EBF7 / 217,235,247|![D9EBF7 örneği](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|Basılan arka plan|Basılan bg|B2D7F0 / 178,215,240|![B2D7F0 örneği](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Anahat|VS ÇIKIŞ|F6F6F6 / 246,246,246|![F6F6F6 örneği](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Bilgi|Bilgi|00BCF2 / 0,188,242|![Renk örneği 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Uyarı|Uyarı|F28300 / 242,131,0|![F28300 örneği](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Hata / negatif|Error_Negative|E81123 / 232,17,35|![E81123 örneği](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Başlat / pozitif|Start_Positive|009E49 / 0,158,73|![Renk örneği 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Sonu türü|Sonu türü|9B4F96 / 155,79,150|![Renk örneği 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Olay işareti|Olay işareti|A51F00 / 165,31,0|![A51F00 örneği](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Kullanıcı işareti|Kullanıcı işareti|F16220 / 241,98,32|![F16220 örneği](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Visual Studio Online simgeler örnekleri

|TFS çevrimiçi||||
|----------------|-|-|-|
|![TFS çevrimiçi ekibi simgesi](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />Çevrimiçi takım|![TFS bilgileri simgesi](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />Bilgi|![TFS geçmiş simgesi](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />Geçmiş|![TFS dalı simgesi](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Dal|

|Napa||||
|----------|-|-|-|
|![Napa içerik simgesi](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />İçerik|![Napa ofis postası simgesi](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />Ofis postası|![Napa SharePoint simgesi](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Napa görev bölmesi simgesi](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />Görev bölmesi|

|Monako||||
|------------|-|-|-|
|![Monako dosyaları simgesi](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />Dosyalar|![Monako git simgesi](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Monako arama simgesi](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />Arama|![Monako metin simgesi](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />Metin|

|F12|||
|---------|-|-|
|![F12 düzgün kod simgesi](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />Oldukça kod|![F12 uyarı simgesi](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Uyarı|![F12 benzetim simgesi](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />Ne|