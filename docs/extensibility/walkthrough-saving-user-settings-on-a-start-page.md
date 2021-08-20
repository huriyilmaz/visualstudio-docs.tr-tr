---
title: "Adım adım kılavuz: Kullanıcı Ayarlar'i Başlangıç Sayfası'| Microsoft Docs"
description: Bu izlenecek yolu kullanarak kayıt defterine bir ayar kaydederek Başlangıç Sayfanız için kullanıcı ayarlarını kalıcı yapmayı öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157949"
---
# <a name="walkthrough-save-user-settings-on-a-start-page"></a>Adım adım kılavuz: Kullanıcı ayarlarını Başlangıç Sayfasına kaydetme

Başlangıç Sayfanız için kullanıcı ayarlarını kalıcı yapabilirsiniz. Bu izlenecek yolu takip edin, kullanıcı bir düğmeye tıkladığında bir ayarı kayıt defterine kaydeden ve ardından Başlangıç Sayfası her yüklenirken bu ayarı alan bir denetim oluşturabilirsiniz. Başlangıç Sayfası proje şablonu özelleştirilebilir bir kullanıcı denetimi içerir ve varsayılan Başlangıç Sayfası XAML bu denetimi çağırarak Başlangıç Sayfası'nın kendisini değiştirmenize gerek yoktur.

Bu kılavuzda örneği verilen ayarlar deposu, şu kayıt defteri konumunda şu kayıt defteri konumunu okur ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> yazar: **HKCU\Software\Microsoft\VisualStudio\14.0 \\ \<CollectionName>**

Visual Studio'nin deneysel örneğinde çalıştır çalıştırılırsa, ayarlar deposu **HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ \<CollectionName>** dizinine okur ve yazar.

Ayarların kalıcı hale nasıl tutulacakları hakkında daha fazla bilgi için bkz. Kullanıcı Ayarlar [Ve Seçenekler.](../extensibility/extending-user-settings-and-options.md)

## <a name="prerequisites"></a>Önkoşullar

> [!NOTE]
> Bu izlenecek yolu takip etmek için Visual Studio SDK'sı yüklemeniz gerekir. Daha fazla bilgi için [bkz. Visual Studio SDK.](../extensibility/visual-studio-sdk.md)
>
> Uzantı Yöneticisi'ni kullanarak Başlangıç Sayfası proje şablonunu **indirebilirsiniz.**

## <a name="set-up-the-project"></a>Projeyi ayarlama

1. Özel Başlangıç Sayfası oluşturma konusunda açıklandığı gibi [bir Başlangıç Sayfası projesi oluşturun.](creating-a-custom-start-page.md) Projeye **SaveMySettings adını girin.**

2. Aşağıdaki **Çözüm Gezgini** StartPageControl projesine aşağıdaki derleme başvurularını ekleyin:

    - Envdte

    - EnvDTE80

    - Microsoft.visualstudio.ole

    - Microsoft.VisualStudio.Shell.Interop.11.0

3. *MyControl.xaml'i açın.*

4. XAML bölmesindeki üst düzey öğe <xref:System.Windows.Controls.UserControl> tanımında, ad alanı bildirimlerinden sonra aşağıdaki olay bildirimini ekleyin.

    ```xml
    Loaded="OnLoaded"
    ```

5. Tasarım bölmesinde denetimin ana alanına tıklayın ve ardından Sil'e **basın.**

     Bu adım, öğesini ve bu öğedeki her şeyi <xref:System.Windows.Controls.Border> kaldırır ve yalnızca üst düzey öğeyi <xref:System.Windows.Controls.Grid> bırakır.

6. Araç **Kutusundan,** bir denetimi <xref:System.Windows.Controls.StackPanel> kılavuza sürükleyin.

7. Şimdi , <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Controls.TextBox> düğmelerini içine <xref:System.Windows.Controls.StackPanel> sürükleyin.

8. Aşağıdaki örnekte gösterildiği gibi , için bir **x:Name** özniteliği <xref:System.Windows.Controls.TextBox> ve için bir olay `Click` <xref:System.Windows.Controls.Button> ekleyin.

    ```xml
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />
        <Button Click="Button_Click" Width="100">Save My Setting</Button>
    </StackPanel>
    ```

