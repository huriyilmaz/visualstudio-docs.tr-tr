---
title: Menüye Alt Menü Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740274"
---
# <a name="add-a-submenu-to-a-menu"></a>Menüye Alt Menü Ekleme
Bu gözden geçirme, **TestMenu** menüsüne nasıl bir alt menü ekleyeceğini göstererek [Visual Studio Menü Çubuğu'na Menü Ekle'deki](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) gösterime göre oluşturur.

 Alt menü, başka bir menüde görünen ikincil bir menüdür. Bir alt menü, adını izleyen okla tanımlanabilir. Adı tıklatmak alt menünün ve komutlarının görüntülenmesine neden olur.

 Bu gözden geçirme, Visual Studio menü çubuğundaki bir menüde bir alt menü oluşturur ve alt menüye yeni bir komut koyar. İzninuzun yeni komutu da uygular.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="add-a-submenu-to-a-menu"></a>Menüye Alt Menü Ekleme

1. Proje yi ve menü öğesini oluşturmak [için Visual Studio Menü Çubuğu'na Menü Ekle'deki](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) adımları izleyin. Bu gözden geçirme deki adımlar VSIX projesinin `TopLevelMenu`adının .

2. *Açık TestCommandPackage.vsct*. `<Symbols>` Bölümde, alt menü `<IDSymbol>` grubu için bir öğe, bir alt menü grubu için bir `<GuidSymbol>` ve komut için bir öğe, tüm düğüm "guidTopLevelMenuCmdSet" adlı ekleyin. Bu, üst düzey menü `<IDSymbol>` için öğeyi içeren aynı düğümdür.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. `<Menus>` Yeni oluşturulan alt menüyü bölüme ekleyin.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Üst öğenin GUID/ID çifti, Visual Studio Menu [Çubuğu'na Menü Ekle'de](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)oluşturulan menü grubunu belirtir ve üst düzey menünün alt öğesidir.

4. 2. adımda tanımlanan menü `<Groups>` grubunu bölüme ekleyin ve alt menünün alt öğesi haline getirin.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Adım 2'de `<Buttons>` oluşturulan komutu alt menüdeki öğe olarak tanımlamak için bölüme yeni `<Button>` bir öğe ekleyin.

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

6. Çözümü oluşturun ve hata ayıklamaya başlayın. Deneysel örneği görmelisin.

7. **Alt Menü**adlı yeni bir alt menü görmek için **TestMenu'yi** tıklatın. **Alt menüyü** açmak ve yeni bir komut görmek için Alt Menü'yü tıklatın, **Alt Komutu Test Edin.** Test Alt **Komutu'na** tıklamanın hiçbir şey sağlamadığını unutmayın.

## <a name="add-a-command"></a>Komut Ekle

1. *TestCommand.cs* açın ve varolan komut kimliğinden sonra aşağıdaki komut kimliğini ekleyin.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Alt komutu ekleyin. Komut oluşturucuyu bulun. `AddCommand` Aramadan hemen sonra yönteme aşağıdaki satırları ekleyin.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Komut `SubItemCallback` işleyicisi daha sonra tanımlanır. Yapıcı şimdi şuna benzemelidir:

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

3. Ekle `SubItemCallback()`. Alt menüdeki yeni komut tıklatıldığında çağrılan yöntem budur.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
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

4. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görünmelidir.

5. **TestMenüsü** menüsünde **Alt Menü'yü** tıklatın ve ardından **Alt Komutu Test'i**tıklatın. Bir ileti kutusu görünmeli ve "TestKomutu İçi Test Komutu.SubItemCallback()" metnini görüntülemelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
