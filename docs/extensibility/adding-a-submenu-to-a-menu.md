---
title: Menü Menüsüne Alt Menü | Microsoft Docs
description: Alt menü oluşturma, menü çubuğuna Visual Studio ve alt menüye yeni bir komut ekleme hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6ebd3a4d97d19977b8a97ff7fcb2a545654f4165
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065195"
---
# <a name="add-a-submenu-to-a-menu"></a>Menüye Alt Menü Ekleme
Bu kılavuz, TestMenu menüsüne bir alt menü [eklemeyi Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Menü Çubuğuna Menü Ekle'de yer alan **gösterime göre ekleyebilirsiniz.**

 Alt menü, başka bir menüde görünen ikincil bir menü olur. Alt menüsü, adının yanındaki ok ile belirlenebilirsiniz. Adına tıklarsınız, alt menü ve komutlarının görüntülenebilir.

 Bu kılavuz, Visual Studio menüsünde bir alt menü oluşturur ve alt menüye yeni bir komut koyar. Kılavuz yeni komutu da uygulamaya almaktadır.

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="add-a-submenu-to-a-menu"></a>Menüye Alt Menü Ekleme

1. Projeyi ve menü [öğesini oluşturmak için Visual Studio Menü Çubuğuna](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) Menü Ekleme'de yer alan adımları izleyin. Bu kılavuzda yer alan adımlarda VSIX projesinin adının olduğu `TopLevelMenu` varsayılacaktır.

2. *TestCommandPackage.vsct'i açın.* bölümünde, alt menüsü için bir öğe, alt menüsü grubu için bir öğe ve komutu için bir öğe ekleyin; bunların hepsi `<Symbols>` `<IDSymbol>` `<GuidSymbol>` "guidTopLevelMenuCmdSet" adlı düğümdedir. Bu, üst düzey menü için `<IDSymbol>` öğesini içeren düğümle aynıdır.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Yeni oluşturulan alt menüsü bölümüne `<Menus>` ekleyin.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Üst öğenin GUID/KIMLIK çifti, Visual Studio Menü Çubuğuna Menü Ekle kısmında oluşturulan menü grubunu belirtir ve üst düzey meninin alt öğesidir. [](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)

4. 2. adımda tanımlanan menü grubunu bölümüne `<Groups>` ekleyin ve alt menü grubunun alt öğesi olarak belirleyin.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. `<Button>`2. adımda `<Buttons>` oluşturulan komutu alt menüdeki bir öğe olarak tanımlamak için bölümüne yeni bir öğe ekleyin.

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

6. Çözümü derleme ve hata ayıklamayı başlatma. Deneysel örneği görüyor gerekir.

7. Alt Menü adlı yeni bir alt menü görmek için **TestMenu'ya** **tıklayın.** Alt **menüyü** açmak için Alt Menü'ye tıklayın ve yeni bir komut olan **Test Alt Komutu'na bakın.** Test Alt **Komutu'na tıklarken hiçbir şey** olmadığını fark etmek.

## <a name="add-a-command"></a>Komut Ekleme

1. *TestCommand.cs'yi* açın ve mevcut komut kimliğinin ardından aşağıdaki komut kimliğini ekleyin.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Alt komutu ekleyin. Komut oluşturucusu bulun. yöntemi çağrısının hemen sonrasını aşağıdaki satırları `AddCommand` ekleyin.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Komut `SubItemCallback` işleyicisi daha sonra tanımlanmalıdır. Oluşturucu şimdi aşağıdaki gibi görünüyor:

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

3. `SubItemCallback()`ekleyin. Bu, altmenüste yeni komut tık olduğunda çağrılır yöntemidir.

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

4. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örneğin görünmesi gerekir.

5. **TestMenu menüsünde Alt** **Menü'ye ve ardından** Test Alt **Komutu'na tıklayın.** Bir ileti kutusu görüntüleniyor ve "TestCommand.SubItemCallback() İçinde Test Komutu" metni görüntüleniyor.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni menü çubuğuna Visual Studio ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