## <a name="implement-the-user-control"></a>Kullanıcı denetimi uygulama

1. XAML bölmesinde öğenin özniteliğine sağ tıklayın ve ardından `Click` Olay İşleyicisi'ne <xref:System.Windows.Controls.Button> **Git'e tıklayın.**

     Bu adım *MyControl.xaml.cs'yi* açar ve olay için bir saplama işleyicisi `Button_Click` oluşturur.

2. Aşağıdaki yönergeleri `using` dosyanın en üstüne ekleyin.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs" id="Snippet11":::

3. Aşağıdaki örnekte `SettingsStore` gösterildiği gibi özel bir özellik ekleyin.

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

     Bu özellik önce kullanıcı denetiminden Otomasyon nesne modelini içeren arabirime bir başvuru alır ve ardından arabirimin bir örneğini almak için <xref:EnvDTE80.DTE2> <xref:System.Windows.FrameworkElement.DataContext%2A> DTE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> kullanır. Ardından geçerli kullanıcı ayarlarını geri dönmek için bu örneği kullanır.

4. Olayı aşağıdaki `Button_Click` gibi doldurun.

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

     Bu, metin kutusunun içeriğini kayıt defterindeki "MySettings" koleksiyonunda bir "MySetting" alanına yazar. Koleksiyon yoksa oluşturulur.

5. Kullanıcı denetimi olayı için `OnLoaded` aşağıdaki işleyiciyi ekleyin.

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

6. Kullanıcı denetimi oluşturma.

7. içinde **Çözüm Gezgini** *source.extension.vsixmanifest .*

8. Bildirim düzenleyicisinde Ürün **Adı'Ayarlar** **Kaydet olarak ayarlayın.**

     Bu özellik, Başlangıç Sayfasının adını Seçenekler iletişim kutusundaki Başlangıç Sayfasını Özelleştir **listesinde** görünecek **şekilde** ayarlar.

9. *StartPage.xaml derlemesi.*

## <a name="test-the-control"></a>Denetimi test etmek

1. **F5 tuşuna basın.**

     Deneysel örnek Visual Studio açılır.

2. Deneysel örnekte, Araçlar menüsünde **Seçenekler'e** **tıklayın.**

3. Ortam **düğümünde** Başlangıç 'a **tıklayın** ve  ardından Başlangıç Sayfasını Özelleştir listesinde [Yüklü Uzantı] İlk Sayfamı **Kaydet'Ayarlar seçin.**

     **Tamam**'a tıklayın.

4. Açıksa Başlangıç Sayfasını kapatın ve görünüm menüsünde  Başlangıç Sayfası'a **tıklayın.**

5. Başlangıç Sayfasında, **MyControl sekmesine** tıklayın.

6. Metin kutusuna Cat yazın ve **Ardından** Ayarımı **Kaydet'e tıklayın.**

7. Başlangıç Sayfasını kapatın ve yeniden açın.

     Metin kutusunda "Cat" sözcüğü görüntüleniyor.

8. "Cat" sözcüğüni "Dog" sözcüğüyle değiştirin. Düğmeye tıklayın.

9. Başlangıç Sayfasını kapatın ve yeniden açın.

     Araç pencereleri kapatılana kadar araç pencerelerini bellekte tutarken ayarı kaydetmeseniz bile metin kutusunda "Köpek Visual Studio" sözcüğü Visual Studio görüntüleniyor.

10. Deneysel Visual Studio.

11. Deneysel örneği yeniden açmak için **F5** tuşuna basın.

12. Metin kutusunda "Cat" sözcüğü görüntüleniyor.

## <a name="next-steps"></a>Sonraki adımlar

Özelliği almak ve ayarlamak için farklı olay işleyicilerinden farklı değerler kullanarak istediğiniz sayıda özel ayarı kaydetmek ve almak için bu kullanıcı denetiminde değişiklik `SettingsStore` yapabilirsiniz. her çağrısı için farklı bir `propertyName` parametre <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> kullanırsınız, değerler kayıt defterinde birbirinin üzerine yazılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:EnvDTE80.DTE2?displayProperty=fullName>
- [Başlangıç Visual Studio komutlarını ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
