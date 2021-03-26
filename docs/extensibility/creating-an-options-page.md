---
title: Seçenekler sayfası oluşturma | Microsoft Docs
description: Özellikleri incelemek ve ayarlamak için özellik kılavuzunu kullanan basit bir Araçlar/Seçenekler sayfası oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb94554b4ac1af30d8187a8ab75aa83f65dccc72
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055810"
---
# <a name="create-an-options-page"></a>Seçenekler sayfası oluşturma

Bu izlenecek yol, özellikleri incelemek ve ayarlamak için özellik kılavuzunu kullanan basit bir Araçlar/Seçenekler sayfası oluşturur.

 Bu özellikleri kaydetmek ve bir ayarlar dosyasından geri yüklemek için, bu adımları izleyin ve ardından [bir ayar oluştur kategorisi](../extensibility/creating-a-settings-category.md)' ne bakın.

 MPF, araç seçenekleri sayfaları, sınıfı ve sınıfı oluşturmanıza yardımcı olmak için iki sınıf sağlar <xref:Microsoft.VisualStudio.Shell.Package> <xref:Microsoft.VisualStudio.Shell.DialogPage> . Bu sayfalar için altsınıflama sınıfının kapsayıcısını sağlamak üzere bir VSPackage oluşturun `Package` . Her bir araç seçenekleri sayfasını sınıfından türeterek oluşturursunuz `DialogPage` .

## <a name="prerequisites"></a>Önkoşullar

 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tools-options-grid-page"></a>Araç seçenekleri kılavuz sayfası oluşturma

 Bu bölümde, basit bir Araçlar Seçenekler özellik Kılavuzu oluşturursunuz. Bir özelliğin değerini göstermek ve değiştirmek için bu kılavuzu kullanın.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSıX projesi oluşturmak ve bir VSPackage eklemek için

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSıX dağıtım projesiyle başlar. Adlı bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projesi oluşturun `MyToolsOptionsExtension` . "VSIX" araması yaparak VSıX proje şablonunu **Yeni proje** iletişim kutusunda bulabilirsiniz.

2. Adlı bir Visual Studio paket öğesi şablonu ekleyerek VSPackage ekleyin `MyToolsOptionsPackage` . **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle iletişim kutusunda** **Visual C# öğeleri**  >  **genişletilebilirliği** ' ne gidin ve **Visual Studio paketi**' ni seçin. İletişim kutusunun alt kısmındaki **ad** alanında, dosya adını olarak değiştirin `MyToolsOptionsPackage.cs` . VSPackage oluşturma hakkında daha fazla bilgi için bkz. [VSPackage ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-vspackage.md).

### <a name="to-create-the-tools-options-property-grid"></a>Araç seçenekleri özellik kılavuzunu oluşturmak için

1. Kod düzenleyicisinde *Myaraçları Optionspackage* dosyasını açın.

2. Aşağıdaki using ifadesini ekleyin.

   ```csharp
   using System.ComponentModel;
   ```

3. Bir `OptionPageGrid` sınıf bildirin ve öğesinden türetirsiniz <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> `VSPackage` OptionPageGrid için bir seçenek kategorisi ve Seçenekler sayfa adı sınıfına atamak üzere sınıfına bir uygulayın. Sonuç şöyle görünmelidir:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. Sınıfına bir `OptionInteger` özellik ekleyin `OptionPageGrid` .

    - Property <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> Grid kategorisi özelliğine atamak için bir uygulayın.

    - <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName>Özelliğe bir ada atamak için bir uygulayın.

    - Bir <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> Açıklama özelliğine atamak için bir uygulayın.

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
    > Varsayılan uygulama, <xref:Microsoft.VisualStudio.Shell.DialogPage> uygun dönüştürücüleri olan veya uygun Dönüştürücülerine sahip özelliklere genişletilebilen yapılar veya diziler olan özellikleri destekler. Dönüştürücülerin listesi için bkz <xref:System.ComponentModel> . ad alanı.

6. Projeyi derleyin ve hata ayıklamayı başlatın.

7. Visual Studio 'nun deneysel örneğinde, **Araçlar** menüsünde **Seçenekler**' e tıklayın.

     Sol bölmede **kategorim**' i görmeniz gerekir. (Seçenek kategorileri alfabetik sırada listelenmiştir, bu nedenle listenin alt yarısında ilgili görünmelidir.) **Kategorim** ' i açın ve **kılavuz sayfam**' ı tıklatın. Seçenekler Kılavuzu sağ bölmede görüntülenir. Özellik kategorisi **My seçeneklerim** ve özellik adı My **Integer seçeneğim**. Özellik açıklaması, **tamsayı seçeneği**, bölmenin en altında görünür. Değeri ilk 256 olan başlangıç değerinden başka bir şeye değiştirin. **Tamam**' a tıklayın ve sonra **kılavuz sayfamı** yeniden açın. Yeni değerin devam etmediğini görebilirsiniz.

     Seçenekler sayfanız, Visual Studio 'nun arama kutusu aracılığıyla da kullanılabilir. IDE 'nin üst kısmındaki arama kutusuna **kategorim** yazın ve **kategorim > kılavuz** sayfam sonuçlar bölümünde listelenmiş olarak görürsünüz.

