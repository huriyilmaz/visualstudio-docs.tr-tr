---
title: Başlangıç Sayfasına Kullanıcı Denetimi Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b426cfbbfca2e301797644a1fc73f188054d0cfa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740134"
---
# <a name="add-user-control-to-the-start-page"></a>Başlangıç Sayfasına kullanıcı denetimi ekleme

Bu izlik, özel bir Başlangıç Sayfasına Nasıl DLL başvurusu ekleyeceğinizi gösterir. Örnek, çözüme bir kullanıcı denetimi ekler, kullanıcı denetimini oluşturur ve ardından Başlangıç Sayfası *.xaml* dosyasından yerleşik derlemeye başvurur. Yeni bir sekme, temel bir Web tarayıcısı işlevi gören kullanıcı denetimini barındırabilir.

*.xaml* dosyasından çağrılabilen herhangi bir derleme eklemek için aynı işlemi kullanabilirsiniz.

## <a name="add-a-wpf-user-control-to-the-solution"></a>Çözüme WPF kullanıcı denetimi ekleme

İlk olarak, Başlangıç Sayfası çözümüne bir Windows Sunu Temeli (WPF) kullanıcı denetimi ekleyin.

1. Özel Bir Başlangıç Sayfası Oluştur'da oluşturduğumuz u kullanarak Başlangıç [Sayfası oluşturun.](../extensibility/creating-a-custom-start-page.md)

2. **Çözüm Gezgini'nde,** çözüme sağ tıklayın, **Ekle'yi**tıklatın ve ardından **Yeni Proje'yi**tıklatın.

3. **Yeni Proje** iletişim kutusunun sol bölmesinde Visual **Basic** veya **Visual C#** düğümlerini genişletin ve **Windows'u**tıklatın. Orta bölmede **WPF Kullanıcı Denetim Kitaplığı'nı**seçin.

4. Denetimi `WebUserControl` adlandırın ve ardından **Tamam'ı**tıklatın.

## <a name="implement-the-user-control"></a>Kullanıcı denetimini uygulayın

WPF kullanıcı denetimini uygulamak için XAML'de kullanıcı arabirimi (UI) oluşturun ve ardından C# veya başka bir .NET dilinde kod arkası olayları yazın.

### <a name="to-write-the-xaml-for-the-user-control"></a>Kullanıcı denetimi için XAML yazmak için

1. Kullanıcı denetimi için XAML dosyasını açın. Öğede, `<Grid>` denetime aşağıdaki satır tanımlarını ekleyin.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Ana `<Grid>` öğede, Web adreslerini yazmak için bir metin kutusu ve yeni adresi ayarlamak için bir düğme içeren aşağıdaki yeni `<Grid>` öğeyi ekleyin.

    ```xml
    <Grid Grid.Row="0">
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width="Auto" />
        </Grid.ColumnDefinitions>
        <TextBox x:Name="UserSource" Grid.Column="0" />
        <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
    </Grid>
    ```

3. Düğme ve textbox içeren `<Grid>` `<Grid>` öğeden hemen sonra üst düzey öğeye aşağıdaki çerçeveyi ekleyin.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Aşağıdaki örnekte, kullanıcı denetimi için tamamlanmış XAML gösterilmektedir.

    ```xml
    <UserControl x:Class="WebUserControl.UserControl1"
                 xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
                 xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
                 mc:Ignorable="d"
                 d:DesignHeight="300" d:DesignWidth="300">
        <Grid>
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*" />
            </Grid.RowDefinitions>
            <Grid Grid.Row="0">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
                <TextBox x:Name="UserSource" Grid.Column="0" />
                <Button Grid.Column="1" x:Name="SetButton" Content="Set Address" Click="SetButton_Click" />
            </Grid>
            <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
        </Grid>
    </UserControl>

    ```

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Kullanıcı denetimi için kod arkası olayları yazmak için

1. XAML tasarımcısında, denetime eklediğiniz **Adresi Ayarla** düğmesini çift tıklatın.

    *UserControl1.cs* dosyası kod düzenleyicisinde açılır.

