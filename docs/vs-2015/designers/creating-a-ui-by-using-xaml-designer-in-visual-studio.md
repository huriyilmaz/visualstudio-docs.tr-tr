---
title: XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 879d8457a0f5fd4bf63a2d69a4f3f026ce4c6fe1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294667"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Visual Studio’da XAML Tasarımcısı’nı kullanarak kullanıcı arabirimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'da XAML Tasarımcısı, XAML tabanlı Windows Store, Windows Phone, WPF ve Silverlight uygulamaları tasarlamanıza yardımcı olması için görsel bir arabirim sağlar. **Araç kutusu** ' ndan denetimleri sürükleyip **Özellikler penceresinde özellikleri** ayarlayarak uygulamalarınız için Kullanıcı arabirimleri oluşturabilirsiniz. Ayrıca, XAML XAML görünümünde doğrudan düzenleyebilirsiniz.

 Animasyonlar ve davranışlar gibi gelişmiş XAML tasarım görevleri için bkz. [Visual Studio için Blend kullanarak Kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>XAML Tasarımcısı çalışma alanı
 XAML Tasarımcısı'nda çalışma birkaç görsel arabirim öğelerini içerir. Çalışma yüzeyini, XAML Düzenleyicisi, bunlar cihaz penceresi ve belge ana hattı penceresinin Özellikler penceresi. XAML Tasarımcısı açmak için **Çözüm Gezgini** bir xaml dosyasına sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin.

## <a name="authoring-views"></a>Yazma görünümleri
 XAML Tasarımcısı, uygulamanızın biçimlendirmenin XAML eşitlenmiş bir Tasarım görünümünü ve XAML görünümü sağlar. Visual Studio 'da bir XAML dosyası açıkken, **Tasarım** ve **xaml** SEKMELERINI kullanarak tasarım görünümü ve XAML görünümü arasında geçiş yapabilirsiniz. En üstte yer alan çalışma yüzeyi ya da XAML Düzenleyicisi olan pencereyi değiştirmek için **bölmeleri Değiştir** düğmesini kullanabilirsiniz.

 Tasarım görünümü, *çalışma yüzeyini* içeren pencere etkin pencere olur ve bunu birincil iş yüzeyi olarak kullanabilirsiniz. Görsel olarak bir sayfa veya çizim öğeleri ekleyerek ve ardından bunları değiştirerek uygulamanızı tasarlamak için kullanabilirsiniz. Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md). Bu örnekte, çalışma yüzeyinde Tasarım görünümünde gösterilmiştir.

 ![XAML Tasarımcısı Tasarım görünümü](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Bu özellikler, çalışma yüzeyine kullanılabilir:

 Anlık görüntü **çizgileri** Anlık görüntü çizgileri, denetimlerin kenarlarının ne zaman hizalandığını göstermek için kırmızı kesikli çizgiler veya metin temelleri hizalı olarak görünen *Hizalama sınırlardır* . Hizalama sınırları yalnızca, **yama çizgilere yaslaması** etkin olduğunda görünür.

 Izgara **rayları** `Grid` raylar [kılavuz](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) panelinde satırları ve sütunları yönetmek için kullanılır. Oluşturma ve satırları ve sütunları Sil ve kendi göreli genişlik ve yükseklik ayarlayabilirsiniz. Çalışma yüzeyinin sol tarafında görünür, dikey kılavuz parmaklık için satırlar kullanılır ve üst kısmında görünür, yatay çizgi sütunlar için kullanılır.

 **Izgara donatıcıları** `Grid` donatıcı, `Grid` Rampadaki dikey veya yatay bir çizgi eklenmiş bir üçgen olarak görünür. Bir `Grid` donatıcı sürüklediğinizde, fareyi taşırken bitişik sütunların veya satırların genişliği veya yükseklikleri güncellenemez.

 `Grid` Donatıcılar, bir `Grid`satırlarının ve sütunlarının genişlik ve yüksekliğini denetlemek için kullanılır. `Grid` raya tıklayarak yeni bir sütun veya satır ekleyebilirsiniz. İki veya daha fazla sütun veya satır içeren bir `Grid` paneli için yeni bir satır veya sütun satırı eklediğinizde, bir mini araç çubuğu, açıkça genişlik ve yükseklik ayarlamanıza olanak tanıyan bir mini araç çubuğudur. Mini araç çubuğu, `Grid` satırları ve sütunları için boyutlandırma seçeneklerini ayarlamanıza olanak sağlar.

 **Yeniden boyutlandırma tutamaçları** Yeniden boyutlandırma tutamaçları seçili denetimlerde görünür ve denetimi yeniden boyutlandırmanızı sağlar. Bir denetimi yeniden boyutlandırdığınızda, genişlik ve yükseklik değerlerini, genellikle denetiminin boyutunu yardımcı olması için görünür. Tasarım görünümü denetimleri düzenleme hakkında daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md).

 **Kenar boşlukları** Kenar boşlukları, bir denetimin kenarı ve kapsayıcısının kenarı arasındaki sabit boşluk miktarını temsil eder. Özellikler penceresi **Düzen** altındaki [kenar boşluğu](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) özelliklerini kullanarak bir denetimin kenar boşluklarını ayarlayabilirsiniz.

 **Kenar boşluğu donatıcıları** Bir öğenin kenar boşluklarını düzen kapsayıcısına göre değiştirmek için kenar boşluğu donatıcıları kullanabilirsiniz. Kenar boşluğu donatıcısı açıksa, bir kenar boşluğu ayarlı değildir ve kenar boşluğu donatıcısı bozuk zincirini görüntüler. Kenar boşluğu ayarlı değil, Düzen kapsayıcısı çalışma zamanında yeniden boyutlandırıldığında öğeleri yerinde kalır. Kenar boşluğu donatıcısı kapalı olduğunda, kenar boşluğu donatıcısı sertifikalarından zinciri görüntüler ve öğeleri Düzen kapsayıcısı (kenar sabit kalır), çalışma zamanında yeniden boyutlandırıldığından kenar boşlukları ile taşınır.

 **Öğe tutamaçları** Bir öğeyi çevreleyen mavi kutunun köşelerinden işaretçiyi taşıdığınızda çalışma yüzeyinde görünen öğe tutamaçlarını kullanarak bir öğeyi değiştirebilirsiniz. Bu tanıtıcıları, döndürme, yeniden boyutlandırma, çevir, taşıyın veya öğeye bir köşe yarıçapı eklemenizi sağlar. Öğesi işleyici için Sembol işlevi değişir ve işaretçiyi tam konumuna bağlı olarak değişir. Öğe tutamaçları görmüyorsanız, öğe seçili olduğundan emin olun.

 Tasarım görünümünde, ek çalışma yüzeyine komutlar burada gösterildiği gibi ekranın sol alt bölümünde kullanılabilir:

 ![Tasarım görünümü komutları](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Bu komutlar, bu araç çubuğunda kullanılabilir:

 **Yakınlaştır** Yakınlaştırma, tasarım yüzeyini boyutlandırmanızı sağlar. % 12,5 ' dan %800 ' e yakınlaştırabilir veya **seçime uygun** ve **tümüne Sığdır**gibi seçenekleri belirleyebilirsiniz.

 **Yaslama kılavuzunu göster/gizle** Kılavuz çizgilerini gösteren yaslama kılavuzunu görüntüler veya gizler. Kılavuz çizgileri **ya da ek** kılavuz **çizgilere** yaslaması etkinleştirildiğinde kılavuz çizgileri kullanılır.

 **Kılavuz çizgilerine yaslamayı aç/kapat** Çalışma yüzeyinde bir öğeyi sürüklediğinizde **kılavuz çizgilere yaslaması** etkinleştirilirse, öğesi en yakın yatay ve dikey kılavuz çizgilerine göre hizalanacaktır.

 Ek **çizgi çizgilere yaslamayı aç/kapat** Anlık görüntü çizgileri, denetimleri birbirlerine göre hizalamanıza yardımcı olur. Daha fazla denetime **yaslaması** etkinse, bir denetimi diğer denetimlere göre sürüklediğinizde, bazı denetimlerin kenarları ve metni yatay veya dikey olarak hizalandığında hizalama sınırları görüntülenir. Bir hizalama sınırı kırmızı kesik çizgili bir çizgi olarak görünür.

 XAML görünümünde, XAML Düzenleyicisi'ni içeren etkin penceresidir ve XAML Düzenleyicisi'ni, birincil yazma aracıdır. Extensible Application Markup Language (XAML), bir uygulamanın kullanıcı arabirimini belirtmek için bildirim temelli, XML tabanlı bir sözlüğünü sağlar. XAML görünümü, IntelliSense, otomatik biçimlendirme, söz dizimi vurgulama ve etiket Gezinti içerir. Bu örnekte, XAML görünümü gösterilmiştir:

 ![XAML görünümü](../designers/media/xaml-editor.png "xaml_editor")

 **Bölünmüş görünüm çubuğu** Bölünmüş görünüm çubuğu, XAML Düzenleyicisi alt pencerede olduğunda XAML görünümünün en üstünde görünür. Bölünmüş Görünüm Çubuğu Tasarım görünümünde ve XAML görünümünde göreli boyutlarını denetlemenizi sağlar. Ayrıca görünümlerin konumlarını da ( **değiştirme bölmeleri** kullanarak) değiş tokuş edebilirsiniz, görünümlerin yatay veya dikey olarak düzenlenmesini belirtebilir ve her iki görünümü de daraltın.

 **Biçimlendirme önizlemesi** Biçimlendirme yakınlaştırma XAML görünümünü boyutlandırmanızı sağlar. %400 %20 değerinden yakınlaştırma yapabilirsiniz.

## <a name="device-window"></a>Cihaz penceresi
 XAML Tasarımcısı'nda cihaz penceresi, tasarım zamanında çeşitli görünümler, görüntüler, benzetimini gerçekleştirmek ve Windows Store veya Windows Phone projeniz için seçenekleri görüntüleme sağlar. XAML Tasarımcısı çalışırken, **Tasarım** menüsünde cihaz penceresi kullanılabilir. İşte bu şekilde görünür:

 ![Cihaz penceresi](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Cihaz penceresindeki Seçenekler şunlardır:

 **Görüntüleme** Uygulama için farklı ekran boyutlarını ve çözümlerini belirtir.

 **Yön** Uygulama için farklı yönleri belirtir: **yatay** veya **Dikey**.

 **Kenar** Uygulamanız için farklı kenar hizalamalarını belirtir: **hem** **sol**, **sağ**, ya da **hiçbiri**.

 **Yüksek karşıtlık** Uygulamanın seçili karşıtlık ayarını temel alarak önizlemesini görüntüleyin. Bu ayar, **varsayılan**dışında bir değer olarak ayarlandığında, App. xaml içinde ayarlanan `RequestedTheme` özelliğini geçersiz kılar.

 **Ölçeklendirmeyi geçersiz kıl** Tasarım yüzeyi içinde belge ölçeklendirmesinin benzetimini açar ve kapatır. Bu bir faktörüyle ölçeğe artırmanıza olanak sağlar. Öykünme üzerinde etkinleştirmek için onay kutusunu seçin. Örneğin, ölçeklendirme, yüzde %100 ise, belge tasarım yüzeyine içinde %140 ölçeklendirin. Geçerli ölçeğe 180 ise bu seçenek devre dışıdır.

 **En küçük genişlik** En düşük genişlik ayarını belirtir. Minimum genişlik, App.xaml içinde değiştirilebilir.

 **Tema** Uygulama temasını belirtir. Örneğin, koyu ve açık bir tema arasında geçiş.

 **Chrome göster** Tasarım görünümü içinde uygulamanızın çevresindeki sanal tablet çerçevesini açar ve kapatır. Çerçeve göstermek için onay kutusunu seçin.

 **Görüntülenecek klip** Görüntüleme modunu belirtir. Belge boyutunu görüntüleme boyutuna kırpmak için bu onay kutusunu seçin.

## <a name="document-outline-window"></a>Belge Anahattı penceresi
 Belge Anahattı penceresi XAML Tasarımcısı'nda bu görevleri gerçekleştirmenize yardımcı olur:

- Çalışma yüzeyinde tüm öğeleri hiyerarşik yapısını görüntüleyin.

- Öğeleri seçin, böylece bunları (hiyerarşisinde etrafında onları çalışma yüzeyinde değiştirin, özelliklerini Özellikler penceresinde ayarlayın ve benzeri taşıma) değiştirebilirsiniz. Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md)

- Denetimleri olan öğeler için şablonları oluşturup yeniden açın.

- Seçilen öğeler için bağlam menüsünü kullanın. Aynı menüyü, çalışma yüzeyinde seçilen öğeleri için de kullanılabilir.

  Belge Anahattı penceresini görüntülemek için, menü çubuğunda **Görünüm**, **diğer pencereler**, **belge ana hattı**' nı seçin.

  ![Belge Anahattı penceresi](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Belge Anahattı penceresindeki Seçenekler şunlardır:

  **Belge ana hattı** Belge ana hattı penceresindeki ana görünüm bir belge hiyerarşisini ağaç yapısında görüntüler. Farklı düzeylerde, belge inceleme ve kilitleme ve öğeleri tek veya grup gizlemek için Belge Anahattı hiyerarşik yapısını kullanabilirsiniz.

  **Göster/Gizle** Belge Anahatdaki öğelere karşılık gelen çalışma yüzeyi öğelerini görüntüler veya gizler. Gösterildiğinde bir gözle sembol görüntüleyen **Göster/Gizle** düğmelerini kullanın veya öğeleri GIZLEMEK için CTRL + h tuşlarına ve bunları görüntülemek için SHIFT + CTRL + h tuşlarına basın.

  **Kilit/kilit açma** Belge Anahatdaki öğelere karşılık gelen çalışma yüzeyi öğelerini kilitler veya kilitlerini kaldırır. Kilitli öğeler değiştirilemez. Kilitliyken bir asma kilit simgesi görüntüleyen **kilit/kilit açma** düğmelerini kullanın veya öğeleri KILITLEMEK için CTRL + l tuşlarına basın ve kilitlerini açmak için SHIFT + CTRL + l tuşlarına basın.

  **Kapsam, pageRoot 'e döndürün** Belge ana hattı penceresinin üst kısmındaki, yukarı ok simgesini gösteren seçeneği, belge ana hattını önceki kapsama geri döndürür. Üst kapsama gitme yalnızca bir stil veya şablon kapsamı içinde olduğunuzda geçerlidir.

## <a name="properties-window"></a>Özellik penceresi
 Özellikler penceresinde denetimlerinde özellik değerlerini ayarlamanıza imkan sağlar. İşte bu şekilde görünür:

 ![Özellikler penceresi](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Özellikler penceresinin üst kısmındaki çeşitli seçenek vardır. **Ad** kutusunu kullanarak şu anda seçili olan öğenin adını değiştirebilirsiniz. Sol üst köşesinde şu anda seçilen öğeyi temsil eden bir simge yoktur. Özellikleri kategoriye veya alfabetik olarak düzenlemek için, **Düzenleme ölçütü** listesinde **Kategori**, **ad**veya **kaynak** ' a tıklayın. Bir denetimin olay listesini görmek için, bir şimşek işareti simgesi görüntüleyen **Olaylar** düğmesine tıklayın. Bir özelliği aramak için, **arama özellikleri** kutusuna özelliğin adını yazmak üzere başlatın. Siz yazarken aramanızla eşleşen özellikleri Özellikler penceresinde görüntülenir. Bazı özellikler bir aşağı ok düğmesini seçerek gelişmiş özelliklerini ayarlamanıza olanak sağlar. Özellikleri kullanma ve olayları işleme hakkında daha fazla bilgi için bkz [. hızlı başlangıç: denetim ekleme ve olayları işleme](https://go.microsoft.com/fwlink/?LinkID=247983)

 Her özellik değerinin sağında, Box simgesi olarak görünen bir *özellik işaretleyicisi* bulunur. Özellik işaretçisi görünümünü veri bağlama veya özelliğine uygulanan bir kaynak olup olmadığını belirtir. Örneğin, beyaz kutu simgesi varsayılan bir değer belirtir, yerel kaynak uygulanan ve turuncu bir kutu, genellikle bir veri bağlamayı uygulanan gösterir genellikle bir siyah kutu simgesi gösterir. Özellik işaretçisi tıkladığınızda stili tanımına gidin, veri bağlama Oluşturucusu'nu açmak veya Kaynak Seçici'yi açın.

## <a name="see-also"></a>Ayrıca Bkz.
 [XAML Tasarımcısı](../designers/working-with-elements-in-xaml-designer.md) [bir kaynak oluşturma ve uygulama](../designers/how-to-create-and-apply-a-resource.md) [izlenecek yol kılavuzu: XAML Tasarımcısı verilere bağlama](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
