---
title: Visual Studio XAML Tasarımcısı ile usıs oluşturma
description: XAML tabanlı uygulamalar tasarlamanıza yardımcı olacak görsel bir arabirim sağlayan Visual Studio için Blend XAML Tasarımcısı çalışma alanı kullanıcı arabirimi ve özellikleri hakkında bilgi edinin.
ms.date: 03/03/2020
ms.topic: conceptual
ms.custom: contperf-fy21q4, SEO-VS-2020
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.DocumentOutline
- Blend.Start.Dev12
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 2c0ba2234cedbc4de9ebf71475c226dbdf838e8d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045729"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma

Visual Studio ve Visual Studio için Blend XAML Tasarımcısı, WPF ve UWP gibi XAML tabanlı uygulamalar tasarlamanıza yardımcı olacak görsel bir arabirim sağlar. araç kutusu penceresinden (Visual Studio için Blend varlıklar penceresi) denetimleri sürükleyerek ve Özellikler penceresi özellikleri ayarlayarak uygulamalarınız için kullanıcı arabirimleri oluşturabilirsiniz. XAML 'yi doğrudan XAML görünümünde de düzenleyebilirsiniz.

İleri düzey kullanıcılar için, XAML Tasarımcısı bile [özelleştirebilirsiniz](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin. Forms bir XAML tasarımcısını desteklemez. Xamarin. Forms XAML Usıs 'nizi görüntülemek ve uygulama çalışırken bunları düzenlemek için, Xamarin. Forms için XAML etkin yeniden yükleme ' yi kullanın. Daha fazla bilgi için bkz. [Xamarin. Forms Için xaml Hot reload (Önizleme)](/xamarin/xamarin-forms/xaml/hot-reload/) sayfası.

## <a name="xaml-designer-workspace"></a>XAML Tasarımcısı çalışma alanı

XAML Tasarımcısı çalışma alanı çeşitli görsel arabirim öğelerinden oluşur. bunlar, *çalışma yüzeyini* (görsel tasarım yüzeyi), XAML düzenleyicisi, belge ana hattı penceresi (Visual Studio için Blend Nesneler ve Zaman Çizelgesi pencere) ve Özellikler penceresi içerir. XAML Tasarımcısı açmak için **Çözüm Gezgini** bir xaml dosyasına sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin.

XAML Tasarımcısı, uygulamanızın işlenmiş XAML işaretlemesini bir XAML görünümü ve eşitlenmiş Tasarım görünümü sağlar. Visual Studio veya Visual Studio için Blend bir XAML dosyası açıkken, **tasarım** ve **xaml** sekmelerini kullanarak Tasarım görünümü ve xaml görünümü arasında geçiş yapabilirsiniz.  ![ ](media/swap-panes.PNG) Üstteki hangi pencerenin çalışma yüzeyi ya da xaml Düzenleyicisi olarak görüneceğini değiştirmek için XAML Tasarımcısı ' deki bölmeleri takas et düğmesini kullanabilirsiniz.

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

**Zoom**

Yakınlaştırma, tasarım yüzeyini boyutlandırmanızı sağlar. % 12,5 ' dan %800 ' e yakınlaştırıp veya **seçimi sığdırma** ve **Tümünü sığdırma** gibi seçenekleri belirleyebilirsiniz.

**Yaslama kılavuzunu göster/gizle**

Kılavuz çizgilerini gösteren yaslama kılavuzunu görüntüler veya gizler. Kılavuz çizgileri, **kılavuz çizgilere yaslamayı** veya ek **yaslama çizgilerine yaslamayı** etkinleştirdiğinizde kullanılır.

**Kılavuz çizgilerine yaslamayı aç/kapat**

**Kılavuz çizgilerine yaslaması** etkinleştirilirse, bir öğe, çalışma yüzeyine sürüklediğinizde en yakın yatay ve dikey kılavuz çizgilerine göre hizalanacaktır.

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

Visual Studio belge anahattı penceresi Visual Studio için Blend [Nesneler ve Zaman Çizelgesi penceresine](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) benzer. Belge ana hattı bu görevleri gerçekleştirmenize yardımcı olur:

- Çalışma yüzeyinde tüm öğelerin hiyerarşik yapısını görüntüleyin.

- Öğeleri değiştirebilmeniz için öğeleri seçin. Örneğin, bunları hiyerarşide etrafında taşıyabilir veya Özellikler penceresi özelliklerini ayarlayabilirsiniz. Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Denetimler olan öğeler için şablonlar oluşturun ve değiştirin.

- [animasyonlar oluşturun](animate-objects-in-xaml-designer.md) (yalnızca Visual Studio için Blend).

Visual Studio içinde belge ana hat penceresini görüntülemek için, menü çubuğunda   >  **diğer Windows**  >  **belge anahattını** görüntüle ' yi seçin.
Visual Studio için Blend Nesneler ve Zaman Çizelgesi penceresini görüntülemek için, menü çubuğunda   >  **belge anahattını** görüntüle ' yi seçin.

![Visual Studio belge anahattı penceresi](media/document-outline-window.png)

Belge ana hat/Nesneler ve Zaman Çizelgesi penceresindeki ana görünüm bir belge hiyerarşisini ağaç yapısında görüntüler. Belge anahattının hiyerarşik yapısını kullanarak belgeyi farklı ayrıntı düzeylerinde inceleyebilir ve öğeleri listedir veya gruplar halinde kilitler ve gizleyebilirsiniz. Belge ana hat/Nesneler ve Zaman Çizelgesi penceresinde aşağıdaki seçenekler mevcuttur:

**Göster/gizle**

Çalışma yüzeyi öğelerini görüntüler veya gizler. Gösterildiğinde bir gözle sembol olarak görünür. Ayrıca, bir öğeyi gizlemek için **CTRL** + **h** tuşlarına basabilir ve  +  + bunu göstermek için CTRL **h** tuşlarına basabilirsiniz.

**Kilitleme/kilidini açma**

Çalışma panosu öğelerini kilitler veya kilidini açar. Kilitli öğeler değiştirilemez. Kilitlendiğinde asma kilit simgesi olarak görünür. Bir öğeyi kilitlemek **için Ctrl** L tuşlarına ve kilidini açmak için +  **Shift** + **Ctrl** + **L** tuşlarına da basebilirsiniz.

**Kapsamı pageRoot'a iade edin**

Yukarı ok simgesini gösteren Belge Ana Hat/Nesneler ve Zaman Çizelgesi penceresinin en üstünde yer alan seçeneği önceki kapsama taşınır. Kapsamın kapsamı yalnızca bir stil veya şablon kapsamındayken geçerlidir.

## <a name="properties-window"></a>Özellik penceresi

Özellikler **penceresi,** denetimlerde özellik değerlerini ayarlamaya olanak sağlar. Şu şekilde görünür:

![Özellik penceresi](media/xaml-designer-properties-window.png)

Özellikler penceresinin üst kısmında çeşitli **seçenekler** vardır:

- Ad kutusunda seçili olan öğenin **adını** değiştirme.
- Sol üst köşede seçili olan öğeyi temsil eden bir simge vardır.
- Özellikleri kategoriye veya alfabetik olarak düzenlemek için, Sıralamaya göre **düzenle listesinde** **Kategori,** **Ad** veya **Kaynak'a** tıklayın.
- Bir denetimin olay listesini görmek için, şimşek **simgesi** olarak görünen Olaylar düğmesine tıklayın.
- Bir özelliği aramak için arama kutusuna özelliğin adını yazın. Özellikler **penceresi,** siz yazarak aramanıza göre özellikleri görüntüler.

Bazı özellikler, aşağı ok düğmesini seçerek gelişmiş özellikleri ayarlamaya olanak sağlar.

Her özellik değerinin sağ yanında, kutu *simgesi olarak* görünen bir özellik işaretçisi yer almaktadır. Özellik işaretçisi görünümü, bir veri bağlaması veya özelliğine uygulanan bir kaynak olup olmadığını gösterir. Örneğin, beyaz kutu simgesi varsayılan değeri, siyah kutu simgesi genellikle yerel bir kaynağın uygulandığını, turuncu kutu ise genellikle bir veri bağlamanın uygulandığını gösterir. Özellik işaretçisi'ne tıklarken stilin tanımına gidip veri bağlama oluşturucusu'nu açabilir veya kaynak seçiciyi açabilirsiniz.

Özellikleri kullanma ve olayları işleme hakkında daha fazla bilgi için [bkz. Denetimlere ve desenlere giriş.](/windows/uwp/design/controls-and-patterns/controls-and-events-intro)

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nda öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Kaynak oluşturma ve uygulama](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [İzlenecek yol: XAML Tasarımcısı’nda verilere bağlama](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
