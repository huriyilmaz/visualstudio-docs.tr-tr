---
title: Hata ayıklarken XAML özelliklerini İnceleme | Microsoft Docs
ms.date: 03/06/2017
ms.topic: conceptual
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: e1d26886eecf09ff8195b7a38338fa62e7f1d0bf
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974958"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Hata ayıklama sırasında XAML özelliklerini denetleme
**Canlı görsel ağaç** ve **canlı Özellik GEZGINI**ile çalışan xaml kodunuzun gerçek zamanlı bir görünümünü alabilirsiniz. Bu araçlar, çalışan XAML uygulamanızın kullanıcı arabirimi öğelerinin ağaç görünümünü sağlar ve seçtiğiniz herhangi bir kullanıcı arabirimi öğesinin çalışma zamanı özelliklerini gösterir.

Aşağıdaki yapılandırmalarda bu araçları kullanabilirsiniz:

|Uygulama türü|İşletim sistemi ve araçlar|
|-----------------|--------------------------------|
|Windows Presentation Foundation (4,0 ve üzeri) uygulamalar|Windows 7 ve üzeri|
|Evrensel Windows uygulamaları|Windows 10 ve üzeri, Windows 10 [SDK](https://dev.windows.com/en-us/downloads/windows-10-sdk) ile|

## <a name="looking-at-elements-in-the-live-visual-tree"></a>Canlı görsel ağaçtaki öğelere bakma
Bir liste görünümü ve bir düğme içeren çok basit bir WPF uygulamasını kullanmaya başlayalım. Düğmeye her tıkladığınızda, listeye başka bir öğe eklenir. Çift numaralı öğeler gri renklendirilir ve tek sayılı öğeler sarı renktedir.

Yeni C# bir WPF uygulaması (Dosya > Yeni > projesi oluşturun ve ardından WPF C# uygulaması seçin ve bulun). **TestXaml**olarak adlandırın.

MainWindow. xaml ' i şu şekilde değiştirin:

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

MainWindow.xaml.cs dosyasına aşağıdaki komut işleyicisini ekleyin:

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

Projeyi oluşturmak ve hata ayıklamaya başlayın. (Derleme yapılandırması, yayın değil, hata ayıklama olmalıdır. Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).)

Pencere geldiğinde, çalışan uygulamanız içinde uygulama içi araç çubuğunun göründüğünü görmeniz gerekir. 

![Uygulamanın ana penceresi](../debugger/media/livevisualtree-app.png "livevisualtree-App")

Şimdi listeye yeni öğeler eklemek için birkaç kez **öğe Ekle** düğmesine tıklayın.

Ardından, uygulama içi araç çubuğunun çok sol düğmesine tıklayarak (veya **> Windows > Live Visual Tree ' Hata Ayıkla**' ya giderek) **canlı görsel ağaç** penceresini açın. Açık olduktan sonra, bu pencereye ve **canlı Özellikler** penceresine yan yana bakabilmemiz için yerleştirme konumundan uzağa sürükleyin. **Canlı görsel ağaç** penceresinde, **ContentPresenter** düğümünü genişletin. Düğme ve liste kutusu için düğüm içermelidir. Liste kutusu öğelerini bulmak için liste kutusunu (ve ardından **ScrollContentPresenter** ve **ItemsPresenter**) genişletin. Pencere şuna benzemelidir:

![Live Visual Tree](../debugger/media/livevisualtree-listboxitems.png "livevisualtree-ListBoxItems") içindeki ListBoxItems

Uygulama penceresine dönüp birkaç öğe daha ekleyin. **Canlı görsel ağaçta**daha fazla liste kutusu öğesi göründüğünü görmeniz gerekir.

Şimdi liste kutusu öğelerinden birinin özelliklerine göz atalım. **Canlı görsel ağaçtaki** ilk liste kutusu öğesini seçin ve araç çubuğundaki **özellikleri göster** simgesine tıklayın. **Canlı Özellik Gezgini** görünmelidir. **İçerik** alanının "Item1" olduğunu ve **arka plan** > **renk** alanının **#FFFFFFE0**olduğunu unutmayın. **Canlı görsel ağaca** dönün ve ikinci liste kutusu öğesini seçin. **Canlı Özellik Gezgini** , **Içerik** alanının "Item2" olduğunu ve **arka plan** > **renk** alanının **#FFD3D3D3**göstermelidir.

