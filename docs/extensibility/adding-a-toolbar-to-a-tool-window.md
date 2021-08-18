---
title: Araç Penceresine Araç Çubuğu Ekleme | Microsoft Docs
description: Tümleşik geliştirme ortamında (IDE) bir araç penceresine komutlara bağlı düğmeler içeren Visual Studio araç çubuğu eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6a2c93459dd588a1a04be098cf675aa4c58b8d37
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051371"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Araç penceresine araç çubuğu ekleme
Bu kılavuzda araç penceresine araç çubuğu ekleme gösterilir.

 Araç çubuğu, komutlara bağlı düğmeleri içeren yatay veya dikey bir şerittir. Araç penceresindeki bir araç çubuğunun uzunluğu, araç çubuğunun yerleştir olduğu yere bağlı olarak her zaman araç penceresinin genişliği veya yüksekliğiyle aynıdır.

 IDE'de araç çubuklarının aksine, araç penceresindeki bir araç çubuğunun yerleştirmesi gerekir ve taşınamaz veya özelleştirilebilir. VSPackage umanaged koduyla yazılmışsa, araç çubuğu herhangi bir kenara yerleştirebilirsiniz.

 Araç çubuğu ekleme hakkında daha fazla bilgi için bkz. [Araç çubuğu ekleme.](../extensibility/adding-a-toolbar.md)

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-toolbar-for-a-tool-window"></a>Araç penceresi için araç çubuğu oluşturma

1. `TWToolbar` **Hem TWTestCommand** adlı bir menü komutuna hem de **TestToolWindow** adlı bir araç penceresine sahip adlı bir VSIX projesi oluşturun. Daha fazla bilgi için [bkz. Menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md) ve [Araç penceresiyle uzantı oluşturma.](../extensibility/creating-an-extension-with-a-tool-window.md) Araç penceresi şablonunu eklemeden önce komut öğesi şablonunu eklemeniz gerekir.

2. *TWTestCommandPackage.vsct* içinde Semboller bölümünü bakın. guidTWTestCommandPackageCmdSet adlı GuidSymbol düğümünde aşağıdaki gibi bir araç çubuğu ve araç çubuğu grubu bildirebilirsiniz.

    ```xml
    <IDSymbol name="TWToolbar" value="0x1000" />
    <IDSymbol name="TWToolbarGroup" value="0x1050" />
    ```

3. Bölümün en üstünde `Commands` bir bölüm `Menus` oluşturun. Araç çubuğunu `Menu` tanımlamak için bir öğe ekleyin.

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

     Araç çubukları alt menüler gibi iç içe yer alamaz. Bu nedenle üst öğe atamaya gerek yok. Ayrıca, kullanıcı araç çubuklarını hareket ettirene kadar bir öncelik ayarlamak zorunda da değilsiniz. Genellikle, araç çubuğunun ilk yerleşimi program aracılığıyla tanımlanır, ancak kullanıcı tarafından yapılan sonraki değişiklikler kalıcı olur.

4. Gruplar bölümünde, araç çubuğunun komutlarını içeren bir grup tanımlayın.

    ```xml

    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />
    </Group>
    ```

5. Düğmeler bölümünde, mevcut Button öğesinin üst öğesini araç çubuğu grubu olarak değiştirarak araç çubuğunun görüntülenebilir.

    ```xml
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke TWTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Varsayılan olarak, araç çubuğunda komut yoksa görünmez.

     Yeni araç çubuğu araç penceresine otomatik olarak eklenmey olduğundan, araç çubuğunun açıkça eklenmiş olması gerekir. Bu konu, sonraki bölümde açıklanmaktadır.

## <a name="add-the-toolbar-to-the-tool-window"></a>Araç çubuğunu araç penceresine ekleme

1. *TWTestCommandPackageGuids.cs içinde* aşağıdaki satırları ekleyin.

    ```csharp
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const int TWToolbar = 0x1000;
    ```

2. *TestToolWindow.cs içinde* aşağıdaki using deyimini ekleyin.

    ```csharp
    using System.ComponentModel.Design;
    ```

3. TestToolWindow oluşturucusu içinde aşağıdaki satırı ekleyin.

    ```csharp
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);
    ```

## <a name="test-the-toolbar-in-the-tool-window"></a>Araç penceresinde araç çubuğunu test edin

1. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel Visual Studio örnek görüntü gerekir.

2. Görünüm **/ Diğer Windows** araç penceresini görüntülemek için **Test AracıWindow'a** tıklayın.

     Araç penceresinin sol üst kısmında başlığın hemen altında bir araç çubuğu (varsayılan simge gibi görünür) görüyorsanız.

3. Araç çubuğunda simgesine tıklar ve **TWToolbar.TWTestCommand.MenuItemCallback() içinde TWTestCommandPackage** iletisi görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Araç çubuğu ekleme](../extensibility/adding-a-toolbar.md)
