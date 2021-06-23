---
title: Visual Studio XAML Tasarımcısı ile kullanıcı Visual Studio XAML Tasarımcısı
description: XAML tabanlı uygulamalar tasarlamanıza yardımcı XAML Tasarımcısı görsel arabirim sağlayan Visual Studio için Blend çalışma alanı kullanıcı arabirimi ve özellikleri hakkında bilgi edinin.
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
ms.openlocfilehash: ef7d94acbb558ef2a8a3c557051e6dea16be916c
ms.sourcegitcommit: 809fff25b7701882c899c639eeb6da38ad4fb88a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2021
ms.locfileid: "112550694"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma

XAML Tasarımcısı ve Visual Studio Visual Studio için Blend WPF ve UWP gibi XAML tabanlı uygulamalar tasarlamanıza yardımcı olacak görsel bir arabirim sağlar. Araç Kutusu penceresinden denetimleri sürükleyerek (Visual Studio için Blend'de Varlıklar penceresi) ve Özellikler penceresi. XAML'yi doğrudan XAML görünümünde de düzenleyebilirsiniz.

İleri düzey kullanıcılar için, [uygulamanın XAML Tasarımcısı.](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md)

> [!NOTE]
> Xamarin.Forms, XAML tasarımcısını desteklemez. Xamarin.Forms XAML KULLANıCıLARıNıZı görüntülemek ve uygulama çalışırken düzenlemek için Xamarin.Forms XAML Çalışırken Yeniden Yükleme kullanın. Daha fazla bilgi için [Xamarin.Forms XAML Çalışırken Yeniden Yükleme (Önizleme) sayfasına](/xamarin/xamarin-forms/xaml/hot-reload/) bakın.

## <a name="xaml-designer-workspace"></a>XAML Tasarımcısı çalışma alanı

XAML Tasarımcısı çalışma alanı çeşitli görsel arabirim öğeleri içerir. Bunlar arasında *çalışma yüzeyi* (görsel tasarım yüzeyi), XAML düzenleyicisi, Belge Ana Hat penceresi (Nesneler ve Zaman Çizelgesi penceresinde Visual Studio için Blend) ve Özellikler penceresi. Dosyayı açmak XAML Tasarımcısı, dosyanın içinde bir XAML dosyasına **sağ tıklayın ve Çözüm Gezgini'yi** **Görünüm Tasarımcısı.**

XAML Tasarımcısı XAML görünümü ve Tasarım görünümü işlenmiş XAML işaretlemesi için eşitlenmiş bir görünüm sağlar. Bir XAML dosyası Visual Studio Visual Studio için Blend, Tasarım ve **XAML Tasarım görünümü XAML** görünümü arasında geçiş  yapın. En üstte hangi **pencerenin** görüntülendiğinden (çalışma panosu veya XAML düzenleyicisi) geçiş yapmak XAML Tasarımcısı Bölmeleri Değiştir düğmesini kullanarak Bölmeleri Değiştir ![ ](media/swap-panes.PNG) düğmesini kullanabilirsiniz.

### <a name="design-view"></a>Tasarım görünümü

Bu Tasarım görünümü çalışma yüzeyini içeren pencere etkin penceredir ve bunu birincil iş yüzeyi olarak kullanabilirsiniz. Öğeleri ekleyerek, çizerek veya değiştirerek uygulamanıza görsel olarak sayfa tasarlamak için bunu kullanabilirsiniz. Daha fazla bilgi için [bkz. XAML Tasarımcısı.](../xaml-tools/working-with-elements-in-xaml-designer.md) Bu çizimde, çalışma panosu Tasarım görünümü.

![Tasarım görünümü XAML Tasarımcısı](media/xaml-artboard.png)

Bu özellikler çalışma panosunda kullanılabilir:

**Snaplines**

Yaslama *çizgileri,* denetimlerin kenarlarının ne zaman hizalı olduğunu veya metin taban çizgilerinin hizalı olduğunu göstermek için kırmızı kesikli çizgi olarak görünen hizalama sınırlarıdır. Hizalama sınırları yalnızca **yaslama çizgilerini yaslama etkinleştirildiğinde** görünür.

**Kılavuz rayları**

Kılavuz rayları, kılavuz panelindeki satırları ve sütunları yönetmek [için](xref:Windows.UI.Xaml.Controls.Grid) kullanılır. Satır ve sütunları oluşturabilir, silebilir ve bunların göreli genişliklerini ve yüksekliklerini ayarlayabilirsiniz. Çalışma şeridinin sol kısmında görünen dikey Kılavuz rayı, satırlar için, üstte görünen yatay çizgi ise sütunlar için kullanılır.

**Kılavuz donatıcıları**

Kılavuz donatıcı, Kılavuz rayı üzerinde dikey veya yatay çizgi eklenmiş bir üçgen olarak görünür. Bir Kılavuz donatıcısını sürüklerken, fareyi hareket ettirerek bitişik sütunların veya satırların genişlikleri veya yükseklikleri uzer.

Kılavuz donatıcıları, bir Kılavuzun satırlarının ve sütunlarının genişliğini ve yüksekliğini kontrol etmek için kullanılır. Kılavuz raylarına tıklayarak yeni bir sütun veya satır abilirsiniz. Kılavuz paneli için iki veya daha fazla sütunu veya satırı olan yeni bir satır veya sütun satırı eklerken, genişliği ve yüksekliği açıkça ayarlamanıza olanak sağlayan bir mini araç çubuğu rayın dışında görünür. Mini araç çubuğu Kılavuz satırları ve sütunları için boyutlandırma seçeneklerini ayarlamaya olanak sağlar.

![XAML Tasarımcısı'de kılavuz donatıcı](media/grid-adorner.png)

**Tanıtıcıları yeniden boyutlandırma**

Seçilen denetimlerde yeniden boyutlandırma tutamaçları görünür ve denetimi yeniden boyutlandırmanıza olanak sağlar. Bir denetimi yeniden boyutlandırarak, genellikle denetimi boyutlandırmanıza yardımcı olacak genişlik ve yükseklik değerleri görünür. Tasarım görünümünde denetimlerin manipülesi hakkında **daha fazla bilgi** için [bkz.](../xaml-tools/working-with-elements-in-xaml-designer.md)XAML Tasarımcısı.

**Kenar boşlukları**

Kenar boşlukları, denetimin kenarı ile kapsayıcının kenarı arasındaki sabit alan miktarını temsil ediyor. Özellikler penceresindeki Düzen altındaki Kenar boşluğu özelliklerini kullanarak [denetimin](xref:Windows.UI.Xaml.FrameworkElement.Margin) **kenar** boşluklarını **ayarlayın.**

**Kenar boşluğu donatıcıları**

Bir öğenin düzen kapsayıcısı ile ilgili kenar boşluklarını değiştirmek için kenar boşluğu donatıcılarını kullanın. Bir kenar boşluğu donatıcısı açık olduğunda, kenar boşluğu ayarlanmaz ve kenar boşluğu donatıcısı bozuk bir zincir görüntüler. Dış boşluk ayarlanmazsa, düzen kapsayıcısı çalışma zamanında yeniden boyutlandırılırken öğeler yerinde kalır. Bir kenar boşluğu donatıcı kapalıyken, kenar boşluğu donatıcısı kırılmamış bir zincir görüntüler ve düzen kapsayıcısı çalışma zamanında yeniden boyutlandırıldıklarında (kenar boşluğu sabit kalır) öğeler kenar boşluğuyla birlikte hareket eder.

**Öğe tanıtıcıları**

İşaretçiyi bir öğenin çevresini çevreleyen mavi kutunun köşelerinin üzerine taşısanız, çalışma panosunda görünen öğe tanıtıcılarını kullanarak bir öğeyi değiştirebilirsiniz. Bu tanıtıcılar öğeye köşe yarıçapı eklemenize, yeniden boyutlandırmanıza, çevirmenize, taşımanıza veya eklemenize olanak sağlar. Öğe tanıtıcısı simgesi işleve göre değişir ve işaretçinin tam konumuna bağlı olarak değişir. Öğe tanıtıcılarını görmüyorsanız öğesinin seçildiğinden emin olun.

Tasarım **görünümünde,** pencerenin sol alt alanında burada gösterildiği gibi ek çalışma panosu komutları kullanılabilir:

![Tasarım görünümü komutları](media/xaml-design-view-controls.png)

Bu komutlar bu araç çubuğunda kullanılabilir:

**Zoom**

Yakınlaştırma, tasarım yüzeyini boyuta alaştırır. %12,5'den %800'e yakınlaştırabilir veya Seçimi sığdır ve **Hepsini** sığdır gibi **seçenekleri seçebilirsiniz.**

**Yasla kılavuzu göster/gizle**

Kılavuz çizgilerini gösteren yasla kılavuzu görüntüler veya gizler. Kılavuz çizgileri, kılavuz çizgilerini **yaslama veya** yaslama çizgilerini **yaslama etkinleştirerek kullanılır.**

**Kılavuz çizgilerini yaslamayı açma/kapatma**

Kılavuz **çizgilerini yaslama** etkinse, bir öğe çalışma panosuna sürüklendikten sonra en yakın yatay ve dikey kılavuz çizgileriyle hizalanır.

**Çalışma panosu arka planını iki durumlu olarak değiştir**

Açık ve koyu arka plan arasında geçişler.

**Yaslama çizgilerini yaslamayı açma/kapatma**

Yas çizgileri denetimleri birbirine göre hizalamanıza yardımcı olur. **Yaslama** çizgilerini yaslama etkinse, bir denetimi diğer denetimlere göre sürüklerken, bazı denetimlerin kenarları ve metni yatay veya dikey olarak hizalanmışsa hizalama sınırları görünür. Hizalama sınırı kırmızı kesik çizgi olarak görünür.

**Proje kodunu devre dışı bırakma**

Özel [denetimler ve](debugging-or-disabling-project-code-in-xaml-designer.md)değer dönüştürücüler gibi proje kodunu devre dışı bırakarak tasarımcıyı yeniden yüklür.

### <a name="xaml-view"></a>XAML görünümü

**XAML görünümünde** XAML düzenleyicisini içeren pencere etkin pencere, XAML düzenleyicisi ise birincil yazma aracınızdır. Bu Extensible Application Markup Language (XAML), bir uygulamanın kullanıcı arabirimini belirtmek için bildirim temelli, XML tabanlı bir sözlük sağlar. XAML görünümü IntelliSense, otomatik biçimlendirme, söz dizimi vurgulama ve etiket gezintisini içerir. Aşağıdaki görüntüde IntelliSense menüsünün açık olduğu XAML görünümü görüntülenir:

![XAML görünümü](media/xaml-editor.png)

## <a name="document-outline-window"></a>Belge Ana Hat penceresi

Visual Studio Belge Ana Hat penceresi, Nesneler ve Zaman Çizelgesi [belge Visual Studio için Blend.](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) Belge Ana Hat şu görevleri gerçekleştirmeye yardımcı olur:

- Çalışma panosunda tüm öğelerin hiyerarşik yapısını görüntüleme.

- Öğeleri seçerek bunları değiştirebilirsiniz. Örneğin, hiyerarşide bunları hareket ettirebilirsiniz veya bunların özelliklerini hiyerarşide Özellikler penceresi. Daha fazla bilgi için [bkz. XAML Tasarımcısı.](../xaml-tools/working-with-elements-in-xaml-designer.md)

- Denetim olan öğeler için şablon oluşturma ve değiştirme.

- [Animasyon oluşturma](animate-objects-in-xaml-designer.md) (yalnızca Visual Studio için Blend).

Belge Ana Hat penceresini Visual Studio menü çubuğunda Diğer Windows Belge Ana Hatlarını  >  **Görüntüle'yi**  >  **seçin.**
Belge ana Nesneler ve Zaman Çizelgesi görüntülemek Visual Studio için Blend çubuğunda Belge Ana Hatlarını **Görüntüle'yi**  >  **seçin.**

![Visual Studio'de Belge Ana Hatları penceresi](media/document-outline-window.png)

Belge Ana Hat/Nesneler ve Zaman Çizelgesi penceresindeki ana görünüm, bir belgenin hiyerarşisini ağaç yapısında görüntüler. Belge ana hatlarının hiyerarşik doğasını kullanarak belgeyi farklı ayrıntı düzeylerinde inceleyip öğeleri tek tek veya gruplar halinde kilitleyip gizleyebilirsiniz. Belge Ana Hat/Ana Hat penceresinde Nesneler ve Zaman Çizelgesi kullanılabilir:

**Göster/gizle**

Çalışma panosu öğelerini görüntüler veya gizler. Gösterildiğinde bir göz simgesi olarak görünür. Ctrl H tuşlarına + **basarak** bir öğeyi gizleyebilirsiniz ve **shift** + **Ctrl** + **H tuşlarına** basarak da gösterebilirsiniz.

**Kilit/kilit açma**

Çalışma yüzeyi öğelerini kilitler veya kilitlerini kaldırır. Kilitli öğeler değiştirilemez. Kilitliyken bir asma kilit simgesi olarak görünür. Ayrıca,  + bir öğeyi kilitlemek için CTRL **l** tuşlarına basabilir ve  +  + kilidini açmak için CTRL **l** tuşlarına basabilirsiniz.

**Kapsam, pageRoot 'e döndürün**

Bir yukarı ok simgesini gösteren belge ana hattı/Nesneler ve Zaman Çizelgesi penceresinin en üstünde bulunan seçenek, önceki kapsama gider. Kapsam, yalnızca bir stil veya şablon kapsamındaysa geçerlidir.

## <a name="properties-window"></a>Özellik penceresi

**Özellikler** penceresi denetimlerde özellik değerlerini ayarlamanıza olanak sağlar. Şu şekilde görünür:

![Özellik penceresi](media/xaml-designer-properties-window.png)

**Özellikler** penceresinin en üstünde çeşitli seçenekler vardır:

- **Ad** kutusunda şu anda seçili olan öğenin adını değiştirin.
- Sol üst köşede, şu anda seçili olan öğeyi temsil eden bir simge vardır.
- Özellikleri kategoriye veya alfabetik olarak düzenlemek için, **Düzenleme ölçütü** listesinde **Kategori**, **ad** veya **kaynak** ' a tıklayın.
- Bir denetimin olay listesini görmek için, bir şimşek işareti simgesi olarak görünen **Olaylar** düğmesine tıklayın.
- Bir özelliği aramak için, arama kutusuna özelliğin adını yazmak üzere başlatın. **Özellikler** penceresinde, yazarken aramanızla eşleşen özellikler görüntülenir.

Bazı özellikler, gelişmiş özellikleri bir aşağı ok düğmesi seçerek ayarlamanıza olanak sağlar.

Her özellik değerinin sağında, Box simgesi olarak görünen bir *özellik işaretleyicisi* bulunur. Özellik işaretinin görünümü, bir veri bağlaması veya özelliğe uygulanmış bir kaynak olup olmadığını gösterir. Örneğin, bir beyaz kutu sembolü varsayılan bir değeri gösteriyorsa, bir siyah kutu sembolü genellikle yerel bir kaynağın uygulandığını ve turuncu bir kutu genellikle bir veri bağlamasının uygulandığını gösterir. Özellik işaretine tıkladığınızda, bir stilin tanımına gidebilir, veri bağlama oluşturucuyu açabilir veya kaynak seçiciyi açabilirsiniz.

Özellikleri kullanma ve olayları işleme hakkında daha fazla bilgi için bkz. [denetimlere ve desenlere giriş](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nda öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Kaynak oluşturma ve uygulama](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [İzlenecek yol: XAML Tasarımcısı’nda verilere bağlama](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