2. SetButton_Click Olay Işleyicisi'ni aşağıdaki gibi doldurun.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            this.WebFrame.Source = new Uri(this.UserSource.Text, UriKind.Absolute);
        }
        catch (Exception error)
        {
            MessageBox.Show(error.Message);
        }
    }
    ```

    Bu kod, metin kutusuna yazılan Web adresini Web tarayıcısının hedefi olarak ayarlar. Adres geçerli değilse, kod bir hata atar.

3. Ayrıca WebFrame_Navigated olayı ele almalısınız:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Çözümü derleyin.

## <a name="add-the-user-control-to-the-start-page"></a>Kullanıcı denetimini Başlangıç Sayfasına ekleme

Bu denetimi Başlat Sayfası projesinde kullanılabilir hale getirmek için, Başlangıç Sayfası proje dosyasında yeni denetim kitaplığına bir başvuru ekleyin. Ardından denetimi Başlangıç Sayfası XAML biçimlendirmesine ekleyebilirsiniz.

1. **Solution**Explorer'da, Başlangıç Sayfası projesinde, **Başvurular'ı** sağ tıklatın ve ardından **Başvuru Ekle'yi**tıklatın.

2. **Projeler** sekmesinde, **WebUserControl'u** seçin ve ardından **Tamam'ı**tıklatın.

3. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

    Çözümü oluşturmak, kullanıcı denetimini çözümdeki diğer dosyalar için IntelliSense'in kullanımına sunar.

    Denetimi Başlangıç Sayfası XAML biçimlendirmesine eklemek için derlemeye bir ad alanı başvurusu ekleyin ve denetimi sayfaya koyun.

### <a name="to-add-the-control-to-the-markup"></a>Denetimi biçimlendirmeye eklemek için

1. **Çözüm Gezgini'nde**Başlangıç Sayfası *.xaml* dosyasını açın.

2. **XAML** bölmesinde, üst düzey <xref:System.Windows.Controls.Grid> öğeye aşağıdaki ad alanı bildirimini ekleyin.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. **XAML** bölmesinde, Izgara \<> bölümüne gidin.

    Bölüm, bir <xref:System.Windows.Controls.TabControl> <xref:System.Windows.Controls.Grid> öğedeki bir öğeyi içerir.

4. Kullanıcı \<denetiminize bir başvuru \<içeren bir TabItem> içeren bir TabDenetimi> öğesi ekleyin.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Artık kontrolü test edebilirsin.

## <a name="test-a-manually-created-custom-start-page"></a>El ile oluşturulmuş özel Başlangıç Sayfasını test edin

1. XAML dosyanızı ve desteklenen metin dosyalarını veya işaretleme dosyalarını *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages\\ * klasörüne kopyalayın.

2. Başlangıç sayfanız Visual Studio tarafından yüklenmeyen derlemelerde herhangi bir denetime veya türe başvuruyorsa, derlemeleri kopyalayın ve _Visual Studio yükleme klasörüne yapıştırın_**\Common7\IDE\PrivateAssemblies\\**.

3. Visual Studio komut isteminde Visual Studio'nun deneysel bir örneğini açmak için **devenv /rootsuffix Exp** yazın.

4. Deneysel durumda, **Araçlar** > **Seçenekleri** > **Ortamı** > **Başlatma** sayfasına gidin ve Başlat Sayfa açılır bırakarak **XAML** dosyanızı seçin.

5. **Görünüm** menüsünde, **Başlat Sayfasını**tıklatın.

    Özel başlangıç sayfanız görüntülenmelidir. Herhangi bir dosyayı değiştirmek istiyorsanız, deneme örneğini kapatmanız, değişiklikleri yapmanız, değiştirilen dosyaları kopyalamanız ve yapıştırmamanız ve değişiklikleri görüntülemek için deneme örneğini yeniden açmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF konteyner kontrolleri](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
- [Walkthrough: Başlangıç Sayfasına özel XAML ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)
