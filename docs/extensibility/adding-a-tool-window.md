---
title: Araç penceresi ekleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 169f386128ccdd79aef6b90a6703f50323b9b6f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904138"
---
# <a name="add-a-tool-window"></a>Araç penceresi ekleme

Bu kılavuzda, bir araç penceresi oluşturmayı ve Visual Studio ile nasıl tümleştirileceğini aşağıdaki yollarla öğreneceksiniz:

- Araç penceresine bir denetim ekleyin.

- Araç penceresine bir araç çubuğu ekleyin.

- Araç çubuğuna bir komut ekleyin.

- Komutları uygulayın.

- Araç penceresi için varsayılan konumu ayarlayın.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio SDK, Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Araç penceresi oluşturma

1. VSıX şablonunu kullanarak **Firsttoolwin** adlı bir proje oluşturun ve **FirstToolWindow**adlı özel bir araç penceresi öğesi şablonu ekleyin.

    > [!NOTE]
    > Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Araç penceresine denetim ekleme

1. Varsayılan denetimi kaldırın. *FirstToolWindowControl. xaml* ' i açın ve **Click ' i silin!** tıklayın.

2. **Araç kutusunda** **tüm WPF denetimleri** bölümünü genişletin ve **medya öğesi** denetimini **FirstToolWindowControl** formuna sürükleyin. Denetimi seçin ve **Özellikler** penceresinde bu öğeyi **mediaElement1**olarak adlandırın.

## <a name="add-a-toolbar-to-the-tool-window"></a>Araç penceresine bir araç çubuğu ekleyin
Aşağıdaki şekilde bir araç çubuğu ekleyerek, degradelerinin ve renklerinin IDE 'nin geri kalanı ile tutarlı olmasını güvence altına alırsınız.

1. **Çözüm Gezgini**' de *FirstToolWindowPackage. vsct*öğesini açın. *. Vsct* dosyası, XML kullanarak araç pencerenizde grafik kullanıcı ARABIRIMI (GUI) öğelerini tanımlar.

2. `<Symbols>`Bölümünde `<GuidSymbol>` özniteliği olan düğümünü bulun `name` `guidFirstToolWindowPackageCmdSet` . `<IDSymbol>` `<IDSymbol>` Bir araç çubuğu ve bir araç çubuğu grubu tanımlamak için aşağıdaki iki öğeyi bu düğümdeki öğe listesine ekleyin.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Bölümünün hemen üzerinde `<Buttons>` `<Menus>` Şuna benzer bir bölüm oluşturun:

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Birçok farklı menü türü vardır. Bu menü, bir araç penceresinde özniteliği tarafından tanımlanan bir araç çubuğudur `type` . `guid`Ve `id` ayarları, araç çubuğunun tam nitelikli kimliğini yapar. Genellikle, `<Parent>` bir menü, içeren grubudur. Ancak, bir araç çubuğu kendi üst öğesi olarak tanımlanır. Bu nedenle, ve öğeleri için aynı tanımlayıcı kullanılır `<Menu>` `<Parent>` . `priority`Öznitelik yalnızca ' 0 '.

4. Araç çubukları birçok şekilde menülere benzer. Örneğin, tıpkı bir menü, komut gruplarına sahip olabileceğinden, araç çubuklarının grupları da olabilir. (Menülerde, komut grupları yatay çizgilerle ayrılır. Araç çubuklarında, gruplar görsel bölücüler tarafından ayrılmaz.)

    `<Groups>`Öğesi içeren bir bölüm ekleyin `<Group>` . Bu, KIMLIĞINI bölümünde bildirdiğiniz grubu tanımlar `<Symbols>` . Bölümü `<Groups>` bölümden hemen sonra ekleyin `<Menus>` .

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Ana GUID ve KIMLIĞI araç çubuğunun GUID 'sine ve KIMLIĞINE ayarlayarak, grubu araç çubuğuna eklersiniz.

## <a name="add-a-command-to-the-toolbar"></a>Araç çubuğuna komut ekleme

Araç çubuğuna düğme olarak görünen bir komut ekleyin.

1. `<Symbols>`Bölümünde, araç çubuğu ve araç çubuğu grup bildirimlerinin hemen ardından aşağıdaki IDSymbol öğelerini bildirin.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Bölümün içine bir Button öğesi ekleyin `<Buttons>` . Bu öğe, araç penceresindeki araç çubuğunda **arama** (Büyüteç Camı) simgesiyle görüntülenir.

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. *FirstToolWindowCommand.cs* ' i açın ve varolan alanlardan hemen sonra sınıfına aşağıdaki satırları ekleyin.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Bunu yaptığınızda, komutlarınız kodda kullanılabilir hale gelir.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>FirstToolWindowControl 'a MediaPlayer özelliği ekleyin
Araç çubuğu denetimlerinin olay işleyicilerinden, kodunuzun FirstToolWindowControl sınıfının bir alt öğesi olan Media Player denetimine erişebilmesi gerekir.

