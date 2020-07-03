---
title: Araç penceresine araç çubuğu ekleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5351fe6a713c217f8fca20d6740b542dc75f053
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904122"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Araç penceresine araç çubuğu ekleme
Bu izlenecek yol, araç penceresine bir araç çubuğunun nasıl ekleneceğini gösterir.

 Bir araç çubuğu, komutlara bağlanan düğmeleri içeren yatay veya dikey bir şerit olur. Araç çubuğundaki bir araç çubuğunun uzunluğu, araç çubuğunun bulunduğu yere bağlı olarak araç penceresinin genişliği veya yüksekliğiyle aynı her zaman aynıdır.

 IDE 'deki araç çubuklarının aksine, araç penceresindeki bir araç çubuğu yerleşik olmalıdır ve taşınamaz ya da özelleştirilemez. VSPackage, umanyaşlandırılmış kodda yazılmışsa, araç çubuğu herhangi bir kenara yerleştirilebilir.

 Araç çubuğu ekleme hakkında daha fazla bilgi için bkz. [araç çubuğu ekleme](../extensibility/adding-a-toolbar.md).

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-toolbar-for-a-tool-window"></a>Araç penceresi için araç çubuğu oluşturma

1. `TWToolbar` **TWTestCommand** adlı bir menü komutu ve **TestToolWindow**adlı bir araç penceresi olan adlı bir VSIX projesi oluşturun. Daha fazla bilgi için bkz. bir [menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md) ve [araç penceresi ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md). Araç penceresi şablonunu eklemeden önce komut öğesi şablonunu eklemeniz gerekir.

2. *TWTestCommandPackage. vsct*içinde semboller bölümüne bakın. GuidTWTestCommandPackageCmdSet adlı GuidSymbol düğümünde aşağıdaki gibi bir araç çubuğu ve bir araç çubuğu grubu bildirin.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Bölümünün üst kısmında `Commands` bir `Menus` bölüm oluşturun. `Menu`Araç çubuğunu tanımlamak için bir öğe ekleyin.

    ```xml
    <Menus>
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     Araç çubukları alt menüler gibi iç içe geçemez. Bu nedenle, bir üst öğe atamanız gerekmez. Ayrıca, Kullanıcı araç çubuklarını taşıyabildiğinden, öncelik ayarlamanız gerekmez. Genellikle, bir araç çubuğunun ilk yerleşimi programlı olarak tanımlanır, ancak kullanıcı tarafından sonraki değişiklikler kalıcı hale getirilir.

4. Gruplar bölümünde, araç çubuğuna ait komutları içerecek bir grup tanımlayın.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Düğmeler bölümünde, araç çubuğunun görüntülenebilmesi için mevcut düğme öğesinin üst öğesini araç çubuğu grubuyla değiştirin.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Varsayılan olarak, bir araç çubuğunda komut yoksa, görüntülenmez.

     Yeni araç çubuğu araç penceresine otomatik olarak eklenmediği için, araç çubuğunun açık olarak eklenmesi gerekir. Bu konu, sonraki bölümde açıklanmaktadır.

## <a name="add-the-toolbar-to-the-tool-window"></a>Araç çubuğunu araç penceresine ekleyin

1. *TWTestCommandPackageGuids.cs* içinde aşağıdaki satırları ekleyin.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. *TestToolWindow.cs* içinde aşağıdaki using ifadesini ekleyin.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. TestToolWindow oluşturucusunda aşağıdaki satırı ekleyin.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Araç çubuğunu araç penceresinde test etme

1. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio deneysel örneği görünmelidir.

2. Araç penceresini görüntülemek için **Görünüm/diğer pencereler** menüsünde **Test ToolWindow** ' e tıklayın.

     Araç penceresinin sol üst kısmında, başlığın hemen altındaki bir araç çubuğu (varsayılan simge gibi görünür) görmeniz gerekir.

3. Araç çubuğunda **TWTestCommandPackage öğesini TWTestCommand. Menuıitemcallback () içinde**göstermek için simgeye tıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Araç çubuğu ekle](../extensibility/adding-a-toolbar.md)
