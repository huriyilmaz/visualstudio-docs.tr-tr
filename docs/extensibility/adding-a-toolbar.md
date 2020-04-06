---
title: Araç Çubuğu Ekleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 655cd87fe59cf4f42361cc24a63eb56653caae1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740222"
---
# <a name="add-a-toolbar"></a>Araç Çubuğu Ekleme
Bu gözden geçirme, Visual Studio IDE'ye nasıl bir araç çubuğu ekleyeceğinigösterir.

 Araç çubuğu, komutlara bağlı düğmeler içeren yatay veya dikey şerittir. Uygulanmasına bağlı olarak, IDE'deki bir araç çubuğu yeniden konumlandırılabilir, ana IDE penceresinin herhangi bir tarafına kenetlenebilir veya diğer pencerelerin önünde kalmak üzere yapılabilir.

 Ayrıca, kullanıcılar bir araç çubuğuna komutlar ekleyebilir veya **Özelleştir** iletişim kutusunu kullanarak komutları kaldırabilir. Genellikle, VSPackages araç çubukları kullanıcı tarafından özelleştirilebilir. IDE tüm özelleştirmeyi işler ve VSPackage komutlara yanıt verir. VSPackage bir komutun fiziksel olarak nerede olduğunu bilmek zorunda değildir.

 Menüler hakkında daha fazla bilgi için [Komutlar, menüler ve araç çubuklarına](../extensibility/internals/commands-menus-and-toolbars.md)bakın.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-toolbar"></a>Araç çubuğuyla uzantı oluşturma
 Adlı `IDEToolbar`bir VSIX projesi oluşturun. **ToolbarTestCommand**adlı bir menü komut öğesi şablonu ekleyin. Bunun nasıl yapılacılayaç yapıla [Create an extension with a menu command](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="create-a-toolbar-for-the-ide"></a>IDE için bir araç çubuğu oluşturma

1. *ToolbarTestCommandPackage.vsct' de*Semboller bölümüne bakın. guidToolbarTestCommandPackageCmdSet adlı GuidSymbol öğesinde, aşağıdaki gibi bir araç çubuğu ve araç çubuğu grubu için bildirimler ekleyin.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Komutlar bölümünün üst kısmında, bir Menüler bölümü oluşturun. Araç çubuğunuzu tanımlamak için Menüler bölümüne bir Menü öğesi ekleyin.

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

     Araç çubukları alt menüler gibi iç içe geçemez. Bu nedenle, bir üst grup atamak zorunda değildir. Ayrıca, kullanıcı araç çubuklarını taşıyabileceğinden öncelik belirlemeniz gerekmez. Genellikle, bir araç çubuğunun ilk yerleşimi programlı olarak tanımlanır, ancak kullanıcı tarafından sonraki değişiklikler kalıcıdır.

3. [Gruplar](../extensibility/groups-element.md) bölümünde, varolan grup girişinden sonra, araç çubuğunun komutlarını içerecek bir [Grup](../extensibility/group-element.md) öğesi tanımlayın.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Düğmenin araç çubuğunda görünmesini sağla. Düğmeler bölümünde, Düğme'deki Üst Öğe bloğunu araç çubuğuna değiştirin. Ortaya çıkan Düğme bloğu aşağıdaki gibi görünmelidir:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Varsayılan olarak, bir araç çubuğunda komut yoksa, görünmez.

5. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örnek görünmelidir.

6. Araç çubuklarının listesini almak için Visual Studio menü çubuğuna sağ tıklayın. **Test Araç Çubuğu'nı**seçin.

7. Araç çubuğunuzu artık Dosyalarda Bul simgesinin sağında bir simge olarak görmeniz gerekir. Simgeyi tıklattığınızda, ToolbarTestCommandPackage yazan bir ileti kutusu görmeniz **gerekir. İç IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
