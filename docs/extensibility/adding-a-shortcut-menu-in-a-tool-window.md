---
title: Araç Penceresine Kısayol Menüsü Ekleme | Microsoft Docs
description: Bir düğme, metin kutusu veya pencere arka planına sağ Visual Studio görüntülenen bir araç penceresine kısayol menüsü ekleme hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d698b0e3ee5e2c629e7d9cc1c1415b40bfbe176208cb87e1f5ee14a2e9a8c3ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435120"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Araç penceresine kısayol menüsü ekleme
Bu kılavuz bir araç penceresine kısayol menüsü koyar. Kısayol menüsü, kullanıcı bir düğmeye, metin kutusuna veya pencere arka planına sağ tıkladığında görüntülenen bir menüyü ifade eder. Kısayol menüsündeki komutlar, diğer menülerde veya araç çubuklarda yer alan komutlar ile aynı şekilde davranır. Kısayol menüsünü desteklemek için bunu *.vsct* dosyasında belirtin ve farenin sağ tıklaması üzerine yanıt olarak görüntüler.

Araç penceresi, 'den devralan özel bir araç penceresi sınıfındaki WPF kullanıcı denetiminden <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> oluşur.

Bu kılavuzda, *.vsct* dosyasında menü öğelerini bildirerek ve ardından Yönetilen Paket Çerçevesi'ni kullanarak bunları araç penceresini tanımlayan sınıfta uygulamak için bir kısayol menüsünün Visual Studio menüsü olarak nasıl oluşturulacakları gösterilir. Bu yaklaşım, kullanıcı arabirimi Visual Studio Otomasyon nesne modeline erişimi kolaylaştırır.

Alternatif olarak, kısayol menüsünüz Visual Studio erişemayacaksa, kullanıcı denetiminde <xref:System.Windows.FrameworkElement.ContextMenu%2A> bir XAML öğesinin özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Önkoşullar
2015 Visual Studio den başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-the-tool-window-shortcut-menu-package"></a>Araç penceresi kısayol menü paketini oluşturma

1. adlı bir VSIX projesi oluşturun `TWShortcutMenu` ve buna **ShortcutMenu** adlı bir araç penceresi şablonu ekleyin. Araç penceresi oluşturma hakkında daha fazla bilgi için [bkz. Araç penceresiyle uzantı oluşturma.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="specifying-the-shortcut-menu"></a>Kısayol menüsünü belirtme
Bu kılavuzda gösterilene gibi bir kısayol menüsü, kullanıcının araç penceresinin arka planını doldurmak için kullanılan renk listesinden seçime olanak sağlar.

1. *ShortcutMenuPackage.vsct* içinde guidShortcutMenuPackageCmdSet adlı GuidSymbol öğesini bulun ve kısayol menüsünü, kısayol menü grubunu ve menü seçeneklerini bildirin. GuidSymbol öğesi şimdi aşağıdaki gibi görünüyor:

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

2. Düğmeler öğesinin hemen öncesinde bir Menü öğesi oluşturun ve ardından içinde kısayol menüsünü tanımlayın.

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

    Kısayol menüsünde üst öğe yok çünkü bir menü veya araç çubuğunun parçası değil.

3. Kısayol menüsü öğelerini içeren bir Group öğesi ile bir Groups öğesi oluşturun ve grubu kısayol menüsüyle ilişkilendirilin.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Düğmeler öğesinde, kısayol menüsünde görünecek komutları tek tek tanımlayın. Düğmeler öğesi aşağıdaki gibi görünüyor olmalı:

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

5. *ShortcutMenuCommand.cs* içinde, komut kümesi GUID'si, kısayol menüsü ve menü öğelerinin tanımlarını ekleyin.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Bunlar *ShortcutMenuPackage.vsct* dosyasının Semboller bölümünde tanımlanan komut kimlikleri ile aynıdır. Bağlam grubu buraya dahil değildir çünkü yalnızca *.vsct dosyasında* gereklidir.

## <a name="implementing-the-shortcut-menu"></a>Kısayol menüsünü uygulama
 Bu bölümde kısayol menüsü ve komutları uygulanır.

1. *ShortcutMenu.cs'de,* araç penceresi menü komut hizmetini edinebilirsiniz, ancak içerdiği denetim bunu eldeamaz. Aşağıdaki adımlarda, menü komut hizmetinin kullanıcı denetimi için nasıl kullanılabilir hale geldi?

2. *ShortcutMenu.cs içinde* aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Menü komut hizmetini almak ve denetimi eklemek için araç penceresinin Initialize() yöntemini geçersiz kılarak menü komut hizmetini oluşturucuya geçirme:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. ShortcutMenu araç penceresi oluşturucusu'nda denetimi ekleyen satırı kaldırın. Oluşturucu şimdi aşağıdaki gibi görünüyor:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. *ShortcutMenuControl.xaml.cs* içinde, menü komut hizmeti için özel bir alan ekleyin ve denetim oluşturucusunu menü komut hizmetini alacak şekilde değiştirebilirsiniz. Ardından menü komut hizmetini kullanarak bağlam menüsü komutlarını ekleyin. ShortcutMenuControl oluşturucusu artık aşağıdaki kod gibi görünüyor. Komut işleyicisi daha sonra tanımlanmalıdır.

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

6. *ShortcutMenuControl.xaml içinde,* üst <xref:System.Windows.UIElement.MouseRightButtonDown> düzey öğesine bir olay <xref:System.Windows.Controls.UserControl> ekleyin. XAML dosyası şimdi aşağıdaki gibi görünüyor:

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

7. *ShortcutMenuControl.xaml.cs* içinde olay işleyicisi için bir saplama ekleyin.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Aşağıdaki using yönergelerini aynı dosyaya ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Olayı `MyToolWindowMouseRightButtonDown` aşağıdaki gibi gerçekleştirin.

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

    Bu, kısayol menüsü için bir nesnesi oluşturur, fare tıklama konumunu tanımlar ve yöntemini kullanarak kısayol <xref:System.ComponentModel.Design.CommandID> menüsünü bu konumda <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> açar.

10. Komut işleyicisini uygulama.

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

    Bu durumda yalnızca bir yöntem, arka plan rengini belirleyerek ve buna uygun şekilde ayarerek tüm <xref:System.ComponentModel.Design.CommandID> menü öğelerinin olaylarını işlemeye devam eder. Menü öğeleri arasında ilgisiz komutlar olsaydı, her komut için ayrı bir olay işleyicisi oluşturulur.

## <a name="test-the-tool-window-features"></a>Araç penceresi özelliklerini test edin

1. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örnek görünür.

2. Deneysel örnekte Görünüm / Diğer **Windows'a** ve ardından **ShortcutMenu'ya tıklayın.** Bunu yapmak araç pencerenizi görüntülemeli.

3. Araç penceresinin gövdesine sağ tıklayın. Renk listesi olan bir kısayol menüsü görüntüleniyor.

4. Kısayol menüsünde bir renge tıklayın. Araç penceresi arka plan rengi seçilen renge değiştirilmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
