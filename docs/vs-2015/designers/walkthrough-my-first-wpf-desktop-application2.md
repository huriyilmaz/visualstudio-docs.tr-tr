---
title: 'İzlenecek yol: Ilk WPF Masaüstü Application2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e800fe651d32435351b2338b4da2f9c55158b3a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664000"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>İzlenecek yol: Ilk WPF Masaüstü Uygulamam
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Name = "giriş" ></a> Bu izlenecek yol, Windows Presentation Foundation (WPF) geliştirmeye bir giriş sağlar. Çoğu WPF Masaüstü uygulaması için ortak olan öğeleri içeren temel bir uygulama oluşturacaksınız: XAML işaretleme, arka plan kod, uygulama tanımları, denetimler, düzen, veri bağlama ve stiller.

## <a name="creating-the-application-project"></a><a name="Create_The_Application_Code_Files"></a> Uygulama projesi oluşturma
 Bu bölümde, projeyi ve ana pencereyi veya formu içeren uygulama altyapısını oluşturacaksınız.

#### <a name="to-create-the-project"></a>Proje oluşturmak için

1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

2. **Yeni proje** iletişim kutusunda, **Visual C#** veya **Visual Basic** düğümünü genişletin ve **Windows** düğümünü seçin ve ardından **Windows** düğümünü genişletin ve **Klasik Masaüstü** düğümünü seçin.

3. Şablon listesinde **WPF uygulama** şablonunu seçin.

4. **Ad** metin kutusuna girin `ExpenseIt` ve **Tamam** düğmesini seçin.

     Proje oluşturulur ve proje dosyaları **Çözüm Gezgini**eklenir ve **MainWindow. xaml** adlı varsayılan uygulama penceresi için tasarımcı görüntülenir.

#### <a name="to-modify-the-main-window"></a>Ana pencereyi değiştirmek için

1. Tasarımcıda zaten etkin Tasarımcı sekmesi yoksa **MainWindow. xaml** sekmesini seçin.

2. C# kullanıyorsanız, satırı bulun `<Window x:Class="ExpenseIt.MainWindow"` ve ile değiştirin `<NavigationWindow x:Class="ExpenseIt.MainWindow"` .

     Visual Basic kullanıyorsanız, satırı bulun `<Window x:Class=" MainWindow"` ve ile değiştirin `<NavigationWindow x:Class="MainWindow"` .

     Etiketini olarak değiştirdiğinizde `<Window` `<NavigationWindow` , IntelliSense otomatik olarak kapanış etiketini de olarak değiştirir `</NavigationWindow>` .

    > [!NOTE]
    > Etiketi değiştirdikten sonra, **hata listesi** penceresi açıksa birkaç hata fark edebilirsiniz. Endişelenmeyin, sonraki birkaç adımda yaptığınız değişiklikler bu şekilde kaybolur.

3. `<Grid>`Ve etiketlerini seçin `</Grid>` ve silin.

     **NavigationWindow** , **kılavuz**gibi diğer kullanıcı arabirimi öğelerini içeremez.

4. **Özellikler** penceresinde **ortak** kategori düğümünü genişletin ve **title** özelliğini seçin ve ENTER `ExpenseIt` tuşuna basın. **Enter**

     XAML penceresindeki **title** öğesinin yeni değerle eşleşecek şekilde değişdiğine dikkat edin. Xaml özelliklerini XAML penceresinde ya da **Özellikler** penceresinde değiştirebilirsiniz ve değişiklikler eşitlenir.

5. XAML penceresinde, **Height** öğesinin değerini olarak ayarlayın `375` ve **Width** özelliğinin değerini olarak ayarlayın `500` .

     Bu öğeler, **Özellikler** penceresindeki **Düzen** kategorisinde bulunan **Yükseklik** ve **Genişlik** özelliklerine karşılık gelir.

     **MainWindow. xaml** dosyanız artık C# dilinde şöyle görünmelidir:

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">

    </NavigationWindow>
    ```

     Bunun gibi Visual Basic:

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500">

    </NavigationWindow>
    ```

#### <a name="to-modify-the-code-behind-file-c"></a>Arka plan kod dosyasını değiştirmek için (C#)

1. **Çözüm Gezgini**, **MainWindow. xaml** düğümünü genişletin ve **MainWindow.xaml.cs** dosyasını açın.