## <a name="create-a-tools-options-custom-page"></a>Araç seçenekleri özel sayfası oluşturma

 Bu bölümde, Özel Kullanıcı arabirimine sahip bir araç seçenekleri sayfası oluşturacaksınız. Bir özelliğin değerini göstermek ve değiştirmek için bu sayfayı kullanın.

1. Kod düzenleyicisinde *Myaraçları Optionspackage* dosyasını açın.

2. Aşağıdaki using ifadesini ekleyin.

    ```csharp
    using System.Windows.Forms;
    ```

3. `OptionPageCustom`Sınıfından hemen önce bir sınıf ekleyin `OptionPageGrid` . Yeni sınıfını öğesinden türet `DialogPage` .

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

4. Bir GUID özniteliği ekleyin. Bir OptionString özelliği ekleyin:

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

5. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>VSPackage sınıfına bir saniye uygulayın. Bu öznitelik bir seçenek kategorisi ve Seçenekler sayfası adı sınıfına atar.

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

6. Projeye MyUserControl adlı yeni bir **Kullanıcı denetimi** ekleyin.

7. Kullanıcı denetimine **TextBox** denetimi ekleyin.

     **Özellikler** penceresinde, araç çubuğunda, **Olaylar** düğmesine tıklayın ve ardından **bırak** olayına çift tıklayın. Yeni olay işleyicisi *MyUserControl. cs* kodunda görünür.

8. `OptionsPage`Denetim sınıfına bir genel alan, bir `Initialize` yöntemi ekleyin ve olay işleyicisini, seçenek değerini metin kutusunun içeriğine ayarlamak için güncelleştirin:

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

     `optionsPage`Alan, üst örneğe bir başvuru içerir `OptionPageCustom` . `Initialize`Yöntemi `OptionString` **TextBox** içinde görüntülenir. Olay **işleyicisi TextBox 'ın** geçerli değerini `OptionString` odak **kutusu** dışına çıktığında içine yazar.

9. Paket kodu dosyasında, `OptionPageCustom.Window` `OptionPageCustom` bir örneği oluşturmak, başlatmak ve döndürmek için sınıfına özelliği için bir geçersiz kılma ekleyin `MyUserControl` . Sınıf şu şekilde görünmelidir:

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

10. Projeyi derleyin ve çalıştırın.

11. Deneysel örnekte **Araçlar**  >  **Seçenekler**' e tıklayın.

12. **Kategorumu** ve sonra **özel sayfamı** bul.

13. **OptionString** değerini değiştirin. **Tamam**' a tıklayın ve ardından **özel sayfamı** yeniden açın. Yeni değerin kalıcı olduğunu görebilirsiniz.

## <a name="access-options"></a>Erişim seçenekleri

 Bu bölümde, bir seçeneğin değerini, ilişkili Araçlar Seçenekler sayfasını barındıran VSPackage öğesinden alırsınız. Herhangi bir ortak özelliğin değerini elde etmek için aynı teknik de kullanılabilir.

1. Paket kodu dosyasında, **Myaraçları Optionspackage** sınıfına **optioninteger** adlı bir public özelliği ekleyin.

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

     Bu kod, <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> bir örnek oluşturmak veya almak için çağırır `OptionPageGrid` . `OptionPageGrid`<xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A>Genel Özellikler olan seçeneklerini yüklemek için çağırır.

2. Şimdi değeri göstermek için **Myaraçları SeçenekAdı komutu** adlı özel bir komut öğesi şablonu ekleyin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#**  >  **genişletilebilirliği** ' ne gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *Myaraçları SeçenekAdı komut. cs* olarak değiştirin.

3. *Myaraçları seçenekleri komut* dosyasında, komut `ShowMessageBox` yönteminin gövdesini aşağıdaki şekilde değiştirin:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Projeyi derleyin ve hata ayıklamayı başlatın.

5. Deneysel örnekte, Araçlar menüsünde, **Myaraçlarý Options komutunu çağır**' a tıklayın. 

     Geçerli değerini görüntüleyen bir ileti kutusu `OptionInteger` .

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler ve Seçenekler sayfaları](../extensibility/internals/options-and-options-pages.md)
