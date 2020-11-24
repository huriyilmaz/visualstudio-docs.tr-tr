---
title: Menüye alt menü ekleme | Microsoft Docs
description: Alt menü oluşturma, Visual Studio menü çubuğuna ekleme ve alt menüye yeni bir komut ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16b58a6ab6a01ff635b3afd58b06133abacf970e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598022"
---
# <a name="add-a-submenu-to-a-menu"></a>Menüye alt menü ekleme
Bu izlenecek yol, **TestMenu** menüsüne bir alt menü nasıl ekleneceğini göstererek, [Visual Studio menü çubuğuna bir menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) bölümündeki gösteride oluşturulur.

 Alt menü, başka bir menüde görünen ikincil bir menü olur. Bir alt menü, adını izleyen ok ile tanımlanabilir. Ada tıklamak alt menüye ve komutlarının görüntülenmesine neden olur.

 Bu izlenecek yol, Visual Studio menü çubuğundaki bir menüde bir alt menü oluşturur ve alt menüye yeni bir komut koyar. İzlenecek yol yeni komutu de uygular.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yüklemeyi](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Menüye alt menü ekleme

1. Projeyi ve menü öğesini oluşturmak için [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) bölümündeki adımları izleyin. Bu izlenecek yolda yer alan adımlarda VSıX projesinin adı olduğu varsayılır `TopLevelMenu` .

2. *TestCommandPackage. vsct* öğesini açın. Bölümünde alt menü için bir `<Symbols>` `<IDSymbol>` , alt menü grubu ve diğeri Ise `<GuidSymbol>` "guidTopLevelMenuCmdSet" adlı düğümde bir öğe ekleyin. Bu, `<IDSymbol>` üst düzey menünün öğesini içeren düğümdür.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Yeni oluşturulan alt menüyü `<Menus>` bölümüne ekleyin.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Üst öğenin GUID/ID çifti, [Visual Studio menü çubuğuna bir menü ekle](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)menüsünde oluşturulan menü grubunu belirtir ve üst düzey menünün bir alt öğesidir.

4. 2. adımda tanımlanan menü grubunu `<Groups>` bölümüne ekleyin ve alt menünün alt öğesi yapın.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. `<Button>` `<Buttons>` 2. adımda oluşturulan komutu alt menüdeki bir öğe olarak tanımlamak için bölümüne yeni bir öğesi ekleyin.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Çözümü oluşturun ve hata ayıklamayı başlatın. Deneysel örneği görmeniz gerekir.

7. **Alt menü** adlı yeni bir alt menü görmek Için **TestMenu** öğesine tıklayın. Alt **menüyü açmak Için alt menü** ' ye tıklayın ve yeni bir komut, **Test Sub komutunu** görüntüleyin. **Test Sub komutunu** tıklatmak hiçbir şey yapmaz.

## <a name="add-a-command"></a>Komut Ekle

1. *TestCommand.cs* ' i açın ve var olan komut kimliğinden sonra AŞAĞıDAKI komut kimliğini ekleyin.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Alt komutunu ekleyin. Komut oluşturucusunu bulun. Yöntemine yapılan çağrıdan hemen sonra aşağıdaki satırları ekleyin `AddCommand` .

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    `SubItemCallback`Komut işleyicisi daha sonra tanımlanacaktır. Oluşturucunun şimdi şöyle görünmesi gerekir:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Ekleyin `SubItemCallback()` . Bu, alt menüdeki New komutuna tıklandığında çağrılan yöntemidir.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        IVsUIShell uiShell = this.package.GetService<SVsUIShell, IVsUIShell>();
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

5. **TestMenu** menüsünde, **alt menü** ' ye tıklayın ve ardından **Sub komutunu test et**' e tıklayın. İleti kutusu görünür ve metin, TestCommand. SubItemCallback () "Içinde" test komutunu "görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio menü çubuğuna bir menü ekleyin](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
