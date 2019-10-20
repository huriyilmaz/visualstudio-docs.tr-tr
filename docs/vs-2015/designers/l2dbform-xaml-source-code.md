---
title: L2DBForm. xaml kaynak kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc0ec53c35f87751efe78359f582e5f4297143c9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664271"
---
# <a name="l2dbformxaml-source-code"></a>L2DBForm.xaml Kaynak Kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, L2DBForm. xaml [LINQ to XML örneği kullanılarak WPF veri bağlaması](../designers/wpf-data-binding-using-linq-to-xml-example.md)için xaml kaynak dosyasını içerir ve tanımlar.

## <a name="overall-ui-structure"></a>Genel Kullanıcı arabirimi yapısı
 Bir WPF projesi için tipik olduğu gibi, bu dosya, `LinqToXmlDataBinding` ad alanındaki türetilmiş `L2XDBFrom` sınıfla ilişkili bir <xref:System.Windows.Window> XML öğesi olan bir üst öğe içerir.

 İstemci alanı, açık mavi arka plan verilen bir <xref:System.Windows.Controls.StackPanel> içinde bulunur. Bu panel, <xref:System.Windows.Controls.Separator> çubuklarıyla ayrılan dört <xref:System.Windows.Controls.DockPanel> UI bölümü içerir. Bu bölümlerin amacı, [önceki konudaki](../designers/walkthrough-linqtoxmldatabinding-example.md) **açıklamalar** bölümünde açıklanmıştır.

 Her bölüm, onu tanımlayan bir etiket içerir. İlk iki bölümde, bu etiket bir <xref:System.Windows.FrameworkElement.LayoutTransform%2A> kullanılarak 90 derece döndürülür. Bölümünün geri kalanı, bu bölümün amacına uygun Kullanıcı arabirimi öğeleri içerir: metin blokları, metin kutuları, düğmeler ve benzeri. Bazen bu alt denetimleri hizalamak için bir alt <xref:System.Windows.Controls.StackPanel> kullanılır.

## <a name="window-resource-section"></a>Pencere kaynağı bölümü
 9\. satırdaki açma `<Window.Resources>` etiketi, pencere kaynağı bölümünün başlangıcını gösterir. 35 satırındaki kapanış etiketiyle biter.

 11 ile 25 arası çizgileri kapsayan `<ObjectDataProvider>` etiketi, kaynak olarak <xref:System.Xml.Linq.XElement> kullanan `LoadedBooks` adlı bir <xref:System.Windows.Data.ObjectDataProvider> bildirir. Bu <xref:System.Xml.Linq.XElement>, gömülü bir XML belgesi (bir `CDATA` öğesi) ayrıştırıldığında başlatılır. Gömülü XML belgesi bildirirken ve aynı zamanda ayrıştırıldığında boşluk ' ın korunduğuna dikkat edin. Bu, Ham XML 'yi göstermek için kullanılan <xref:System.Windows.Controls.TextBlock> denetimi özel XML biçimlendirme özelliklerine sahip olmadığı için gerçekleştirildi.

 Son olarak, `BookTemplate` adlı bir <xref:System.Windows.DataTemplate> 28 ile 34 arası satırlarda tanımlanmıştır. Bu şablon, girdileri **kitap listesi** UI bölümünde göstermek için kullanılacaktır. Aşağıdaki atamalar aracılığıyla kitap KIMLIĞI ve defter adını almak için veri bağlamayı ve dinamik özellikleri LINQ to XML kullanır:

```
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>Veri bağlama kodu
 @No__t_0 öğesine ek olarak, veri bağlama bu dosyadaki birçok farklı yerde kullanılır.

 38 satırındaki açma `<StackPanel>` etiketinde, bu panelin <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği `LoadedBooks` veri sağlayıcısına ayarlanır.

```
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

 Bu, `tbRawXml` adlı <xref:System.Windows.Controls.TextBlock>, bu veri sağlayıcısının `Xml` özelliğine bağlayarak ham XML 'yi görüntülemesi mümkün hale getirir (satır 46):

```
Text="{Binding Path=Xml}"
```

 **Kitap listesi** Kullanıcı arabirimi bölümündeki <xref:System.Windows.Controls.ListBox>, 58 ile 62 arası satırlarda, görüntüleme öğelerinin şablonunu pencere kaynağı bölümünde tanımlanan `BookTemplate` olarak ayarlar:

```
ItemTemplate ="{StaticResource BookTemplate}"
```

 Ardından, 59 ile 62 arasındaki satırlarda, kitapların gerçek değerleri bu liste kutusuna bağlıdır:

```
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

 Üçüncü Kullanıcı arabirimi bölümü, **Seçili kitabı Düzenle**, önce üst <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.FrameworkElement.DataContext%2A>, **kitap listesi** Kullanıcı arabirimi bölümünden içindeki seçili olan öğeye bağlar (satır 82):

```
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

 Daha sonra iki yönlü veri bağlamayı kullanır, böylece kitap öğelerinin geçerli değerleri bu paneldeki iki metin kutusundan görüntülenir ve güncelleştirilir. Dinamik özelliklere veri bağlama, `BookTemplate` veri şablonunda kullanılanlara benzerdir:

```
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

 Son Kullanıcı arabirimi bölümü, **Yeni kitap ekle**, XAML kodunda veri bağlamayı kullanmaz; Bunun yerine, bu kod L2DBForm.xaml.cs dosyasında olay işleme kodunda bulunabilir.

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

> [!NOTE]
> Satır numaralarının izlenmesi daha kolay olması için aşağıdaki kodu, Visual Studio 'daki C# kaynak kodu Düzenleyicisi gibi bir kod düzenleyicisine kopyalamanız önerilir.

### <a name="code"></a>Kod

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>

```

### <a name="comments"></a>Açıklamalar
 WPF UI C# öğeleriyle ilişkili olay işleyicilerinin kaynak kodu için bkz. [L2DBForm.xaml.cs kaynak kodu](../designers/l2dbform-xaml-cs-source-code.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: LinqToXmlDataBinding örneği](../designers/walkthrough-linqtoxmldatabinding-example.md) [L2DBForm.xaml.cs kaynak kodu](../designers/l2dbform-xaml-cs-source-code.md)
