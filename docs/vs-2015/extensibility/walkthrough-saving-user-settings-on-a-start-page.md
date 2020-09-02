---
title: 'İzlenecek yol: bir başlangıç sayfasına kullanıcı ayarlarını kaydetme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8976d329f6303d60cc00609bc9ed9471456c1b63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837687"
---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>İzlenecek Yol: Kullanıcı Ayarlarını Başlangıç Sayfasına Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Başlangıç sayfanız için Kullanıcı ayarlarını kalıcı hale getirebilirsiniz. Bu izlenecek yolu izleyerek, Kullanıcı bir düğmeye tıkladığında kayıt defterine bir ayar kaydeden ve sonra başlangıç sayfası her yüklendiğinde bu ayarı alan bir denetim oluşturabilirsiniz. Başlangıç sayfası proje şablonu özelleştirilebilir bir kullanıcı denetimi içerdiğinden ve varsayılan başlangıç sayfası XAML bu denetimi çağırırsa, başlangıç sayfasının kendisini değiştirmek zorunda değilsiniz.  
  
 Bu izlenecek yolda oluşturulan ayarlar deposu, bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore> arabirimin örneğidir ve çağrıldığında aşağıdaki kayıt defteri konumunu okur ve yazar: Hkcu\software\microsoft\visualstudio\14.exe \\ *CollectionName*  
  
 Visual Studio 'nun deneysel örneğinde çalışırken, ayarlar deposu HKCU\Software\Microsoft\VisualStudio\14.0Exp \\ *ToplamaAdı* ' na okur ve yazar.  
  
 Ayarları kalıcı hale getirme hakkında daha fazla bilgi için bkz. [Kullanıcı ayarlarını ve seçeneklerini genişletme](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
  
> [!NOTE]
> Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).  
>   
> **Uzantı Yöneticisi**' ni kullanarak başlangıç sayfası proje şablonunu indirebilirsiniz.  
  
## <a name="setting-up-the-project"></a>Projeyi ayarlama  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Projeyi Bu izlenecek yol için yapılandırmak için  
  
1. Başlangıç sayfası proje şablonunu kullanarak, [kendi başlangıç sayfanızı oluşturma](../misc/creating-your-own-start-page.md)bölümünde açıklandığı gibi bir başlangıç sayfası projesi oluşturun. Projeyi **SaveMySettings**olarak adlandırın.  
  
2. **Çözüm Gezgini**' de, StartPageControl projesine aşağıdaki derleme başvurularını ekleyin:  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft. VisualStudio. OLE. Interop  
  
    - Microsoft. VisualStudio. Shell. Interop. 11.0  
  
3. MyControl. xaml ' i açın.  
  
4. XAML bölmesinden, en üst düzey <xref:System.Windows.Controls.UserControl> öğe tanımında, ad alanı bildirimlerinden sonra aşağıdaki olay bildirimini ekleyin.  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5. Tasarım bölmesinde, denetimin ana alanına tıklayın ve ardından SIL ' e basın.  
  
     Bu, <xref:System.Windows.Controls.Border> öğeyi ve içindeki her şeyi kaldırır ve yalnızca en üst düzey <xref:System.Windows.Controls.Grid> öğeyi bırakır.  
  
6. **Araç kutusundan**bir <xref:System.Windows.Controls.StackPanel> denetimi kılavuza sürükleyin.  
  
7. Şimdi bir <xref:System.Windows.Controls.TextBlock> , a <xref:System.Windows.Controls.TextBox> ve bir düğmesini öğesine sürükleyin <xref:System.Windows.Controls.StackPanel> .  
  
8. Aşağıdaki örnekte gösterildiği gibi, için bir **X:Name** özniteliği <xref:System.Windows.Controls.TextBox> ve `Click` için bir olay ekleyin <xref:System.Windows.Controls.Button> .  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Kullanıcı denetimini uygulama  
  
#### <a name="to-implement-the-user-control"></a>Kullanıcı denetimini uygulamak için  
  