2. Satırı bulun `public partial class MainWindow : Window` ve ile değiştirin `public partial class MainWindow : NavigationWindow` .

     Bu, `MainWindow` öğesinden türetmek için sınıfını değiştirir `NavigationWindow` . Visual Basic, XAML 'de pencereyi değiştirdiğinizde bu otomatik olarak gerçekleşir, bu nedenle kod değişikliği gerekli değildir.

## <a name="adding-files-to-the-application"></a><a name="add_files_to_the_application"></a> Uygulamaya dosya ekleme
 Bu bölümde, uygulamaya iki sayfa ve bir görüntü ekleyeceksiniz.

#### <a name="to-add-a-home-screen"></a>Bir giriş ekranı eklemek için

1. **Çözüm Gezgini**, **ExpenseIt** düğümünün kısayol menüsünü açın ve **Ekle**, **sayfa**' yı seçin.

2. **Yeni öğe Ekle** Iletişim kutusunda **ad** metin kutusunu seçin ve girin `ExpenseItHome` ve sonra **Ekle** düğmesini seçin.

     Bu sayfa, uygulama başlatıldığında görüntülenen ilk penceredir.

3. Tasarımcıda zaten etkin Tasarımcı sekmesi yoksa **ExpenseItHome. xaml** sekmesini seçin.

4. Öğesini seçin `<Title>` ve başlığı **ExpenseIt – Home**olarak değiştirin.

     **ExpenseItHome. xaml** dosyanız artık C# dilinde şöyle görünmelidir:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">

        <Grid>

        </Grid>
    </Page>
    ```

     Bunun gibi Visual Basic:

    ```xaml
    <Page x:Class="ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid>

        </Grid>
    </Page>
    ```

5. Tasarımcıda **MainWindow. xaml** sekmesini seçin.

6. Çizgi öğesini bulun `Title="ExpenseIt" Height="375" Width="500">` ve bir özellik ekleyin `Source="ExpenseItHome.xaml"` .

     Bu, uygulama başlatıldığında **ExpenseItHome. xaml** ' i açılan ilk sayfa olacak şekilde ayarlar. **MainWindow. xaml** dosyanız artık C# dilinde şöyle görünmelidir:

    ```xaml
    <NavigationWindow x:Class="ExpenseIt.MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">

    </NavigationWindow>
    ```

     Bunun gibi Visual Basic:

    ```xaml
    <NavigationWindow x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
            xmlns:local="clr-namespace:ExpenseIt"
            mc:Ignorable="d"
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">

    </NavigationWindow>
    ```

     Daha önce ayarladığınız özelliklerde olduğu gibi, `Source` özelliği **Özellikler** penceresinin **çeşitli** kategorisinde ayarlamış olabilirsiniz.

#### <a name="to-add-a-details-window"></a>Ayrıntılar penceresi eklemek için

1. **Çözüm Gezgini**, **ExpenseIt** düğümünün kısayol menüsünü açın ve **Ekle**, **sayfa**' yı seçin.

2. **Yeni öğe Ekle** Iletişim kutusunda **ad** metin kutusunu seçin ve girin `ExpenseReportPage` ve sonra **Ekle** düğmesini seçin.

     Bu pencerede tek bir gider raporu görüntülenir.

3. Tasarımcıda, zaten etkin Tasarımcı sekmesi değilse **ExpenseReportPage. xaml** sekmesini seçin.

4. Öğeyi seçin `<Title>` ve başlığı ExpenseIt ile değiştirin. **gideri görüntüleyin**.

     ExpenseReportPage. xaml dosyanız artık C# dilinde şöyle görünmelidir:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">

        <Grid>

        </Grid>
    </Page>
    ```

     Bunun gibi Visual Basic:

    ```xaml
    <Page x:Class="ExpenseReportPage"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - View Expense">
        <Grid>

        </Grid>
    </Page>
    ```

