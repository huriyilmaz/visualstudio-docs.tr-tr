---
title: Araç Penceresinde Kısayol Menüsü Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740288"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Araç penceresinde kısayol menüsü ekleme
Bu gözden geçirme, bir araç penceresine bir kısayol menüsü koyar. Kısayol menüsü, bir kullanıcı bir düğmeyi, metin kutusunu veya pencere arka planını sağ tıklattığında görünen bir menüdür. Kısayol menüsündeki komutlar, diğer menülerde veya araç çubuklarındaki komutlarla aynı şekilde olur. Kısayol menüsünü desteklemek için *,.vsct* dosyasında belirtin ve farenin sağ tıklamasına yanıt olarak görüntüleyin.

Araç penceresi, özel bir araç penceresi sınıfından devralan bir <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>WPF kullanıcı denetiminden oluşur.

Bu gözden geçirme, *.vsct* dosyasındaki menü öğelerini beyan ederek ve sonra araç penceresini tanımlayan sınıfta uygulamak için Yönetilen Paket Çerçevesi'ni kullanarak Visual Studio menüsü olarak kısayol menüsünün nasıl oluşturulacağını gösterir. Bu yaklaşım Visual Studio komutlarına, UI öğelerine ve Otomasyon nesnemodeline erişimi kolaylaştırır.

Alternatif olarak, kısayol menünüz Visual Studio işlevine erişmiyorsa, kullanıcı denetiminde bir XAML öğesinin <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliğini kullanabilirsiniz. Daha fazla bilgi için [ContextMenu'ye](/dotnet/framework/wpf/controls/contextmenu)bakın.

## <a name="prerequisites"></a>Ön koşullar
Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleme ye](../extensibility/installing-the-visual-studio-sdk.md)bakın.

## <a name="create-the-tool-window-shortcut-menu-package"></a>Araç penceresi kısayol menü paketini oluşturma

1. Adlandırılmış `TWShortcutMenu` bir VSIX projesi oluşturun ve buna **KısayolMenüsü** adında bir araç penceresi şablonu ekleyin. Araç penceresi oluşturma hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="specifying-the-shortcut-menu"></a>Kısayol menüsünü belirtme
Bu izbinde gösterilen gibi kısayol menüsü, kullanıcının araç penceresinin arka planını doldurmak için kullanılan renkler listesinden seçim yapmanızı sağlar.

1. *ShortcutMenuPackage.vsct'de*guidShortcutMenuPackageCmdSet adlı GuidSymbol öğesini bulun ve kısayol menüsünü, kısayol menü grubunu ve menü seçeneklerini bildirin. GuidSymbol öğesi şimdi şu na benzemelidir:

    ```xml
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />
        <IDSymbol name="ColorMenu" value="0x1000"/>
        <IDSymbol name="ColorGroup" value="0x1100"/>
        <IDSymbol name="cmdidRed" value="0x102"/>
        <IDSymbol name="cmdidYellow" value="0x103"/>
        <IDSymbol name="cmdidBlue" value="0x104"/>
    </GuidSymbol>
    ```

2. Düğmeler öğesinden hemen önce, bir Menüler öğesi oluşturun ve kısayol menüsünü tanımlayın.

    ```vb
    <Menus>
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">
        <Strings>
          <ButtonText>Color change</ButtonText>
          <CommandName>ColorChange</CommandName>
        </Strings>
      </Menu>
    </Menus>
    ```

    Kısayol menüsünde bir menü veya araç çubuğunun parçası olmadığından bir üst öğe yoktur.

3. Kısayol menü öğelerini içeren bir Grup öğesi yle gruplar öğesi oluşturun ve grubu kısayol menüsüyle ilişkilendirin.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Düğmeler öğesinde, kısayol menüsünde görünecek tek tek komutları tanımlayın. Düğmeler öğesi aşağıdaki gibi görünmelidir:

    ```xml
    <Buttons>
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
            <Icon guid="guidImages" id="bmpPic1" />
            <Strings>
                <ButtonText>ShortcutMenu</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Red</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Yellow</ButtonText>
            </Strings>
        </Button>

        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />
            <Strings>
                <ButtonText>Blue</ButtonText>
            </Strings>
        </Button>
    </Buttons>
    ```

5. *ShortcutMenuCommand.cs,* komut kümesi GUID, kısayol menüsü ve menü öğeleri için tanımları ekleyin.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Bunlar, *KısayolMenuPackage.vsct* dosyasının Semboller bölümünde tanımlanan komut tevkimilerdir. Yalnızca *.vsct* dosyasında gerekli olduğundan bağlam grubu burada dahil edilmez.

## <a name="implementing-the-shortcut-menu"></a>Kısayol menüsünü uygulama
 Bu bölümde kısayol menüsü ve komutları uygular.

