---
title: Başlangıç Sayfası girişlerine Kullanıcı Denetimi | Microsoft Docs
description: Windows Presentation Foundation'da Başlangıç Sayfasına bir Windows Presentation Foundation (WPF) kullanıcı denetimi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page dll
- custom start page
- start page assembly
ms.assetid: 5b7997db-af6f-4fa9-a128-bceb42bddaf1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 794ff65d58e03b22584f0a4d2a291371b1e08c81
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725331"
---
# <a name="add-user-control-to-the-start-page"></a>Başlangıç Sayfasına kullanıcı denetimi ekleme

Bu kılavuzda, özel bir Başlangıç Sayfasına DLL başvurusu ekleme adımlarını gösterir. Örnek, çözüme bir kullanıcı denetimi ekler, kullanıcı denetimi oluşturur ve ardından Başlangıç Sayfası *.xaml* dosyasından derlemeye başvurur. Yeni bir sekme, temel bir Web tarayıcısı olarak işlev yapan kullanıcı denetimi barındırr.

Bir *.xaml* dosyasından çağrılabilirsiniz herhangi bir derleme eklemek için aynı işlemi kullanabilirsiniz.

## <a name="add-a-wpf-user-control-to-the-solution"></a>Çözüme WPF kullanıcı denetimi ekleme

İlk olarak, Windows Presentation Foundation (WPF) kullanıcı denetimine bir Başlangıç Sayfası çözümü ekleyin.

1. Özel başlangıç sayfası oluşturma içinde oluşturduğum [sayfayı kullanarak bir Başlangıç Sayfası oluşturun.](../extensibility/creating-a-custom-start-page.md)

2. Bu **Çözüm Gezgini,** çözüme sağ tıklayın, Ekle'ye **tıklayın** ve ardından Yeni **giriş'e Project.**

3. Yeni Project iletişim **kutusunun sol** bölmesinde, **Visual Basic** veya **Visual C# düğümünü genişletin** ve **Windows.** Orta bölmede **WPF Kullanıcı Denetimi Kitaplığı'ni seçin.**

4. Denetime bir ad `WebUserControl` ve ardından Tamam'a **tıklayın.**

## <a name="implement-the-user-control"></a>Kullanıcı denetimi uygulama

WPF kullanıcı denetimi uygulamak için, XAML'de kullanıcı arabirimini (UI) derlemek ve ardından C# veya başka bir .NET dilinde arka arkasındaki kod olaylarını yazın.

### <a name="to-write-the-xaml-for-the-user-control"></a>Kullanıcı denetimi için XAML yazmak için

1. Kullanıcı denetimi için XAML dosyasını açın. `<Grid>`öğesinde, denetime aşağıdaki satır tanımlarını ekleyin.

    ```vb
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="*" />
    </Grid.RowDefinitions>

    ```

2. main öğesinde, Web adresleri yazmak için bir metin kutusu ve yeni adresi ayarlama düğmesi içeren `<Grid>` `<Grid>` aşağıdaki yeni öğeyi ekleyin.

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

3. Düğmeyi ve metin kutusunu içeren `<Grid>` öğenin hemen sonrasındaki `<Grid>` üst düzey öğeye aşağıdaki çerçeveyi ekleyin.

    ```vb
    <Frame Grid.Row="1" x:Name="WebFrame" Source="http://www.bing.com" Navigated="WebFrame_Navigated" />
    ```

4. Aşağıdaki örnek, kullanıcı denetimi için tamamlanmış XAML'i gösterir.

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

### <a name="to-write-the-code-behind-events-for-the-user-control"></a>Kullanıcı denetimi için arka arkasındaki kod olaylarını yazmak için

1. XAML tasarımcısında, denetime **eklenen Adresi** Ayarla düğmesine çift tıklayın.

    *UserControl1.cs* dosyası kod düzenleyicisinde açılır.

2. Olay İşleyicisi SetButton_Click aşağıdaki gibi doldurun.

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

    Bu kod, metin kutusuna web tarayıcısının hedefi olarak yazarak Web adresini ayarlar. Adres geçerli değilse kod bir hata verir.

