---
title: Hata ayıklama sırasında XAML özelliklerini | Microsoft Docs
description: XAML özelliklerini incelemek ve ui öğelerinin ağaç görünümünü elde etmek için hata ayıklarken Canlı Görsel Ağaç ve Canlı Özellik Gezgini araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/26/2021
ms.topic: how-to
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- uwp
ms.openlocfilehash: 4ff5d56a29642d67a59f06b73270336af73219a3
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127708"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Hata ayıklama sırasında XAML özelliklerini denetleme

Canlı Görsel Ağaç ve Canlı Özellik Gezgini ile çalışan XAML kodunuzun **gerçek** zamanlı bir **görünümünü eldeebilirsiniz.** Bu araçlar, çalışan XAML uygulamanıza kullanıcı arabirimi öğelerinin ağaç görünümünü sağlar ve seçerek herhangi bir kullanıcı arabirimi öğesinin çalışma zamanı özelliklerini gösterir.

Bu araçları aşağıdaki yapılandırmalarda kullanabilirsiniz:

|Uygulama Türü|İşletim Sistemi ve Araçlar|
|-----------------|--------------------------------|
|Windows Presentation Foundation (4.0 ve sonrası) uygulamaları|Windows 7 ve sonrası|
|Evrensel Windows uygulamaları|Windows 10 SDK ve sonraki ile [Windows 10 ve](https://dev.windows.com/downloads/windows-10-sdk) sonrası|

## <a name="look-at-elements-in-the-live-visual-tree"></a>Canlı Görsel AğaçtaKi Öğelere Bakma

Liste görünümü ve düğmesi olan çok basit bir WPF uygulamasıyla çalışmaya bakalım. Düğmeye her tıklarken listeye başka bir öğe eklenir. Çift numaralı öğeler gri renkte, tek numaralı öğeler ise sarı renktedir.

### <a name="create-the-project"></a>Proje oluşturma

::: moniker range=">=vs-2019"

1. Yeni bir C# WPF uygulaması **oluşturun** ( Dosya >  > **Yeni Project,**"C# WPF" yazın, **WPF** Uygulaması proje şablonunu seçin, **projeyi TestXAML**  olarak adlar ve ardından Hedef Çerçeve açılır listesinde **.NET Core 3.1'in** görüntülendiğinden emin olun.

::: moniker-end

::: moniker range="vs-2017"

1. Yeni bir C# WPF uygulaması **oluşturun**( Dosya  >    >  **Yeni Project**, ardından "C# WPF" yazın ve WPF Uygulaması **(.NET Framework) ) seçin.** **TestXAML olarak ad girin.**

::: moniker-end

1. MainWindow.xaml'i aşağıdakiyle değiştirebilirsiniz:

   ```xaml
   <Window x:Class="TestXAML.MainWindow"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:local="clr-namespace:TestXAML"
      mc:Ignorable="d"
      Title="MainWindow" Height="350" Width="525">
      <Grid>
         <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>
         <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>
      </Grid>
   </Window>
   ```

1. MainWindow.xaml.cs dosyasına aşağıdaki komut işleyicisini ekleyin:

   ```csharp
   int count;

   private void button_Click(object sender, RoutedEventArgs e)
   {
      ListBoxItem item = new ListBoxItem();
      item.Content = "Item" + ++count;
      if (count % 2 == 0)
      {
         item.Background = Brushes.LightGray;
      }
      else
      {
         item.Background = Brushes.LightYellow;
      }
      listBox.Items.Add(item);
   }
   ```

1. Projeyi derleme ve hata ayıklamayı başlatma. (Derleme yapılandırması Yayın değil Hata Ayıklaması'dır. Derleme yapılandırmaları hakkında daha fazla bilgi için [bkz. Derleme Yapılandırmalarını Anlama](../ide/understanding-build-configurations.md).)

   Pencere açılırken, çalışan uygulamanın içinde uygulama içindeki araç çubuğunun görünmesi gerekir.

   ::: moniker range=">= vs-2019"
   ![Uygulamanın ana penceresi](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Uygulamanın ana penceresi](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end

1. Şimdi, listeye **yeni öğeler** eklemek için Öğe Ekle düğmesine birkaç kez tıklayın.

### <a name="inspect-xaml-properties"></a>XAML özelliklerini inceleme

1. Ardından, uygulama **içinde araç çubuğunun** sol üst düğmesine tıklayarak (veya Canlı Görsel Ağaç'ta hata ayıkla'ya > Windows > tıklayarak) Canlı Görsel **Ağaç penceresini açın.** Açıldıktan sonra, bu pencereye ve Canlı Özellikler penceresine yan yana bakmak için yerleştirme **konumundan** sürükleyin.

1. Canlı **Görsel Ağaç penceresinde** **ContentPresenter düğümünü** genişletin. Düğme ve liste kutusu için düğümler içermesi gerekir. Liste kutusu öğelerini bulmak için liste kutusunu (ve **ardından ScrollContentPresenter** ve **ItemsPresenter**) genişletin.

   ::: moniker range=">= vs-2019"
   **ContentPresenter** düğümünü görmüyorsanız araç çubuğundaki **Yalnızca Benim XAML'imi Göster** simgesini açıp seçin. 2019 Visual Studio 16.4 sürümünden başlayarak, Yalnızca Benim XAML'im özelliği kullanılarak XAML öğelerinin görünümü varsayılan olarak basitleştirilir. Tüm XAML [öğelerini her zaman](../debugger/general-debugging-options-dialog-box.md) göstermek için seçeneklerde de bu ayarı devre dışı abilirsiniz.
   ::: moniker-end

   Pencere şu şekilde görünür:

   ::: moniker range=">= vs-2019"
   ![Canlı Görsel Ağacında ListBoxItems](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Canlı Görsel Ağacında ListBoxItems](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end

1. Geri dön penceresine tıklayın ve birkaç öğe daha ekleyin. Canlı Görsel Ağaç'ta daha fazla liste kutusu **öğelerinin görünmesi gerekir.**

1. Şimdi liste kutusu öğelerine göz atabilirsiniz.

   Canlı Görsel Ağaç'ta ilk liste **kutusu öğesini seçin** ve araç çubuğunda Özellikleri **Göster** simgesine tıklayın. Canlı **Özellik Gezgini görünmektedir.** İçerik alanı **"Item1"** ve Arka Plan Rengi **alanı** da  >  **#FFFFFFE0.** 

1. Geri dön Görsel **Ağaç'a tıklayın** ve ikinci liste kutusu öğesini seçin. Canlı **Özellik Gezgini,** İçerik  alanı "Item2" ve Arka Plan Rengi alanı da #FFD3D3D3 (temaya bağlı  >   olarak)  göster gerekir.

   > [!NOTE]
   > Live **Property Explorer'daki** bir özelliğin çevresindeki sarı kenarlık, özellik değerinin gibi bir bağlama aracılığıyla ayarlanacak olduğu anlamına `Color = {BindingExpression}` gelir. Yeşil kenarlık, değerin gibi bir kaynak kullanılarak ayar anlamına `Color = {StaticResource MyBrush}` gelir.

   XAML'nin gerçek yapısı büyük olasılıkla doğrudan ilgilenmeyilen birçok öğeye sahiptir ve kodu iyi bilmiyorsanız arayabilirsiniz. Bu **nedenle Canlı Görsel** Ağaç, incelemek istediğiniz öğeyi bulanıza yardımcı olmak için uygulamanın kullanıcı arabirimini kullanmanın birkaç yolu vardır.

   ::: moniker range=">= vs-2019"
   **Çalışan uygulamada öğesini seçin.** Canlı Görsel Ağaç araç çubuğunda en soldaki düğmeyi seçerek **bu modu etkinleştirebilirsiniz.** Bu mod açılırken, uygulamada bir kullanıcı arabirimi öğesi seçebilirsiniz ve **Canlı** Görsel Ağaç (ve Canlı Özellik Görüntüleyicisi) otomatik olarak bu öğeye karşılık gelen düğümdeki düğümü ve özelliklerini gösterecek şekilde günceller. 2019 Visual Studio 16.4 sürümünden başlayarak öğe [seçiminin davranışını yapılandırabilirsiniz.](../debugger/general-debugging-options-dialog-box.md)

   **Çalışan uygulamada düzen donatıcılarını görüntüleme.** Seçimi etkinleştir düğmesinin hemen sağ tarafından düğmeyi seçerek bu modu etkinleştirebilirsiniz. Görüntü **düzeni donatıcıları** açık olduğunda, kenar boşluklarını gösteren dikdörtgenlerin yanı sıra hangi hizaya sahip olduğunu görmek için uygulama penceresinin seçili nesnenin sınırları boyunca yatay ve dikey çizgileri göstermesi gerekir. Örneğin, Hem Öğe **seçin hem** de **Düzeni görüntüle'yi** açarak uygulamanın **Öğe** Ekle metin bloğuna tıklayın. Canlı Görsel Ağaç'ta metin  bloğu düğümünü ve **Canlı** Özellik Görüntüleyicisi'nde metin bloğu özelliklerini ve metin bloğu sınırları üzerinde yatay ve dikey çizgileri görüyor gerekir.

   ![DisplayLayout'ta LivePropertyViewer](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Önizleme Seçimi**. Canlı Görsel Ağaç araç çubuğunun sol tarafından üçüncü düğmeyi seçerek bu modu etkinleştirebilirsiniz. Bu mod, uygulamanın kaynak koduna erişiminiz varsa öğenin bildiril olduğu XAML'i gösterir. Öğe **seçin ve** Önizleme **seçimi'ne** tıklayın ve ardından test uygulamamızda düğmesini seçin. MainWindow.xaml dosyası Visual Studio açılır ve imleç düğmenin tanımlandığı satıra yerleştirilir.
   ::: moniker-end

   ::: moniker range="vs-2017"
   **Çalışan uygulamada seçimi etkinleştirin.** Canlı Görsel Ağaç araç çubuğunda en soldaki düğmeyi seçerek **bu modu etkinleştirebilirsiniz.** Bu mod açılırken, uygulamada bir kullanıcı arabirimi öğesi seçebilirsiniz ve **Canlı** Görsel Ağaç (ve Canlı Özellik Görüntüleyicisi) otomatik olarak bu öğeye karşılık gelen düğümdeki düğümü ve özelliklerini gösterecek şekilde günceller.

   **Çalışan uygulamada düzen donatıcılarını görüntüleme.** Seçimi etkinleştir düğmesinin hemen sağ tarafından düğmeyi seçerek bu modu etkinleştirebilirsiniz. Görüntü **düzeni donatıcıları** açık olduğunda, kenar boşluklarını gösteren dikdörtgenlerin yanı sıra hangi hizaya sahip olduğunu görmek için uygulama penceresinin seçili nesnenin sınırları boyunca yatay ve dikey çizgileri göstermesi gerekir. Örneğin, Hem Seçimi etkinleştir **hem de** **Düzeni görüntüle'yi** etkinleştirin ve **uygulamada Öğe** Ekle metin bloğu seçin. Canlı Görsel Ağaç'ta metin  bloğu düğümünü ve **Canlı** Özellik Görüntüleyicisi'nde metin bloğu özelliklerini ve metin bloğu sınırları üzerinde yatay ve dikey çizgileri görüyor gerekir.

   ![DisplayLayout'ta LivePropertyViewer](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Önizleme Seçimi**. Canlı Görsel Ağaç araç çubuğunun sol tarafından üçüncü düğmeyi seçerek bu modu etkinleştirebilirsiniz. Bu mod, uygulamanın kaynak koduna erişiminiz varsa öğenin bildiril olduğu XAML'i gösterir. Seçimi **etkinleştir ve** Önizleme seçimini **seçin** ve ardından test uygulamamızda düğmesini seçin. MainWindow.xaml dosyası Visual Studio açılır ve imleç düğmenin tanımlandığı satıra yerleştirilir.
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>Uygulama çalıştırma ile XAML araçlarını kullanma

Kaynak koduna sahip değilken bile bu XAML araçlarını kullanabilirsiniz. Çalışan bir XAML uygulamasına iliştirerek, o uygulamanın kullanıcı arabirimi **öğelerinde** Canlı Görsel Ağaç'ı da kullanabilirsiniz. Burada daha önce kullanılan WPF test uygulamasını kullanan bir örnek ve ardından bir örnek ve ardından.

1. Yayın **yapılandırmasında TestXaml** uygulamasını başlatma. Hata ayıklama yapılandırmasında çalışan bir işleme ek **olamaz.**

2. dosyanın ikinci bir örneğini açın Visual Studio İşleme **Ekle'> Hata Ayıkla'ya tıklayın.** Kullanılabilir **TestXaml.exe** listesinde bir liste bulun ve Ekle'ye **tıklayın.**

3. Uygulama çalışmaya başlar.

4. uygulamanın ikinci örneğinde Visual Studio Ağacını açın ( Canlı **Görsel** **Ağaç> Windows > hata ayıkla**). **TestXaml** kullanıcı arabirimi öğelerini görüyor ve uygulamanın doğrudan hata ayıklamasını yaparken olduğu gibi bunları yönetebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

[XAML Çalışırken Yeniden Yükleme ile XAML kodu çalıştırmayı ve hata ayıklamayı XAML Çalışırken Yeniden Yükleme](xaml-hot-reload.md)