5. Uygulamayı çalıştırmak için menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat** (veya F5 tuşuna basın) öğesini seçin.

     Aşağıdaki çizim, uygulamayı gezinti penceresi düğmeleriyle gösterir.

     ![ExpenseIt örnek ekran görüntüsü](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")

6. Tasarım moduna geri dönmek için uygulamayı kapatın.

## <a name="creating-the-user-interface"></a><a name="Add_Layout"></a> Kullanıcı arabirimi oluşturma
 Düzen, öğeleri yerleştirmek için sıralı bir yol sağlar ve ayrıca form yeniden boyutlandırılırken bu öğelerin boyutunu ve konumunu yönetir. Bu bölümde, üç satırlık bir tek sütunlu kılavuz oluşturacaksınız. İki sayfaya denetimler ekleyecek, bazı kodlar ekleyecek ve son olarak denetimler için yeniden kullanılabilir stiller tanımlayacaksınız.

#### <a name="to-create-the-layout"></a>Düzen oluşturmak için

1. **ExpenseItHome. xaml** açın ve öğesini seçin `<Grid>` .

2. **Özellikler** penceresinde, **Düzen** kategorisi düğümünü genişletin ve **kenar boşluğu** değerlerini `10` `10` `0` `10` sol, sağ, üst ve alt kenar boşluklarına karşılık gelen,, ve olarak ayarlayın.

     Öğesi `Margin="10,0,10,10"` `<Grid>` xaml içindeki öğesine eklenir. Bir kez daha, bu değerleri, aynı sonuçla **Özellikler** penceresi yerıne doğrudan xaml kodunda girmiş olabilirsiniz.

3. `Grid`Satır ve sütun tanımlarını oluşturmak için AŞAĞıDAKI xaml kodunu öğesine ekleyin:

    ```xaml
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition />
        <RowDefinition Height="Auto"/>
    </Grid.RowDefinitions>
    ```

#### <a name="to-add-controls"></a>Denetim eklemek için

1. **ExpenseItHome. xaml**açın.

2. `</Grid>`Ve denetimlerini oluşturmak için AŞAĞıDAKI xaml kodunu etiketinin hemen üstüne ekleyin `Border` `ListBox` `Button` .

    ```xaml
    <!-- People list -->
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>
      </Border>
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">
          <ListBoxItem>Mike</ListBoxItem>
          <ListBoxItem>Lisa</ListBoxItem>
          <ListBoxItem>John</ListBoxItem>
          <ListBoxItem>Mary</ListBoxItem>
      </ListBox>

      <!-- View report button -->
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>

    ```

     Denetimlerin tasarım penceresinde görünmediğine dikkat edin. Ayrıca, denetimleri **araç kutusu** penceresinden tasarım penceresine sürükleyip **Özellikler** penceresinde özelliklerini ayarlayarak da oluşturmuş olabilirsiniz.

3. Uygulamayı derleyin ve çalıştırın. Aşağıdaki çizimde, bu yordamda XAML tarafından oluşturulan denetimlerin çalışma zamanı görünümü gösterilmektedir.

     ![ExpenseIt örnek ekran görüntüsü](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")

4. Tasarım moduna geri dönmek için uygulamayı kapatın.

#### <a name="to-add-a-background-image"></a>Arka plan görüntüsü eklemek için

1. Aşağıdaki görüntüyü seçin ve farklı kaydedin `watermark.png` .

     ![İzlenecek yol için filigran resmi](../designers/media/wpf-watermark.png "WPF_watermark")

    > [!NOTE]
    > Alternatif olarak, kendi görüntünüzü oluşturabilir ve farklı kaydedebilirsiniz `watermark.png` .

2. **Çözüm Gezgini**, **ExpenseIt** düğümünün kısayol menüsünü açın ve **Ekle**, **Varolan öğe**' yi seçin.

3. **Varolan öğe Ekle** iletişim kutusunda, az önce eklediğiniz **watermark.png** görüntüsünü bulun, seçin ve sonra **Ekle** düğmesini seçin.

    > [!NOTE]
    > **Dosya türleri** listesini genişletmeniz ve **görüntü dosyaları**' nı seçmeniz gerekebilir.

4. **ExpenseItHome. xaml** dosyasını açın ve `</Grid>` bir arka plan görüntüsü oluşturmak için etiketinin hemen üstüne aşağıdaki xaml kodunu ekleyin:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png"/>
    </Grid.Background>

    ```

#### <a name="to-add-a-title"></a>Başlık eklemek için

1. **ExpenseItHome. xaml**açın.

2. Satırı bulun `<Grid.ColumnDefinitions>` ve hemen altına aşağıdaki satırı ekleyin:

    ```xaml
    <ColumnDefinition Width="230" />

    ```

     Bu, diğer sütunların solunda, 230 piksel sabit genişliğinde ek bir sütun oluşturur.

3. Satırı bulun `<Grid.RowDefinitions>` ve hemen altına aşağıdaki satırı ekleyin:

    ```xaml
    <RowDefinition />

    ```

     Bu, kılavuzun üst kısmına bir satır ekler.

4. Değeri 1 olarak ayarlayarak denetimleri ikinci sütuna taşıyın `Grid.Column` . Her bir değeri 1 ' i artırarak her bir denetimi bir satıra taşıyın `Grid.Row` .

    1. Satırı bulun `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">` . `Grid.Column="0"`Olarak değiştirin `Grid.Column="1"` ve öğesini `Grid.Row="0"` olarak değiştirin `Grid.Row="1"` .

    2. Satırı bulun `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"` . `Grid.Column="0"`Olarak değiştirin `Grid.Column="1"` ve öğesini `Grid.Row="1"` olarak değiştirin `Grid.Row="2"` .

    3. Satırı bulun `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"` . `Grid.Column="0"`Olarak değiştirin `Grid.Column="1"` ve öğesini `Grid.Row="2"` olarak değiştirin `Grid.Row="3"` .

5. Öğesinden hemen önce, `<Border` başlığı göstermek için AŞAĞıDAKI xaml kodunu ekleyin:

    ```xaml
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        View Expense Report
    </Label>

    ```

     **ExpenseItHome. xaml** Içeriği artık C# dilinde şöyle görünmelidir:

    ```xaml
    <Page x:Class="ExpenseIt.ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home">
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

     Bunun gibi Visual Basic:

    ```xaml
    <Page x:Class="ExpenseItHome"
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
          xmlns:local="clr-namespace:ExpenseIt"
          mc:Ignorable="d"
          d:DesignHeight="300" d:DesignWidth="300"
          Title="ExpenseIt - Home" >
        <Grid Margin="10,0,10,10">
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>
            <Grid.RowDefinitions>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>
            </Border>
            <!-- People list -->
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
                View Expense Report
            </Label>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"/>
            </Grid.Background>
        </Grid>
    </Page>
    ```

6. Uygulamayı bu noktada oluşturup çalıştırırsanız, aşağıdaki gibi görünmelidir:

     ![ExpenseIt örnek ekran görüntüsü](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")

#### <a name="to-add-code-to-the-button"></a>Düğmeye kod eklemek için

1. **ExpenseItHome. xaml**açın.

2. Öğesini seçin `<Button` ve **HorizontalAlignment = "Right"** öğesinden hemen sonra şu xaml kodunu ekleyin: `Click="Button_Click"` .

     Bu, düğmenin olayı için bir olay işleyicisi ekler `Click` . **<Button** öğesi kodu şu şekilde görünmelidir:

    ```
    <!-- View report button -->
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>
    ```

3. **ExpenseItHome.xaml.cs** veya **ExpenseItHome. xaml. vb** dosyasını açın.

4. Sınıfına aşağıdaki kodu ekleyin `ExpenseItHome` :

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        // View Expense Report
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();
        this.NavigationService.Navigate(expenseReportPage);

    }
    ```

    ```vb
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
        ' View Expense Report
        Dim expenseReportPage As New ExpenseReportPage()
    Me.NavigationService.Navigate(expenseReportPage)
    End Sub
    ```

     Bu olay işleyicisi, düğme tıklandığında gider raporu sayfasını açar.

#### <a name="to-create-the-ui-for-the-report-page"></a>Rapor sayfası için Kullanıcı arabirimi oluşturmak için

1. **ExpenseReportPage. xaml**' i açın.

     Bu sayfada, giriş sayfasında seçili olan kişinin gider raporu görüntülenir.

2. Ve etiketleri arasına aşağıdaki XAML kodunu ekleyin `<Grid>` `</Grid>` :

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>

    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">

        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.ColumnHeaderStyle>
                    <Style TargetType="{x:Type DataGridColumnHeader}">
                        <Setter Property="Height" Value="35" />
                        <Setter Property="Padding" Value="5" />
                        <Setter Property="Background" Value="#4E87D4" />
                        <Setter Property="Foreground" Value="White" />
                    </Style>
                </DataGrid.ColumnHeaderStyle>
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>
    ```

     Bu Kullanıcı arabirimi, giriş sayfası için oluşturulan kullanıcı arabirimine benzerdir, ancak rapor verileri bir **DataGrid** denetiminde görüntülenir.

3. Uygulamayı derleyin ve çalıştırın.

4. **Görünüm** düğmesini seçin.

     Gider raporu sayfası görüntülenir.

     Aşağıdaki çizimde gider raporu sayfası gösterilmektedir. Geri gezinti düğmesinin etkin olduğuna dikkat edin.

     ![ExpenseIt örnek ekran görüntüsü](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")

#### <a name="to-style-controls"></a>Stil denetimlerine

1. **App. xaml** dosyasını (C#) veya **Application. xaml** dosyasını (Visual Basic) açın.

2. Ve etiketleri arasına aşağıdaki XAML `<Application.Resources>` 'yi ekleyin `</Application.Resources>` :

    ```xaml
    <!-- Header text style -->
    <Style x:Key="headerTextStyle">
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>
        <Setter Property="Label.FontSize" Value="18"></Setter>
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>
    </Style>

    <!-- Label style -->
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">
        <Setter Property="VerticalAlignment" Value="Top" />
        <Setter Property="HorizontalAlignment" Value="Left" />
        <Setter Property="FontWeight" Value="Bold" />
        <Setter Property="Margin" Value="0,0,0,5" />
    </Style>

    <!-- DataGrid header style -->
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
        <Setter Property="Foreground" Value="White" />
    </Style>

    <!-- List header style -->
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">
        <Setter Property="Height" Value="35" />
        <Setter Property="Padding" Value="5" />
        <Setter Property="Background" Value="#4E87D4" />
    </Style>

    <!-- List header text style -->
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">
        <Setter Property="Foreground" Value="White" />
        <Setter Property="VerticalAlignment" Value="Center" />
        <Setter Property="HorizontalAlignment" Value="Left" />
    </Style>

    <!-- Button style -->
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">
        <Setter Property="Width" Value="125" />
        <Setter Property="Height" Value="25" />
        <Setter Property="Margin" Value="0,10,0,0" />
        <Setter Property="HorizontalAlignment" Value="Right" />
    </Style>
    ```

     Bu XAML aşağıdaki stilleri ekler:

    - `headerTextStyle`: Sayfa başlığını biçimlendirmek için `Label` .

    - `labelStyle`: Denetimleri biçimlendirmek için `Label` .

    - `columnHeaderStyle`: Öğesini biçimlendirmek için `DataGridColumnHeader` .

    - `listHeaderStyle`: Liste üst bilgi denetimlerini biçimlendirmek için `Border` .

    - `listHeaderTextStyle`: Liste üst bilgisi **etiketini**biçimlendirmek için.

    - `buttonStyle`: `Button` **ExpenseItHome. xaml** pppage üzerinde biçimlendirmek için.

3. **ExpenseItHome. xaml** açın ve `<Grid>` `</Grid>` aşağıdaki xaml ile ve öğeleri arasındaki her şeyi değiştirin

    ```xaml
    <Grid.ColumnDefinitions>
                <ColumnDefinition Width="230" />
                <ColumnDefinition />
            </Grid.ColumnDefinitions>

            <Grid.RowDefinitions>
                <RowDefinition/>
                <RowDefinition Height="Auto"/>
                <RowDefinition />
                <RowDefinition Height="Auto"/>
            </Grid.RowDefinitions>
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >
                View Expense Report
            </Label>
            <!-- People list -->
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>
            </Border>
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">
                <ListBoxItem>Mike</ListBoxItem>
                <ListBoxItem>Lisa</ListBoxItem>
                <ListBoxItem>John</ListBoxItem>
                <ListBoxItem>Mary</ListBoxItem>
            </ListBox>

            <!-- View report button -->
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>
            <Grid.Background>
                <ImageBrush ImageSource="watermark.png"  />
            </Grid.Background>
    ```

     `VerticalAlignment`Ve `FontFamily` her bir denetimin görünümünü tanımlayan özellikler, stiller uygulanarak kaldırılır ve değiştirilmez.

4. **ExpenseReportPage. xaml** ' i açın ve `<Grid>` `</Grid>` aşağıdaki xaml ile son öğeler arasındaki her şeyi değiştirin

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png" />
    </Grid.Background>
    <Grid.ColumnDefinitions>
        <ColumnDefinition Width="230" />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto" />
        <RowDefinition />
    </Grid.RowDefinitions>
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">
        Expense Report For:
    </Label>
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto" />
            <RowDefinition Height="Auto" />
            <RowDefinition />
        </Grid.RowDefinitions>

        <!-- Name -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Name:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <!-- Department -->
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"
    Orientation="Horizontal">
            <Label Style="{StaticResource labelStyle}">Department:</Label>
            <Label Style="{StaticResource labelStyle}"></Label>
        </StackPanel>

        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"
              HorizontalAlignment="Left">
            <!-- Expense type and Amount table -->
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"
                      AutoGenerateColumns="False" RowHeaderWidth="0" >
                <DataGrid.Columns>
                    <DataGridTextColumn Header="ExpenseType" />
                    <DataGridTextColumn Header="Amount"  />
                </DataGrid.Columns>
            </DataGrid>
        </Grid>
    </Grid>

    ```

     Bu, `<Label>` ve öğelerine stiller ekler `<Border>` .

## <a name="connecting-to-data"></a>Verilere Bağlanma
 Bu bölümde, bir veri sağlayıcısı ve bir veri şablonu oluşturacak ve sonra verileri görüntüleyecek denetimleri bağlayacaksınız.

#### <a name="to-bind-data-to-a-control"></a>Bir denetime veri bağlamak için

1. **ExpenseItHome. xaml** açın ve öğesini seçin `<Grid>` ...

2. Aşağıdaki XAML kodunu ekleyin:

    ```xaml

    <Grid.Resources>
    <!-- Expense Report Data -->
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">
        <x:XData>
            <Expenses xmlns="">
                <Person Name="Mike" Department="Legal">
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />
                </Person>
                <Person Name="Lisa" Department="Marketing">
                    <Expense ExpenseType="Document printing"
          ExpenseAmount="50"/>
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />
                </Person>
                <Person Name="John" Department="Engineering">
                    <Expense ExpenseType="Magazine subscription"
         ExpenseAmount="50"/>
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />
                    <Expense ExpenseType="Software" ExpenseAmount="500" />
                </Person>
                <Person Name="Mary" Department="Finance">
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />
                </Person>
            </Expenses>
        </x:XData>
    </XmlDataProvider>
    </Grid.Resources>
    ```

     Bu kod `XmlDataProvider` , her kişiye ait verileri içeren bir sınıf oluşturur. Normalde bu bir dosya olarak yüklenir, ancak kolaylık sağlaması için veriler satır içi eklenir.

3. Öğesinin içinde `<Grid.Resources>` , AŞAĞıDAKI xaml kodunu ekleyin:

    ```xaml
    <!-- Name item template -->
    <DataTemplate x:Key="nameItemTemplate">
        <Label Content="{Binding XPath=@Name}"/>
    </DataTemplate>
    ```

     Bu `Data Template` , **ListBox**'ta verilerin nasıl görüntüleneceğini tanımlayan bir ekler.

4. Var olan `<ListBox>` öğeyi AŞAĞıDAKI XAML ile değiştirin.

    ```xaml
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"
             ItemTemplate="{StaticResource nameItemTemplate}">
    </ListBox>
    ```

     Bu kod `ItemsSource` , öğesinin özelliğini `ListBox` veri kaynağına bağlar ve veri şablonunu olarak uygular `ItemTemplate` .

#### <a name="to-connect-data-to-controls"></a>Denetimlere veri bağlamak için

1. **ExpenseReportPage. xaml. vb** veya **ExpenseReportPage.xaml.cs**öğesini açın.

2. C# ' de, aşağıdaki oluşturucuyu **ExpenseReportPage** sınıfına ekleyin veya Visual Basic var olan sınıfı aşağıdaki kodla değiştirin:

    ```csharp
    // Custom constructor to pass expense report data
        public ExpenseReportPage(object data):this()
        {
            // Bind to expense report data.
            this.DataContext = data;
        }
    ```

    ```vb
    Partial Public Class ExpenseReportPage
    Inherits Page
    Public Sub New()
    InitializeComponent()
    End Sub

    ' Custom constructor to pass expense report data
    Public Sub New(ByVal data As Object)
    Me.New()
    ' Bind to expense report data.
    Me.DataContext = data
    End Sub

    End Class
    ```

     Bu Oluşturucu bir veri nesnesini parametre olarak alır. Bu durumda, veri nesnesi seçili kişinin adını içerecektir.

3. **ExpenseItHome. xaml. vb** veya **ExpenseItHome.xaml.cs**öğesini açın.

4. `Click`Olay işleyicisi kodunu aşağıdaki kodla değiştirin:

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        // View Expense Report
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);
        this.NavigationService.Navigate(expenseReportPage);

    }
    ```

    ```vb
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
        ' View Expense Report
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)
        Me.NavigationService.Navigate(expenseReportPage)
    End Sub
    ```

     Bu kod yeni oluşturucuyu çağırır.

#### <a name="to-update-the-ui-with-data-templates"></a>Kullanıcı arabirimini veri şablonlarıyla güncelleştirmek için

1. **ExpenseReportPage. xaml**' i açın.

2. **Ad** ve **bölüm** `<StackPanel` öğelerinin xaml kodunu aşağıdakiler ile değiştirin:

    ```xaml
    <!-- Name -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Name:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>
    </StackPanel>

    <!-- Department -->
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">
        <Label Style="{StaticResource labelStyle}">Department:</Label>
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>
    </StackPanel>

    ```

     Bu, **etiket** denetimlerini uygun veri kaynağı özelliklerine bağlar.

3. Aşağıdaki XAML kodunu öğesi içine ekleyin `<Grid>` :

    ```xaml
    <!--Templates to display expense report data-->
    <Grid.Resources>
        <!-- Reason item template -->
        <DataTemplate x:Key="typeItemTemplate">
            <Label Content="{Binding XPath=@ExpenseType}"/>
        </DataTemplate>
        <!-- Amount item template -->
        <DataTemplate x:Key="amountItemTemplate">
            <Label Content="{Binding XPath=@ExpenseAmount}"/>
        </DataTemplate>
    </Grid.Resources>

    ```

     Bu, harcama raporu verilerinin nasıl görüntüleneceğini tanımlar.

4. `<DataGrid>`Öğesini aşağıdaki ile değiştirin:

    ```xaml
    <!-- Expense type and Amount table -->
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >

        <DataGrid.Columns>
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />
        </DataGrid.Columns>

    </DataGrid>
    ```

     Bu bir **ItemSource** ekler ve gider öğelerinin bağlamalarını tanımlar.

5. Uygulamayı derleyin ve çalıştırın.

6. Bir kişi seçin ve ardından **Görünüm** düğmesini seçin.

     Aşağıdaki çizimde, tüm ExpenseIt uygulamasının denetimleri, düzeni, stilleri, veri bağlama ve veri şablonları uygulanmış sayfaları gösterilmektedir.

     ![ExpenseIt örnek ekran görüntüleri](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")

## <a name="best-practices"></a><a name="Best_Practices"></a> En iyi uygulamalar
 Bu örnek WPF hakkında temel bilgileri gösterir ve sonuç olarak uygulama geliştirme en iyi yöntemlerini izlemez. WPF 'nin kapsamlı kapsamı ve uygulama geliştirme en iyi uygulamaları .NET Framework için aşağıdaki konulara bakın:

- Erişilebilirlik- [Erişilebilirlik En Iyi uygulamaları](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)

- Güvenlik- [Windows Presentation Foundation güvenliği](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

- Yerelleştirme- [WPF Genelleştirme ve yerelleştirme genel bakış](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- Performansı [En Iyi duruma GETIRME WPF uygulama performansı](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

## <a name="whats-next"></a><a name="Whats_Next"></a> Sıradaki
 Artık, WPF kullanarak bir masaüstü uygulaması oluşturmaya yönelik bir dizi teknikte sahip olursunuz. Artık, veri bağlantılı WPF uygulamasının yapı taşlarından daha basit bir bilgiye sahip olmanız gerekir. Bu konu, önemli değildir, ancak artık bu konudaki tekniklerin ötesinde sizin de keşfedecek bazı olasılıklar hakkında daha fazla fikir sahibi oldunuz.

 WPF mimarisi ve programlama modelleri hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [WPF Mimarisi](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)

- [XAML genel bakış](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)

- [Bağımlılık Özelliklerine Genel Bakış](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)

- [Düzen sistemi](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)

- [Stiller ve şablonlar](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)

  Uygulama oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [Uygulama geliştirmeye genel bakış](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)

- [Denetimlere genel bakış](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)

- [Veri Bağlamaya Genel Bakış](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)

- [WPF grafikleri, animasyon ve medyaya genel bakış](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)

- [WPF'deki Belgeler](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: Azure Mobil hizmetine bağlı BIR WPF Masaüstü uygulaması oluşturma](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md) [Windows Presentation Foundation Ile modern masaüstü uygulamaları oluşturun](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
