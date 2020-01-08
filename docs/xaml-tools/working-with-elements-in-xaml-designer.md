---
title: XAML Tasarımcısı'nda öğelerle çalışma
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 3f544501a7d8a792af9ddd89c682324a21002c4f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592926"
---
# <a name="work-with-elements-in-xaml-designer"></a>XAML Tasarımcısı’nda öğelerle çalışma

Uygulamanıza XAML 'de, kod içinde veya XAML Tasarımcısı kullanarak öğe (denetimler, düzenler ve şekiller) ekleyebilirsiniz. Bu konu başlığı altında, Visual Studio veya Visual Studio için Blend XAML Tasarımcısı öğeleri ile nasıl çalışılacağı açıklanmaktadır.

## <a name="add-an-element-to-a-layout"></a>Düzene öğe ekleme

*Düzen* , BIR kullanıcı arabirimindeki öğeleri boyutlandırma ve konumlandırma işlemidir. Görsel öğeleri konumlandırmak için bunları bir düzen [paneline](xref:Windows.UI.Xaml.Controls.Panel)koymanız gerekir. Bir `Panel` [FrameworkElement](xref:Windows.UI.Xaml.FrameworkElement) türleri koleksiyonu olan bir alt özelliği vardır. Düzen kapsayıcıları olarak görev yapmak ve öğeleri bir sayfada konumlandırmak ve düzenlemek için [tuval](xref:Windows.UI.Xaml.Controls.Canvas), [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel)ve [kılavuz](xref:Windows.UI.Xaml.Controls.Grid)gibi çeşitli `Panel` alt öğeleri kullanabilirsiniz.

Varsayılan olarak, bir `Grid` paneli sayfa veya form içinde en üst düzey düzen kapsayıcısı olarak kullanılır. Üst düzey sayfa düzeni içinde düzen bölmeleri, denetimler veya diğer öğeleri ekleyebilirsiniz.

XAML Tasarımcısı bir düzene öğe eklemek için aşağıdakilerden birini yapın:

- **Araç kutusunda** bir öğeye çift tıklayın (veya araç kutusunda bir öğe seçin ve **ENTER**tuşuna basın).

- **Araç kutusundan** bir öğeyi çalışma yüzeyine sürükleyin.

- **Araç kutusunda**, çizim araçlarından birini seçin (örneğin, [elips](xref:Windows.UI.Xaml.Shapes.Ellipse) veya [dikdörtgen](xref:Windows.UI.Xaml.Shapes.Rectangle)) ve ardından etkin panelde bir öğe çizin.

## <a name="change-the-layering-order-of-elements"></a>Öğelerin katmanlama sırasını değiştirme

XAML Tasarımcısı çalışma yüzeyinde iki öğe olduğunda, katman sırasında diğeri önünde bir öğe görünür. Öğe listesinin en altında, belge ana hattı penceresi en öndeki öğedir (bir öğe için **ZIndex** özelliğinin ayarlandığı durumlar dışında). Bir sayfa, form veya Düzen kapsayıcısına bir öğe eklediğinizde, öğe, etkin kapsayıcı öğesindeki diğer öğelerin önüne otomatik olarak yerleştirilir. Öğelerin sırasını değiştirmek için, **Düzen** komutlarını kullanabilir veya öğeleri belge ana hattı penceresinde nesne ağacında sürükleyebilirsiniz.

Katman sırasını değiştirmek için aşağıdakilerden birini yapın:

- **Belge Anahattı** penceresinde, istenen katman sırasını oluşturmak için öğeleri yukarı veya aşağı sürükleyin.

- Belge Anahattı penceresinde veya katman sırasını değiştirmek istediğiniz çalışma yüzeyinde öğesine sağ tıklayın, **sırasıyla Order**' a gelin ve sonra aşağıdakilerden birine tıklayın:

  - Öğeyi sıranın önüne getirmek için **önüne getirin** .

  - Öğeyi sırayla bir düzey öne çıkarmak için **Ileri getirin** .

  - Öğeyi sırayla bir düzey geri göndermek için **geri gönderin** .

  - Öğeyi sıranın sonuna kadar bir şekilde göndermek için **geri gönderin** .

