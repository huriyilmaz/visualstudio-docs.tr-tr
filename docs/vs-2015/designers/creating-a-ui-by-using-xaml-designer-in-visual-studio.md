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
ms.openlocfilehash: 1c5d0770115fffd8c81078fd0e3d187ec5d3c5ae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657941"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Visual Studio’da XAML Tasarımcısı’nı kullanarak kullanıcı arabirimi oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'daki XAML Tasarımcısı XAML tabanlı Windows Mağazası, Windows Phone, WPF ve Silverlight uygulamaları tasarlamanıza yardımcı olacak görsel bir arabirim sağlar. **Araç kutusu** ' ndan denetimleri sürükleyip **Özellikler penceresinde özellikleri** ayarlayarak uygulamalarınız için Kullanıcı arabirimleri oluşturabilirsiniz. XAML 'yi doğrudan XAML görünümünde de düzenleyebilirsiniz.

 Animasyonlar ve davranışlar gibi gelişmiş XAML tasarım görevleri için bkz. [Visual Studio için Blend kullanarak Kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>XAML Tasarımcısı çalışma alanı
 XAML Tasarımcısı çalışma alanı çeşitli görsel arabirim öğelerinden oluşur. Bunlar çalışma yüzeyi, XAML Düzenleyicisi, cihaz penceresi, belge anahattı penceresi ve Özellikler penceresi içerir. XAML Tasarımcısı açmak için **Çözüm Gezgini** bir xaml dosyasına sağ tıklayın ve **Görünüm Tasarımcısı**' nı seçin.

## <a name="authoring-views"></a>Yazma görünümleri
 XAML Tasarımcısı, uygulamanızın işlenmiş XAML işaretlemesini bir XAML görünümü ve eşitlenmiş Tasarım görünümü sağlar. Visual Studio 'da bir XAML dosyası açıkken, **Tasarım** ve **xaml** SEKMELERINI kullanarak tasarım görünümü ve XAML görünümü arasında geçiş yapabilirsiniz. En üstte yer alan çalışma yüzeyi ya da XAML Düzenleyicisi olan pencereyi değiştirmek için **bölmeleri Değiştir** düğmesini kullanabilirsiniz.

 Tasarım görünümü, *çalışma yüzeyini* içeren pencere etkin pencere olur ve bunu birincil iş yüzeyi olarak kullanabilirsiniz. Bu uygulamayı, öğeleri ekleyerek veya çizerek ve sonra değiştirerek bir sayfayı görsel olarak tasarlamak için kullanabilirsiniz. Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md). Bu çizimde Tasarım görünümü çalışma yüzeyi gösterilmektedir.

 ![XAML Tasarımcısı Tasarım görünümü](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Çalışma yüzeyinde bu özellikler mevcuttur:

 Anlık görüntü **çizgileri** Anlık görüntü çizgileri, denetimlerin kenarlarının ne zaman hizalandığını göstermek için kırmızı kesikli çizgiler veya metin temelleri hizalı olarak görünen *Hizalama sınırlardır* . Hizalama sınırları yalnızca, **yama çizgilere yaslaması** etkin olduğunda görünür.

 Izgara **rayları** `Grid` raylar [kılavuz](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) panelinde satırları ve sütunları yönetmek için kullanılır. Satır ve sütun oluşturup silebilir ve bunlara göreli genişlikleri ve yükseklikleri ayarlayabilirsiniz. Çalışma yüzeyinin solunda görünen dikey ızgara rampaları, satırlar için kullanılır ve üstte görünen yatay çizgi sütunlar için kullanılır.

 **Izgara donatıcıları** @No__t_1 donatıcı, `Grid` Rampadaki dikey veya yatay bir çizgi eklenmiş bir üçgen olarak görünür. Bir `Grid` donatıcı sürüklediğinizde, fareyi taşırken bitişik sütunların veya satırların genişliği veya yükseklikleri güncellenemez.

 `Grid` Donatıcılar, bir `Grid` satırlarının ve sütunlarının genişlik ve yüksekliğini denetlemek için kullanılır. @No__t_0 raya tıklayarak yeni bir sütun veya satır ekleyebilirsiniz. İki veya daha fazla sütun veya satır içeren bir `Grid` paneli için yeni bir satır veya sütun satırı eklediğinizde, bir mini araç çubuğu, açıkça genişlik ve yükseklik ayarlamanıza olanak tanıyan bir mini araç çubuğudur. Mini araç çubuğu, `Grid` satırları ve sütunları için boyutlandırma seçeneklerini ayarlamanıza olanak sağlar.

 **Yeniden boyutlandırma tutamaçları** Yeniden boyutlandırma tutamaçları seçili denetimlerde görünür ve denetimi yeniden boyutlandırmanızı sağlar. Bir denetimi yeniden boyutlandırdığınızda, genellikle denetimi boyutlandırmanıza yardımcı olmak için Genişlik ve yükseklik değerleri görüntülenir. Tasarım görünümü denetimleri düzenleme hakkında daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md).

 **Kenar boşlukları** Kenar boşlukları, bir denetimin kenarı ve kapsayıcısının kenarı arasındaki sabit boşluk miktarını temsil eder. Özellikler penceresi **Düzen** altındaki [kenar boşluğu](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) özelliklerini kullanarak bir denetimin kenar boşluklarını ayarlayabilirsiniz.

 **Kenar boşluğu donatıcıları** Bir öğenin kenar boşluklarını düzen kapsayıcısına göre değiştirmek için kenar boşluğu donatıcıları kullanabilirsiniz. Bir kenar boşluğu donatıcısı açık olduğunda, bir kenar boşluğu ayarlı değildir ve kenar boşluğu donatıcısı bozuk bir zincir görüntüler. Kenar boşluğu ayarlanmamışsa, düzen kapsayıcısı çalışma zamanında yeniden boyutlandırılırken öğeler yerinde kalır. Bir kenar boşluğu donatıcısı kapalıyken, bir kenar boşluğu donatıcısı bozuk bir zincir görüntüler ve düzen kapsayıcısı çalışma zamanında yeniden boyutlandırıldığından (kenar boşluğu sabit kalır) öğeler kenar boşluğu ile birlikte hareket eder.

 **Öğe tutamaçları** Bir öğeyi çevreleyen mavi kutunun köşelerinden işaretçiyi taşıdığınızda çalışma yüzeyinde görünen öğe tutamaçlarını kullanarak bir öğeyi değiştirebilirsiniz. Bu tutamaçlar, öğe için bir köşe yarıçapı döndürmenizi, yeniden boyutlandırmanızı, çevirmenizi, taşımanızı veya eklemenizi sağlar. Öğe tanıtıcısı sembolü işleve göre değişir ve işaretçinin tam konumuna göre değişir. Öğe tutamaçlarını görmüyorsanız, öğenin seçili olduğundan emin olun.

 Tasarım görünümü, aşağıda gösterildiği gibi, ekranın sol alt bölümünde ek çalışma yüzeyi komutları kullanılabilir:

 ![Tasarım görünümü komutları](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Bu komutlar bu araç çubuğunda kullanılabilir:

 **Yakınlaştır** Yakınlaştırma, tasarım yüzeyini boyutlandırmanızı sağlar. % 12,5 ' dan %800 ' e yakınlaştırabilir veya **seçime uygun** ve **tümüne Sığdır**gibi seçenekleri belirleyebilirsiniz.

 **Yaslama kılavuzunu göster/gizle** Kılavuz çizgilerini gösteren yaslama kılavuzunu görüntüler veya gizler. Kılavuz çizgileri **ya da ek** kılavuz **çizgilere** yaslaması etkinleştirildiğinde kılavuz çizgileri kullanılır.

 **Kılavuz çizgilerine yaslamayı aç/kapat** Çalışma yüzeyinde bir öğeyi sürüklediğinizde **kılavuz çizgilere yaslaması** etkinleştirilirse, öğesi en yakın yatay ve dikey kılavuz çizgilerine göre hizalanacaktır.

 Ek **çizgi çizgilere yaslamayı aç/kapat** Anlık görüntü çizgileri, denetimleri birbirlerine göre hizalamanıza yardımcı olur. Daha fazla denetime **yaslaması** etkinse, bir denetimi diğer denetimlere göre sürüklediğinizde, bazı denetimlerin kenarları ve metni yatay veya dikey olarak hizalandığında hizalama sınırları görüntülenir. Bir hizalama sınırı kırmızı kesikli çizgi olarak görünür.

 XAML görünümünde, XAML düzenleyicisini içeren pencere etkin pencere ve XAML Düzenleyicisi ise birincil yazma aracdır. Extensible Application Markup Language (XAML), bir uygulamanın kullanıcı arabirimini belirtmek için bildirime dayalı XML tabanlı bir sözlük sağlar. XAML görünümü IntelliSense, otomatik biçimlendirme, sözdizimi vurgulama ve etiket gezintisi içerir. Bu çizimde XAML görünümü gösterilmektedir:

 ![XAML görünümü](../designers/media/xaml-editor.png "xaml_editor")

 **Bölünmüş görünüm çubuğu** Bölünmüş görünüm çubuğu, XAML Düzenleyicisi alt pencerede olduğunda XAML görünümünün en üstünde görünür. Bölünmüş görünüm çubuğu, Tasarım görünümü ve XAML görünümünün göreli boyutlarını denetlemenize olanak sağlar. Ayrıca görünümlerin konumlarını da ( **değiştirme bölmeleri** kullanarak) değiş tokuş edebilirsiniz, görünümlerin yatay veya dikey olarak düzenlenmesini belirtebilir ve her iki görünümü de daraltın.

 **Biçimlendirme önizlemesi** Biçimlendirme yakınlaştırma XAML görünümünü boyutlandırmanızı sağlar. %20 ' den %400 ' a yakınlaştırma yapabilirsiniz.

## <a name="device-window"></a>Cihaz penceresi
 XAML Tasarımcısı cihaz penceresi, Windows Mağazası veya Windows Phone projeniz için tasarım zamanında çeşitli görünümlerde, ekranlarda ve görüntüleme seçeneklerinde benzetim yapmanızı sağlar. XAML Tasarımcısı çalışırken, **Tasarım** menüsünde cihaz penceresi kullanılabilir. Şöyle görünür:

 ![Cihaz penceresi](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Bunlar, cihaz penceresinde kullanılabilen seçeneklerdir:

 **Görüntüleme** Uygulama için farklı ekran boyutlarını ve çözümlerini belirtir.

 **Yön** Uygulama için farklı yönleri belirtir: **yatay** veya **Dikey**.

 **Kenar** Uygulamanız için farklı kenar hizalamalarını belirtir: **hem** **sol**, **sağ**, ya da **hiçbiri**.

 **Yüksek karşıtlık** Uygulamanın seçili karşıtlık ayarını temel alarak önizlemesini görüntüleyin. Bu ayar, **varsayılan**dışında bir değer olarak ayarlandığında, App. xaml içinde ayarlanan `RequestedTheme` özelliğini geçersiz kılar.

 **Ölçeklendirmeyi geçersiz kıl** Tasarım yüzeyi içinde belge ölçeklendirmesinin benzetimini açar ve kapatır. Bu, ölçek yüzdesini bir faktörle artırmanıza olanak sağlar. Öykünmeyi açmak için onay kutusunu seçin. Örneğin, ölçekleme yüzdesi %100 ise tasarım yüzeyi içindeki belge, %140 ' e kadar ölçeklendirecektir. Geçerli ölçekleme yüzdesi 180 ise bu seçenek devre dışıdır.

 **En küçük genişlik** En düşük genişlik ayarını belirtir. En düşük genişlik App. xaml içinde değiştirilebilir.

 **Tema** Uygulama temasını belirtir. Örneğin, karanlık bir açık tema arasında geçiş yapabilirsiniz.

 **Chrome göster** Tasarım görünümü içinde uygulamanızın çevresindeki sanal tablet çerçevesini açar ve kapatır. Çerçeveyi göstermek için onay kutusunu seçin.

 **Görüntülenecek klip** Görüntüleme modunu belirtir. Belge boyutunu görüntüleme boyutuna kırpmak için onay kutusunu seçin.

## <a name="document-outline-window"></a>Belge Anahattı penceresi
 XAML Tasarımcısı belge anahattı penceresi, bu görevleri gerçekleştirmenize yardımcı olur:

- Çalışma yüzeyinde tüm öğelerin hiyerarşik yapısını görüntüleyin.

- Öğeleri değiştirmek için öğeleri seçin (hiyerarşide hiyerarşik olarak taşıyın, çalışma yüzeyinde değiştirin, Özellikler penceresi özelliklerini ayarlayın ve bu şekilde devam edin). Daha fazla bilgi için bkz. [XAML Tasarımcısı öğelerle çalışma](../designers/working-with-elements-in-xaml-designer.md)

- Denetimler olan öğeler için şablonlar oluşturun ve değiştirin.

- Seçili öğeler için bağlam menüsünü kullanın. Aynı menü, çalışma yüzeyinde seçilen öğeler için de kullanılabilir.

  Belge Anahattı penceresini görüntülemek için, menü çubuğunda **Görünüm**, **diğer pencereler**, **belge ana hattı**' nı seçin.

  ![Belge Anahattı penceresi](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Bunlar belge anahattı penceresinde kullanılabilen seçeneklerdir:

  **Belge ana hattı** Belge ana hattı penceresindeki ana görünüm bir belge hiyerarşisini ağaç yapısında görüntüler. Belge anahattının hiyerarşik yapısını kullanarak belgeyi farklı ayrıntı düzeylerinde inceleyebilir ve öğeleri listedir veya gruplar halinde kilitlemek ve gizlemek için kullanabilirsiniz.

  **Göster/Gizle** Belge Anahatdaki öğelere karşılık gelen çalışma yüzeyi öğelerini görüntüler veya gizler. Gösterildiğinde bir gözle sembol görüntüleyen **Göster/Gizle** düğmelerini kullanın veya öğeleri GIZLEMEK için CTRL + h tuşlarına ve bunları görüntülemek için SHIFT + CTRL + h tuşlarına basın.

  **Kilit/kilit açma** Belge Anahatdaki öğelere karşılık gelen çalışma yüzeyi öğelerini kilitler veya kilitlerini kaldırır. Kilitli öğeler değiştirilemez. Kilitliyken bir asma kilit simgesi görüntüleyen **kilit/kilit açma** düğmelerini kullanın veya öğeleri KILITLEMEK için CTRL + l tuşlarına basın ve kilitlerini açmak için SHIFT + CTRL + l tuşlarına basın.

  **Kapsam, pageRoot 'e döndürün** Belge ana hattı penceresinin üst kısmındaki, yukarı ok simgesini gösteren seçeneği, belge ana hattını önceki kapsama geri döndürür. Kapsam, yalnızca bir stil veya şablon kapsamındaysa geçerlidir.

## <a name="properties-window"></a>Özellik penceresi
 Özellikler penceresi denetimlerde özellik değerlerini ayarlamanıza olanak sağlar. Şöyle görünür:

 ![Özellikler penceresi](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Özellikler penceresi en üstünde çeşitli seçenekler vardır. **Ad** kutusunu kullanarak şu anda seçili olan öğenin adını değiştirebilirsiniz. Sol üst köşede, şu anda seçili olan öğeyi temsil eden bir simge vardır. Özellikleri kategoriye veya alfabetik olarak düzenlemek için, **Düzenleme ölçütü** listesinde **Kategori**, **ad**veya **kaynak** ' a tıklayın. Bir denetimin olay listesini görmek için, bir şimşek işareti simgesi görüntüleyen **Olaylar** düğmesine tıklayın. Bir özelliği aramak için, **arama özellikleri** kutusuna özelliğin adını yazmak üzere başlatın. Özellikler penceresi, sizin yazarken aramanızla eşleşen özellikleri görüntüler. Bazı özellikler, gelişmiş özellikleri bir aşağı ok düğmesi seçerek ayarlamanıza olanak sağlar. Özellikleri kullanma ve olayları işleme hakkında daha fazla bilgi için bkz [. hızlı başlangıç: denetim ekleme ve olayları işleme](http://go.microsoft.com/fwlink/?LinkID=247983)

 Her özellik değerinin sağında, Box simgesi olarak görünen bir *özellik işaretleyicisi* bulunur. Özellik işaretinin görünümü, bir veri bağlaması veya özelliğe uygulanmış bir kaynak olup olmadığını gösterir. Örneğin, bir beyaz kutu sembolü varsayılan bir değeri gösteriyorsa, bir siyah kutu sembolü genellikle yerel bir kaynağın uygulandığını ve turuncu bir kutu genellikle bir veri bağlamasının uygulandığını gösterir. Özellik işaretine tıkladığınızda, bir stilin tanımına gidebilir, veri bağlama oluşturucuyu açabilir veya kaynak seçiciyi açabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.
 [XAML Tasarımcısı](../designers/working-with-elements-in-xaml-designer.md) [bir kaynak oluşturma ve uygulama](../designers/how-to-create-and-apply-a-resource.md) [izlenecek yol kılavuzu: XAML Tasarımcısı verilere bağlama](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
