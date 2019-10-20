---
title: 'İzlenecek yol: bir başlangıç sayfasına kullanıcı ayarlarını kaydetme | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: fe3d1040089a4b78368a4da94933a4a1440afafd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647916"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>İzlenecek yol: bir başlangıç sayfasına kullanıcı ayarlarını kaydetme

Başlangıç sayfanız için Kullanıcı ayarlarını kalıcı hale getirebilirsiniz. Bu izlenecek yolu izleyerek, Kullanıcı bir düğmeye tıkladığında kayıt defterine bir ayar kaydeden ve sonra başlangıç sayfası her yüklendiğinde bu ayarı alan bir denetim oluşturabilirsiniz. Başlangıç sayfası proje şablonu özelleştirilebilir bir kullanıcı denetimi içerdiğinden ve varsayılan başlangıç sayfası XAML bu denetimi çağırırsa, başlangıç sayfasının kendisini değiştirmeniz gerekmez.

Bu izlenecek yolda örneği oluşturulan ayarlar deposu, çağrıldığında aşağıdaki kayıt defteri konumunu okuyan ve yazan <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> arabiriminin bir örneğidir: **Hkcu\software\microsoft\visualstudio\14.exe \\ \<CollectionName >**

Visual Studio 'nun deneysel örneğinde çalışırken, ayarlar deposu **Hkcu\software\microsoft\visualstudio\14.0Exp \\ \<CollectionName >** okur ve yazar.

Ayarları kalıcı hale getirme hakkında daha fazla bilgi için bkz. [Kullanıcı ayarlarını ve seçeneklerini genişletme](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Prerequisites

> [!NOTE]
> Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).
>
> **Uzantı Yöneticisi**' ni kullanarak başlangıç sayfası proje şablonunu indirebilirsiniz.

## <a name="set-up-the-project"></a>Projeyi ayarlama

1. [Özel başlangıç sayfası oluşturma](creating-a-custom-start-page.md)bölümünde açıklandığı gibi bir başlangıç sayfası projesi oluşturun. Projeyi **SaveMySettings**olarak adlandırın.

2. **Çözüm Gezgini**' de, StartPageControl projesine aşağıdaki derleme başvurularını ekleyin:

    - EnvDTE

    - EnvDTE80

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. Shell. Interop. 11.0

3. *MyControl. xaml*' i açın.

4. XAML bölmesinde, üst düzey <xref:System.Windows.Controls.UserControl> öğesi tanımında, ad alanı bildirimlerinden sonra aşağıdaki olay bildirimini ekleyin.

    ```xml
    Loaded="OnLoaded"
    ```

5. Tasarım bölmesinde, denetimin ana alanına tıklayın ve ardından **Sil**' e basın.

     Bu adım <xref:System.Windows.Controls.Border> öğesi ve içindeki her şeyi kaldırır ve yalnızca üst düzey <xref:System.Windows.Controls.Grid> öğesini bırakır.

6. **Araç kutusundan**bir <xref:System.Windows.Controls.StackPanel> denetimini kılavuza sürükleyin.

7. Şimdi bir <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox> ve bir düğmeyi <xref:System.Windows.Controls.StackPanel> sürükleyin.

8. Aşağıdaki örnekte gösterildiği gibi, <xref:System.Windows.Controls.TextBox> için bir **X:Name** özniteliği ve <xref:System.Windows.Controls.Button> için `Click` bir olay ekleyin.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Kullanıcı denetimini uygulama

1. XAML bölmesinde, <xref:System.Windows.Controls.Button> öğesinin `Click` özniteliğine sağ tıklayıp **olay Işleyicisine git ' e**tıklayın.

     Bu adım *MyControl.xaml.cs*' ı açar ve `Button_Click` olayı için bir saplama işleyicisi oluşturur.

