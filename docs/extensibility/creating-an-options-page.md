---
title: Seçenekler Sayfası Oluşturma | Microsoft Docs
description: Özellikleri incelemek ve ayarlamak için özellik kılavuzu kullanan basit bir Araçlar/Seçenekler sayfası oluşturma hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f7ff61649cfa9c2d78256751e9c25fb0a4b670bb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146088"
---
# <a name="create-an-options-page"></a>Seçenekler sayfası oluşturma

Bu kılavuz, özellikleri incelemek ve ayarlamak için bir özellik kılavuzu kullanan basit bir Araçlar/Seçenekler sayfası oluşturur.

 Bu özellikleri bir ayarlar dosyasına kaydetmek ve bir ayarlar dosyasından geri yüklemek için bu adımları izleyin ve ardından [bkz. Ayarlar kategorisi oluşturma.](../extensibility/creating-a-settings-category.md)

 MPF, Araçlar Seçenekleri sayfaları, sınıfı ve sınıfı oluşturmanıza yardımcı <xref:Microsoft.VisualStudio.Shell.Package> olmak için iki sınıf <xref:Microsoft.VisualStudio.Shell.DialogPage> sağlar. Sınıfını alt sınıfa göre sınıflandırarak bu sayfalar için kapsayıcı sağlamak için bir VSPackage `Package` oluşturun. Sınıftan türeterek her araç seçenekleri sayfasını `DialogPage` oluşturabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

 2015 Visual Studio den başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tools-options-grid-page"></a>Araç Seçenekleri kılavuz sayfası oluşturma

 Bu bölümde basit bir Araçlar Seçenekleri özellik kılavuzu oluşturacağız. Bir özelliğin değerini görüntülemek ve değiştirmek için bu kılavuzu kullanırsiniz.

### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>VSIX projesini oluşturmak ve bir VSPackage eklemek için

1. Her Visual Studio uzantısı, uzantı varlıklarını içeren bir VSIX dağıtım projesiyle başlar. adlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir VSIX projesi `MyToolsOptionsExtension` oluşturun. VSIX proje şablonunu New **Project** iletişim kutusunda "vsix" ifadesini arayarak bulabilirsiniz.

2. adlı bir Paket öğesi şablonu Visual Studio VSPackage `MyToolsOptionsPackage` ekleyin. Giriş **Çözüm Gezgini** proje düğümüne sağ tıklayın ve Yeni Öğe **Ekle'yi**  >  **seçin.** Yeni Öğe **Ekle iletişim kutusunda** Visual C# Öğeleri **Genişletilebilirliği'ne** gidin  >  **ve** Paketle'Visual Studio **seçin.** İletişim **kutusunun** altındaki Ad alanında dosya adını olarak `MyToolsOptionsPackage.cs` değiştirebilirsiniz. VSPackage oluşturma hakkında daha fazla bilgi için [bkz. VSPackage ile uzantı oluşturma.](../extensibility/creating-an-extension-with-a-vspackage.md)

### <a name="to-create-the-tools-options-property-grid"></a>Araçlar Seçenekleri özellik kılavuzu oluşturmak için

1. Kod *düzenleyicisinde MyToolsOptionsPackage* dosyasını açın.

2. Aşağıdaki using deyimini ekleyin.

   ```csharp
   using System.ComponentModel;
   ```

3. Bir sınıf `OptionPageGrid` bildirin ve sınıfından türetin. <xref:Microsoft.VisualStudio.Shell.DialogPage>

   ```csharp
   public class OptionPageGrid : DialogPage
   {  }
   ```

