---
title: Komutun görünümünü değiştirme | Microsoft Docs
description: Komutların kullanılabilir/kullanılamaz, gizli/gösterilen veya işaretli/işaretsiz gibi bir komutun görünümünü değiştirme hakkında geri bildirim sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6344d5d58856c420807e80020d80f0067d0f973c566b3e613782e5fa0b85ef11
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452634"
---
# <a name="change-the-appearance-of-a-command"></a>Komutun görünümünü değiştirme
Bir komutun görünümünü değiştirerek, kullanıcıya geri bildirim sağlayabilirsiniz. Örneğin, kullanılamayan bir komutun farklı görünmesini isteyebilirsiniz. Komutları kullanılabilir veya kullanılamaz hale getirebilirsiniz, gizleyebilir veya gösterebilir veya menüdeki bu öğeleri denetleyebilir ya da işaretini kaldırabilirsiniz.

Bir komutun görünüşünü değiştirmek için şu eylemlerden birini gerçekleştirin:

- Komut tablosu dosyasındaki komut tanımında uygun bayrakları belirtin.

- Hizmetini kullanın <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> .

- Arabirimini uygulayın <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ve ham komut nesnelerini değiştirin.

  Aşağıdaki adımlarda, yönetilen paket çerçevesi (MPF) kullanılarak bir komutun görünümünü bulma ve güncelleştirme işlemi gösterilmektedir.

### <a name="to-change-the-appearance-of-a-menu-command"></a>Bir menü komutunun görünüşünü değiştirmek için

1. Adlı bir menü öğesi oluşturmak için [menü komutunun metnini değiştirme](../extensibility/changing-the-text-of-a-menu-command.md) bölümündeki yönergeleri izleyin `New Text` .

2. *ChangeMenuText. cs* dosyasında aşağıdaki using ifadesini ekleyin:

    ```csharp
    using System.Security.Permissions;
    ```

3. *Changemenutextpackageguid. cs* dosyasında aşağıdaki satırı ekleyin:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. *ChangeMenuText. cs* dosyasında, ShowMessageBox yöntemindeki kodu aşağıdaki kodla değiştirin:

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Nesnesinden güncelleştirmek istediğiniz komutu edinin <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> ve ardından komut nesnesinde uygun özellikleri ayarlayın. Örneğin, aşağıdaki yöntem, belirtilen komutu VSPackage komut kümesinden kullanılabilir veya kullanılamaz hale getirir. Aşağıdaki kod, menü öğesinin tıklandıktan sonra kullanılamaz olarak adlandırılmasına neden olur `New Text` .

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
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

6. Projeyi derleyin ve hata ayıklamayı başlatın. deneysel Visual Studio örneği görünmelidir.

7. **Araçlar** menüsünde, **ChangeMenuText komutunu çağır** komutuna tıklayın. Bu noktada, komut adı **ChangeMenuText olarak çağırılır**, bu nedenle komut Işleyicisi **ChangeMyCommand ()** öğesini çağırmaz.

8. **Araçlar** menüsünde şimdi **Yeni metin** görmeniz gerekir. **Yeni metin**' e tıklayın. Komutun şimdi gri olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
- [VSPackages Kullanıcı arabirimi öğeleri ekleme](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
