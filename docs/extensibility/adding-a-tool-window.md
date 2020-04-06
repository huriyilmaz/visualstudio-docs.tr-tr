---
title: Araç Penceresi Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740259"
---
# <a name="add-a-tool-window"></a>Araç penceresi ekleme

Bu izne bir araç penceresi oluşturmayı ve Visual Studio'ya nasıl entegre edilebilirsiniz:

- Araç penceresine bir denetim ekleyin.

- Araç penceresine araç çubuğu ekleyin.

- Araç çubuğuna bir komut ekleyin.

- Komutları uygulayın.

- Araç penceresi için varsayılan konumu ayarlayın.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio SDK, Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tool-window"></a>Araç penceresi oluşturma

1. VSIX şablonu kullanarak **FirstToolWin** adında bir proje oluşturun ve **FirstToolWindow**adlı özel bir araç penceresi öğesi şablonu ekleyin.

    > [!NOTE]
    > Araç penceresi yle uzantı oluşturma hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="add-a-control-to-the-tool-window"></a>Araç penceresine denetim ekleme

1. Varsayılan denetimi kaldırın. *FirstToolWindowControl.xaml'ı* açın ve **Beni Tıklayın'ı silin!** tıklayın.

2. Araç **kutusunda,** Tüm **WPF Denetimleri** bölümünü genişletin ve **Media Element** denetimini **FirstToolWindowControl** formuna sürükleyin. Denetimi seçin ve **Özellikler** penceresinde bu **öğeyi mediaElement1**olarak adlandırın.

## <a name="add-a-toolbar-to-the-tool-window"></a>Araç penceresine araç çubuğu ekleme
Aşağıdaki şekilde bir araç çubuğu ekleyerek, degradelerinin ve renklerinin IDE'nin geri kalanıyla tutarlı olduğunu garanti elabilirsiniz.

1. **Çözüm Explorer'** da *FirstToolWindowPackage.vsct'i*açın. *.vsct* dosyası, XML kullanarak araç pencerenizdeki grafik kullanıcı arabirimi (GUI) öğelerini tanımlar.

2. `<Symbols>` Bölümde, `<GuidSymbol>` özniteliği `name` `guidFirstToolWindowPackageCmdSet`. Bir araç `<IDSymbol>` çubuğu ve araç `<IDSymbol>` çubuğu grubu tanımlamak için bu düğümdeki öğeler listesine aşağıdaki iki öğeyi ekleyin.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. `<Buttons>` Bölümün hemen üstünde, `<Menus>` buna benzeyen bir bölüm oluşturun:

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

    Menü birkaç farklı türü vardır. Bu menü, özniteliğiyle `type` tanımlanan bir araç penceresindeki bir araç çubuğudur. Ve `guid` `id` ayarlar araç çubuğunun tam nitelikli kimliğini oluşturur. Genellikle, `<Parent>` bir menünün içeren grubudur. Ancak, bir araç çubuğu kendi üst olarak tanımlanır. Bu nedenle, aynı tanımlayıcı `<Menu>` ve `<Parent>` öğeler için kullanılır. Öznitelik `priority` sadece '0'dır.

4. Araç çubukları menülere birçok yönden benzer. Örneğin, bir menünün komut grupları olabileceği gibi, araç çubuklarının da grupları olabilir. (Menülerde komut grupları yatay çizgilerle ayrılır. Araç çubuklarında gruplar görsel bölücüler tarafından ayrılmaz.)

    Öğe `<Groups>` içeren bir `<Group>` bölüm ekleyin. Bu, `<Symbols>` bölümde kimliğini beyan ettiğiniz grubu tanımlar. `<Menus>` Bölümden `<Groups>` hemen sonra bölümü ekleyin.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Üst GUID ve Kimliğini araç çubuğunun GUID ve kimliğine ayarlayarak grubu araç çubuğuna eklersiniz.

## <a name="add-a-command-to-the-toolbar"></a>Araç çubuğuna komut ekleme

Düğme olarak görüntülenen araç çubuğuna bir komut ekleyin.

1. `<Symbols>` Bölümde, araç çubuğu ve araç çubuğu grup bildirimlerinden hemen sonra aşağıdaki IDSymbol öğelerini bildirin.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. `<Buttons>` Bölümün içine bir Düğme öğesi ekleyin. Bu öğe, araç penceresindeki araç çubuğunda **arama** (büyüteç) simgesiyle görünür.

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

