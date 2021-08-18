---
title: XAML Tasarımcısı'nda öğelerle çalışma
description: Visual Studio veya Visual Studio için Blend'da XAML Tasarımcısı çalışma hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/14/2018
ms.topic: conceptual
ms.assetid: a29690bf-f212-4ac6-a77a-adc53d14102e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 9db24c368bdbf3f7503b650f5ba588b603b0b2a4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037778"
---
# <a name="work-with-elements-in-xaml-designer"></a>XAML Tasarımcısı’nda öğelerle çalışma

XAML'de, kodda veya kodda uygulamanıza öğeler (denetimler, düzenler ve şekiller) ekleyebilir veya XAML Tasarımcısı. Bu konu başlığında, bir veya daha fazla XAML Tasarımcısı öğeleriyle Visual Studio Visual Studio için Blend.

## <a name="add-an-element-to-a-layout"></a>Bir düzene öğe ekleme

*Düzen,* kullanıcı arabiriminde öğeleri boyutlandırma ve konumlandırma işlemidir. Görsel öğeleri konumlandırmak için bunları bir düzen Paneline [koyabilirsiniz.](xref:Windows.UI.Xaml.Controls.Panel) , `Panel` FrameworkElement türlerinin koleksiyonu olan bir alt [özelliğine](xref:Windows.UI.Xaml.FrameworkElement) sahiptir. Düzen kapsayıcıları olarak hizmet vermek ve öğeleri bir sayfada konumlandırmak ve düzenlemek için `Panel` [Tuval,](xref:Windows.UI.Xaml.Controls.Canvas) [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel)ve [Kılavuz](xref:Windows.UI.Xaml.Controls.Grid)gibi çeşitli alt öğeleri kullanabilirsiniz.

Varsayılan olarak, `Grid` bir sayfa veya formda üst düzey düzen kapsayıcısı olarak bir panel kullanılır. Üst düzey sayfa düzeninde düzen panelleri, denetimler veya diğer öğeler ekleyebilirsiniz.

XAML Tasarımcısı düzenine öğe eklemek için, XAML Tasarımcısı birini yapın:

- Araç Kutusunda bir öğeye **çift tıklayın (veya** Araç Kutusundan bir öğe seçin ve Enter tuşuna **basın).**

- Araç Kutusundan bir **öğeyi çalışma** panosuna sürükleyin.

- Araç **Kutusunda çizim** araçlarından birini (örneğin, [Üç](xref:Windows.UI.Xaml.Shapes.Ellipse) Nokta veya [Dikdörtgen)](xref:Windows.UI.Xaml.Shapes.Rectangle)seçin ve ardından etkin panelde bir öğe çizin.

## <a name="change-the-layering-order-of-elements"></a>Öğelerin katmanlama sıralamalarını değiştirme

Çalışma panosunda iki öğe XAML Tasarımcısı öğelerden biri katmanlama sırasına göre diğerinin önünde görünür. Öğe listesinin en altında, Belge Ana Hat penceresinde en öndeki öğedir (bir öğenin **ZIndex** özelliğinin ne zaman ayarlansa hariç). Bir sayfa, form veya düzen kapsayıcısı içine bir öğe eklerken, öğe otomatik olarak etkin kapsayıcı öğesinde diğer öğelerin önüne yerleştirilir. Öğelerin sıralamalarını değiştirmek için Order  komutlarını kullanabilir veya Belge Ana Hat penceresindeki nesne ağacında öğeleri sürükleyebilirsiniz.

Katmanlama sırası değiştirmek için, aşağıdakilerden birini yapın:

- İstenen **katmanlama sırası** oluşturmak için Belge Ana Hat penceresinde öğeleri yukarı veya aşağı sürükleyin.

- Belge Ana Hat penceresindeki öğeye veya katmanlama sırası değiştirmek istediğiniz çalışma panosuna sağ tıklayın, Sırası'nın üzerine **gelin** ve ardından aşağıdakilerden birini tıklatın:

  - **Öğeyi sıranın** önüne getirmek için Öne Getir.

  - **Öğeyi sırayla** bir düzey ileri getirmek için Öne Getir.

  - **Öğeyi sırayla** bir düzey geri göndermek için Geriye Gönder.

  - **Öğeyi siparişin** en gerisinde göndermek için Geri'ye gönder.