3. Ayrıca olayla ilgili WebFrame_Navigated gerekir:

    ```csharp
    private void WebFrame_Navigated(object sender, EventArgs e)
    { }
    ```

4. Çözümü derleyin.

## <a name="add-the-user-control-to-the-start-page"></a>Kullanıcı denetimlerini Başlangıç Sayfasına ekleme

Bu denetimi Başlangıç Sayfası projesinin kullanılabilir hale eklemek için Başlangıç Sayfası proje dosyasında yeni denetim kitaplığına bir başvuru ekleyin. Ardından denetimi Başlangıç Sayfası XAML işaretlemesi'ne ekleyebilirsiniz.

1. Bu **Çözüm Gezgini** Sayfasında, Başlangıç Sayfası projesinde Başvurular'a **sağ tıklayın ve ardından** Başvuru **Ekle'ye tıklayın.**

2. Projeler sekmesinde **WebUserControl'u seçin ve** ardından Tamam'a **tıklayın.** 

3. **Yapı** menüsünde **Yapı Çözümü**’ne tıklayın.

    Çözümün inşası, kullanıcı denetimine çözümde bulunan diğer dosyalar için IntelliSense tarafından kullanılabilir.

    Denetimi Başlangıç Sayfası XAML işaretlemeye eklemek için derlemeye bir ad alanı başvurusu ekleyin ve denetimi sayfaya ekleyin.

### <a name="to-add-the-control-to-the-markup"></a>Denetimi işaretlemeye eklemek için

1. Bu **Çözüm Gezgini**, Başlangıç Sayfası *.xaml dosyasını* açın.

2. **XAML bölmesinde,** aşağıdaki ad alanı bildirimini üst düzey öğeye <xref:System.Windows.Controls.Grid> ekleyin.

   ```xml
   xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
   ```

3. **XAML bölmesinde** bölümüne \<Grid> kaydırın.

    bölümü bir <xref:System.Windows.Controls.TabControl> öğesinde bir öğesi <xref:System.Windows.Controls.Grid> içerir.

4. Kullanıcı \<TabControl> denetiminize başvuru \<TabItem> içeren bir öğesi ekleyin.

    ```xml

    <TabItem Header="Web" Height="Auto">
        <vsc:UserControl1 />
    </TabItem>

    ```

    Artık denetimi test etmek için.

## <a name="test-a-manually-created-custom-start-page"></a>El ile oluşturulan özel Başlangıç Sayfasını test edin

1. XAML dosyanızı ve tüm desteklenen metin dosyalarını veya işaretleme dosyalarını *%USERPROFILE%\My Documents\Visual Studio 2015\StartPages klasörüne \\* kopyalayın.

2. Başlangıç sayfanız, Visual Studio tarafından yüklenmemiş derlemelerde herhangi bir denetime veya türe başvurursa, derlemeleri kopyalayın ve **ardından \Common7\IDE\PrivateAssemblies \\** Visual Studio yükleme klasörüne yapıştırın.

3. Bir Visual Studio komut isteminde, deneysel bir örnek açmak için **devenv /rootsuffix Exp** Visual Studio.

4. Deneysel örnekte Araçlar Seçenekleri Ortam Başlatma **sayfasına** gidin ve Başlangıç Sayfasını Özelleştir açılan  >    >    >   menüsünden XAML **dosyanızı** seçin.

5. Görünüm menüsünde **Başlangıç** **Sayfası'nın üzerine tıklayın.**

    Özel başlangıç sayfanız görüntüleniyor. Herhangi bir dosyayı değiştirmek için deneysel örneği kapatmanız, değişiklikleri yapmanız, değiştirilen dosyaları kopyalayıp yapıştırmanız ve ardından deneysel örneği yeniden açıp değişiklikleri görüntülemeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF kapsayıcı denetimleri](/previous-versions/bb675291(v=vs.110))
- [Adım adım kılavuz: Başlangıç Sayfasına özel XAML ekleme](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md)