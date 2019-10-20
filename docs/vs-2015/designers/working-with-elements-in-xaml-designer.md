---
title: XAML Tasarımcısı öğelerle çalışma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 483023fbd28da26d9967dd2d88bc37748d00f088
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663981"
---
# <a name="working-with-elements-in-xaml-designer"></a>XAML Tasarımcısı'nda öğelerle çalışma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanıza XAML 'de, kod içinde veya XAML Tasarımcısı kullanarak öğe (denetimler, düzenler ve şekiller) ekleyebilirsiniz. Bu konu başlığı altında, Visual Studio veya Visual Studio için Blend XAML Tasarımcısı öğeleri ile nasıl çalışılacağı açıklanmaktadır.

## <a name="adding-an-element-to-a-layout"></a>Bir düzene öğe ekleme
 *Düzen* , BIR kullanıcı arabirimindeki öğeleri boyutlandırma ve konumlandırma işlemidir. Görsel öğeleri konumlandırmak için bunları bir düzen [paneline](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.panel.aspx)koymanız gerekir. @No__t_0, [FrameworkElement](https://msdn.microsoft.com/library/windows/apps/br208706.aspx) türlerinin bir koleksiyonu olan bir child özelliğine sahiptir. Düzen kapsayıcıları olarak görev yapmak ve öğeleri bir sayfada konumlandırmak ve düzenlemek için [tuval](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.canvas.aspx), [StackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.aspx)ve [kılavuz](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx)gibi çeşitli `Panel` alt öğeleri kullanabilirsiniz.

 Varsayılan olarak, bir sayfa veya form içinde en üst düzey düzen kapsayıcısı olarak bir `Grid` paneli kullanılır. Üst düzey sayfa düzeni içinde düzen bölmeleri, denetimler veya diğer öğeleri ekleyebilirsiniz.

#### <a name="to-add-an-element-to-a-layout"></a>Bir düzene öğe eklemek için

- XAML Tasarımcısı, aşağıdakilerden birini yapın:

  - **Araç kutusunda** bir öğeye çift tıklayın (veya araç kutusunda bir öğe seçin ve ENTER tuşuna basın).

  - **Araç kutusundan** bir öğeyi çalışma yüzeyine sürükleyin.

  - **Araç kutusunda**, çizim araçlarından birini seçin (örneğin, [elips](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.ellipse.aspx) veya [dikdörtgen](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.shapes.rectangle.aspx)) ve ardından etkin panelde bir öğe çizin.

## <a name="changing-the-layering-order-of-elements"></a>Öğelerin katmanlama sırasını değiştirme
 XAML Tasarımcısı çalışma yüzeyinde iki öğe olduğunda, katman sırasında diğeri önünde bir öğe görünür. Belge ana hattı penceresindeki öğelerin listesinin en altında, en öndeki öğedir (bir öğe için **ZIndex** özelliğinin ayarlandığı durumlar dışında). Bir sayfa, form veya Düzen kapsayıcısına bir öğe eklediğinizde, öğe, etkin kapsayıcı öğesindeki diğer öğelerin önüne otomatik olarak yerleştirilir. Öğelerin sırasını değiştirmek için, **Düzen** komutlarını kullanabilir veya öğeleri belge ana hattı penceresinde nesne ağacında sürükleyebilirsiniz.

#### <a name="to-change-the-layering-order"></a>Katman sırasını değiştirmek için

- Aşağıdakilerden birini yapın:

  - **Belge Anahattı** penceresinde, istenen katman sırasını oluşturmak için öğeleri yukarı veya aşağı sürükleyin.

  - Belge Anahattı penceresinde veya katman sırasını değiştirmek istediğiniz çalışma yüzeyinde öğesine sağ tıklayın, **sırasıyla Order**' a gelin ve sonra aşağıdakilerden birine tıklayın:

    - Öğeyi sıranın önüne getirmek için **önüne getirin** .

    - Öğeyi sırayla bir düzey öne çıkarmak için **Ileri getirin** .

    - Öğeyi sırayla bir düzey geri göndermek için **geri gönderin** .

    - Öğeyi sıranın sonuna kadar bir şekilde göndermek için **geri gönderin** .

    Özellikler penceresi **Düzen** bölümündeki **ZIndex** özelliğini değiştirin. Örtüşen öğeler için, **ZIndex** özelliği, belge ana hattı penceresinde gösterilen öğelerin sırasına göre önceliklidir. Alt **zindex** değeri olan bir öğe, öğeler çakıştığında önünde görünür.

## <a name="changing-the-alignment-of-an-element"></a>Bir öğenin hizalamasını değiştirme
 Çalışma yüzeyindeki öğeleri menü komutlarını kullanarak veya öğeleri yama çizgilere sürükleyerek hizalayabilirsiniz.

 Bir anlık görüntü *satırı* , bir öğeyi uygulamadaki diğer öğelere göre hizalamanıza yardımcı olan bir görsel ipucudur.

#### <a name="to-align-two-or-more-elements-by-using-menu-commands"></a>Menü komutlarını kullanarak iki veya daha fazla öğeyi hizalamak için

1. Hizalamak istediğiniz öğeleri seçin. Öğeleri seçerken CTRL tuşuna basarak ve basılı tutarak birden fazla öğe seçebilirsiniz.

2. Özellikler penceresi **Düzen** bölümünde **HorizontalAlignment** altında aşağıdaki özelliklerden birini seçin: **sol**, **Orta**, **sağ**veya **Esnetme**.

3. Özellikler penceresi **Düzen** bölümünde **VerticalAlignment** altında aşağıdaki özelliklerden birini seçin: **top**, **Center**, **Bottom**veya **Esnetme**.

#### <a name="to-align-two-or-more-elements-by-using-snaplines"></a>İki veya daha fazla öğeyi Snapın çizgilerini kullanarak hizalamak için

- XAML Tasarımcısı, en az iki öğe içeren bir düzende, kenar başka bir öğeyle hizalı olacak şekilde öğelerinden birini sürükleyin veya yeniden boyutlandırın.

     Kenarlar hizalandığında, hizalamayı göstermek için bir *Hizalama sınırı* belirir. Hizalama sınırı kırmızı kesikli bir çizgi. Hizalama sınırları yalnızca, **yama çizgilere yaslaması** etkin olduğunda görünür. Bir hizalama sınırını gösteren çalışma yüzeyi çizimi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="changing-the-an-elements-margins"></a>Öğenin kenar boşluklarını değiştirme
 XAML Tasarımcısı kenar boşlukları, çalışma yüzeyinde bir öğe etrafında bulunan boş alan miktarını tespit ediyor. Örneğin, kenar boşlukları, bir öğenin dış kenarları arasındaki boşluk miktarını ve öğeyi içeren `Grid` panelinin sınırlarını belirtir. Kenar boşlukları Ayrıca, `StackPanel` içinde bulunan öğeler arasındaki boşluk miktarını da belirtir.

#### <a name="to-change-an-elements-margins-in-the-properties-window"></a>Özellikler penceresi bir öğenin kenar boşluklarını değiştirmek için

1. Kenar boşluklarını değiştirmek istediğiniz öğeyi seçin.

2. Özellikler penceresi **Düzen** altında, **kenar boşluğu** özelliklerinden herhangi biri (**üst**, **sol**, **sağ**veya **alt**) için değeri (piksel veya yaklaşık 1/96 inç olan cihazdan bağımsız birimler) değiştirin.

#### <a name="to-change-an-elements-margins-in-the-artboard"></a>Çalışma yüzeyinde bir öğenin kenar boşluklarını değiştirmek için

- Bir öğenin düzen kapsayıcısına göre kenar boşluklarını değiştirmek için, öğe seçildiğinde ve bir düzen kapsayıcısı içinde olduğunda, çalışma yüzeyinde öğe etrafında görünen *kenar boşluğu donatıcıları* ' na tıklayın. Kenar boşluğu donatıcıları gösteren bir çizim için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     Bir kenar boşluğu donatıcısı, dikey veya yatay olarak açıksa, bu kenar boşluğu ayarlı değildir. Bir kenar boşluğu donatıcısı kapalıysa, bu kenar boşluğu ayarlanır.

     Bir kenar boşluğu donatıcısını açtığınızda ve ters kenar boşluğu ayarlanmamışsa, ters kenar boşluğu, çalışma yüzeyinde öğenin konumuna göre doğru değere ayarlanır. **Sol** ve **sağ** kenar boşlukları gibi zıt kenar boşlukları için en az bir özellik her zaman ayarlanır.

    > [!IMPORTANT]
    > @No__t_0 gibi bazı Düzen kapsayıcıları içine yerleştirilmiş öğelerin kenar boşluğu donatıcıları yoktur. @No__t_0 içine yerleştirilmiş öğelerin, `StackPanel` yönüne bağlı olarak sol ve sağ kenar boşlukları veya üst ve alt kenar boşlukları için kenar boşluğu donatıcıları vardır.

## <a name="grouping-and-ungrouping-elements"></a>Öğeleri gruplandırma ve gruplarını çözme
 XAML Tasarımcısı iki veya daha fazla öğeyi gruplandırmak yeni bir düzen kapsayıcısı oluşturur ve bu öğeleri bu kapsayıcıya koyar. İki veya daha fazla öğeyi bir düzen kapsayıcısına yerleştirmek, bu gruptaki öğeler bir öğe gibi, grubu kolayca seçmenizi, taşımanızı ve dönüştürmenizi sağlar. Gruplama, bir gezinti öğesini oluşturan düğmeler gibi her bir şekilde birbirleriyle ilgili öğeleri tanımlamak için de yararlıdır. Öğelerin grubunu kaldırdığınızda, öğeleri içeren düzen kapsayıcısını silmeniz yeterlidir.

#### <a name="to-group-elements-into-a-new-layout-container"></a>Öğeleri yeni bir düzen kapsayıcısına gruplandırmak için

1. Gruplandırmak istediğiniz öğeleri seçin. (Birden çok öğe seçmek için, tıkladığınızda CTRL tuşunu basılı tutun.)

2. Seçilen öğelere sağ tıklayın, **grupla**' nın üzerine gelin ve ardından grubun bulunmasını istediğiniz düzen kapsayıcısı türüne tıklayın.

    > [!TIP]
    > Öğelerinizi gruplamak için <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> veya <xref:Windows.UI.Xaml.Controls.ScrollViewer> ' yı seçerseniz, öğeler <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> veya <xref:Windows.UI.Xaml.Controls.ScrollViewer> içinde yeni bir <xref:Windows.UI.Xaml.Controls.Grid> paneline yerleştirilir. Bu düzen kapsayıcılarından birindeki öğelerin grubunu çözerseniz, yalnızca <xref:Windows.UI.Xaml.Controls.Viewbox>, <xref:Windows.UI.Xaml.Controls.Border> veya <xref:Windows.UI.Xaml.Controls.ScrollViewer> silinir ve <xref:Windows.UI.Xaml.Controls.Grid> paneli kalır. @No__t_0 panelini silmek için öğelerin grubunu yeniden çözün.

#### <a name="to-ungroup-elements-and-delete-the-layout"></a>Öğelerin grubunu çözme ve düzeni silme

- Grubunu çözmek istediğiniz gruba sağ tıklayın ve grubu **Çöz**' e tıklayın.

  Ayrıca, belge ana hat penceresinde seçili öğelere sağ tıklayıp grupla veya grubu **Çöz**' **e** tıklayarak öğeleri gruplandırabilir veya gruplarını kaldırabilirsiniz.

## <a name="resetting-the-element-layout"></a>Öğe düzeni sıfırlanıyor
 Düzen sıfırlama komutlarını kullanarak bir öğenin belirli düzen özellikleri için varsayılan değerleri geri yükleyebilirsiniz. Bu komutu kullanarak bir öğenin kenar boşluğunu, hizalamasını, genişliğini, yüksekliğini ve boyutunu tek tek veya topluca sıfırlayabilirsiniz.

#### <a name="to-reset-the-element-layout"></a>Öğe yerleşimini sıfırlamak için

- Belge Anahattı penceresinde veya çalışma yüzeyinde öğesine sağ tıklayın, **Düzen**' i, *PropertyName*'i **Sıfırla** ' yı seçin, burada *PropertyName* sıfırlamak istediğiniz özelliktir (veya **Düzen**' i seçin, **Tümünü Sıfırla** öğe için tüm düzen özelliklerini sıfırlayın).

## <a name="see-also"></a>Ayrıca Bkz.
 [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
