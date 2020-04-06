---
title: Menü Komutunun Metnini Değiştirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739839"
---
# <a name="change-the-text-of-a-menu-command"></a>Menü komutunun metnini değiştirme
Aşağıdaki adımlar, hizmeti kullanarak bir menü komutunun metin <xref:System.ComponentModel.Design.IMenuCommandService> etiketini nasıl değiştireceğini gösterir.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>IMenuCommandService ile menü komut etiketini değiştirme

1. **ChangeMenuText**adlı `MenuText` bir menü komutu ile adlı bir VSIX projesi oluşturun. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. *.vsct* dosyasında, aşağıdaki `TextChanges` örnekte gösterildiği gibi, menü komutunuze bayrağı ekleyin.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. *ChangeMenuText.cs* dosyasında, menü komutu görüntülenmeden önce çağrılacak bir olay işleyicisi oluşturun.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    Bu yöntemdeki menü <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>komutunun <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> durumunu, nesneüzerindeki , ve özellikleri değiştirerek de güncelleştirebilirsiniz.

4. ChangeMenuText oluşturucuda, özgün komut başlatma ve yerleşim kodunu, menü <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> komutunu `MenuCommand`temsil eden, olay işleyicisini <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> ekleyen ve menü komutu servisine veren bir (yerine) oluşturan kodla değiştirin.

    İşte nasıl görünmesi gerektiği:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. Projeyi oluşturun ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneği ortaya çıkar.

6. **Araçlar** menüsünde **ChangeMenuText'i Çağır**adlı bir komut görmeniz gerekir.

7. Komutu tıklatın. **MenuItemCallback'in** çağrıldığını bildiren ileti kutusunu görmeniz gerekir. İleti kutusunu kapatırken, Araçlar menüsündeki komutun adının artık Yeni **Metin**olduğunu görmeniz gerekir.
