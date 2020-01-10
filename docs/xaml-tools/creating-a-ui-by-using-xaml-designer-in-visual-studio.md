---
title: XAML Tasarımcısı’na genel bakış
ms.date: 07/31/2019
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
ms.openlocfilehash: 912468cf95b7b5a4b611fb568048c2ba62cc635d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593003"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma

Visual Studio ve Visual Studio için Blend XAML Tasarımcısı, WPF, UWP ve Xamarin. Forms uygulamaları gibi XAML tabanlı uygulamalar tasarlamanıza yardımcı olacak görsel bir arabirim sağlar. Araç kutusu penceresinden (Visual Studio için Blend varlıklar penceresi) denetimleri sürükleyerek ve Özellikler penceresi özellikleri ayarlayarak uygulamalarınız için Kullanıcı arabirimleri oluşturabilirsiniz. Ayrıca, XAML XAML görünümünde doğrudan düzenleyebilirsiniz.

İleri düzey kullanıcılar için, XAML Tasarımcısı bile [özelleştirebilirsiniz](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

## <a name="xaml-designer-workspace"></a>XAML Tasarımcısı çalışma alanı

XAML Tasarımcısı'nda çalışma birkaç görsel arabirim öğelerini içerir. Bunlar, *çalışma yüzeyini* (görsel tasarım yüzeyi), XAML Düzenleyicisi, belge ana hattı penceresi (Visual Studio için Blend nesneler ve zaman çizelgesi pencere) ve Özellikler penceresi içerir. XAML Tasarımcısı açmak için **Çözüm Gezgini** bir xaml dosyasına sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin.

XAML Tasarımcısı, uygulamanızın biçimlendirmenin XAML eşitlenmiş bir Tasarım görünümünü ve XAML görünümü sağlar. Visual Studio 'da veya Visual Studio için Blend bir XAML dosyası açıkken, **Tasarım** ve **xaml** SEKMELERINI kullanarak tasarım görünümü ve XAML görünümü arasında geçiş yapabilirsiniz. En üstte yer alan çalışma yüzeyi ya da XAML Düzenleyicisi olarak değiştirmek için, XAML Tasarımcısı](media/swap-panes.PNG) **bölmeleri takas et düğmesini ![** .

### <a name="design-view"></a>Tasarım görünümü

Tasarım görünümü, çalışma yüzeyini içeren pencere etkin pencere olur ve bunu birincil iş yüzeyi olarak kullanabilirsiniz. Bu uygulamayı, öğeleri ekleyerek, çizerek veya değiştirerek uygulamanızdaki bir sayfayı görsel olarak tasarlamak için kullanabilirsiniz. Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md). Bu örnekte, çalışma yüzeyinde Tasarım görünümünde gösterilmiştir.

![XAML Tasarımcısı Tasarım görünümü](media/xaml-artboard.png)

Bu özellikler, çalışma yüzeyine kullanılabilir:

**Dayama çizgileri**

Anlık görüntü çizgileri, denetimlerin kenarlarının ne zaman hizalanacağını veya metin temellerinin hizalandığını göstermek için kırmızı kesikli çizgiler olarak görünen *Hizalama sınırlardır* . Hizalama sınırları yalnızca, **yama çizgilere yaslaması** etkin olduğunda görünür.

**Izgara rayları**

Izgara rayları, [kılavuz](xref:Windows.UI.Xaml.Controls.Grid) panelinde satırları ve sütunları yönetmek için kullanılır. Oluşturma ve satırları ve sütunları Sil ve kendi göreli genişlik ve yükseklik ayarlayabilirsiniz. Çalışma yüzeyinin sol tarafında görünür, dikey kılavuz parmaklık için satırlar kullanılır ve üst kısmında görünür, yatay çizgi sütunlar için kullanılır.

**Izgara donatıcıları**

Kılavuz bir donatıcı, bir ızgara rampasının üzerine dikey veya yatay bir çizgi eklenmiş bir üçgen olarak görünür. Bir kılavuz donatıcısını sürüklediğinizde, fareyi taşırken bitişik sütunların veya satırların genişliği veya yükseklikleri güncellemektir.

Izgara donatıcıları, bir kılavuzun satır ve sütunlarının genişlik ve yüksekliğini denetlemek için kullanılır. Izgara rayları ' na tıklayarak yeni bir sütun veya satır ekleyebilirsiniz. İki veya daha fazla sütun veya satır içeren bir kılavuz paneli için yeni bir satır veya sütun satırı eklediğinizde, daha fazla genişlik ve yükseklik ayarlamanıza olanak tanıyan bir mini araç çubuğu, demiryolu dışında görünür. Mini araç çubuğu, kılavuz satırları ve sütunları için boyutlandırma seçeneklerini ayarlamanıza olanak sağlar.

![XAML Tasarımcısı kılavuz donatıcı](media/grid-adorner.png)

**Yeniden boyutlandırma tutamaçları**

