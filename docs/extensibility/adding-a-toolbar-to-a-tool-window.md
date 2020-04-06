---
title: Araç Penceresine Araç Çubuğu Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 094515eb94279623974bd7b55cc9923c49625a70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740252"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Araç penceresine araç çubuğu ekleme
Bu gözden geçirme, araç penceresine araç çubuğunun nasıl ekleyeceğini gösterir.

 Araç çubuğu, komutlara bağlı düğmeler içeren yatay veya dikey bir şerittir. Araç penceresindeki araç çubuğunun uzunluğu, araç çubuğunun kenetlendiği yere bağlı olarak her zaman araç penceresinin genişliği veya yüksekliğiyle aynıdır.

 IDE'deki araç çubuklarının aksine, araç penceresindeki bir araç çubuğu sabitlenmeli ve taşınamaz veya özelleştirilemez. VSPackage umanaged koduyla yazılmışsa, araç çubuğu herhangi bir kenarına sabitlenebilir.

 Araç çubuğu ekleme hakkında daha fazla bilgi için [bkz.](../extensibility/adding-a-toolbar.md)

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleme ye](../extensibility/installing-the-visual-studio-sdk.md)bakın.

## <a name="create-a-toolbar-for-a-tool-window"></a>Araç penceresi için araç çubuğu oluşturma

1. **Hem TWTestCommand** `TWToolbar` adlı bir menü komutu ve **TestToolWindow**adlı bir araç penceresi olan bir VSIX projesi oluşturun. Daha fazla bilgi için bkz: [Menü komutu yla uzantı oluştur](../extensibility/creating-an-extension-with-a-menu-command.md) ve [araç penceresi olan uzantı oluştur.](../extensibility/creating-an-extension-with-a-tool-window.md) Araç penceresi şablonunu eklemeden önce komut öğesi şablonunu eklemeniz gerekir.

2. *TWTestCommandPackage.vsct,* Semboller bölümüne bakın. GuidTWTestCommandPackageCmdSet adlı GuidSymbol düğümünde bir araç çubuğu ve araç çubuğu grubu aşağıdaki gibi bildirir.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. `Commands` Bölümün üst kısmında bir `Menus` bölüm oluşturun. Araç `Menu` çubuğunu tanımlamak için bir öğe ekleyin.

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

     Araç çubukları alt menüler gibi iç içe işletilemiyor. Bu nedenle, bir ebeveyn atamak zorunda değilsiniz. Ayrıca, kullanıcı araç çubuklarını taşıyabileceğinden öncelik belirlemeniz de gerekyoktur. Genellikle, bir araç çubuğunun ilk yerleşimi programlı olarak tanımlanır, ancak kullanıcı tarafından sonraki değişiklikler kalıcıdır.

4. Gruplar bölümünde, araç çubuğu nun komutlarını içerecek bir grup tanımlayın.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Düğmeler bölümünde, varolan Düğme öğesinin üst öğesini araç çubuğu nun görüntülenmesi için araç çubuğu grubuna değiştirin.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Varsayılan olarak, bir araç çubuğunda komut yoksa, görünmez.

     Yeni araç çubuğu araç penceresine otomatik olarak eklenmediği için araç çubuğunun açıkça eklenmesi gerekir. Bu konu, sonraki bölümde açıklanmaktadır.

## <a name="add-the-toolbar-to-the-tool-window"></a>Araç penceresine araç çubuğu ekleme

1. TWTestCommandPackageGuids.cs *TWTestCommandPackageGuids.cs* aşağıdaki satırları ekleyin.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. Buna *TestToolWindow.cs* aşağıdaki ifadesini kullanarak ekleyin.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. TestToolWindow oluşturucu aşağıdaki satırı ekleyin.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Araç penceresindearaç çubuğunu test edin

1. Projeyi oluşturun ve hata ayıklamaya başlayın. Visual Studio deneysel örneği görünmelidir.

2. Görünüm **/ Diğer Windows** menüsünde, araç penceresini görüntülemek için **Araç Penceresi'ni** tıklatın.

     Araç penceresinin sol üst kısmında başlığın hemen altında bir araç çubuğu (varsayılan simgegibi görünüyor) görmeniz gerekir.

3. Araç çubuğunda, **TWTestCommandPackage Inside TWToolbar.TWTestCommand.MenuItemCallback()** mesajını görüntülemek için simgeyi tıklatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Araç çubuğu ekleme](../extensibility/adding-a-toolbar.md)