1. *ShortcutMenu.cs,* araç penceresi menü komut hizmeti alabilirsiniz, ancak içerdiği denetim olamaz. Aşağıdaki adımlar, menü komut hizmetinin kullanıcı denetiminde nasıl kullanılabilir hale getirilebildiğini gösterir.

2. *ShortcutMenu.cs,* aşağıdaki yönergeleri kullanarak ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Menü komut hizmetini almak ve denetim eklemek için araç penceresinin Initialize() yöntemini geçersiz kılın ve menü komut hizmetini oluşturucuya geçirin:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. KısayolMenü araç penceresi oluşturucuda, denetimi ekleyen satırı kaldırın. Yapıcı şimdi şuna benzemelidir:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. *ShortcutMenuControl.xaml.cs,* menü komut hizmeti için özel bir alan ekleyin ve menü komut hizmeti almak için denetim oluşturucu değiştirin. Ardından bağlam menüsü komutlarını eklemek için menü komutu hizmetini kullanın. KısayolMenuControl oluşturucu şimdi aşağıdaki kod gibi görünmelidir. Komut işleyicisi daha sonra tanımlanır.

    ```csharp
    public ShortcutMenuControl(OleMenuCommandService service)
    {
        this.InitializeComponent();
        commandService = service;

        if (null !=commandService)
        {
            // Create an alias for the command set guid.
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);

            // Create the command IDs.
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);

            // Add a command for each command ID.
            commandService.AddCommand(new MenuCommand(ChangeColor, red));
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));
        }
    }
    ```

6. *ShortcutMenuControl.xaml,* üst <xref:System.Windows.UIElement.MouseRightButtonDown> düzey <xref:System.Windows.Controls.UserControl> öğeye bir olay ekleyin. XAML dosyası şimdi şu na benzemelidir:

    ```vb
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
            Background="{DynamicResource VsBrush.Window}"
            Foreground="{DynamicResource VsBrush.WindowText}"
            mc:Ignorable="d"
            d:DesignHeight="300" d:DesignWidth="300"
            Name="MyToolWindow"
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">
        <Grid>
            <StackPanel Orientation="Vertical">
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>
            </StackPanel>
        </Grid>
    </UserControl>
    ```

7. *ShortcutMenuControl.xaml.cs,* olay işleyicisi için bir saplama ekleyin.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Yönergeleri kullanarak aynı dosyaya aşağıdaki yönergeleri ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Olayı `MyToolWindowMouseRightButtonDown` aşağıdaki gibi uygulayın.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
        if (null != commandService)
        {
            CommandID menuID = new CommandID(
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),
                ShortcutMenuCommand.ColorMenu);
            Point p = this.PointToScreen(e.GetPosition(this));
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);
        }
    }
    ```

    Bu, kısayol menüsü için bir <xref:System.ComponentModel.Design.CommandID> nesne oluşturur, fare tıklamasının konumunu tanımlar ve yöntemi kullanarak <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> o konumdaki kısayol menüsünü açar.

10. Komut işleyicisini uygulayın.

    ```csharp
    private void ChangeColor(object sender, EventArgs e)
    {
        var mc = sender as MenuCommand;

        switch (mc.CommandID.ID)
        {
            case ShortcutMenuCommand.cmdidRed:
                MyToolWindow.Background = Brushes.Red;
                break;
            case ShortcutMenuCommand.cmdidYellow:
                MyToolWindow.Background = Brushes.Yellow;
                break;
            case ShortcutMenuCommand.cmdidBlue:
                MyToolWindow.Background = Brushes.Blue;
                break;
        }
    }
    ```

    Bu durumda, sadece bir yöntem, tüm menü öğeleri için <xref:System.ComponentModel.Design.CommandID> olayları tanımlayarak ve buna göre arka plan rengini ayarlayarak işler. Menü öğeleri ilgisiz komutlar içerseydi, her komut için ayrı bir olay işleyicisi oluşturmuş olurdunuz.

## <a name="test-the-tool-window-features"></a>Araç penceresi özelliklerini test edin

1. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görüntülenir.

2. Deneme örneğinde, **Görünüm / Diğer Windows'u**tıklatın ve ardından **Kısayol Menüsü'nü**tıklatın. Bunu yapmak araç pencerenizi görüntülemelidir.

3. Araç penceresinin gövdesine sağ tıklayın. Renk listesi olan bir kısayol menüsü görüntülenmelidir.

4. Kısayol menüsünde bir renk tıklatın. Araç penceresi arka plan rengi seçili renge değiştirilmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
- [Hizmet kullanma ve sağlama](../extensibility/using-and-providing-services.md)