2. Aşağıdaki `using` yönergelerini dosyanın en üstüne ekleyin.

     [!code-csharp[StartPageDTE#11](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]

3. Aşağıdaki örnekte gösterildiği gibi özel bir `SettingsStore` özelliği ekleyin.

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

     Bu özellik ilk olarak, Kullanıcı denetiminin <xref:System.Windows.FrameworkElement.DataContext%2A> Otomasyon nesne modelini içeren <xref:EnvDTE80.DTE2> arabirimine bir başvuru alır ve ardından <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> arabiriminin bir örneğini almak için DTE 'yi kullanır. Ardından, geçerli kullanıcı ayarlarını döndürmek için bu örneği kullanır.

4. @No__t_0 olayını aşağıdaki şekilde girin.

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

     Bu, metin kutusunun içeriğini kayıt defterindeki bir "MySettings" koleksiyonundaki "MySetting" alanına yazar. Koleksiyon yoksa, oluşturulur.

5. Kullanıcı denetiminin `OnLoaded` olayı için aşağıdaki işleyiciyi ekleyin.

    ```csharp
    private void OnLoaded(Object sender, RoutedEventArgs e)
    {
        string value;
        SettingsStore.GetStringOrDefault(
            "MySettings", "MySetting", "", out value);
        txtblk.Text = value;
    }
    ```

     Bu kod metin kutusunun metnini "MySetting" öğesinin geçerli değerine ayarlar.

6. Kullanıcı denetimini oluşturun.

7. **Çözüm Gezgini**, *kaynak. Extension. valtmanifest*' i açın.

8. Bildirim düzenleyicisinde, **ürün adı** ' nı ayarlarımı **Kaydet başlangıç sayfası**olarak ayarlayın.

     Bu özellik, başlangıç sayfasının adını **Seçenekler** Iletişim kutusundaki **Başlangıç sayfası Özelleştir** listesinde görünecek şekilde ayarlar.

9. Build *StartPage. xaml*.

## <a name="test-the-control"></a>Denetimi test etme

1. **F5**tuşuna basın.

     Visual Studio 'nun deneysel örneği açılır.

2. Deneysel örnekte, **Araçlar** menüsünde **Seçenekler**' e tıklayın.

3. **Ortam** düğümünde, **Başlangıç**' a tıklayın ve ardından **Başlangıç sayfası Özelleştir** listesinde **[yüklü uzantı] Ayarlarımı Kaydet başlangıç sayfası**' nı seçin.

     **Tamam**'a tıklayın.

4. Açık ise başlangıç sayfasını kapatın ve ardından **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.

5. Başlangıç sayfasında, **MyControl** sekmesine tıklayın.

6. Metin kutusuna **Cat**yazın ve sonra **ayarımı kaydet**' e tıklayın.

7. Başlangıç sayfasını kapatın ve yeniden açın.

     "Cat" sözcüğünün metin kutusunda görüntülenmesi gerekir.

8. "Cat" sözcüğünü "köpek" kelimesiyle değiştirin. Düğmeye tıklamayın.

9. Başlangıç sayfasını kapatın ve yeniden açın.

     "Köpek" sözcüğünün metin kutusunda görüntülenmesi gerekir, çünkü Visual Studio kapalı olsalar bile, Visual Studio tarafından kapanana kadar araç pencerelerini bellekte tutar.

10. Visual Studio 'nun Deneysel örneğini kapatın.

11. Deneysel örneği yeniden açmak için **F5** 'e basın.

12. "Cat" sözcüğünün metin kutusunda görüntülenmesi gerekir.

## <a name="next-steps"></a>Sonraki adımlar

@No__t_0 özelliğini almak ve ayarlamak için farklı olay işleyicilerinden farklı değerler kullanarak istediğiniz sayıda özel ayarı kaydetmek ve almak için bu kullanıcı denetimini değiştirebilirsiniz. Her <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> çağrısı için farklı bir `propertyName` parametresi kullandığınız sürece, değerler kayıt defterindeki bir diğerinin üzerine yazmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Başlangıç sayfasına Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
