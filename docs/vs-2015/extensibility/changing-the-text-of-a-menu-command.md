---
title: Menü komutunun metnini değiştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184489"
---
# <a name="changing-the-text-of-a-menu-command"></a>Bir Menü Komutunun Metnini Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşağıdaki adımlarda, hizmetini kullanarak bir menü komutunun metin etiketinin nasıl değiştirileceği gösterilmektedir <xref:System.ComponentModel.Design.IMenuCommandService> .  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Bir menü komut etiketini ımtrcommandservice ile değiştirme  
  
1. `MenuText` **ChangeMenuText**adlı bir menü komutuyla adlı bir VSIX projesi oluşturun. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. . Vstc dosyasında, `TextChanges` Aşağıdaki örnekte gösterildiği gibi, menü komutunuz bayrağını ekleyin.  
  
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
  
3. ChangeMenuText.cs dosyasında, menü komutu görüntülenmeden önce çağrılacak bir olay işleyicisi oluşturun.  
  
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
  
5. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio 'nun deneysel örneği görüntülenir.  
  
6. **Araçlar** menüsünde **değiştirme ChangeMenuText**adlı bir komut görmeniz gerekir.  
  
7. Komutuna tıklayın. MenuItemCallback çağrıldığında bildiren ileti kutusunu görmeniz gerekir. İleti kutusunu kapattığınızda, Araçlar menüsündeki komutun adının artık **Yeni metin**olduğunu görmeniz gerekir.