3. *FirstToolWindowCommand.cs* açın ve varolan alanlardan hemen sonra sınıfa aşağıdaki satırları ekleyin.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Bunu yapmak, komutlarınızı kod olarak kullanılabilir hale getirir.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>FirstToolWindowControl'e MediaPlayer özelliği ekleme
Araç çubuğu denetimleri için olay işleyicilerinden, kodunuz FirstToolWindowControl sınıfının bir alt parçası olan Media Player denetimine erişebilmeli.

**Solution**Explorer'da, *FirstToolWindowControl.xaml'ı*sağ tıklatın, **Kodu Görüntüle'yi**tıklatın ve FirstToolWindowControl sınıfına aşağıdaki kodu ekleyin.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Araç penceresini ve araç çubuğunu anında
**Dosya aç** iletişim kutusunu çağıran ve seçili ortam dosyasını çalan bir araç çubuğu ve menü komutu ekleyin.

1. *açık FirstToolWindow.cs* ve `using` aşağıdaki yönergeleri ekleyin:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. FirstToolWindow sınıfının içinde, FirstToolWindowControl denetimine genel bir başvuru ekleyin.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Oluşturucunun sonunda, bu denetim değişkenini yeni oluşturulan denetime ayarlayın.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Araç çubuğunu oluşturucunun içindeki anında girin.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. Bu noktada, FirstToolWindow oluşturucu su şuna görünmelidir:

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

6. Menü komutunu araç çubuğuna ekleyin. FirstToolWindowCommand.cs sınıfında aşağıdaki yönergeleri ekleyin:

    ```csharp
    using System.Windows.Forms;
    ```

7. FirstToolWindowCommand sınıfında, ShowToolWindow() yönteminin sonuna aşağıdaki kodu ekleyin. ButtonHandler komutu sonraki bölümde uygulanacaktır.

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

1. FirstToolWindowCommand sınıfında, **Dosyaaç** iletişim kutusunu çağıran bir ButtonHandler yöntemi ekleyin. Bir dosya seçildiğinde, ortam dosyasını çalar.

2. FirstToolWindowCommand sınıfında, FindToolWindow() yönteminde oluşturulan FirstToolWindow penceresine özel bir başvuru ekleyin.

    ```csharp
    private FirstToolWindow window;
    ```

3. Yukarıda tanımladığınız pencereyi ayarlamak için ShowToolWindow() yöntemini değiştirin (böylece ButtonHandler komut işleyicisi pencere denetimine erişebilir. Burada tam ShowToolWindow() yöntemidir.

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

4. ButtonHandler yöntemini ekleyin. Kullanıcının oynatılacağı ortam dosyasını belirtmesi için bir OpenFileDialog oluşturur ve seçili dosyayı çalar.

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

Ardından, araç penceresi için IDE'de varsayılan bir konum belirtin. Araç penceresinin yapılandırma bilgileri *FirstToolWindowPackage.cs* dosyasındadır.

1. *FirstToolWindowPackage.cs,* firsttoolwindow türünü `FirstToolWindowPackage` oluşturucuya geçen sınıftaki özniteliği bulun. <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> Varsayılan bir konum belirtmek için, aşağıdaki örnekte oluşturucuya daha fazla parametre eklemeniz gerekir.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    İlk adlandırılmış parametre `Style` ve `Tabbed`değeri , pencere varolan bir pencerede bir sekme olacağı anlamına gelir. Yerleştirme konumu `Window` parametre ile belirtilir, n bu durumda, **Çözüm Gezgini**GUID .

    > [!NOTE]
    > IDE'deki pencere türleri hakkında daha fazla <xref:EnvDTE.vsWindowType>bilgi için bkz.

## <a name="test-the-tool-window"></a>Araç penceresini test edin

1. Visual Studio deneysel yapının yeni bir örneğini açmak için **F5** tuşuna basın.

2. **Görünüm** menüsünde, **Diğer Windows'u** işaret edin ve ardından İlk **Araç Penceresi'ni**tıklatın.

    Media player araç penceresi **Solution Explorer**ile aynı konumda açılmalıdır. Hala eskisi gibi aynı konumda görünüyorsa, pencere düzenini sıfırla (**Pencere / Pencere Düzenini Sıfırla).**

3. Araç penceresindeki düğmeyi **(Arama** simgesi vardır) tıklatın. Desteklenen bir ses veya video dosyası seçin, örneğin, *C:\windows\media\chimes.wav*, sonra **Aç**tuşuna basın.

    Çan sesini duymalısın.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