- Özellikler penceresi **Düzen** bölümündeki **ZIndex** özelliğini değiştirin. Örtüşen öğeler için, **ZIndex** özelliği, belge ana hattı penceresinde gösterilen öğelerin sırasına göre önceliklidir. Daha yüksek bir **ZIndex** değeri olan bir öğe, öğeler çakıştığında önünde görünür.

## <a name="change-the-alignment-of-an-element"></a>Bir öğenin hizalamasını değiştirme

Çalışma yüzeyindeki öğeleri menü komutlarını kullanarak veya öğeleri yama çizgilere sürükleyerek hizalayabilirsiniz.

Bir anlık görüntü *satırı* , bir öğeyi uygulamadaki diğer öğelere göre hizalamanıza yardımcı olan bir görsel ipucudur.

Menü komutlarını kullanarak iki veya daha fazla öğeyi hizalamak için:

1. Hizalamak istediğiniz öğeleri seçin. Öğeleri seçerken **CTRL** tuşuna basarak ve basılı tutarak birden fazla öğe seçebilirsiniz.

2. Özellikler penceresi **Düzen** bölümünde **HorizontalAlignment** altında aşağıdaki özelliklerden birini seçin: **sol**, **Orta**, **sağ**veya **Esnetme**.

3. Özellikler penceresi **Düzen** bölümünde **VerticalAlignment** altında aşağıdaki özelliklerden birini seçin: **top**, **Center**, **Bottom**veya **Esnetme**.

İki veya daha fazla öğeyi, XAML Tasarımcısı ' de, en az iki öğe içeren bir düzende hizalamak için, kenar başka bir öğeyle hizalanmak üzere öğelerden birini sürükleyin veya yeniden boyutlandırın.

Kenarlar hizalandığında, hizalamayı göstermek için bir *Hizalama sınırı* belirir. Hizalama sınırı kırmızı kesikli bir çizgi. Hizalama sınırları yalnızca görünür **dayama çizgilerine yaslamayı** etkinleştirilir. Bir hizalama sınırını gösteren çalışma yüzeyi çizimi için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

## <a name="change-an-elements-margins"></a>Öğenin kenar boşluklarını değiştirme

XAML Tasarımcısı kenar boşlukları, çalışma yüzeyinde bir öğe etrafında bulunan boş alan miktarını tespit ediyor. Örneğin, kenar boşlukları, bir öğenin dış kenarları arasındaki boşluk miktarını ve öğeyi içeren bir `Grid` panelinin sınırlarını belirtir. Kenar boşlukları Ayrıca bir `StackPanel`bulunan öğeler arasındaki boşluk miktarını da belirler.

Özellikler penceresi bir öğenin kenar boşluklarını değiştirmek için:

1. Kenar boşluklarını değiştirmek istediğiniz öğeyi seçin.

2. Özellikler penceresi **Düzen** altında, **kenar boşluğu** özelliklerinden herhangi biri (**üst**, **sol**, **sağ**veya **alt**) için değeri (piksel veya yaklaşık 1/96 inç olan cihazdan bağımsız birimler) değiştirin.

Çalışma yüzeyinde öğenin düzen kapsayıcısına göre bir öğenin kenar boşluklarını değiştirmek için, öğe seçildiğinde ve bir düzen kapsayıcısı içinde olduğunda, öğenin etrafında görüntülenen *kenar boşluğu donatıcıları* ' na tıklayın. Kenar boşluğu donatıcıları gösteren bir çizim için, bkz. [XAML Tasarımcısı kullanarak Kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

Bir kenar boşluğu donatıcısı, dikey veya yatay olarak açıksa, bu kenar boşluğu ayarlı değildir. Bir kenar boşluğu donatıcısı kapalıysa, bu kenar boşluğu ayarlanır.