- Özellikler penceresi'daki **Düzen bölümündeki** **ZIndex** özelliğini Özellikler penceresi. Çakışan öğeler için **ZIndex** özelliği, Belge Ana Hat penceresinde gösterilen öğelerin sırasına göre önceliklidir. Öğeler çakışıyorken önünde **daha yüksek ZIndex** değerine sahip bir öğe görünür.

## <a name="change-the-alignment-of-an-element"></a>Bir öğenin hizalamasını değiştirme

Menü komutlarını kullanarak veya öğeleri yaslık çizgilere sürükleyerek çalışma panosunda öğeleri hizaabilirsiniz.

Ek *bileşen,* bir öğeyi uygulamanın diğer öğelerine göre hizalamanıza yardımcı olan görsel bir ipucudur.

Menü komutlarını kullanarak iki veya daha fazla öğe hizalamak için:

1. Hizalamak istediğiniz öğeleri seçin. Öğeleri seçerken **Ctrl** tuşuna basarak ve basılı tutarak birden fazla öğe seçin.

2. Aşağıdaki özelliklerden birini seçin: Sol,  Orta , Sağ veya Özellikler penceresi Düzen bölümünde **HorizontalAlignment.** 

3. Sayfanın Düzen bölümünde **VerticalAlignment** altında  aşağıdaki özelliklerden birini **seçin:** **Özellikler penceresi,** Orta, **Alt** veya **Esndir.**

İki veya daha fazla öğeyi yas çizgileri kullanarak hizalamak için XAML Tasarımcısı'da en az iki öğe içeren bir düzende, kenar başka bir öğeyle hizalanmış olacak şekilde öğelerden birini sürükleyip yeniden boyutlandırın.

Kenarlar hizalanmış olduğunda, *hizalamayı göstermek için bir* hizalama sınırı görünür. Hizalama sınırı kırmızı bir kesikli çizgidir. Hizalama sınırları yalnızca **yaslama çizgilerini yaslama etkinleştirildiğinde** görünür. Hizalama sınırını gösteren çalışma panosu çizimi için bkz. XAML Tasarımcısı kullanarak [kullanıcı arabirimi oluşturma.](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)

## <a name="change-an-elements-margins"></a>Bir öğenin kenar boşluklarını değiştirme

Çalışma XAML Tasarımcısı kenar boşlukları, çalışma panosunda bir öğenin çevresindeki boş alan miktarını belirler. Örneğin kenar boşlukları, bir öğenin dış kenarları ile öğesini içeren panelin sınırları arasındaki  `Grid` boşluk miktarını belirtir. Kenar boşlukları, bir içinde yer alan öğeler arasındaki boşluk miktarını da `StackPanel` belirtir.

Bir öğenin kenar boşluklarını Özellikler penceresi:

1. Kenar boşluklarını değiştirmek istediğiniz öğeyi seçin.

2. Özellikler penceresi  düzeni altında, Kenar Boşluğu özelliklerinin herhangi biri (Üst, Sol, Sağ veya Alt) için değeri (piksel veyacihazdan bağımsız birimlerde yaklaşık 1/96 inç) **değiştirin.**  

Çalışma panosunda, öğenin düzen kapsayıcısı ile ilgili olarak bir öğenin  kenar boşluklarını değiştirmek için öğe seçildiğinde ve bir düzen kapsayıcısı içinde olduğunda öğenin etrafında görünen kenar boşluğu donatıcılara tıklayın. Kenar boşluğu donatıcılarını gösteren bir çizim için [bkz.](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)XAML Tasarımcısı.

Kenar boşluğu donatıcısı açık, dikey veya yatay olarak açıksa bu kenar boşluğu ayarlanmaz. Bir kenar boşluğu donatıcı kapalı ise bu kenar boşluğu ayarlanır.

Bir kenar boşluğu donatıcısı açıp karşı kenar boşluğu ayarlanmasa da, kenar boşluğu, çalışma panosunda öğenin konumuna göre doğru değere ayarlanır. Sol ve Sağ kenar boşlukları gibi **karşıt** **kenar boşlukları** için her zaman en az bir özellik ayarlanır.

