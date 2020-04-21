---
title: XAML Tasarımcısı’na genel bakış
ms.date: 03/03/2020
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
- Blend.Start.Dev12
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 31a31e413ecd39b7d15f8ea3cd0417c2493463ca
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649618"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma

Visual Studio ve Blend for Visual Studio'daki XAML Designer, WPF ve UWP gibi XAML tabanlı uygulamalar tasarlamanıza yardımcı olacak görsel bir arayüz sağlar. Denetimleri Toolbox penceresinden sürükleyerek uygulamalarınız için kullanıcı arabirimleri oluşturabilir (Visual Studio için Karışım'daki Varlıklar penceresi) ve Özellikler penceresinde özellikleri ayarlayabilirsiniz. XAML'yi doğrudan XAML görünümünde de edinebilirsiniz.

Gelişmiş kullanıcılar için [XAML Tasarımcısı'nı](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md)bile özelleştirebilirsiniz.

> [!NOTE]
> Xamarin.Forms bir XAML tasarımcısı desteklemez. Xamarin.Forms XAML UI'lerinizi görüntülemek ve uygulama çalışırken bunları yönetmek için Xamarin.Forms için XAML Hot Reload'ı kullanın. Daha fazla bilgi [için Xamarin.Forms (Önizleme) sayfasına](/xamarin/xamarin-forms/xaml/hot-reload/) bakın.

## <a name="xaml-designer-workspace"></a>XAML Tasarımcı çalışma alanı

XAML Designer'daki çalışma alanı birkaç görsel arabirim öğesinden oluşur. Bunlar arasında *artboard* (görsel tasarım yüzeyi olan), XAML düzenleyicisi, Document Outline penceresi (Visual Studio için Karışım'daki Nesneler ve Zaman Çizelgesi penceresi) ve Özellikler penceresi yer almaktadır. XAML Tasarımcısı'nı açmak için **Solution Explorer'da** bir XAML dosyasına sağ tıklayın ve **Tasarımcıyı Görüntüle'yi**seçin.

XAML Designer, uygulamanızın işlenen XAML biçimlendirmesinin bir XAML görünümü ve senkronize Tasarım görünümü sağlar. Visual Studio veya Blend for Visual Studio'da açık olan bir XAML dosyasıyla, **Tasarım** ve **XAML** sekmelerini kullanarak Tasarım görünümü ile XAML görünümü arasında geçiş yapabilirsiniz. Üstte hangi pencerenin ![göründüğünü değiştirmek için XAML](media/swap-panes.PNG) Designer'daki **Takas Bölmeleri** düğmesini kullanabilirsiniz: artboard veya XAML düzenleyicisi.

### <a name="design-view"></a>Tasarım görünümü

