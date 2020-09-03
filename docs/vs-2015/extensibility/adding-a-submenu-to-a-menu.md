---
title: Menüye alt menü ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f458d46395c3a902e62ba5dd4ac7d624c326700c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184896"
---
# <a name="adding-a-submenu-to-a-menu"></a>Bir Menüye Alt Menü Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, **TestMenu** menüsüne bir alt menü nasıl ekleneceğini göstererek [Visual Studio menü çubuğuna bir menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) konusunda tanıtım oluşturur.  
  
 Alt menü, başka bir menüde görünen ikincil bir menü olur. Bir alt menü, adını izleyen ok ile tanımlanabilir. Ada tıklamak alt menüye ve komutlarının görüntülenmesine neden olur.  
  
 Bu izlenecek yol, Visual Studio menü çubuğundaki bir menüde bir alt menü oluşturur ve alt menüye yeni bir komut koyar. İzlenecek yol yeni komutu de uygular.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Bir Menüye Alt Menü Ekleme  
  
1. Projeyi ve menü öğesini oluşturmak için [Visual Studio menü çubuğuna bir menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) bölümündeki adımları izleyin. Bu izlenecek yolda yer alan adımlarda VSıX projesinin adı olduğu varsayılır `TopLevelMenu` .  
  
2. TestCommandPackage. vsct öğesini açın. Bölümünde alt menü için bir `<Symbols>` `<IDSymbol>` , alt menü grubu ve diğeri Ise `<GuidSymbol>` "guidTopLevelMenuCmdSet" adlı düğümde bir öğe ekleyin. Bu, `<IDSymbol>` üst düzey menünün öğesini içeren düğümdür.  
  
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
  
     Üst öğenin GUID/ID çifti, [Visual Studio menü çubuğuna bir menü eklenirken](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)oluşturulan menü grubunu belirtir ve üst düzey menünün bir alt öğesidir.  
  
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
  
7. **Alt menü**adlı yeni bir alt menü görmek Için **TestMenu** öğesine tıklayın. Alt **menüyü açmak Için alt menü** ' ye tıklayın ve yeni bir komut, **Test Sub komutunu**görüntüleyin. **Test Sub komutunu** tıklatmak hiçbir şey yapmaz.  
  
## <a name="adding-a-command"></a>Komut ekleme  
  
1. TestCommand.cs ' i açın ve var olan komut KIMLIĞINDEN sonra aşağıdaki komut KIMLIĞINI ekleyin.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2. Alt komutunu ekleyin. Komut oluşturucusunu bulun. Yöntemine yapılan çağrıdan hemen sonra aşağıdaki satırları ekleyin `AddCommand` .  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
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
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3. SubItemCallback () ekleyin. Bu, alt menüdeki New komutuna tıklandığında çağrılan yöntemidir.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio menü çubuğuna menü ekleme](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