4. Sınıfa <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> `VSPackage` OptionPageGrid için bir seçenek kategorisi ve seçenekler sayfası adı atamak için sınıfına bir uygulama. Sonuç aşağıdaki gibi görünüyor olmalı:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [Guid(GuidList.guidMyToolsOptionsPkgString)]
    [ProvideOptionPage(typeof(OptionPageGrid),
        "My Category", "My Grid Page", 0, 0, true)]
    public sealed class MyToolsOptionsPackage : Package
    ```

5. sınıfına `OptionInteger` bir özellik `OptionPageGrid` ekleyin.

    - Özelliği bir <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> özellik kılavuzu kategorisine atamak için bir uygulama.

    - Özelliğine <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> bir ad atamak için bir uygulama.

    - özelliğine <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> bir açıklama atamak için bir uygulama.

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
    > varsayılan uygulaması, uygun dönüştürücülere sahip olan veya uygun dönüştürücülere sahip özelliklere genişletilebilir yapılar veya <xref:Microsoft.VisualStudio.Shell.DialogPage> diziler olan özellikleri destekler. Dönüştürücülerin listesi için bkz. ad <xref:System.ComponentModel> alanı.

6. Projeyi derleme ve hata ayıklamayı başlatma.

7. Deneysel Visual Studio Araçlar menüsünde **Seçenekler'e** **tıklayın.**

     Sol bölmede Kategorim'i **görüyor gerekir.** (Seçenekler kategorileri alfabetik sırada listelenmiştir, bu nedenle listenin yarısı kadar görünecektir.) **Kategorim'i açın** ve Ardından **Kılavuz Sayfam'a tıklayın.** Seçenekler kılavuzu sağ bölmede görünür. Özellik kategorisi **Seçeneklerim,** özellik adı ise Tamsayım **Seçeneği'dir.** Bölmenin alt **kısmında Tamsayım** seçeneği olan özellik açıklaması görüntülenir. İlk değeri olan 256 değerini başka bir değerle değiştirir. **Tamam'a** tıklayın ve sonra **Kılavuz Sayfam'ı yeniden açın.** Yeni değerin kalıcı olduğunu görüyorsunuz.

     Seçenekler sayfanız, Visual Studio kutusu aracılığıyla da kullanılabilir. IDE'nin üst kısmında bulunan arama  kutusuna Kategorim yazın. Sonuçlarda **Kategorim -> Kılavuzum Sayfası'nın** listelenmiş olduğunu görebilirsiniz.

## <a name="create-a-tools-options-custom-page"></a>Araç Seçenekleri özel sayfası oluşturma

 Bu bölümde, özel kullanıcı arabirimine sahip bir Araç Seçenekleri sayfası oluşturabilirsiniz. Bir özelliğin değerini görüntülemek ve değiştirmek için bu sayfayı kullanırsiniz.

1. Kod *düzenleyicisinde MyToolsOptionsPackage* dosyasını açın.

2. Aşağıdaki using deyimini ekleyin.

    ```csharp
    using System.Windows.Forms;
    ```

3. Sınıfın `OptionPageCustom` hemen öncesinde bir sınıf `OptionPageGrid` ekleyin. yeni sınıfını 'den `DialogPage` türetin.

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

5. <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>VSPackage sınıfına bir saniye uygulama. Bu öznitelik, sınıfa bir seçenek kategorisi ve seçenekler sayfası adı atar.

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

6. Projeye **MyUserControl adlı** yeni bir Kullanıcı Denetimi ekleyin.

7. Kullanıcı **denetimine** bir TextBox denetimi ekleyin.

     Özellikler **penceresinde,** araç çubuğunda Olaylar düğmesine tıklayın **ve** ardından Olayı bırak'a **çift** tıklayın. Yeni olay işleyicisi *MyUserControl.cs kodunda* görünür.

8. Denetim sınıfına bir genel alan, bir yöntem ekleyin ve seçenek değerini metin kutusunun içeriğine ayarlamak için `OptionsPage` `Initialize` olay işleyicisini güncelleştirin:

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

     alanı, `optionsPage` üst örnek için bir başvuru `OptionPageCustom` tutar. yöntemi `Initialize` `OptionString` TextBox içinde **görüntülenir.** Olay işleyicisi, odak **TextBox'dan** ayrıldığında `OptionString` TextBox'ın geçerli **değerini üzerine yazar.**

9. Paket kodu dosyasında, bir örneği oluşturmak, başlatmak ve dönmek üzere sınıfına özelliği `OptionPageCustom.Window` için bir geçersiz kılma `OptionPageCustom` `MyUserControl` ekleyin. Sınıf şimdi aşağıdaki gibi görünüyor:

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

10. Projeyi derleme ve çalıştırma.

11. Deneysel örnekte Araçlar **Seçenekleri'ne**  >  **tıklayın.**

12. Kategorimi **ve ardından** Özel **Sayfam'ı bulun.**

13. **OptionString değerini değiştirme.** **Tamam'a** tıklayın ve Özel **Sayfam'ı yeniden açın.** Yeni değerin kalıcı olduğunu görüyorsunuz.

## <a name="access-options"></a>Erişim seçenekleri

 Bu bölümde, ilişkili Araçlar Seçenekleri sayfasını barındıran VSPackage'dan bir seçeneğin değerini elde edebilirsiniz. Herhangi bir ortak özelliğin değerini almak için aynı teknik kullanılabilir.

1. Paket kodu **dosyasında, MyToolsOptionsPackage** sınıfına **OptionInteger** adlı bir genel özellik ekleyin.

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

     Bu kod, <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> örnek oluşturmak veya almak için `OptionPageGrid` çağrısında bulundu. `OptionPageGrid` genel <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> özellikler olan seçeneklerini yüklemek için çağrısında bulundu.

2. Şimdi değeri görüntülemek için **MyToolsOptionsCommand adlı özel** bir komut öğesi şablonu ekleyin. Yeni Öğe **Ekle iletişim kutusunda** Visual **C#**  >  **Genişletilebilirliği'ne** gidin ve Özel **Komut'ı seçin.** Pencerenin **altındaki** Ad alanında, komut dosyası adını *MyToolsOptionsCommand.cs olarak değiştirebilirsiniz.*

3. *MyToolsOptionsCommand* dosyasında, komutun yönteminin `ShowMessageBox` gövdesini aşağıdakiyle değiştirin:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));
    }

    ```

4. Projeyi derleme ve hata ayıklamayı başlatma.

5. Deneysel örnekte, Araçlar menüsünde, **MyToolsOptionsCommand'e tıklayın.** 

     Geçerli değerini görüntüleyen bir ileti `OptionInteger` kutusu.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler ve seçenekler sayfaları](../extensibility/internals/options-and-options-pages.md)
