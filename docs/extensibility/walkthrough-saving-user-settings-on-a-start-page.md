---
title: 'Walkthrough: Başlangıç Sayfasında Kullanıcı Ayarlarını Kaydetme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 8c791bb33d6c6a3952c14d5073857b0c3131cecf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697091"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Walkthrough: Başlangıç Sayfasında kullanıcı ayarlarını kaydetme

Başlangıç Sayfanız için kullanıcı ayarlarını devam ettirebilirsiniz. Bu izbiyi izleyerek, kullanıcı bir düğmeyi tıklattığında kayıt defterine bir ayar kaydeden ve başlat Sayfası her yüklendiğinde bu ayarı alan bir denetim oluşturabilirsiniz. Başlangıç Sayfası proje şablonu özelleştirilebilir bir kullanıcı denetimi içerdiğinden ve varsayılan Başlangıç Sayfası XAML bu denetimi aradığından, Başlangıç Sayfasının kendisini değiştirmeniz gerekmez.

Bu gözden geçirmede anlık olarak bulunan ayarlar deposu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> çağrıldığında aşağıdaki kayıt defteri konumuna okuyan ve yazan arabirimin bir örneğidir: **HKCU\Software\Microsoft\VisualStudio\14.0\\\<CollectionName>**

Visual Studio'nun deneysel örneğinde çalışırken, ayarlar deposu **HKCU\Software\Microsoft\VisualStudio\14.0Exp\\\<CollectionName>** okur ve yazar.

Ayarları nasıl devam ettirecekleri hakkında daha fazla bilgi için [bkz.](../extensibility/extending-user-settings-and-options.md)

## <a name="prerequisites"></a>Ön koşullar

> [!NOTE]
> Bu izlenmeyi takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'ya](../extensibility/visual-studio-sdk.md)bakın.
>
> **Uzantı Yöneticisi'ni**kullanarak Başlat Sayfası proje şablonuna indirebilirsiniz.

## <a name="set-up-the-project"></a>Projeyi ayarlama

1. Özel Bir Başlangıç Sayfası Oluştur'da açıklandığı gibi bir Başlangıç Sayfası projesi [oluşturun.](creating-a-custom-start-page.md) Projeyi **SaveMySettings**olarak adlandırın.

2. **Solution**Explorer'da, StartPageControl projesine aşağıdaki derleme başvurularını ekleyin:

    - Envdte

    - EnvDTE80

    - Microsoft.visualstudio.ole

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. *MyControl.xaml'ı*açın.

4. XAML bölmesinden, üst düzey <xref:System.Windows.Controls.UserControl> öğe tanımında, ad alanı bildirimlerinden sonra aşağıdaki olay bildirimini ekleyin.

    ```xml
    Loaded="OnLoaded"
    ```

5. Tasarım bölmesinde, denetimin ana alanını tıklatın ve sonra **Sil'e**basın.

     Bu adım, <xref:System.Windows.Controls.Border> öğeyi ve her şeyi kaldırır ve <xref:System.Windows.Controls.Grid> yalnızca üst düzey öğeyi bırakır.

6. Araç **Kutusundan,** bir <xref:System.Windows.Controls.StackPanel> denetimi ızgaraya sürükleyin.

7. Şimdi bir <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>a , ve <xref:System.Windows.Controls.StackPanel>bir Düğme sürükleyin .

8. **X:Ad** özniteliği ekleyin <xref:System.Windows.Controls.TextBox>ve aşağıdaki `Click` örnekte <xref:System.Windows.Controls.Button>gösterildiği gibi, bir olay için.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Kullanıcı denetimini uygulayın

1. XAML bölmesinde, `Click` <xref:System.Windows.Controls.Button> öğenin özniteliğini sağ tıklatın ve ardından Olay **İşleyicisi'ne Git'i**tıklatın.

     Bu adım *MyControl.xaml.cs*açar ve olay için bir `Button_Click` saplama işleyicisi oluşturur.

