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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0facc87df720af8376561ae7599fe20afeab1a12
ms.sourcegitcommit: c6af923c1f485959d751b23ab3f03541013fc4a7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73925972"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma

Visual Studio ve Visual Studio için Blend XAML Tasarımcısı, WPF, UWP ve Xamarin. Forms uygulamaları gibi XAML tabanlı uygulamalar tasarlamanıza yardımcı olacak görsel bir arabirim sağlar. Araç kutusu penceresinden (Visual Studio için Blend varlıklar penceresi) denetimleri sürükleyerek ve Özellikler penceresi özellikleri ayarlayarak uygulamalarınız için Kullanıcı arabirimleri oluşturabilirsiniz. XAML 'yi doğrudan XAML görünümünde de düzenleyebilirsiniz.

İleri düzey kullanıcılar için, XAML Tasarımcısı bile [özelleştirebilirsiniz](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

## <a name="xaml-designer-workspace"></a>XAML Tasarımcısı çalışma alanı

XAML Tasarımcısı çalışma alanı çeşitli görsel arabirim öğelerinden oluşur. Bunlar, *çalışma yüzeyini* (görsel tasarım yüzeyi), XAML Düzenleyicisi, belge ana hattı penceresi (Visual Studio için Blend nesneler ve zaman çizelgesi pencere) ve Özellikler penceresi içerir. XAML Tasarımcısı açmak için **Çözüm Gezgini** bir xaml dosyasına sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin.

XAML Tasarımcısı, uygulamanızın işlenmiş XAML işaretlemesini bir XAML görünümü ve eşitlenmiş Tasarım görünümü sağlar. Visual Studio 'da veya Visual Studio için Blend bir XAML dosyası açıkken, **Tasarım** ve **xaml** SEKMELERINI kullanarak tasarım görünümü ve XAML görünümü arasında geçiş yapabilirsiniz. En üstte yer alan çalışma yüzeyi ya da XAML Düzenleyicisi olarak değiştirmek için, XAML Tasarımcısı](media/swap-panes.PNG) **bölmeleri takas et düğmesini ![** .

### <a name="design-view"></a>Tasarım görünümü

Tasarım görünümü, çalışma yüzeyini içeren pencere etkin pencere olur ve bunu birincil iş yüzeyi olarak kullanabilirsiniz. Bu uygulamayı, öğeleri ekleyerek, çizerek veya değiştirerek uygulamanızdaki bir sayfayı görsel olarak tasarlamak için kullanabilirsiniz. Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md). Bu çizimde Tasarım görünümü çalışma yüzeyi gösterilmektedir.

![XAML Tasarımcısı Tasarım görünümü](media/xaml-artboard.png)

Çalışma yüzeyinde bu özellikler mevcuttur:

**Dayama çizgileri**

Anlık görüntü çizgileri, denetimlerin kenarlarının ne zaman hizalanacağını veya metin temellerinin hizalandığını göstermek için kırmızı kesikli çizgiler olarak görünen *Hizalama sınırlardır* . Hizalama sınırları yalnızca, **yama çizgilere yaslaması** etkin olduğunda görünür.

**Izgara rayları**

Izgara rayları, [kılavuz](xref:Windows.UI.Xaml.Controls.Grid) panelinde satırları ve sütunları yönetmek için kullanılır. Satır ve sütun oluşturup silebilir ve bunlara göreli genişlikleri ve yükseklikleri ayarlayabilirsiniz. Çalışma yüzeyinin solunda görünen dikey ızgara rampaları, satırlar için kullanılır ve üstte görünen yatay çizgi sütunlar için kullanılır.

**Izgara donatıcıları**

Kılavuz bir donatıcı, bir ızgara rampasının üzerine dikey veya yatay bir çizgi eklenmiş bir üçgen olarak görünür. Bir kılavuz donatıcısını sürüklediğinizde, fareyi taşırken bitişik sütunların veya satırların genişliği veya yükseklikleri güncellemektir.

Izgara donatıcıları, bir kılavuzun satır ve sütunlarının genişlik ve yüksekliğini denetlemek için kullanılır. Izgara rayları ' na tıklayarak yeni bir sütun veya satır ekleyebilirsiniz. İki veya daha fazla sütun veya satır içeren bir kılavuz paneli için yeni bir satır veya sütun satırı eklediğinizde, daha fazla genişlik ve yükseklik ayarlamanıza olanak tanıyan bir mini araç çubuğu, demiryolu dışında görünür. Mini araç çubuğu, kılavuz satırları ve sütunları için boyutlandırma seçeneklerini ayarlamanıza olanak sağlar.

![XAML Tasarımcısı kılavuz donatıcı](media/grid-adorner.png)

**Yeniden boyutlandırma tutamaçları**

Yeniden boyutlandırma tutamaçları seçili denetimlerde görünür ve denetimi yeniden boyutlandırmanızı sağlar. Bir denetimi yeniden boyutlandırdığınızda, genellikle denetimi boyutlandırmanıza yardımcı olmak için Genişlik ve yükseklik değerleri görüntülenir. **Tasarım** görünümünde denetimleri düzenleme hakkında daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Kenar boşlukları**

