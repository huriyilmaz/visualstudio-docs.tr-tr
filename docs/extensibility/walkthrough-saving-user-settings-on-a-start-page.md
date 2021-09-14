---
title: 'izlenecek yol: bir başlangıç sayfasına kullanıcı Ayarlar kaydetme | Microsoft Docs'
description: Bu yönergeyi kullanarak bir ayarı kayıt defterine kaydederek başlangıç sayfanız için Kullanıcı ayarlarını nasıl kalıcı hale getirebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 3f312bb9b62ebbcc694a64ad485d19ca628b1e8e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634481"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>İzlenecek yol: bir başlangıç sayfasına kullanıcı ayarlarını kaydetme

Başlangıç sayfanız için Kullanıcı ayarlarını kalıcı hale getirebilirsiniz. Bu izlenecek yolu izleyerek, Kullanıcı bir düğmeye tıkladığında kayıt defterine bir ayar kaydeden ve sonra başlangıç sayfası her yüklendiğinde bu ayarı alan bir denetim oluşturabilirsiniz. Başlangıç sayfası proje şablonu özelleştirilebilir bir kullanıcı denetimi içerdiğinden ve varsayılan başlangıç sayfası XAML bu denetimi çağırırsa, başlangıç sayfasının kendisini değiştirmeniz gerekmez.

Bu izlenecek yolda oluşturulan ayarlar deposu, bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> arabirimin örneğidir ve çağrıldığında aşağıdaki kayıt defteri konumunu okur ve yazar: **Hkcu\software\microsoft\visualstudio\14.exe \\ \<CollectionName>**

Visual Studio deneysel örneğinde çalışırken, ayarlar deposu **hkcu\software\microsoft\visualstudio\14.0exp \\ \<CollectionName>** ' ye okur ve yazar.

ayarları kalıcı hale getirme hakkında daha fazla bilgi için bkz. [genişletme kullanıcı Ayarlar ve seçenekleri](../extensibility/extending-user-settings-and-options.md).

## <a name="prerequisites"></a>Önkoşullar

> [!NOTE]
> bu yönergeyi izlemek için Visual Studio SDK 'sını yüklemelisiniz. daha fazla bilgi için bkz. [SDK Visual Studio](../extensibility/visual-studio-sdk.md).
>
> **Uzantı Yöneticisi**' ni kullanarak başlangıç sayfası proje şablonunu indirebilirsiniz.

## <a name="set-up-the-project"></a>Projeyi ayarlama

1. [Özel başlangıç sayfası oluşturma](creating-a-custom-start-page.md)bölümünde açıklandığı gibi bir başlangıç sayfası projesi oluşturun. Projeyi **SaveMySettings** olarak adlandırın.

2. **Çözüm Gezgini**' de, StartPageControl projesine aşağıdaki derleme başvurularını ekleyin:

    - EnvDTE

    - EnvDTE80

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. Shell. Interop. 11.0

3. *MyControl. xaml*' i açın.

4. XAML bölmesinden, en üst düzey <xref:System.Windows.Controls.UserControl> öğe tanımında, ad alanı bildirimlerinden sonra aşağıdaki olay bildirimini ekleyin.

    ```xml
    Loaded="OnLoaded"
    ```

5. Tasarım bölmesinde, denetimin ana alanına tıklayın ve ardından **Sil**' e basın.

     Bu adım <xref:System.Windows.Controls.Border> öğeyi ve içindeki her şeyi kaldırır ve yalnızca en üst düzey <xref:System.Windows.Controls.Grid> öğeyi bırakır.

6. **Araç kutusundan** bir <xref:System.Windows.Controls.StackPanel> denetimi kılavuza sürükleyin.

7. Şimdi bir <xref:System.Windows.Controls.TextBlock> , a <xref:System.Windows.Controls.TextBox> ve bir düğmesini öğesine sürükleyin <xref:System.Windows.Controls.StackPanel> .

