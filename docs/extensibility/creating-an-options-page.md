---
title: Seçenekler Sayfası Oluşturma | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1607af2a6f68bd5593f9a185188b25b364926fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739522"
---
# <a name="create-an-options-page"></a>Seçenekler sayfası oluşturma

Bu izne, özellikleri incelemek ve ayarlamak için bir özellik ızgarası kullanan basit bir Araçlar/Seçenekler sayfası oluşturur.

 Bu özellikleri bir ayarlar dosyasına kaydetmek ve geri yüklemek için aşağıdaki adımları izleyin ve ardından [ayarlar kategorisi oluştur'a](../extensibility/creating-a-settings-category.md)bakın.

 MPF, Araçlar Seçenekleri sayfaları, <xref:Microsoft.VisualStudio.Shell.Package> sınıf ve <xref:Microsoft.VisualStudio.Shell.DialogPage> sınıf oluşturmanıza yardımcı olacak iki sınıf sağlar. `Package` Sınıfı alt sınıflayarak bu sayfalar için bir kapsayıcı sağlamak için bir VSPackage oluşturursunuz. `DialogPage` Sınıftan türeyen her araç seçenekleri sayfasını oluşturursunuz.

## <a name="prerequisites"></a>Ön koşullar

 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tools-options-grid-page"></a>Araç Seçenekleri ızgara sayfası oluşturma

 Bu bölümde, basit bir Araç Seçenekleri özellik ızgarası oluşturursunuz. Bu ızgarayı, bir özelliğin değerini görüntülemek ve değiştirmek için kullanırsınız.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSIX projesini oluşturmak ve bir VSPackage eklemek için

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. Adlı `MyToolsOptionsExtension` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.

2. Adlı `MyToolsOptionsPackage`bir Visual Studio Package öğe şablonu ekleyerek bir VSPackage ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** > seçin. Yeni **Öğe Ekle iletişim kutusunda,** **Visual C# Items** > **Extensibility'e** gidin ve **Visual Studio Paketi'ni**seçin. İletişim kutusunun altındaki **Ad** alanında, dosya adını ' `MyToolsOptionsPackage.cs`da ' olarak değiştirin VSPackage nasıl oluşturulacak hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-vspackage.md)

### <a name="to-create-the-tools-options-property-grid"></a>Araçlar Seçenekleri özellik ızgarasını oluşturmak için

1. Kod düzenleyicisinde *MyToolsOptionsPackage* dosyasını açın.

2. Aşağıdaki ifadesini kullanarak ifadesini ekleyin.

   ```csharp
   using System.ComponentModel;
   ```

3. Bir `OptionPageGrid` sınıf bildirin ve <xref:Microsoft.VisualStudio.Shell.DialogPage>ondan türetin.

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Class'a `VSPackage` OptionPageGrid için seçenekler kategorisi ve seçenekler sayfa adı atamak için sınıfa bir <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> uygulama. Sonuç şu şekilde görünmelidir:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Sınıfa `OptionInteger` `OptionPageGrid` bir özellik ekleyin.

    - Özellik <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> ızgara kategorisi atamak için a uygulayın.

    - Bir <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> ad atamak için bir özellik uygulayın.

    - Bir <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> açıklama özelliği atamak için a uygulayın.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;

        [Category("My Category")]
        [DisplayName("My Integer Option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
    }
    ```

    > [!NOTE]
    > Varsayılan uygulama, <xref:Microsoft.VisualStudio.Shell.DialogPage> uygun dönüştürücülere sahip veya uygun dönüştürücülere sahip özelliklere genişletilebilen yapılar veya diziler olan özellikleri destekler. Dönüştürücülerin listesi için <xref:System.ComponentModel> ad alanına bakın.

6. Projeyi oluşturun ve hata ayıklamaya başlayın.

7. Visual Studio'nun deneysel örneğinde, **Araçlar** menüsünde **Seçenekler'i**tıklatın.

     Sol bölmede, **Benim Kategorim'i**görmelisiniz. (Seçenekler kategorileri alfabetik sırada listelenir, bu nedenle listenin yarısında niçin görünmesi gerekir.) **Kategorimi** açın ve Ardından **Izgara Sayfamı**tıklatın. Seçenekler ızgarası sağ bölmede görünür. Özellik kategorisi **Seçeneklerim,** özellik adı ise **Myteger Seçeneğidir.** Özellik açıklaması, **Tamsayı seçeneğim,** bölmenin alt kısmında görünür. Değeri ilk değeri olan 256'dan başka bir şeye değiştirin. **Tamam'ı**tıklatın ve ardından **Izgara Sayfamı**yeniden açın. Yeni değerin devam ettiğini görebilirsiniz.

     Seçenekler sayfanıza Visual Studio'nun arama kutusundan da ulaşabilirsiniz. IDE'nin üst kısmındaki arama kutusunda **Kategorim'i** yazın ve sonuçları listelenmiş **Kategorim -> Izgaram Sayfam'ı** görürsünüz.

## <a name="create-a-tools-options-custom-page"></a>Araç Seçenekleri özel sayfası oluşturma

 Bu bölümde, özel bir kullanıcı arama aracı içeren bir Araç Seçenekleri sayfası oluşturursunuz. Bu sayfayı bir özelliğin değerini görüntülemek ve değiştirmek için kullanırsınız.

1. Kod düzenleyicisinde *MyToolsOptionsPackage* dosyasını açın.

2. Aşağıdaki ifadesini kullanarak ifadesini ekleyin.

    ```csharp
    using System.Windows.Forms;
    ```

3. Sınıftan `OptionPageCustom` `OptionPageGrid` hemen önce bir sınıf ekleyin. Yeni sınıfı `DialogPage`türetin.

    ```csharp
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

4. GUID özniteliği ekleyin. OptionString özelliği ekleyin:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }
    }
    ```

5. VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> sınıfına ikinci bir uygulama uygulayın. Bu öznitelik sınıfa bir seçenek kategorisi ve seçenekler sayfa adı atar.

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    [ProvideOptionPage(typeof(OptionPageCustom),
        "My Category", "My Custom Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

6. Projeye MyUserControl adlı yeni bir **Kullanıcı Denetimi** ekleyin.

7. Kullanıcı denetimine **TextBox** denetimi ekleyin.

     **Özellikler** penceresinde, araç çubuğunda, **Etkinlikler** düğmesini tıklatın ve ardından **Bırak** olayını çift tıklatın. Yeni olay işleyicisi *MyUserControl.cs* kodunda görünür.

8. Ortak `OptionsPage` alan, denetim `Initialize` sınıfına bir yöntem ekleyin ve metin kutusunun içeriğine seçenek değerini ayarlamak için olay işleyicisini güncelleştirin:

    ```csharp
    public partial class MyUserControl : UserControl
    {
        public MyUserControl()
        {
            InitializeComponent();
        }

        internal OptionPageCustom optionsPage;

        public void Initialize()
        {
            textBox1.Text = optionsPage.OptionString;
        }

        private void textBox1_Leave(object sender, EventArgs e)
        {
            optionsPage.OptionString = textBox1.Text;
        }
    }
    ```

     Alan, `optionsPage` üst `OptionPageCustom` örneğin referansını tutar. Yöntem `Initialize` `OptionString` **TextBox'ta**görüntülenir. Olay işleyicisi, **textbox'ın** geçerli `OptionString` değerini odak **TextBox'tan**ayrıldığında yazar.

9. Paket kodu dosyasında, bir örneğini `OptionPageCustom.Window` `MyUserControl`oluşturmak, `OptionPageCustom` başlatmak ve döndürmek için sınıfa özellik için geçersiz kılma ekleyin Sınıf şimdi şuna benzemeli:

    ```csharp
    [Guid("00000000-0000-0000-0000-000000000000")]
    public class OptionPageCustom : DialogPage
    {
        private string optionValue = "alpha";

        public string OptionString
        {
            get { return optionValue; }
            set { optionValue = value; }
        }

        protected override IWin32Window Window
        {
            get
            {
                MyUserControl page = new MyUserControl();
                page.optionsPage = this;
                page.Initialize();
                return page;
            }
        }
    }
    ```

10. Projeyi oluşturun ve çalıştırın.

11. Deneme örneğinde, **Araç** > **Seçenekleri'ni**tıklatın.

12. **Kategorimi** ve ardından **Özel Sayfamı**bulun.

13. **OptionString**değerini değiştirin. **Tamam'ı**tıklatın ve ardından **Özel Sayfamı**yeniden açın. Yeni değerin devam ettiğini görebilirsiniz.

## <a name="access-options"></a>Erişim seçenekleri

 Bu bölümde, ilişkili Araçlar Seçenekleri sayfasını barındıran VSPackage'dan bir seçeneğin değerini alırsınız. Aynı teknik herhangi bir kamu malı değerini elde etmek için kullanılabilir.

1. Paket kodu dosyasında, **MyToolsOptionsPackage** sınıfına **OptionInteger** adlı bir kamu malı ekleyin.

    ```csharp
    public int OptionInteger
    {
        get
        {
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));
            return page.OptionInteger;
        }
    }

    ```

     Bu kod, bir <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> `OptionPageGrid` örnek oluşturmak veya almak için çağırır. `OptionPageGrid`kamu <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> malları olan seçeneklerini yüklemek için çağırır.

2. Şimdi değeri görüntülemek için **MyToolsOptionsCommand** adlı özel bir komut öğesi şablonu ekleyin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C#** > **Genişletilebilirlik'e** gidin ve **Özel Komut'u**seçin. Pencerenin altındaki **Ad** alanında komut dosyası adını *MyToolsOptionsCommand.cs*olarak değiştirin.

3. *MyToolsOptionsCommand* dosyasında, komut `ShowMessageBox` yönteminin gövdesini aşağıdakilerle değiştirin:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Projeyi oluşturun ve hata ayıklamaya başlayın.

5. Deneysel örnekte, **Araçlar** menüsünde **MyToolsOptionsCommand'ı çağır'ı**tıklatın.

     İleti kutusu geçerli değerini `OptionInteger`görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler ve seçenekler sayfaları](../extensibility/internals/options-and-options-pages.md)