1. XAML bölmesinde, `Click` öğesinin özniteliğini sağ tıklatın <xref:System.Windows.Controls.Button> ve ardından **olay işleyicisine git**' i tıklatın.  
  
     Bu, MyControl.xaml.cs açar ve olay için bir saplama işleyicisi oluşturur `Button_Click` .  
  
2. Aşağıdaki `using` deyimlerini dosyanın en üstüne ekleyin.  
  
     [!code-csharp[StartPageDTE#11](../snippets/csharp/VS_Snippets_VSSDK/startpagedte/cs/startpagecontrol/mycontrol.xaml.cs#11)]  
  
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
  
     Bu, metin kutusunun metnini "MySetting" öğesinin geçerli değerine ayarlar.  
  
6. Kullanıcı denetimini oluşturun.  
  
7. **Çözüm Gezgini**, kaynak. Extension. valtmanifest ' i açın.  
  
8. Bildirim düzenleyicisinde, **ürün adı** ' nı ayarlarımı **Kaydet başlangıç sayfası**olarak ayarlayın.  
  
     Bu, başlangıç sayfasının adını **Seçenekler** Iletişim kutusundaki **Başlangıç sayfası Özelleştir** listesinde görünecek şekilde ayarlar.  
  
9. Build StartPage. xaml.  
  
## <a name="testing-the-control"></a>Denetimi test etme  
  
#### <a name="to-test-the-user-control"></a>Kullanıcı denetimini test etmek için  
  
1. F5 tuşuna basın.  
  
     Visual Studio 'nun deneysel örneği açılır.  
  
2. Deneysel örnekte, **Araçlar** menüsünde **Seçenekler**' e tıklayın.  
  
3. **Ortam** düğümünde, **Başlangıç**' a tıklayın ve ardından **Başlangıç sayfası Özelleştir** listesinde **[yüklü uzantı] Ayarlarımı Kaydet başlangıç sayfası**' nı seçin.  
  
     **Tamam**’a tıklayın.  
  
4. Açık ise başlangıç sayfasını kapatın ve ardından **Görünüm** menüsünde, **Başlangıç sayfası**' nı tıklatın.  
  
5. Başlangıç sayfasında, **MyControl** sekmesine tıklayın.  
  
6. Metin kutusuna **Cat**yazın ve sonra **ayarımı kaydet**' e tıklayın.  
  
7. Başlangıç sayfasını kapatın ve yeniden açın.  
  
     "Cat" sözcüğünün metin kutusunda görüntülenmesi gerekir.  
  
8. "Cat" sözcüğünü "köpek" kelimesiyle değiştirin. Düğmeye tıklamayın.  
  
9. Başlangıç sayfasını kapatın ve yeniden açın.  
  
     "Köpek" sözcüğünün, ayar kaydedilmese bile metin kutusunda görüntülenmesi gerekir. Bunun nedeni, Visual Studio 'nun, kapalı olsalar bile, Visual Studio 'Nun kendisi kapatılana kadar, araç pencerelerini bellekte tutmasından kaynaklanır.  
  
10. Visual Studio 'nun Deneysel örneğini kapatın.  
  
11. Deneysel örneği yeniden açmak için F5 'e basın.  
  
12. "Cat" sözcüğünün metin kutusunda görüntülenmesi gerekir.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Özelliği almak ve ayarlamak için farklı olay işleyicilerinden farklı değerler kullanarak istediğiniz sayıda özel ayarı kaydetmek ve almak üzere bu kullanıcı denetimini değiştirebilirsiniz `SettingsStore` . `propertyName`Her çağrısı için farklı bir parametre kullandığınız sürece <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A> , değerler kayıt defterindeki bir diğerinin üzerine yazmaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:EnvDTE80.DTE2?displayProperty=fullName>   
 [Kendi başlangıç sayfanızı oluşturma](../misc/creating-your-own-start-page.md)   
 [Başlangıç Sayfasına Visual Studio Komutları Ekleme](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