**Çözüm Gezgini**, *FirstToolWindowControl. xaml*öğesine sağ tıklayın, **kodu görüntüle**' ye tıklayın ve aşağıdaki kodu FirstToolWindowControl sınıfına ekleyin.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Araç penceresini ve araç çubuğunu oluşturma
**Dosya Aç** iletişim kutusunu çağıran ve seçilen medya dosyasını oynatan bir araç çubuğu ve bir menü komutu ekleyin.

1. *FirstToolWindow.cs* açın ve aşağıdaki yönergeleri ekleyin `using` :

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. FirstToolWindow sınıfının içinde, FirstToolWindowControl denetimine ortak bir başvuru ekleyin.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Oluşturucunun sonunda, bu denetim değişkenini yeni oluşturulan denetim olarak ayarlayın.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Oluşturucunun içindeki Araç çubuğunu oluşturun.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. Bu noktada, FirstToolWindow Oluşturucusu şöyle görünmelidir:

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Araç çubuğuna menü komutunu ekleyin. FirstToolWindowCommand.cs sınıfında, aşağıdaki using yönergesini ekleyin:

    ```csharp
    using System.Windows.Forms;
    ```

7. FirstToolWindowCommand sınıfında, ShowToolWindow () yönteminin sonuna aşağıdaki kodu ekleyin. ButtonHandler komutu sonraki bölümde uygulanacak.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Araç penceresinde bir menü komutu uygulamak için

1. FirstToolWindowCommand sınıfında **Dosya Aç** iletişim kutusunu çağıran bir ButtonHandler yöntemi ekleyin. Bir dosya seçildiğinde, medya dosyası oynatılır.

2. FirstToolWindowCommand sınıfında, FindToolWindow () yönteminde oluşturulan FirstToolWindow penceresine özel bir başvuru ekleyin.

    ```csharp
    private FirstToolWindow window;
    ```

3. Yukarıda tanımladığınız pencereyi ayarlamak için ShowToolWindow () yöntemini değiştirin (ButtonHandler komut işleyicisinin pencere denetimine erişebilmesi için). Burada, ShowToolWindow () yöntemi tamamlanmıştır.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. ButtonHandler metodunu ekleyin. Kullanıcının oynatacak medya dosyasını belirtmesi için bir OpenFileDialog oluşturur ve sonra seçili dosyayı yürütür.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Araç penceresi için varsayılan konumu ayarlama

Ardından, araç penceresi için IDE 'de varsayılan bir konum belirtin. Araç penceresi için yapılandırma bilgileri *FirstToolWindowPackage.cs* dosyasında bulunur.

1. *FirstToolWindowPackage.cs*Içinde, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> `FirstToolWindowPackage` FirstToolWindow türünü oluşturucuya geçiren sınıfında özniteliğini bulun. Varsayılan bir konum belirtmek için, aşağıdaki örnekteki oluşturucuya daha fazla parametre eklemeniz gerekir.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    İlk adlandırılmış parametre `Style` ve değeridir ve `Tabbed` Bu, pencerenin varolan bir pencerede bir sekme olacağı anlamına gelir. Yerleştirme konumu parametresi tarafından belirtilir `Window` , bu durum n **Çözüm Gezgini**GUID 'si.

    > [!NOTE]
    > IDE 'deki pencere türleri hakkında daha fazla bilgi için bkz <xref:EnvDTE.vsWindowType> ..

## <a name="test-the-tool-window"></a>Araç penceresini test etme

1. Visual Studio deneysel yapısının yeni bir örneğini açmak için **F5** tuşuna basın.

2. **Görünüm** menüsünde **diğer pencereler** ' in üzerine gelin ve ardından **ilk araç penceresi**' ne tıklayın.

    Media Player araç penceresi **Çözüm Gezgini**aynı konumda açılmalıdır. Daha önceki ile aynı konumda görünüyorsa pencere mizanpajını sıfırlayın (pencere **/pencere düzeni düzeni**).

3. Araç penceresinde ( **arama** simgesine sahiptir) düğmesine tıklayın. Desteklenen bir ses veya video dosyası seçin, örneğin *C:\Windows\Media\chimes.exe*, sonra **Aç**' a basın.

    CHIME sesini duymalısınız.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