> [!IMPORTANT]
> Tuval gibi bazı düzen kapsayıcılarına yerleştirilen [öğelerin](xref:Windows.UI.Xaml.Controls.Canvas)kenar boşluğu donatıcısı yoktur. [StackPanel](xref:Windows.UI.Xaml.Controls.StackPanel) içine yerleştirilen öğeler, yönüne bağlı olarak sol ve sağ kenar boşlukları ya da üst ve alt kenar boşlukları için kenar boşluğu donatıcılarına `StackPanel` sahiptir.

## <a name="group-and-ungroup-elements"></a>Öğeleri grupla ve grupla

İki veya daha fazla öğenin XAML Tasarımcısı yeni bir düzen kapsayıcısı oluşturur ve bu öğeleri bu kapsayıcıya yer ettirin. İki veya daha fazla öğeyi bir düzen kapsayıcısı içine yerleştirmek, grubu kolayca bir öğe gibi seçmenize, taşımaya ve dönüştürmeye olanak sağlar. Gruplama, bir gezinti öğesinin düğmeleri gibi bir şekilde ilişkili öğeleri tanımlamak için de yararlıdır. Öğelerin grubunu kaldırsanız, öğeleri içeren düzen kapsayıcısı silinir.

Öğeleri yeni bir düzen kapsayıcısı içinde grup haline etmek için:

1. Grup eklemek istediğiniz öğeleri seçin. (Birden çok öğe seçmek için, tıklarken **Ctrl** tuşuna basın ve basılı tutun.)

2. Seçili öğelere sağ tıklayın, Grupla'nın **üzerine** gelin ve ardından grubun içinde yer almak istediğiniz düzen kapsayıcısı türüne tıklayın.

    > [!TIP]
    > Öğelerinizi [gruplandırarak](xref:Windows.UI.Xaml.Controls.Viewbox)Görünüm Kutusu, Kenarlık veya [ScrollViewer'ı](xref:Windows.UI.Xaml.Controls.ScrollViewer) seçersiniz, öğeler Görünüm [](xref:Windows.UI.Xaml.Controls.Border) [kutusu,](xref:Windows.UI.Xaml.Controls.Viewbox)Kenarlık veya ScrollViewer içindeki yeni bir Kılavuz [paneline yerleştirilir.](xref:Windows.UI.Xaml.Controls.ScrollViewer) [](xref:Windows.UI.Xaml.Controls.Border) [](xref:Windows.UI.Xaml.Controls.Grid) Bu düzen kapsayıcılarından birinin öğelerinin grubunu kaldırırsanız yalnızca [Görünüm kutusu,](xref:Windows.UI.Xaml.Controls.Viewbox) [Kenarlık](xref:Windows.UI.Xaml.Controls.Border)veya [ScrollViewer](xref:Windows.UI.Xaml.Controls.ScrollViewer) silinir ve [Kılavuz](xref:Windows.UI.Xaml.Controls.Grid) paneli kalır. Paneli silmek `Grid` için öğelerin grubunu yeniden çözebilirsiniz.

Öğelerin grubunu çözmek ve düzeni silmek için, grubunu çözmek istediğiniz gruba sağ tıklayın ve Grubunu **Çöz'e tıklayın.** Ayrıca, Belge Ana Hat penceresinde seçili öğelere sağ tıklar ve Grupla veya Grubunu Çöz'e tıklayarak **öğeleri gruplandırabilirsiniz** veya **gruplandırabilirsiniz.**

## <a name="reset-the-element-layout"></a>Öğe düzenini sıfırlama

Düzen Sıfırlama komutlarını kullanarak bir öğenin belirli düzen özellikleri için varsayılan değerleri geri yükleyebilirsiniz. Bu komutu kullanarak bir öğenin kenar boşluğu, hizalama, genişlik, yükseklik ve boyutunu tek tek veya toplu olarak sıfırlayabilirsiniz.

Öğe düzenini sıfırlamak için, Belge Ana Hat penceresinde veya çalışma panosunda öğeye sağ tıklayın ve ardından Düzen Sıfırlama  >   *ÖzelliğiAdı'yı* seçin; burada *PropertyName,* sıfırlamak istediğiniz özelliktir (veya öğenin tüm düzen özelliklerini sıfırlamak için Düzen Sıfırla'yı   >   seçin).

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
