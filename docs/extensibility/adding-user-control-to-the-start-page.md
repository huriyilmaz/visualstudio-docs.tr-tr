---
title: Başlangıç sayfasına kullanıcı denetimi ekleniyor | Microsoft Docs
description: Visual Studio 'da başlangıç sayfasına Windows Presentation Foundation (WPF) Kullanıcı denetimi eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 735e77868b85bdd8f85fb27957602d6759b5b097
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879182"
---
# <a name="add-user-control-to-the-start-page"></a>Başlangıç sayfasına kullanıcı denetimi Ekle

Bu izlenecek yol, bir DLL başvurusunun özel bir başlangıç sayfasına nasıl ekleneceğini gösterir. Örnek, çözüme bir kullanıcı denetimi ekler, Kullanıcı denetimini oluşturur ve sonra başlangıç sayfası *. xaml* dosyasından oluşturulan derlemeye başvurur. Yeni bir sekme, temel bir Web tarayıcısı olarak işlev gören Kullanıcı denetimini barındırır.

Bir *. xaml* dosyasından çağrılabilecek herhangi bir derlemeyi eklemek için aynı işlemi kullanabilirsiniz.

## <a name="add-a-wpf-user-control-to-the-solution"></a>Çözüme WPF Kullanıcı denetimi ekleme

İlk olarak, başlangıç sayfası çözümüne bir Windows Presentation Foundation (WPF) Kullanıcı denetimi ekleyin.

1. [Özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md)bölümünde oluşturduğumuz kullanarak bir başlangıç sayfası oluşturun.

2. **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni proje**' ye tıklayın.

3. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual Basic** veya **Visual C#** düğümünü genişletin ve **Windows**' a tıklayın. Orta bölmede, **WPF Kullanıcı denetimi kitaplığı**' nı seçin.

4. Denetimi adlandırın `WebUserControl` ve ardından **Tamam**' a tıklayın.

## <a name="implement-the-user-control"></a>Kullanıcı denetimini uygulama

WPF Kullanıcı denetimi uygulamak için XAML 'de Kullanıcı arabirimi (UI) oluşturun ve ardından C# veya başka bir .NET dilinde arka plan kod olaylarını yazın.

### <a name="to-write-the-xaml-for-the-user-control"></a>Kullanıcı denetimi için XAML yazmak için

1. Kullanıcı denetimi için XAML dosyasını açın. `<Grid>`Öğesinde, denetime aşağıdaki satır tanımlarını ekleyin.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. Ana `<Grid>` öğesinde, `<Grid>` Web adreslerini yazmak için bir metin kutusu ve yeni adresi ayarlamaya yönelik bir düğme içeren aşağıdaki yeni öğeyi ekleyin.

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

3. Aşağıdaki çerçeveyi, `<Grid>` `<Grid>` düğme ve metin kutusunu içeren öğeden hemen sonra en üst düzey öğeye ekleyin.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Aşağıdaki örnek, Kullanıcı denetimi için tamamlanan XAML 'yi gösterir.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Kullanıcı denetimi için arka plan kod olaylarını yazmak için

1. XAML tasarımcısında, denetime eklediğiniz **adresi ayarla** düğmesine çift tıklayın.

    *UserControl1.cs* dosyası kod düzenleyicisinde açılır.

2. SetButton_Click olay Işleyicisini aşağıda gösterildiği gibi girin.

    ```csharp
    private void SetButton_Click(object sender, RoutedEventArgs e)
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

    Bu kod, Web tarayıcısının hedefi olarak metin kutusuna yazılan Web adresini ayarlar. Adres geçerli değilse, kod bir hata oluşturur.

3. WebFrame_Navigated olayını da işlemeniz gerekir:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Çözümü derleyin.

## <a name="add-the-user-control-to-the-start-page"></a>Başlangıç sayfasına kullanıcı denetimini ekleyin

Bu denetimi başlangıç sayfası projesi için kullanılabilir hale getirmek için, başlangıç sayfası proje dosyasında, yeni denetim kitaplığına bir başvuru ekleyin. Ardından, başlangıç sayfası XAML biçimlendirmesine denetim ekleyebilirsiniz.

1. **Çözüm Gezgini**, başlangıç sayfası projesinde, **Başvurular** ' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.

2. **Projeler** sekmesinde **WebUserControl** ' ı seçin ve ardından **Tamam**' a tıklayın.

3. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

    Çözümün oluşturulması, Kullanıcı denetiminin çözümdeki diğer dosyalar için IntelliSense tarafından kullanılabilmesini sağlar.

    Başlangıç sayfası XAML biçimlendirmesine denetim eklemek için derlemeye bir ad alanı başvurusu ekleyin ve sonra denetimi sayfaya yerleştirin.

### <a name="to-add-the-control-to-the-markup"></a>Denetimi biçimlendirmeye eklemek için

1. **Çözüm Gezgini**' de, başlangıç sayfası *. xaml* dosyasını açın.

2. **Xaml** bölmesinde, en üst düzey öğeye aşağıdaki ad alanı bildirimini ekleyin <xref:System.Windows.Controls.Grid> .

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. **Xaml** bölmesinde \<Grid> bölümüne gidin.

    Bölüm <xref:System.Windows.Controls.TabControl> bir öğesi içindeki bir öğesi içerir <xref:System.Windows.Controls.Grid> .

4. \<TabControl>Kullanıcı denetiminizin başvurusunu içeren bir öğesi içeren bir öğesi ekleyin \<TabItem> .

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Artık denetimi test edebilirsiniz.

## <a name="test-a-manually-created-custom-start-page"></a>El ile oluşturulan özel başlangıç sayfasını test etme

1. XAML dosyanızı ve destekleyici metin dosyalarını veya biçimlendirme dosyalarını, *%USERPROFILE%\My SiteStudio 2015 \ StartPages \\* klasörüne kopyalayın.

2. Başlangıç sayfanız, Visual Studio tarafından yüklenmeyen derlemelerdeki herhangi bir denetime veya türe başvuruyorsa, derlemeleri kopyalayın ve sonra _Visual Studio yükleme klasörü_**\Common7\IDE\PrivateAssemblies \\**' na yapıştırın.

3. Visual Studio komut isteminde **devenv/rootsuffix exp** yazarak Visual Studio 'nun deneysel bir örneğini açın.

4. Deneysel örnekte, **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Başlangıç** sayfasına gidin ve **Başlangıç sayfasını Özelleştir** açılan menüsünden XAML dosyanızı seçin.

5. **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.

    Özel başlangıç sayfanız görüntülenmelidir. Herhangi bir dosyayı değiştirmek istiyorsanız, deneysel örneği kapatmanız, değişiklikleri yapmanız, değiştirilen dosyaları kopyalayıp yapıştırmanız ve sonra değişiklikleri görüntülemek için deneysel örneği yeniden açmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF kapsayıcı denetimleri](/previous-versions/bb675291(v=vs.110))
- [İzlenecek yol: başlangıç sayfasına özel XAML ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)