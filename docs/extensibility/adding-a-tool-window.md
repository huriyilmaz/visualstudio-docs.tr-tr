---
title: Araç Penceresi Ekleme | Microsoft Docs
description: Araç penceresi oluşturma ve araç penceresine Visual Studio içeren bir araç çubuğu ekleyerek bu pencereyi araç penceresiyle tümleştirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1ca15236ee7a077a79308b46f9f4a57f43ee3e295cda9ca6694d0af23a89ce5f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434990"
---
# <a name="add-a-tool-window"></a>Araç penceresi ekleme

Bu kılavuzda bir araç penceresi oluşturma ve bunu aşağıdaki yollarla Visual Studio ile tümleştirebilirsiniz:

- Araç penceresine bir denetim ekleyin.

- Araç penceresine araç çubuğu ekleyin.

- Araç çubuğuna bir komut ekleyin.

- Komutları uygulama.

- Araç penceresi için varsayılan konumu ayarlayın.

## <a name="prerequisites"></a>Önkoşullar

Visual Studio SDK, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-tool-window"></a>Araç penceresi oluşturma

1. VSIX şablonunu kullanarak **FirstToolWin** adlı bir proje oluşturun ve **FirstToolWindow** adlı özel bir araç penceresi öğesi şablonu ekleyin.

    > [!NOTE]
    > Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için [bkz. Araç penceresiyle uzantı oluşturma.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="add-a-control-to-the-tool-window"></a>Araç penceresine denetim ekleme

1. Varsayılan denetimi kaldırın. *FirstToolWindowControl.xaml'i açın* ve Bana **Tıklayın!** tıklayın.

2. Araç Kutusunda **Tüm** **WPF** Denetimleri bölümünü genişletin ve **Media Element denetimi'i** **FirstToolWindowControl formuna** sürükleyin. Denetimi seçin ve Özellikler penceresinde bu **öğeyi** **mediaElement1 olarak değiştirin.**

## <a name="add-a-toolbar-to-the-tool-window"></a>Araç penceresine araç çubuğu ekleme
Aşağıdaki şekilde bir araç çubuğu ekleyerek, gradyanlarının ve renklerinin IDE'nin geri kalanıyla tutarlı olduğunu garanti edersiniz.

1. içinde **Çözüm Gezgini** *FirstToolWindowPackage.vsct'i açın.* *.vsct dosyası,* XML kullanarak araç pencerenizin grafik kullanıcı arabirimi (GUI) öğelerini tanımlar.

2. bölümünde `<Symbols>` özniteliği olan `<GuidSymbol>` düğümü `name` `guidFirstToolWindowPackageCmdSet` bulun. Bir araç çubuğu `<IDSymbol>` ve araç çubuğu grubu tanımlamak için bu `<IDSymbol>` düğümdeki öğeler listesine aşağıdaki iki öğeyi ekleyin.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Bölümün hemen `<Buttons>` üzerinde, `<Menus>` aşağıdakine benzer bir bölüm oluşturun:

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

    Çeşitli türlerde menüler vardır. Bu menü, bir araç penceresindeki bir araç çubuğu ve özniteliğiyle `type` tanımlanmıştır. ve `guid` `id` ayarları, araç çubuğunun tam kimliğini ayarlar. Genellikle, `<Parent>` bir menenin içeren grup olduğu yer. Ancak, bir araç çubuğu kendi üst öğesi olarak tanımlanır. Bu nedenle, ve öğeleri için aynı `<Menu>` tanımlayıcı `<Parent>` kullanılır. Özniteliği `priority` yalnızca '0'dır.

4. Araç çubukları birçok şekilde menülere benzer. Örneğin, bir menüde komut grupları olduğu gibi, araç çubuklarının da grupları olabilir. (Menülerde, komut grupları yatay çizgilerle ayrılır. Araç çubuklarında gruplar görsel bölücülerle ayrılmaz.)

    öğesi `<Groups>` içeren bir bölüm `<Group>` ekleyin. Bu, bölümünde kimliğini bildiren grubu `<Symbols>` tanımlar. bölümünü `<Groups>` bölümün hemen sonrası `<Menus>` ekleyin.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    Üst GUID ve kimliği araç çubuğunun GUID ve kimliği olarak ayarerek grubu araç çubuğuna eklersiniz.

## <a name="add-a-command-to-the-toolbar"></a>Araç çubuğuna komut ekleme

Araç çubuğuna düğme olarak görüntülenen bir komut ekleyin.

1. bölümünde, araç çubuğu ve araç çubuğu grup bildirimlerini hemen sonra `<Symbols>` aşağıdaki IDSymbol öğelerini bildirin.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. bölümüne bir Düğme öğesi `<Buttons>` ekleyin. Bu öğe araç penceresindeki araç çubuğunda arama  (büyüteç) simgesiyle görünür.

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

3. *FirstToolWindowCommand.cs'yi* açın ve var olan alanların hemen sonrasını sınıfına aşağıdaki satırları ekleyin.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Bunu yapmak, komutlarınızı kodda kullanılabilir yapar.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>FirstToolWindowControl'a MediaPlayer özelliği ekleme
Araç çubuğu denetimleri için olay işleyicilerinden, kodunuzun FirstToolWindowControl sınıfının bir alt Media Player denetim denetimine erişmesi gerekir.

Bu **Çözüm Gezgini** *FirstToolWindowControl.xaml'e* sağ tıklayın, Kodu Görüntüle'ye tıklayın ve aşağıdaki kodu FirstToolWindowControl sınıfına ekleyin.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Araç penceresi ve araç çubuğunun örneğini açma
Dosya Aç iletişim kutusunu çağıran ve seçili medya **dosyasını oynatan** bir araç çubuğu ve menü komutu ekleyin.

1. *FirstToolWindow.cs'yi* açın ve aşağıdaki `using` yönergeleri ekleyin:

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. FirstToolWindow sınıfının içine FirstToolWindowControl denetimine genel bir başvuru ekleyin.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. Oluşturucusun sonunda, bu denetim değişkenlerini yeni oluşturulan denetime ayarlayın.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Oluşturucu içinde araç çubuğunun örneğini oluşturma.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. Bu noktada FirstToolWindow oluşturucusu aşağıdaki gibi görünüyordur:

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

6. Menü komutunu araç çubuğuna ekleyin. FirstToolWindowCommand.cs sınıfında aşağıdaki using yönergesine ekleyin:

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

1. FirstToolWindowCommand sınıfında, Dosya Aç iletişim kutusunu çağıran bir ButtonHandler **yöntemi** ekleyin. Bir dosya seçildiğinde medya dosyası oynatır.

2. FirstToolWindowCommand sınıfında, FindToolWindow() yönteminde oluşturulan FirstToolWindow penceresine özel bir başvuru ekleyin.

    ```csharp
    private FirstToolWindow window;
    ```

3. Yukarıda tanımlandığı pencereyi (ButtonHandler komut işleyicisi pencere denetimine erişemeyecek şekilde) ayarlamak için ShowToolWindow() yöntemini değiştirme. ShowToolWindow() yönteminin eksiksiz bir örneğidir.

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

4. ButtonHandler yöntemini ekleyin. Kullanıcının oynatılacak medya dosyasını belirtmesi için bir OpenFileDialog oluşturur ve ardından seçilen dosyayı oynatır.

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

Ardından, araç penceresi için IDE'de varsayılan bir konum belirtin. Araç penceresi için yapılandırma bilgileri *FirstToolWindowPackage.cs dosyasındadır.*

1. *FirstToolWindowPackage.cs* içinde, FirstToolWindow türünü oluşturucuya ileten sınıfında <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> `FirstToolWindowPackage` özniteliğini bulun. Varsayılan konumu belirtmek için aşağıdaki örnekte oluşturucuya daha fazla parametre eklemeniz gerekir.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    İlk adlandırılmış parametre, değeri ise `Style` `Tabbed` değeridir. Bu, pencerenin mevcut bir pencerede bir sekme olacağını gösterir. Yerleştirme konumu parametresi tarafından `Window` belirtilir, n bu durumda, Çözüm Gezgini.

    > [!NOTE]
    > IDE'de pencere türleri hakkında daha fazla bilgi için bkz. <xref:EnvDTE.vsWindowType> .

## <a name="test-the-tool-window"></a>Araç penceresini test edin

1. Deneysel derlemenin yeni bir örneğini açmak için **F5** Visual Studio basın.

2. Görünüm menüsünde **Diğer** Girişler'in **üzerine Windows** ardından İlk Araç **Penceresi'ne tıklayın.**

    Medya oynatıcı aracı penceresi, ile aynı konumda **Çözüm Gezgini.** Öncekiyle aynı konumda görünüyorsa pencere düzenini sıfırlayın (**Pencere / Pencere Düzenini Sıfırla**).

3. Araç penceresinde düğmesine tıklayın **(Ara** simgesine sahip). *C:\windows\media\chimes.wav* gibi desteklenen bir ses veya video dosyası seçin ve ardından Aç'a **basın.**

    Chime (chime) sesi duyasın.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
