---
title: Hata ayıklarken XAML özelliklerini İnceleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 52d978472f057359cb2b1e0375f2d7ba524d1925
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423857"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Hata ayıklama sırasında XAML özelliklerini denetleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Canlı görsel ağaç** ve **canlı Özellik GEZGINI**ile çalışan xaml kodunuzun gerçek zamanlı bir görünümünü alabilirsiniz. Bu araçlar, çalışan XAML uygulamanızın kullanıcı arabirimi öğelerinin ağaç görünümünü sağlar ve seçtiğiniz herhangi bir kullanıcı arabirimi öğesinin çalışma zamanı özelliklerini gösterir.  
  
 Aşağıdaki yapılandırmalarda bu araçları kullanabilirsiniz:  
  
|Uygulama türü|İşletim sistemi ve araçlar|  
|-----------------|--------------------------------|  
|Windows Presentation Foundation (4,0 ve üzeri) uygulamalar|Windows 7 ve üzeri|  
|Windows Mağazası ve Windows Phone 8,1 uygulamaları|Windows 10 ve üzeri, Windows 10 [SDK](https://dev.windows.com/downloads/windows-10-sdk) ile|  
|Evrensel Windows uygulamaları|Windows 10 ve üzeri, Windows 10 [SDK](https://dev.windows.com/downloads/windows-10-sdk) ile|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Canlı görsel ağaçtaki öğelere bakma  
 Bir liste görünümü ve bir düğme içeren çok basit bir WPF uygulamasını kullanmaya başlayalım. Düğmeye her tıkladığınızda, listeye başka bir öğe eklenir. Çift numaralı öğeler gri renklendirilir ve tek sayılı öğeler sarı renktedir.  
  
 Yeni bir C# WPF uygulaması (dosya/yeni/proje) oluşturun, ardından C# ' ı seçin ve WPF uygulaması bulun. **TestXaml**olarak adlandırın.  
  
 MainWindow. xaml ' i şu şekilde değiştirin:  
  
```xaml  
<Window x:Class="WpfApplication1.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:WpfApplication1"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 MainWindow.xaml.cs dosyasına aşağıdaki komut işleyicisini ekleyin:  
  
```csharp  
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
  
 Projeyi derleyin ve hata ayıklamayı başlatın. (Derleme yapılandırması, yayın değil, hata ayıklama olmalıdır. Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).)  
  
 Pencere geldiğinde, birkaç kez **öğe Ekle** düğmesine tıklayın. Şuna benzer bir şey görmeniz gerekir:  
  
 ![Uygulamanın ana penceresi](../debugger/media/livevisualtree-app.png "LiveVIsualTree-uygulama")  
  
 Şimdi **canlı görsel ağaç** penceresini açın (**Hata Ayıkla/Windows/canlı görsel ağaç**veya IDE 'nin sol tarafında bulun). Bu pencereye ve **canlı Özellikler** penceresine yan yana bakabilmemiz için yerleştirme konumundan uzağa sürükleyin. **Canlı görsel ağaç** penceresinde, **ContentPresenter** düğümünü genişletin. Düğme ve liste kutusu için düğüm içermelidir. Liste kutusu öğelerini bulmak için liste kutusunu (ve ardından **ScrollContentPresenter** ve **ItemsPresenter**) genişletin. Pencere şuna benzemelidir:  
  
 ![Canlı görsel ağaçtaki ListBoxItems](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")  
  
 Uygulama penceresine dönüp birkaç öğe daha ekleyin. **Canlı görsel ağaçta**daha fazla liste kutusu öğesi göründüğünü görmeniz gerekir.  
  
 Şimdi liste kutusu öğelerinden birinin özelliklerine göz atalım. **Canlı görsel ağaçtaki** ilk liste kutusu öğesini seçin ve araç çubuğundaki **özellikleri göster** simgesine tıklayın. **Canlı Özellik Gezgini** görünmelidir. **İçerik** alanının "Item1" olduğunu ve **arka plan** alanının **#FFFFFFE0** (açık sarı) olduğunu unutmayın. **Canlı görsel ağaca** dönün ve ikinci liste kutusu öğesini seçin. **Canlı Özellik Gezgini** , **Içerik** alanının "Item2" olduğunu ve **arka plan** alanının **#FFD3D3D3** (açık gri) olduğunu göstermelidir.  
  
 XAML gerçek yapısı, muhtemelen doğrudan ilgilenmediğiniz çok sayıda öğeye sahiptir ve kodun iyi olduğunu bilmiyorsanız, aradığınız şeyi bulmak için ağaçta gezinmek için bir sabit zaman olabilir. Bu nedenle, **canlı görsel ağaç** , incelemek istediğiniz öğeyi bulmanıza yardımcı olmak için uygulamanın kullanıcı arabirimini kullanmanıza olanak sağlayan birkaç yol içerir.  
  
 **Çalışan uygulamada seçimi etkinleştirin**. **Canlı görsel ağaç** araç çubuğunda en soldaki düğmeyi seçtiğinizde bu modu etkinleştirebilirsiniz. Bu mod üzerinde, uygulamada bir UI öğesi seçebilirsiniz ve **canlı görsel ağaç** (ve **canlı Özellik Görüntüleyicisi**), düğümü ilgili öğeye ve özelliklerine karşılık gelen ağaçta göstermek için otomatik olarak güncelleştirilir.  
  
 **Çalışan uygulamada düzen donatıcıları görüntüleyin**. Seçimi Etkinleştir düğmesinin hemen sağında bulunan düğmeyi seçtiğinizde bu modu etkinleştirebilirsiniz. **Görüntüleme düzeni donatıcıları** açık olduğunda, uygulama penceresinin seçili nesnenin sınırları üzerinde yatay ve dikey çizgiler görüntülemesine neden olur, böylece neyin ne kadar hizalanacağını görebilir ve kenar boşluklarını gösteren dikdörtgenler de gösterilir. Örneğin, her ikisini de **seçimi** ve **görüntüleme yerleşimini** etkinleştirin ve uygulamada **öğe Ekle** metin bloğunu seçin. **Canlı görsel ağaçta** metin bloğu düğümünü ve **canlı Özellik görüntüleyicisinde**metin bloğu özelliklerinin yanı sıra metin bloğunun sınırları üzerindeki yatay ve dikey çizgileri görmeniz gerekir.  
  
 ![DisplayLayout içinde LivePropertyViewer](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")  
  
 **Önizleme seçimi**. Canlı görsel ağaç araç çubuğunda sol taraftaki üçüncü düğmeyi seçerek bu modu etkinleştirebilirsiniz. Bu mod, uygulamanın kaynak koduna erişiminiz varsa, öğenin bildirildiği XAML 'yi gösterir. Seçim ve **Önizleme seçimini** **Etkinleştir** ' i seçin ve ardından test uygulamamızda düğmesini seçin. MainWindow. xaml dosyası Visual Studio 'da açılır ve imleç düğmenin tanımlandığı satıra yerleştirilir.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Çalışan uygulamalarla XAML araçlarını kullanma  
 Kaynak kodunuz olmadığında bile bu XAML araçlarını kullanabilirsiniz. Çalışan bir XAML uygulamasına iliştirmeye çalıştığınızda, bu uygulamanın UI öğelerinde **canlı görsel ağaç** ' ı da kullanabilirsiniz. Daha önce kullandığımız aynı WPF test uygulamasını kullanarak bir örnek aşağıda verilmiştir.  
  
1. Sürüm yapılandırmasında **TestXaml** uygulamasını başlatın. **Hata ayıklama** yapılandırmasında çalışan bir işleme iliştiremezsiniz.  
  
2. Visual Studio 'nun ikinci bir örneğini açın ve **işlemek Için hata ayıkla/İliştir ' e**tıklayın. Kullanılabilir süreçler listesinde **TestXaml.exe** bulun ve **Ekle**' ye tıklayın.  
  
3. Uygulama çalışmaya başlar.  
  
4. Visual Studio 'nun ikinci örneğinde, **canlı görsel ağacını** (**hata ayıklama/Windows/canlı görsel ağaç**) açın. **TestXaml** Kullanıcı arabirimi öğelerini görmeniz gerekir ve uygulamayı doğrudan hata ayıklarken yaptığınız gibi işleyebilmelisiniz.