2. Aşağıdaki `using` yönergeleri dosyanın üst bölümüne ekleyin.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Aşağıdaki örnekte gösterildiği gibi özel `SettingsStore` bir özellik ekleyin.

    ```csharp
    private IVsWritableSettingsStore _settingsStore = null;
    private IVsWritableSettingsStore SettingsStore
    {
        get
        {
            if (_settingsStore == null)
            {
                // Get a reference to the DTE from the DataContext.
                var typeDescriptor = DataContext as ICustomTypeDescriptor;
                var propertyCollection = typeDescriptor.GetProperties();
                var dte = propertyCollection.Find("DTE", false).GetValue(
                    DataContext) as DTE2;

                // Get the settings manager from the DTE.
                var serviceProvider = new ServiceProvider(
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);
                var settingsManager = serviceProvider.GetService(
                    typeof(SVsSettingsManager)) as IVsSettingsManager;

                // Write the user settings to _settingsStore.
                settingsManager.GetWritableSettingsStore(
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,
                    out _settingsStore);
            }
            return _settingsStore;
        }
    }
    ```

     Bu özellik, önce kullanıcı <xref:EnvDTE80.DTE2> denetiminden <xref:System.Windows.FrameworkElement.DataContext%2A> Otomasyon nesnesi modelini içeren arabirime bir başvuru alır ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> daha sonra arabirimin bir örneğini almak için DTE'yi kullanır. Ardından, geçerli kullanıcı ayarlarını döndürmek için bu örneği kullanır.

4. `Button_Click` Olayı aşağıdaki gibi doldurun.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {
        int exists = 0;
        SettingsStore.CollectionExists("MySettings", out exists);
        if (exists != 1)
        {
            SettingsStore.CreateCollection("MySettings");
        }
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);
    }
    ```

     Bu, metin kutusunun içeriğini kayıt defterindeki "MySettings" koleksiyonundaki "MySetting" alanına yazar. Koleksiyon yoksa, oluşturulur.

5. Kullanıcı denetimi olayı `OnLoaded` için aşağıdaki işleyiciyi ekleyin.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Bu kod, metin kutusunun metnini "MySetting" geçerli değerine ayarlar.

6. Kullanıcı denetimini oluşturun.

7. **Çözüm Gezgini,** açık *kaynak.extension.vsixmanifest*olarak.

8. Bildirim düzenleyicisinde, **Ayarlar** Başlangıç Sayfasını **Kaydetmek**için Ürün Adı ayarlayın.

     Bu özellik, Başlangıç Sayfasının **adını, Seçenekler** iletişim kutusundaki **Başlangıç Sayfasını Özelleştir** listesinde görünecek şekilde ayarlar.

9. *StartPage.xaml*oluşturun.

## <a name="test-the-control"></a>Denetimi test edin

1. **F5 tuşuna**basın.

     Visual Studio'nun deneysel örneği açılır.

2. Deneysel örnekte, **Araçlar** menüsünde **Seçenekler'i**tıklatın.

3. **Ortam** düğümünde **Başlangıç**düğmesini tıklatın ve ardından **Başlat Sayfasını Özelleştir** listesinde **[Yüklü Uzantı] Ayarlarımı Kaydet Başlangıç Sayfasını**seçin.

     **Tamam**'a tıklayın.

4. Açıksa Başlat Sayfasını kapatın ve ardından **Görünüm** menüsünde **Sayfayı Başlat'ı**tıklatın.

5. Başlangıç Sayfasında, **MyControl** sekmesini tıklatın.

6. Metin **kutusunda, Cat**yazın ve ardından **Ayarmı Kaydet'i**tıklatın.

7. Başlangıç Sayfasını kapatın ve yeniden açın.

     "Kedi" sözcüğü metin kutusunda görüntülenmelidir.

8. "Kedi" kelimesini "Köpek" ile değiştirin. Düğmeyi tıklatmayın.

9. Başlangıç Sayfasını kapatın ve yeniden açın.

     Visual Studio kapalı olsalar bile, Visual Studio'nun kendisi kapanana kadar ayarı kaydetmemiş olsanız bile, "Köpek" sözcüğü metin kutusunda görüntülenmelidir.

10. Visual Studio'nun deneysel örneğini kapatın.

11. Deneysel örneği yeniden açmak için **F5** tuşuna basın.

12. "Kedi" sözcüğü metin kutusunda görüntülenmelidir.

## <a name="next-steps"></a>Sonraki adımlar

Özelliği almak ve ayarlamak için farklı olay işleyicilerinden farklı değerler kullanarak herhangi bir sayıda `SettingsStore` özel ayarı kaydetmek ve almak için bu kullanıcı denetimini değiştirebilirsiniz. Her arama için farklı `propertyName` bir parametre <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>kullandığınız sürece, değerler kayıt defterinde birbirinin üzerine yazmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Başlangıç Sayfasına Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