Yeniden boyutlandırma tutamaçları seçili denetimlerde görünür ve denetimi yeniden boyutlandırmanızı sağlar. Bir denetimi yeniden boyutlandırdığınızda, genişlik ve yükseklik değerlerini, genellikle denetiminin boyutunu yardımcı olması için görünür. **Tasarım** görünümünde denetimleri düzenleme hakkında daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Kenar boşlukları**

Kenar boşlukları, bir denetimin kenarı ve kapsayıcısının kenarı arasındaki sabit boşluk miktarını temsil eder. Bir denetimin kenar boşluklarını, **Özellikler** penceresinde **Düzen** altındaki [kenar boşluğu](xref:Windows.UI.Xaml.FrameworkElement.Margin) özelliklerini kullanarak ayarlayabilirsiniz.

**Kenar boşluğu donatıcıları**

Bir öğenin kenar boşluklarını düzen kapsayıcısına göre değiştirmek için kenar boşluğu donatıcıları kullanın. Kenar boşluğu donatıcısı açıksa, bir kenar boşluğu ayarlı değildir ve kenar boşluğu donatıcısı bozuk zincirini görüntüler. Kenar boşluğu ayarlanmamışsa, düzen kapsayıcısı çalışma zamanında yeniden boyutlandırılırken öğeler yerinde kalır. Bir kenar boşluğu donatıcısı kapalıyken, bir kenar boşluğu donatıcısı bozuk bir zincir görüntüler ve düzen kapsayıcısı çalışma zamanında yeniden boyutlandırıldığından (kenar boşluğu sabit kalır) öğeler kenar boşluğu ile birlikte taşınır.

**Öğe tutamaçları**

Bir öğeyi çevreleyen mavi kutunun köşelerinden işaretçiyi taşıdığınızda çalışma yüzeyinde görünen öğe tutamaçlarını kullanarak bir öğeyi değiştirebilirsiniz. Bu tanıtıcıları, döndürme, yeniden boyutlandırma, çevir, taşıyın veya öğeye bir köşe yarıçapı eklemenizi sağlar. Öğe tanıtıcısı sembolü, işaretçinin tam konumuna bağlı olarak işleve ve değişikliklere göre değişir. Öğe tutamaçları görmüyorsanız, öğe seçili olduğundan emin olun.

**Tasarım** görünümünde, aşağıda gösterildiği gibi pencerenin sol alt bölümünde ek çalışma yüzeyi komutları kullanılabilir:

![Tasarım görünümü komutları](media/xaml-design-view-controls.png)

Bu komutlar, bu araç çubuğunda kullanılabilir:

**Yakınlaştırma**

Yakınlaştırma, tasarım yüzeyini boyutlandırmanızı sağlar. % 12,5 ' dan %800 ' e yakınlaştırıp veya **seçimi sığdırma** ve **Tümünü sığdırma**gibi seçenekleri belirleyebilirsiniz.

**Yaslama kılavuzunu göster/gizle**

Kılavuz çizgilerini gösteren yaslama kılavuzunu görüntüler veya gizler. Kılavuz çizgileri, **kılavuz çizgilere yaslamayı** veya ek **yaslama çizgilerine yaslamayı**etkinleştirdiğinizde kullanılır.

**Kılavuz çizgilerine yaslamayı aç/kapat**

**Kılavuz çizgilerine yaslaması** etkinleştirilirse, çalışma yüzeyinde bir öğe sürüklediğinizde, öğesi en yakın yatay ve dikey kılavuz çizgilerine göre hizalanacaktır.

**Çalışma yüzeyi arka planını aç**

Açık ve koyu arka plan arasında geçiş yapar.

**Ek çizgi çizgilere yaslamayı aç/kapat**

Anlık görüntü çizgileri, denetimleri birbirlerine göre hizalamanıza yardımcı olur. Daha fazla denetime **yaslaması** etkinse, bir denetimi diğer denetimlere göre sürüklediğinizde, bazı denetimlerin kenarları ve metni yatay veya dikey olarak hizalandığında hizalama sınırları görüntülenir. Bir hizalama sınırı kırmızı kesik çizgili bir çizgi olarak görünür.

**Proje kodunu devre dışı bırak**

[Proje kodunu](debugging-or-disabling-project-code-in-xaml-designer.md)devre dışı bırakır, örneğin, özel denetimler ve değer dönüştürücüler ve tasarımcıyı yeniden yükler.

### <a name="xaml-view"></a>XAML görünümü

**Xaml** görünümünde, XAML düzenleyicisini içeren pencere etkin pencere ve xaml Düzenleyicisi ise birincil yazma aracdır. Extensible Application Markup Language (XAML), bir uygulamanın kullanıcı arabirimini belirtmek için bildirim temelli, XML tabanlı bir sözlüğünü sağlar. XAML görünümü, IntelliSense, otomatik biçimlendirme, söz dizimi vurgulama ve etiket Gezinti içerir. Aşağıdaki görüntüde bir IntelliSense menüsü açık olan XAML görünümü gösterilmektedir:

![XAML görünümü](media/xaml-editor.png)

## <a name="document-outline-window"></a>Belge Anahattı penceresi

Visual Studio 'daki belge anahattı penceresi, Visual Studio için Blend [nesneler ve zaman çizelgesi penceresine](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) benzer. Belge ana hattı bu görevleri gerçekleştirmenize yardımcı olur:

- Çalışma yüzeyinde tüm öğeleri hiyerarşik yapısını görüntüleyin.

- Öğeleri değiştirmek için öğeleri seçin (örneğin, hiyerarşide hiyerarşi içine taşıyın veya Özellikler penceresi özelliklerini ayarlayın). Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Denetimleri olan öğeler için şablonları oluşturup yeniden açın.

- [Animasyonlar oluşturun](animate-objects-in-xaml-designer.md) (yalnızca Visual Studio için Blend).

Visual Studio 'da belge ana hat penceresini görüntülemek için, menü çubuğunda **görünüm** > **diğer Windows** > **Belge Anahattı**' nı seçin.
Nesneler ve Zaman Çizelgesi penceresini Visual Studio için Blend görüntülemek için, menü çubuğunda > **belge anahattını** **görüntüle** ' yi seçin.

![Visual Studio 'da belge anahattı penceresi](media/document-outline-window.png)

Belge ana hat/Nesneler ve Zaman Çizelgesi penceresindeki ana görünüm bir belge hiyerarşisini ağaç yapısında görüntüler. Belge anahattının hiyerarşik yapısını kullanarak belgeyi farklı ayrıntı düzeylerinde inceleyebilir ve öğeleri listedir veya gruplar halinde kilitler ve gizleyebilirsiniz. Bunlar belge ana hat/Nesneler ve Zaman Çizelgesi penceresinde kullanılabilen seçeneklerdir:

**Göster/gizle**

Çalışma yüzeyi öğelerini görüntüler veya gizler. Gösterildiğinde bir gözle sembol olarak görünür. Ayrıca, bir öğeyi gizlemek için **ctrl**+**h** tuşlarına **basabilir ve bunu** göstermek için **CTRL**+**h**+.

**Kilit/kilit açma**

Çalışma yüzeyi öğelerini kilitler veya kilitlerini kaldırır. Kilitli öğeler değiştirilemez. Kilitliyken bir asma kilit simgesi olarak görünür. Ayrıca, bir öğeyi kilitlemek için **ctrl**+**l** tuşlarına basabilir ve kilidini açmak Için **CTRL**+**l** **tuşlarını**+.

**Kapsam, pageRoot 'e döndürün**

Bir yukarı ok simgesini gösteren belge ana hattı/Nesneler ve Zaman Çizelgesi penceresinin en üstünde bulunan seçenek, önceki kapsama gider. Üst kapsama gitme yalnızca bir stil veya şablon kapsamı içinde olduğunuzda geçerlidir.

## <a name="properties-window"></a>Özellik penceresi

**Özellikler** penceresi denetimlerde özellik değerlerini ayarlamanıza olanak sağlar. İşte bu şekilde görünür:

![Özellik penceresi](media/xaml-designer-properties-window.png)

**Özellikler** penceresinin en üstünde çeşitli seçenekler vardır:

- **Ad** kutusunda şu anda seçili olan öğenin adını değiştirin.
- Sol üst köşesinde şu anda seçilen öğeyi temsil eden bir simge yoktur.
- Özellikleri kategoriye veya alfabetik olarak düzenlemek için, **Düzenleme ölçütü** listesinde **Kategori**, **ad**veya **kaynak** ' a tıklayın.
- Bir denetimin olay listesini görmek için, bir şimşek işareti simgesi olarak görünen **Olaylar** düğmesine tıklayın.
- Bir özelliği aramak için, arama kutusuna özelliğin adını yazmak üzere başlatın. **Özellikler** penceresinde, yazarken aramanızla eşleşen özellikler görüntülenir.

Bazı özellikler bir aşağı ok düğmesini seçerek gelişmiş özelliklerini ayarlamanıza olanak sağlar.

Her özellik değerinin sağında, Box simgesi olarak görünen bir *özellik işaretleyicisi* bulunur. Özellik işaretçisi görünümünü veri bağlama veya özelliğine uygulanan bir kaynak olup olmadığını belirtir. Örneğin, beyaz kutu simgesi varsayılan bir değer belirtir, yerel kaynak uygulanan ve turuncu bir kutu, genellikle bir veri bağlamayı uygulanan gösterir genellikle bir siyah kutu simgesi gösterir. Özellik işaretçisi tıkladığınızda stili tanımına gidin, veri bağlama Oluşturucusu'nu açmak veya Kaynak Seçici'yi açın.

Özellikleri kullanma ve olayları işleme hakkında daha fazla bilgi için bkz. [denetimlere ve desenlere giriş](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nda öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Kaynak oluşturma ve uygulama](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [İzlenecek yol: XAML Tasarımcısı’nda verilere bağlama](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