Kenar boşlukları, bir denetimin kenarı ve kapsayıcısının kenarı arasındaki sabit boşluk miktarını temsil eder. Bir denetimin kenar boşluklarını, **Özellikler** penceresinde **Düzen** altındaki [kenar boşluğu](xref:Windows.UI.Xaml.FrameworkElement.Margin) özelliklerini kullanarak ayarlayabilirsiniz.

**Kenar boşluğu donatıcıları**

Bir öğenin kenar boşluklarını düzen kapsayıcısına göre değiştirmek için kenar boşluğu donatıcıları kullanın. Bir kenar boşluğu donatıcısı açık olduğunda, bir kenar boşluğu ayarlı değildir ve kenar boşluğu donatıcısı bozuk bir zincir görüntüler. Kenar boşluğu ayarlanmamışsa, düzen kapsayıcısı çalışma zamanında yeniden boyutlandırılırken öğeler yerinde kalır. Bir kenar boşluğu donatıcısı kapalıyken, bir kenar boşluğu donatıcısı bozuk bir zincir görüntüler ve düzen kapsayıcısı çalışma zamanında yeniden boyutlandırıldığından (kenar boşluğu sabit kalır) öğeler kenar boşluğu ile birlikte taşınır.

**Öğe tutamaçları**

Bir öğeyi çevreleyen mavi kutunun köşelerinden işaretçiyi taşıdığınızda çalışma yüzeyinde görünen öğe tutamaçlarını kullanarak bir öğeyi değiştirebilirsiniz. Bu tutamaçlar, öğe için bir köşe yarıçapı döndürmenizi, yeniden boyutlandırmanızı, çevirmenizi, taşımanızı veya eklemenizi sağlar. Öğe tanıtıcısı sembolü, işaretçinin tam konumuna bağlı olarak işleve ve değişikliklere göre değişir. Öğe tutamaçlarını görmüyorsanız, öğenin seçili olduğundan emin olun.

**Tasarım** görünümünde, aşağıda gösterildiği gibi pencerenin sol alt bölümünde ek çalışma yüzeyi komutları kullanılabilir:

![Tasarım görünümü komutları](media/xaml-design-view-controls.png)

Bu komutlar bu araç çubuğunda kullanılabilir:

**Yakınlaştırma**

Yakınlaştırma, tasarım yüzeyini boyutlandırmanızı sağlar. % 12,5 ' dan %800 ' e yakınlaştırıp veya **seçimi sığdırma** ve **Tümünü sığdırma**gibi seçenekleri belirleyebilirsiniz.

**Yaslama kılavuzunu göster/gizle**

Kılavuz çizgilerini gösteren yaslama kılavuzunu görüntüler veya gizler. Kılavuz çizgileri, **kılavuz çizgilere yaslamayı** veya ek **yaslama çizgilerine yaslamayı**etkinleştirdiğinizde kullanılır.

**Kılavuz çizgilerine yaslamayı aç/kapat**

**Kılavuz çizgilerine yaslaması** etkinleştirilirse, çalışma yüzeyinde bir öğe sürüklediğinizde, öğesi en yakın yatay ve dikey kılavuz çizgilerine göre hizalanacaktır.

**Çalışma yüzeyi arka planını aç**

Açık ve koyu arka plan arasında geçiş yapar.

**Ek çizgi çizgilere yaslamayı aç/kapat**

Anlık görüntü çizgileri, denetimleri birbirlerine göre hizalamanıza yardımcı olur. Daha fazla denetime **yaslaması** etkinse, bir denetimi diğer denetimlere göre sürüklediğinizde, bazı denetimlerin kenarları ve metni yatay veya dikey olarak hizalandığında hizalama sınırları görüntülenir. Bir hizalama sınırı kırmızı kesikli çizgi olarak görünür.

**Proje kodunu devre dışı bırak**

[Proje kodunu](debugging-or-disabling-project-code-in-xaml-designer.md)devre dışı bırakır, örneğin, özel denetimler ve değer dönüştürücüler ve tasarımcıyı yeniden yükler.

### <a name="xaml-view"></a>XAML görünümü

**Xaml** görünümünde, XAML düzenleyicisini içeren pencere etkin pencere ve xaml Düzenleyicisi ise birincil yazma aracdır. Extensible Application Markup Language (XAML), bir uygulamanın kullanıcı arabirimini belirtmek için bildirime dayalı XML tabanlı bir sözlük sağlar. XAML görünümü IntelliSense, otomatik biçimlendirme, sözdizimi vurgulama ve etiket gezintisi içerir. Aşağıdaki görüntüde bir IntelliSense menüsü açık olan XAML görünümü gösterilmektedir:

![XAML görünümü](media/xaml-editor.png)

