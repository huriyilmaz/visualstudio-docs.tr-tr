---
title: Araç penceresine kısayol menüsü ekleme | Microsoft Docs
description: Bir düğme, metin kutusu veya pencere arka planı sağ tıklandığında görüntülenen Visual Studio 'daki bir araç penceresine kısayol menüsü eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a35652c0eacf22a46eed3f3fc64c3bcc0d6d10ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951543"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Araç penceresine kısayol menüsü ekleme
Bu izlenecek yol, bir araç penceresine kısayol menüsü yerleştirir. Kısayol menüsü, bir Kullanıcı bir düğmeyi, metin kutusunu veya pencere arka planını sağ tıklattığında görüntülenen bir menü olur. Kısayol menüsündeki komutlar, diğer menülerdeki veya araç çubuklarındaki komutlarla aynı şekilde davranır. Bir kısayol menüsünü desteklemek için, *. vsct* dosyasında belirtin ve fareyi sağ tıklaması karşılığında görüntüleyin.

Bir araç penceresi, öğesinden devralan özel bir araç penceresi sınıfındaki WPF Kullanıcı denetiminden oluşur <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

Bu izlenecek yol, *. vsct* dosyasındaki menü öğelerini bildirerek ve ardından yönetilen paket çerçevesini araç penceresini tanımlayan sınıfta uygulamak için kullanarak, bir kısayol menüsünün bir Visual Studio menüsü olarak nasıl oluşturulduğunu gösterir. Bu yaklaşım, Visual Studio komutlarına, UI öğelerine ve Otomasyon nesne modeline erişimi kolaylaştırır.

Alternatif olarak, kısayol menünüzün Visual Studio işlevselliğine erişimi yoksa, <xref:System.Windows.FrameworkElement.ContextMenu%2A> Kullanıcı DENETIMINDEKI xaml öğesinin özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Önkoşullar
Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Araç penceresi kısayol menüsü paketini oluşturma

1. Adlı bir VSıX projesi oluşturun `TWShortcutMenu` ve bunun Için **ShortcutMenu** adlı bir araç penceresi şablonu ekleyin. Araç penceresi oluşturma hakkında daha fazla bilgi için bkz. bir [araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Kısayol menüsünü belirtme
Bu kılavuzda gösterildiği gibi bir kısayol menüsü, kullanıcının araç penceresinin arka planını göstermek için kullanılan bir renk listesinden seçim yapmanızı sağlar.

1. *ShortcutMenuPackage. vsct* Içinde, guidShortcutMenuPackageCmdSet adlı GuidSymbol öğesinde bulun ve kısayol menüsünü, kısayol menü grubunu ve menü seçeneklerini bildirin. GuidSymbol öğesi şu şekilde görünmelidir:

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

2. Düğmeler öğesinden hemen önce bir menü öğesi oluşturun ve sonra kısayol menüsünü tanımlayın.

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

    Bir menü veya araç çubuğunun parçası olmadığından, kısayol menüsü bir üst öğeye sahip değil.

3. Kısayol menü öğelerini içeren bir grup öğesiyle bir gruplar öğesi oluşturun ve grubu kısayol menüsüyle ilişkilendirin.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. Düğmeler öğesinde, kısayol menüsünde görünecek komutları tek tek tanımlayın. Düğmeler öğesi şöyle görünmelidir:

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

5. *ShortcutMenuCommand.cs*' de, komut kümesi GUID 'si, kısayol menüsü ve menü öğeleri için tanımları ekleyin.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Bunlar, *ShortcutMenuPackage. vsct* dosyasının semboller bölümünde tanımlanan komut kimlikleridir. Yalnızca *. vsct* dosyasında gerekli olduğu için bağlam grubu buraya dahil edilmez.

## <a name="implementing-the-shortcut-menu"></a>Kısayol menüsünü uygulama
 Bu bölüm, kısayol menüsünü ve komutlarını uygular.

1. *ShortcutMenu.cs*' de, araç penceresi menü komutu hizmetini alabilir, ancak içerdiği denetim olamaz. Aşağıdaki adımlarda menü komut hizmetinin Kullanıcı denetimi için nasıl kullanılabilir yapılacağı gösterilmektedir.

2. *ShortcutMenu.cs*' de, aşağıdaki using yönergelerini ekleyin:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Menü komut hizmetini almak ve denetimi eklemek için araç penceresinin Initialize () yöntemini geçersiz kılın ve menü komut hizmetini oluşturucuya geçirerek:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. ShortcutMenu araç penceresi oluşturucusunda, denetimi ekleyen çizgiyi kaldırın. Oluşturucunun şimdi şöyle görünmesi gerekir:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. *ShortcutMenuControl.xaml.cs*' de menü komut hizmeti için bir özel alan ekleyin ve menü komut hizmetini alacak şekilde denetim oluşturucusunu değiştirin. Ardından kısayol menü komutlarını eklemek için menü komut hizmetini kullanın. ShortcutMenuControl Oluşturucusu şimdi aşağıdaki kod gibi görünmelidir. Komut işleyicisi daha sonra tanımlanacaktır.

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

6. *ShortcutMenuControl. xaml* içinde, <xref:System.Windows.UIElement.MouseRightButtonDown> en üst düzey öğeye bir olay ekleyin <xref:System.Windows.Controls.UserControl> . XAML dosyası şu şekilde görünmelidir:

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

7. *ShortcutMenuControl.xaml.cs*' de, olay işleyicisi için bir saplama ekleyin.

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

9. `MyToolWindowMouseRightButtonDown`Olayı aşağıdaki şekilde uygulayın.

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

    Bu, <xref:System.ComponentModel.Design.CommandID> kısayol menüsü için bir nesne oluşturur, fare tıklaması konumunu tanımlar ve yöntemi kullanılarak bu konumdaki kısayol menüsünü açar <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> .

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

    Bu durumda, yalnızca bir yöntem, <xref:System.ComponentModel.Design.CommandID> arka plan rengini tanımlayarak ve ayarlayarak tüm menü öğelerinin olaylarını işler. Menü öğelerinde ilişkisiz komutlar varsa, her komut için ayrı bir olay işleyicisi oluşturmuş olursunuz.

## <a name="test-the-tool-window-features"></a>Araç penceresi özelliklerini test etme

1. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görüntülenir.

2. Deneysel örnekte, **Görünüm/diğer pencereler**' i ve ardından **ShortcutMenu**' ı tıklatın. Bunu yapmak araç pencerenizi görüntülemelidir.

3. Araç penceresinin gövdesine sağ tıklayın. Renklerin listesini içeren bir kısayol menüsü görüntülenmelidir.

4. Kısayol menüsünde bir renge tıklayın. Araç penceresi arka plan rengi seçili renge değiştirilmelidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
- [Hizmetleri kullanma ve sağlama](../extensibility/using-and-providing-services.md)