Bir kenar boşluğu donatıcısını açtığınızda ve ters kenar boşluğu ayarlanmamışsa, ters kenar boşluğu, çalışma yüzeyinde öğenin konumuna göre doğru değere ayarlanır. **Sol** ve **sağ** kenar boşlukları gibi zıt kenar boşlukları için en az bir özellik her zaman ayarlanır.

> [!IMPORTANT]
> [Tuval](xref:Windows.UI.Xaml.Controls.Canvas)gibi bazı düzen kapsayıcılarının içine yerleştirilmiş olan öğelerin kenar boşluğu donatıcıları yoktur. Bir [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) içine yerleştirilmiş öğelerin, `StackPanel`yönüne bağlı olarak sol ve sağ kenar boşlukları ya da üst ve alt kenar boşlukları için kenar boşluğu donatıcıları vardır.

## <a name="group-and-ungroup-elements"></a>Öğeleri gruplandırma ve grubunu çözme

XAML Tasarımcısı iki veya daha fazla öğeyi gruplandırmak yeni bir düzen kapsayıcısı oluşturur ve bu öğeleri bu kapsayıcıya koyar. İki veya daha fazla öğeyi bir düzen kapsayıcısına yerleştirmek, bu gruptaki öğeler bir öğe gibi, grubu kolayca seçmenizi, taşımanızı ve dönüştürmenizi sağlar. Gruplama, bir gezinti öğesini oluşturan düğmeler gibi her bir şekilde birbirleriyle ilgili öğeleri tanımlamak için de yararlıdır. Öğelerin grubunu kaldırdığınızda, öğeleri içeren düzen kapsayıcısını silmeniz yeterlidir.

Öğeleri yeni bir düzen kapsayıcısına gruplandırmak için:

1. Gruplandırmak istediğiniz öğeleri seçin. (Birden çok öğe seçmek için, tıkladığınızda **CTRL** tuşunu basılı tutun.)

2. Seçilen öğelere sağ tıklayın, **grupla**' nın üzerine gelin ve ardından grubun bulunmasını istediğiniz düzen kapsayıcısı türüne tıklayın.

    > [!TIP]
    > Öğelerinizi gruplamak için [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border)veya [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) ' ı seçerseniz, öğeler [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border)veya [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer)içindeki yeni bir [ızgara](xref:Windows.UI.Xaml.Controls.Grid) paneline yerleştirilir. Bu düzen kapsayıcılarından birindeki öğelerin grubunu çözerseniz, yalnızca [Viewbox](xref:Windows.UI.Xaml.Controls.Viewbox), [Border](xref:Windows.UI.Xaml.Controls.Border)veya [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) silinir ve [kılavuz](xref:Windows.UI.Xaml.Controls.Grid) paneli kalır. `Grid` panelini silmek için öğelerin grubunu yeniden çözün.

Öğelerin grubunu çözmek ve düzeni silmek için, grubunu çözmek istediğiniz gruba sağ tıklayın ve grubu **Çöz**' e tıklayın. Ayrıca, belge ana hat penceresinde seçili öğelere sağ tıklayıp grupla veya grubu **Çöz**' **e** tıklayarak öğeleri gruplandırabilir veya gruplarını kaldırabilirsiniz.

## <a name="reset-the-element-layout"></a>Öğe yerleşimini sıfırlayın

Düzen sıfırlama komutlarını kullanarak bir öğenin belirli düzen özellikleri için varsayılan değerleri geri yükleyebilirsiniz. Bu komutu kullanarak bir öğenin kenar boşluğunu, hizalamasını, genişliğini, yüksekliğini ve boyutunu tek tek veya topluca sıfırlayabilirsiniz.

Öğe yerleşimini sıfırlamak için belge anahattı penceresinde veya çalışma yüzeyinde öğesine sağ tıklayın ve ardından **PropertyName 'i sıfırla > seçin** . burada *PropertyName* **, sıfırlamak istediğiniz** özelliktir (veya öğenin tüm düzen özelliklerini sıfırlamak için **Düzen** seçin > **Tümünü Sıfırla** *' yı*seçin).

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