## <a name="document-outline-window"></a>Belge Anahattı penceresi

Visual Studio 'daki belge anahattı penceresi, Visual Studio için Blend [nesneler ve zaman çizelgesi penceresine](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) benzer. Belge ana hattı bu görevleri gerçekleştirmenize yardımcı olur:

- Çalışma yüzeyinde tüm öğelerin hiyerarşik yapısını görüntüleyin.

- Öğeleri değiştirmek için öğeleri seçin (örneğin, hiyerarşide hiyerarşi içine taşıyın veya Özellikler penceresi özelliklerini ayarlayın). Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Denetimler olan öğeler için şablonlar oluşturun ve değiştirin.

- [Animasyonlar oluşturun](animate-objects-in-xaml-designer.md) (yalnızca Visual Studio için Blend).

Visual Studio 'da belge ana hat penceresini görüntülemek için, menü çubuğunda **görüntüle** > **diğer Windows** > **Belge Anahattı**' nı seçin.
Nesneler ve Zaman Çizelgesi penceresini Visual Studio için Blend görüntülemek için, menü çubuğunda **görünüm** > **belge anahattını**seçin.

![Visual Studio 'da belge anahattı penceresi](media/document-outline-window.png)

Belge ana hat/Nesneler ve Zaman Çizelgesi penceresindeki ana görünüm bir belge hiyerarşisini ağaç yapısında görüntüler. Belge anahattının hiyerarşik yapısını kullanarak belgeyi farklı ayrıntı düzeylerinde inceleyebilir ve öğeleri listedir veya gruplar halinde kilitler ve gizleyebilirsiniz. Bunlar belge ana hat/Nesneler ve Zaman Çizelgesi penceresinde kullanılabilen seçeneklerdir:

**Göster/gizle**

Çalışma yüzeyi öğelerini görüntüler veya gizler. Gösterildiğinde bir gözle sembol olarak görünür. Ayrıca, bir öğeyi gizlemek için **ctrl**+**H** tuşlarına basabilir ve +**CTRL**+**h** **tuşlarına basarak gösterebilirsiniz**.

**Kilit/kilit açma**

Çalışma yüzeyi öğelerini kilitler veya kilitlerini kaldırır. Kilitli öğeler değiştirilemez. Kilitliyken bir asma kilit simgesi olarak görünür. Ayrıca, bir öğeyi kilitlemek için **ctrl**+**L** tuşlarına basabilir ve kilidini açmak Için +**CTRL**+**l** **tuşlarına basabilirsiniz.**

**Kapsam, pageRoot 'e döndürün**

Bir yukarı ok simgesini gösteren belge ana hattı/Nesneler ve Zaman Çizelgesi penceresinin en üstünde bulunan seçenek, önceki kapsama gider. Kapsam, yalnızca bir stil veya şablon kapsamındaysa geçerlidir.

## <a name="properties-window"></a>Özellik penceresi

**Özellikler** penceresi denetimlerde özellik değerlerini ayarlamanıza olanak sağlar. Şöyle görünür:

![Özellik penceresi](media/xaml-designer-properties-window.png)

**Özellikler** penceresinin en üstünde çeşitli seçenekler vardır:

- **Ad** kutusunda şu anda seçili olan öğenin adını değiştirin.
- Sol üst köşede, şu anda seçili olan öğeyi temsil eden bir simge vardır.
- Özellikleri kategoriye veya alfabetik olarak düzenlemek için, **Düzenleme ölçütü** listesinde **Kategori**, **ad**veya **kaynak** ' a tıklayın.
- Bir denetimin olay listesini görmek için, bir şimşek işareti simgesi olarak görünen **Olaylar** düğmesine tıklayın.
- Bir özelliği aramak için, arama kutusuna özelliğin adını yazmak üzere başlatın. **Özellikler** penceresinde, yazarken aramanızla eşleşen özellikler görüntülenir.

Bazı özellikler, gelişmiş özellikleri bir aşağı ok düğmesi seçerek ayarlamanıza olanak sağlar.

Her özellik değerinin sağında, Box simgesi olarak görünen bir *özellik işaretleyicisi* bulunur. Özellik işaretinin görünümü, bir veri bağlaması veya özelliğe uygulanmış bir kaynak olup olmadığını gösterir. Örneğin, bir beyaz kutu sembolü varsayılan bir değeri gösteriyorsa, bir siyah kutu sembolü genellikle yerel bir kaynağın uygulandığını ve turuncu bir kutu genellikle bir veri bağlamasının uygulandığını gösterir. Özellik işaretine tıkladığınızda, bir stilin tanımına gidebilir, veri bağlama oluşturucuyu açabilir veya kaynak seçiciyi açabilirsiniz.

Özellikleri kullanma ve olayları işleme hakkında daha fazla bilgi için bkz. [denetimlere ve desenlere giriş](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nda öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Kaynak oluşturma ve uygulama](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [İzlenecek yol: XAML Tasarımcısı’nda verilere bağlama](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)