8. Aşağıdaki örnekte gösterildiği gibi, için bir **X:Name** özniteliği <xref:System.Windows.Controls.TextBox> ve `Click` için bir olay ekleyin <xref:System.Windows.Controls.Button> .

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Kullanıcı denetimini uygulama

1. XAML bölmesinde, `Click` öğesinin özniteliğini sağ tıklatın <xref:System.Windows.Controls.Button> ve ardından **olay işleyicisine git**' i tıklatın.

     Bu adım *MyControl. xaml. cs* öğesini açar ve olay için bir saplama işleyicisi oluşturur `Button_Click` .

2. Aşağıdaki `using` yönergeleri dosyanın en üstüne ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs" id="Snippet11":::

3. `SettingsStore`Aşağıdaki örnekte gösterildiği gibi özel bir özellik ekleyin.

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

     Bu özellik ilk olarak, <xref:EnvDTE80.DTE2> Kullanıcı denetiminin öğesinden Otomasyon nesne modeli içeren arabirime bir başvuru alır <xref:System.Windows.FrameworkElement.DataContext%2A> ve sonra arabirimin bir örneğini almak için DTE 'yi kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> . Ardından, geçerli kullanıcı ayarlarını döndürmek için bu örneği kullanır.

4. `Button_Click`Olayı aşağıdaki şekilde girin.

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

5. Kullanıcı denetiminin olayı için aşağıdaki işleyiciyi ekleyin `OnLoaded` .

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

8. bildirim düzenleyicisi 'nde, **Ayarlar başlangıç sayfamı kaydetmek** için **ürün adı** ' nı ayarlayın.

     Bu özellik, başlangıç sayfasının adını **Seçenekler** Iletişim kutusundaki **Başlangıç sayfası Özelleştir** listesinde görünecek şekilde ayarlar.

9. Build *StartPage. xaml*.

## <a name="test-the-control"></a>Denetimi test etme

1. **F5** tuşuna basın.

     Visual Studio deneysel örneği açılır.

2. Deneysel örnekte, **Araçlar** menüsünde **Seçenekler**' e tıklayın.

3. **ortam** düğümünde, **başlangıç**' a tıklayın ve ardından **başlangıç sayfası özelleştir** listesinde **[yüklü uzantı] Ayarlar başlangıç sayfasını kaydet**' i seçin.

     **Tamam**'a tıklayın.

4. Açık ise başlangıç sayfasını kapatın ve ardından **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.

5. Başlangıç sayfasında, **MyControl** sekmesine tıklayın.

6. Metin kutusuna **Cat** yazın ve sonra **ayarımı kaydet**' e tıklayın.

7. Başlangıç sayfasını kapatın ve yeniden açın.

     "Cat" sözcüğünün metin kutusunda görüntülenmesi gerekir.

8. "Cat" sözcüğünü "köpek" kelimesiyle değiştirin. Düğmeye tıklamayın.

9. Başlangıç sayfasını kapatın ve yeniden açın.

     "köpek" sözcüğünün metin kutusunda görüntülenmesi gerekir, çünkü Visual Studio, kapalı olsalar bile, Visual Studio kendisi kapanana kadar araç pencerelerini bellekte tutar.

10. Visual Studio Deneysel örneğini kapatın.

11. Deneysel örneği yeniden açmak için **F5** 'e basın.

12. "Cat" sözcüğünün metin kutusunda görüntülenmesi gerekir.

## <a name="next-steps"></a>Sonraki adımlar

Özelliği almak ve ayarlamak için farklı olay işleyicilerinden farklı değerler kullanarak istediğiniz sayıda özel ayarı kaydetmek ve almak üzere bu kullanıcı denetimini değiştirebilirsiniz `SettingsStore` . `propertyName`Her çağrısı için farklı bir parametre kullandığınız sürece <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , değerler kayıt defterindeki bir diğerinin üzerine yazmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [başlangıç sayfasına Visual Studio komutları ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
