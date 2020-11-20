---
title: Menü komutunun metnini değiştirme | Microsoft Docs
description: Bu kod örneğini inceleyerek, bir menü komutunun metin etiketini ımtrcommandservice hizmetini kullanarak nasıl değiştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d22669e67becb62d5e90f58c0cdd6b572e684bcf
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974396"
---
# <a name="change-the-text-of-a-menu-command"></a>Menü komutunun metnini değiştirme
Aşağıdaki adımlarda, hizmetini kullanarak bir menü komutunun metin etiketinin nasıl değiştirileceği gösterilmektedir <xref:System.ComponentModel.Design.IMenuCommandService> .

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Bir menü komut etiketini ımtrcommandservice ile değiştirme

1. `MenuText` **ChangeMenuText** adlı bir menü komutuyla adlı bir VSIX projesi oluşturun. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2. *. Vsct* dosyasında, `TextChanges` Aşağıdaki örnekte gösterildiği gibi, menü komutunuz bayrağını ekleyin.

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

    Ayrıca, <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> nesne üzerindeki, ve özelliklerini değiştirerek bu yöntemde menü komutunun durumunu güncelleştirebilirsiniz <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .

4. ChangeMenuText oluşturucusunda, özgün komut başlatma ve yerleştirme kodunu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> menü komutunu temsil eden bir (yerine bir) oluşturan kodla değiştirin `MenuCommand` , <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> olay işleyicisini ekler ve menü komutunu menü komutu hizmetine verir.

    Şöyle görünmelidir:

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneği görüntülenir.

6. **Araçlar** menüsünde **değiştirme ChangeMenuText** adlı bir komut görmeniz gerekir.

7. Komutuna tıklayın. **Menuitemcallback** çağrıldığında bildiren ileti kutusunu görmeniz gerekir. İleti kutusunu kapattığınızda, Araçlar menüsündeki komutun adının artık **Yeni metin** olduğunu görmeniz gerekir.
