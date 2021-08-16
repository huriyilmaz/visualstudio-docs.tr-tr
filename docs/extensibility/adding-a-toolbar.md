---
title: Araç Çubuğu Ekleme | Microsoft Docs
description: Tümleşik geliştirme ortamına (IDE) komutlara bağlı düğmeler içeren Visual Studio araç çubuğu eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ca32c96358982352d1570f916799409fbf8090a270424beaf5e1651a54d66a5d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434977"
---
# <a name="add-a-toolbar"></a>Araç Çubuğu Ekleme
Bu kılavuzda, IDE'ye araç çubuğu Visual Studio gösterir.

 Araç çubuğu, komutlara bağlı düğmeleri içeren yatay veya dikey bir şerittir. Uygulamasına bağlı olarak, IDE'de bir araç çubuğu yeniden konumlandırabilir, ana IDE penceresinin herhangi bir tarafına konumlandırabilir veya diğer pencerelerin önünde kalacak şekilde ekleyebilirsiniz.

 Ayrıca, kullanıcılar özelleştir iletişim kutusunu kullanarak bir araç çubuğuna komut ekleyebilir veya araç **çubuğundan komut** kaldırabilir. VSPackage'lar genellikle kullanıcı tarafından özelleştirilebilir. IDE tüm özelleştirmeleri işler ve VSPackage komutlara yanıt verir. VSPackage'ın bir komutun fiziksel olarak nerede olduğunu bilmek zorunda değildir.

 Menüler hakkında daha fazla bilgi için [bkz. Komutlar, menüler ve araç çubukları.](../extensibility/internals/commands-menus-and-toolbars.md)

## <a name="prerequisites"></a>Önkoşullar
 2015 Visual Studio den başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-toolbar"></a>Araç çubuğu ile uzantı oluşturma
 adlı bir VSIX projesi `IDEToolbar` oluşturun. **ToolbarTestCommand** adlı bir menü komut öğesi şablonu ekleyin. Bunun nasıl olduğu hakkında bilgi için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="create-a-toolbar-for-the-ide"></a>IDE için araç çubuğu oluşturma

1. *ToolbarTestCommandPackage.vsct* içinde Semboller bölümünü seçin. guidToolbarTestCommandPackageCmdSet adlı GuidSymbol öğesinde, bir araç çubuğu ve araç çubuğu grubu için bildirimleri aşağıdaki gibi ekleyin.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Komutlar bölümünün en üstünde bir Menüler bölümü oluşturun. Araç çubuğularınızı tanımlamak için Menüler bölümüne bir Menü öğesi ekleyin.

    ```xml
    <Menus>
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"
            type="Toolbar" >
            <CommandFlag>DefaultDocked</CommandFlag>
            <Strings>
                <ButtonText>Test Toolbar</ButtonText>
                <CommandName>Test Toolbar</CommandName>
            </Strings>
          </Menu>
    </Menus>
    ```

     Araç çubukları alt menüler gibi iç içe olamaz. Bu nedenle, bir üst grup atamaya gerek yok. Ayrıca, kullanıcı araç çubuklarını hareket ettirene kadar bir öncelik ayarlamak zorunda değildir. Genellikle, araç çubuğunun ilk yerleşimi program aracılığıyla tanımlanır, ancak kullanıcı tarafından yapılan sonraki değişiklikler kalıcı olur.

3. Gruplar [bölümünde,](../extensibility/groups-element.md) mevcut grup girdiden sonra, araç [çubuğunun komutlarını](../extensibility/group-element.md) içeren bir Group öğesi tanımlayın.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Düğmenin araç çubuğunda görünmesini sağlar. Düğmeler bölümünde, Düğme'de Üst bloğu araç çubuğuyla değiştirin. Sonuçta elde edilen Düğme bloğu şu şekilde görünüyor:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Varsayılan olarak, araç çubuğunda komut yoksa görünmez.

5. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel örneğin görünmesi gerekir.

6. Araç çubuklarının listesini Visual Studio menü çubuğuna sağ tıklayın. Test Araç **Çubuğu'nu seçin.**

7. Artık Dosyalarda Bul simgesinin sağ köşesinde bir simge olarak araç çubuğu görüntüleyebilirsiniz. Simgeye tıklarsanız **ToolbarTestCommandPackage iletisi görüntülenir. IDEToolbar.ToolbarTestCommand.MenuItemCallback() içinde.**

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