> [!NOTE]
> **Canlı Özellik Gezgini** içindeki bir özelliğin etrafında sarı bir kenarlık, özellik değerinin `Color = {BindingExpression}` gibi bir bağlama üzerinden ayarlandığı anlamına gelir. Yeşil kenarlık, değerin `Color = {StaticResource MyBrush}` gibi bir kaynak kullanılarak ayarlandığı anlamına gelir.

XAML gerçek yapısı, muhtemelen doğrudan ilgilenmediğiniz çok sayıda öğeye sahiptir ve kodun iyi olduğunu bilmiyorsanız, aradığınız şeyi bulmak için ağaçta gezinmek için bir sabit zaman olabilir. Bu nedenle, **canlı görsel ağaç** , incelemek istediğiniz öğeyi bulmanıza yardımcı olmak için uygulamanın kullanıcı arabirimini kullanmanıza olanak sağlayan birkaç yol içerir.

**Çalışan uygulamada seçimi etkinleştirin**. **Canlı görsel ağaç** araç çubuğunda en soldaki düğmeyi seçtiğinizde bu modu etkinleştirebilirsiniz. Bu mod üzerinde, uygulamada bir UI öğesi seçebilirsiniz ve **canlı görsel ağaç** (ve **canlı Özellik Görüntüleyicisi**), düğümü ilgili öğeye ve özelliklerine karşılık gelen ağaçta göstermek için otomatik olarak güncelleştirilir.

**Çalışan uygulamada düzen donatıcıları görüntüleyin**. Seçimi Etkinleştir düğmesinin hemen sağında bulunan düğmeyi seçtiğinizde bu modu etkinleştirebilirsiniz. **Görüntüleme düzeni donatıcıları** açık olduğunda, uygulama penceresinin seçili nesnenin sınırları üzerinde yatay ve dikey çizgiler görüntülemesine neden olur, böylece neyin ne kadar hizalanacağını görebilir ve kenar boşluklarını gösteren dikdörtgenler de gösterilir. Örneğin, her ikisini de **seçimi** ve **görüntüleme yerleşimini** etkinleştirin ve uygulamada **öğe Ekle** metin bloğunu seçin. **Canlı görsel ağaçta** metin bloğu düğümünü ve **canlı Özellik görüntüleyicisinde**metin bloğu özelliklerinin yanı sıra metin bloğunun sınırları üzerindeki yatay ve dikey çizgileri görmeniz gerekir.

DisplayLayout(../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "livevisualtreelivepropertyviewer") !['Da livepropertyviewer]-displaylayout

**Önizleme seçimi**. Canlı görsel ağaç araç çubuğunda sol taraftaki üçüncü düğmeyi seçerek bu modu etkinleştirebilirsiniz. Bu mod, uygulamanın kaynak koduna erişiminiz varsa, öğenin bildirildiği XAML 'yi gösterir. Seçim ve **Önizleme seçimini** **Etkinleştir** ' i seçin ve ardından test uygulamamızda düğmesini seçin. MainWindow. xaml dosyası Visual Studio 'da açılır ve imleç düğmenin tanımlandığı satıra yerleştirilir.

## <a name="using-xaml-tools-with-running-applications"></a>Çalışan uygulamalarla XAML araçlarını kullanma
Kaynak kodunuz olmadığında bile bu XAML araçlarını kullanabilirsiniz. Çalışan bir XAML uygulamasına iliştirmeye çalıştığınızda, bu uygulamanın UI öğelerinde **canlı görsel ağaç** ' ı da kullanabilirsiniz. Daha önce kullandığımız aynı WPF test uygulamasını kullanarak bir örnek aşağıda verilmiştir.

1. Sürüm yapılandırmasında **TestXaml** uygulamasını başlatın. **Hata ayıklama** yapılandırmasında çalışan bir işleme iliştiremezsiniz.

2. Visual Studio 'nun ikinci bir örneğini açın ve **Işleme eklemek > hata ayıkla**' ya tıklayın. Kullanılabilir süreçler listesinde **TestXaml. exe dosyasını** bulun ve **Ekle**' ye tıklayın.

3. Uygulama çalışmaya başlar.

4. Visual Studio 'nun ikinci örneğinde, **Live Visual Tree** (**hata ayıkla > Windows > Live Visual Tree**) öğesini açın. **TestXaml** Kullanıcı arabirimi öğelerini görmeniz gerekir ve uygulamayı doğrudan hata ayıklarken yaptığınız gibi işleyebilmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

[Xaml dinamik yeniden yüklemesine çalışan XAML kodu yazma ve hata ayıklama](xaml-hot-reload.md)
