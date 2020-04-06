---
title: Bir Komutun Görünümünü Değiştirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739855"
---
# <a name="change-the-appearance-of-a-command"></a>Komutun görünümünü değiştirme
Bir komutun görünümünü değiştirerek kullanıcınıza geri bildirim sağlayabilirsiniz. Örneğin, bir komutun kullanılamadığında farklı görünmesini isteyebilirsiniz. Komutları kullanılabilir veya kullanılamaz hale getirebilir, bunları gizleyebilir veya gösterebilir veya menüde bunları denetleyebilir veya denetleyebilirsiniz.

Bir komutun görünümünü değiştirmek için aşağıdaki eylemlerden birini gerçekleştirin:

- Komut tablosu dosyasındaki komut tanımında uygun bayrakları belirtin.

- <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Hizmeti kullanın.

- Arabirimi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> uygulayın ve ham komut nesnelerini değiştirin.

  Aşağıdaki adımlar, Yönetilen Paket Çerçevesi 'ni (MPF) kullanarak bir komutun görünümünü nasıl bulabileceğinizi ve güncelleştireceğimi gösterir.

### <a name="to-change-the-appearance-of-a-menu-command"></a>Menü komutunun görünümünü değiştirmek için

1. Adlı `New Text`bir menü öğesi oluşturmak için [menü komutunun metnini değiştir'deki](../extensibility/changing-the-text-of-a-menu-command.md) yönergeleri izleyin.

2. *ChangeMenuText.cs* dosyasında, aşağıdaki leri kullanarak ifade ekleyin:

    ```csharp
    using System.Security.Permissions;
    ```

3. *ChangeMenuTextPackageGuids.cs* dosyasına aşağıdaki satırı ekleyin:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. *ChangeMenuText.cs* dosyasında, ShowMessageBox yöntemindeki kodu aşağıdakilerle değiştirin:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> Nesneden güncelleştirmek istediğiniz komutu edinin ve ardından komut nesnesi üzerinde uygun özellikleri ayarlayın. Örneğin, aşağıdaki yöntem, VSPackage komut kümesinden belirtilen komutu kullanılabilir veya kullanılamaz hale getirir. Aşağıdaki kod, tıklatıldıktan `New Text` sonra adlı menü öğesini kullanılamaz hale getirir.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))
            as OleMenuCommandService;
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);
        MenuCommand mc = mcs.FindCommand(newCmdID);
        if (mc != null)
        {
            mc.Enabled = enableCmd;
            cmdUpdated = true;
        }
        return cmdUpdated;
    }
    ```

6. Projeyi oluşturun ve hata ayıklamaya başlayın. Visual Studio'nun deneysel örneği görünmelidir.

7. **Araçlar** **menüsünde, Invoke ChangeMenuText** komutunu tıklatın. Bu noktada komut adı **ChangeMenuText çağırın**, böylece komut işleyicisi **ChangeMyCommand()** aramaz.

8. **Araçlar** menüsünde artık **Yeni Metin'i**görmelisiniz. **Yeni Metin'i**tıklatın. Komut şimdi gri olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
- [VSPackages kullanıcı arabirimi öğelerini nasıl ekler?](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [Visual Studio komut tablosu (. Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