Tasarım görünümünde, resim panosunu içeren pencere etkin penceredir ve bunu birincil çalışma yüzeyi olarak kullanabilirsiniz. Öğeleri ekleyerek, çizerek veya değiştirerek uygulamanızdaki bir sayfayı görsel olarak tasarlamak için kullanabilirsiniz. Daha fazla bilgi için [XAML Designer'daki öğelerle çalışma bilgisine](../xaml-tools/working-with-elements-in-xaml-designer.md)bakın. Bu resimde Tasarım görünümünde resim tahtası gösterilmektedir.

![XAML Designer tasarım görünümü](media/xaml-artboard.png)

Bu özellikler resim tahtasında mevcuttur:

**Snaplines**

Tutturma çizgileri, denetimlerin kenarları hizalandığında veya metin taban çizgilerinin hizalandığında göstermek için kırmızı kesikli çizgiler olarak görünen *hizalama sınırlarıdır.* Hizalama sınırları yalnızca **snapline'a tutturulduğunda** görünür.

**Izgara rayları**

Izgara rayları, [Grid](xref:Windows.UI.Xaml.Controls.Grid) panelindeki satırları ve sütunları yönetmek için kullanılır. Satır lar ve sütunlar oluşturabilir ve silebilir ve göreli genişliklerini ve yüksekliklerini ayarlayabilirsiniz. Artboard'un solunda görünen dikey Izgara rayları satırlar için, üstte görünen yatay çizgi ise sütunlar için kullanılır.

**Izgara süsleyiciler**

Izgara süsleyici, Grid rayÜzerinde dikey veya yatay bir çizgiye sahip bir üçgen olarak görünür. Izgara süsleyicisini sürüklediğinizde, fareyi hareket ettirirken bitişik sütunların veya satırların genişlikleri veya yükseklikleri güncellenir.

Izgara süsleyiciler, Izgara satırlarının ve sütunlarının genişliğini ve yüksekliğini denetlemek için kullanılır. Izgara raylarını tıklatarak yeni bir sütun veya satır ekleyebilirsiniz. İki veya daha fazla sütunveya satıriçeren bir Izgara paneli için yeni bir satır veya sütun satırı eklediğinizde, genişliği ve yüksekliği açıkça ayarlamanızı sağlayan rayın dışında bir mini araç çubuğu görüntülenir. Mini araç çubuğu, Izgara satırları ve sütunları için boyutlandırma seçenekleri ayarlamanızı sağlar.

![XAML Tasarımcısı Izgara süsleyici](media/grid-adorner.png)

**Tutamaçları yeniden boyutlandırma**

Yeniden boyutlandırma tanıtıcıları seçili denetimlerde görünür ve denetimi yeniden boyutlandırmanızı sağlar. Denetimi yeniden boyutlandırdığınızda, genişlik ve yükseklik değerleri genellikle denetimi boyutlandırmanıza yardımcı olur. **Tasarım** görünümünde denetimleri işleme hakkında daha fazla bilgi için Bkz. [XAML Designer'daki öğelerle Çalışma.](../xaml-tools/working-with-elements-in-xaml-designer.md)

**Kenar boşlukları**

Kenar boşlukları, denetimin kenarı ile kapsayıcının kenarı arasındaki sabit boşluk miktarını temsil eder. **Özellikler** penceresinde **Düzen** altında [Kenar Boşluğu](xref:Windows.UI.Xaml.FrameworkElement.Margin) özelliklerini kullanarak denetimkenar kenar boşluklarını ayarlayabilirsiniz.

**Marj süsleyiciler**

Bir öğenin kenar boşluklarını düzen kapsayıcısına göre değiştirmek için kenar boşluğu süsleyicilerini kullanın. Bir kenar boşluğu süsleyici açık olduğunda, bir kenar boşluğu ayarlanmaz ve kenar boşluğu süsleyici kırık bir zincir görüntüler. Kenar boşluğu ayarlanmadığında, düzen kapsayıcısı çalışma zamanında yeniden boyutlandırıldığında öğeler yerinde kalır. Bir kenar boşluğu süsleyicisi kapatıldığında, kenar boşluğu süsleyicisi kırılmamış bir zincir görüntüler ve düzen kapsayıcısı çalışma zamanında yeniden boyutlandırılırken (kenar boşluğu sabit kalır) kenar boşluğuyla birlikte hareket eder.

**Eleman tutamaçları**

İşaretçiyi bir öğeyi çevreleyen mavi kutunun köşelerine taşırken, artboard'da görünen öğe tutamaçlarını kullanarak bir öğeyi değiştirebilirsiniz. Bu tutamaçları, öğeye bir köşe yarıçapı döndürmenizi, yeniden boyutlandırmanızı, çevirmenizi, hareket etmenizi veya eklemenizi sağlar. Öğe kolu için sembol işleve işaretçi tam konumuna bağlı olarak değişir. Öğenin tutamacını görmüyorsanız, öğenin seçildiğinden emin olun.

**Tasarım** görünümünde, pencerenin sol alt alanında, burada gösterildiği gibi ek artboard komutları mevcuttur:

![Tasarım görünümü komutları](media/xaml-design-view-controls.png)

Bu komutlar bu araç çubuğunda kullanılabilir:

**Zoom**

Yakınlaştırma, tasarım yüzeyini boyutlandırmanızı sağlar. %12,5 ile %800 arasında yakınlaştırabilir veya **Seçime Sığdır** ve **Tümünü Sığdır**gibi seçenekleri seçebilirsiniz.

**Tutturma ızgarası göster/gizle**

Izgara çizgilerini gösteren anlık ızgarayı görüntüler veya gizler. **Gridlines, Gridlines'a tutturma** veya **tutturma çizgisine tutturma**yı etkinleştirdiğinizde kullanılır.

**Gridlines'a tutturulmayı açma/kapatma**

**Izgara çizgilerine tutturulmak** etkinse, bir öğe, onu artboard'a sürüklediğizde en yakın yatay ve dikey Kılavuz çizgilerle hizalama eğilimindedir.

**Artboard arka planını geçiş**

Açık ve koyu arka plan arasında geçiş.

**Snaplines'e tutturma yı kapatma/kapatma**

Snaplines, denetimleri birbirine göre hizalamanıza yardımcı olur. **Snapline'a tutturma** etkinse, denetimi diğer denetimlere göre sürüklediğinizde, kenarlar ve bazı denetimlerin metni yatay veya dikey olarak hizalandığında hizalama sınırları görüntülenir. Bir hizalama sınırı kırmızı kesikli çizgi olarak görünür.

**Proje kodunu devre dışı**

[Proje kodunu](debugging-or-disabling-project-code-in-xaml-designer.md)devre dışı kılabilir , örneğin, özel denetimler ve değer dönüştürücüler, ve tasarımcı yeniden yükler.

### <a name="xaml-view"></a>XAML görünümü

**XAML** görünümünde, XAML düzenleyicisini içeren pencere etkin penceredir ve XAML düzenleyicisi birincil yazma aracınızdır. Genişletilebilir Uygulama Biçimlendirme Dili (XAML), bir uygulamanın kullanıcı arabirimini belirtmek için bildirimsel, XML tabanlı bir kelime dağarcığı sağlar. XAML görünümü, IntelliSense, otomatik biçimlendirme, sözdizimi vurgulama ve etiket gezintisi içerir. Aşağıdaki resimde, IntelliSense menüsü açıkken XAML görünümü gösterilmektedir:

![XAML görünümü](media/xaml-editor.png)

## <a name="document-outline-window"></a>Belge Anahat penceresi

Visual Studio'daki Belge Anahat penceresi, Visual Studio için Karışım'daki [Nesneler ve Zaman Çizelgesi penceresine](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) benzer. Belge Anahattı bu görevleri gerçekleştirmenize yardımcı olur:

- Resim panosundaki tüm öğelerin hiyerarşik yapısını görüntüleyin.

- Öğeleri değiştirebilmeniz için seçin. Örneğin, bunları hiyerarşide taşıyabilir veya Özellikler penceresinde özelliklerini ayarlayabilirsiniz. Daha fazla bilgi için [XAML Designer'daki öğelerle çalışma bilgisine](../xaml-tools/working-with-elements-in-xaml-designer.md)bakın.

- Denetimolan öğeler için şablonlar oluşturun ve değiştirin.

- [Animasyonlar oluşturun](animate-objects-in-xaml-designer.md) (yalnızca Visual Studio için Karışım).

Visual Studio'daki Belge Anahat penceresini görüntülemek için menü çubuğunda**Diğer Windows** > **Belge Anahattını** **Görüntüle'yi** > seçin.
Visual Studio için Karışım'daki Nesneler ve Zaman Çizelgesi penceresini görüntülemek için menü çubuğunda**Belge Anahattını** **Görüntüle'yi** > seçin.

![Visual Studio'da Belge Anahattı penceresi](media/document-outline-window.png)

Belge Anahat/Nesneler ve Zaman Çizelgesi penceresindeki ana görünüm, bir ağaç yapısındaki belgehiyerarşisini görüntüler. Belge anahattının hiyerarşik yapısını, belgeyi farklı ayrıntı düzeylerinde incelemek ve öğeleri tek tek veya gruplar halinde kilitlemek ve gizlemek için kullanabilirsiniz. Aşağıdaki seçenekler Belge Anahattı/Nesneler ve Zaman Çizelgesi penceresinde mevcuttur:

**Göster/gizle**

Artboard öğelerini görüntüler veya gizler. Gösterildiğinde bir gözün sembolü olarak görünür. Ayrıca bir öğeyi gizlemek için **Ctrl**+**H** tuşuna basabilir ve göstermek için**Ctrl**+ **H'yi kaydırabilirsiniz.**+**H**

**Kilitleme/kilidini açma**

Artboard öğelerini kilitler veya açar. Kilitli öğeler değiştirilemez. Kilitlendiğinde asma kilit simgesi olarak görünür. Ayrıca bir öğeyi kilitlemek için **Ctrl**+**L** tuşuna basabilir ve kilidini açmak için**Ctrl**+**L** **tuşuna basabilirsiniz.**+

**Kapsamı pageRoot'a döndür**

Yukarı ok simgesini gösteren Belge Anahattı/Nesneler ve Zaman Çizelgesi penceresinin üst kısmındaki seçenek önceki kapsama taşınır. Kapsam oluşturma, yalnızca bir stil veya şablon kapsamında olduğunuzda uygulanabilir.

## <a name="properties-window"></a>Özellik penceresi

**Özellikler** penceresi, denetimlerde özellik değerlerini ayarlamanızı sağlar. İşte böyle görünüyor:

![Özellik penceresi](media/xaml-designer-properties-window.png)

**Özellikler** penceresinin üst kısmında çeşitli seçenekler vardır:

- **Ad** kutusunda şu anda seçili öğenin adını değiştirin.
- Sol üst köşede, şu anda seçili öğeyi temsil eden bir simge vardır.
- Özellikleri kategoriye veya alfabetik olarak düzenlemek için, listeye göre **Düzenle'deki** **Kategori**, **Ad**veya **Kaynak'ı** tıklatın.
- Denetim için olayların listesini görmek için, yıldırım simgesi olarak görünen **Olaylar** düğmesini tıklatın.
- Bir özelliği aramak için, arama kutusuna özelliğin adını yazmaya başlayın. **Özellikler** penceresi, siz yazarken aramanızla eşleşen özellikleri görüntüler.

Bazı özellikler, aşağı ok düğmesini seçerek gelişmiş özellikleri ayarlamanızı sağlar.

Her özellik değerinin sağında bir kutu simgesi olarak görünen bir *özellik işaretçisi* vardır. Özellik işaretçisinin görünümü, bir veri bağlama veya özellik için uygulanan bir kaynak olup olmadığını gösterir. Örneğin, beyaz kutu simgesi varsayılan değeri gösterir, kara kutu simgesi genellikle yerel bir kaynağın uygulandığını gösterir ve turuncu kutu genellikle bir veri bağlamanın uygulandığını gösterir. Özellik işaretçisini tıklattığınızda, stil tanımına gidebilir, veri bağlama oluşturucuyu açabilir veya kaynak seçiciyi açabilirsiniz.

Özellikleri kullanma ve olayları işleme hakkında daha fazla bilgi [için, denetimler ve desenler için Giriş'e](/windows/uwp/design/controls-and-patterns/controls-and-events-intro)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nda öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Kaynak oluşturma ve uygulama](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [İzlenecek yol: XAML Tasarımcısı’nda verilere bağlama](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
