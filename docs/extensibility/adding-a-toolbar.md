---
title: Araç çubuğu ekleme | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamına (ıde) komutlara bağlanan düğmeleri içeren bir araç çubuğu eklemeyi öğrenin.
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
ms.openlocfilehash: 40d28a92e6c4c0695c21bc7271417aff2fd778f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035325"
---
# <a name="add-a-toolbar"></a>Araç çubuğu ekle
bu izlenecek yol, Visual Studio ıde 'ye bir araç çubuğunun nasıl ekleneceğini gösterir.

 Bir araç çubuğu, komutlara bağlanan düğmeleri içeren yatay veya dikey bir şerit olur. Uygulamasına bağlı olarak, IDE 'deki bir araç çubuğu, ana IDE penceresinin herhangi bir tarafına yerleştirilmiş olan veya diğer pencerelerin önünde kalmak için yeniden konumlandırılabilir.

 Ayrıca, kullanıcılar bir araç çubuğuna komut ekleyebilir veya **Özelleştir** iletişim kutusunu kullanarak bunları kaldırabilir. Genellikle, VSPackages 'teki araç çubukları Kullanıcı tarafından özelleştirilebilir. IDE tüm özelleştirmeyi işler ve VSPackage, komutlara yanıt verir. VSPackage 'ın bir komutun fiziksel olarak nerede bulunduğunu bilmeleri gerekmez.

 Menüler hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Araç çubuğuyla uzantı oluşturma
 Adlı bir VSıX projesi oluşturun `IDEToolbar` . **ToolbarTestCommand** adlı bir menü komut öğesi şablonu ekleyin. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>IDE için bir araç çubuğu oluşturma

1. *ToolbarTestCommandPackage. vsct* içinde semboller bölümüne bakın. Guıdtoolbartestcommandpackagecmdset adlı GuidSymbol öğesinde, bir araç çubuğu ve bir araç çubuğu grubu için aşağıdaki gibi bildirimler ekleyin.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. Komutlar bölümünün en üstünde bir menü bölümü oluşturun. Araç çubuğinizi tanımlamak için menüler bölümüne bir menü öğesi ekleyin.

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

     Araç çubukları alt menüler gibi iç içe geçirilemez. Bu nedenle, bir üst grup atamanız gerekmez. Ayrıca, Kullanıcı araç çubuklarını taşıyabildiğinden, öncelik ayarlamanız gerekmez. Genellikle, bir araç çubuğunun ilk yerleşimi programlı olarak tanımlanır, ancak kullanıcı tarafından sonraki değişiklikler kalıcı hale getirilir.

3. [Gruplar](../extensibility/groups-element.md) bölümünde, varolan Grup girişinden sonra, araç çubuğu komutlarını Içeren bir [Grup](../extensibility/group-element.md) öğesi tanımlayın.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Düğmenin araç çubuğunda görünmesini sağlayın. Düğmeler bölümünde, düğmedeki üst bloğu araç çubuğuna değiştirin. Ortaya çıkan düğme bloğu şöyle görünmelidir:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Varsayılan olarak, bir araç çubuğunda komut yoksa, görüntülenmez.

5. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örnek görünmelidir.

6. araç çubuklarının listesini almak için Visual Studio menü çubuğuna sağ tıklayın. **Test araç çubuğunu** seçin.

7. Artık araç çubuğudur dosyaları bul simgesinin sağında bir simge olarak görmeniz gerekir. Simgeye tıkladığınızda, ToolbarTestCommandPackage adlı bir ileti kutusu görmeniz gerekir **. Onıtoolbar. ToolbarTestCommand. Menuıitemcallback () içinde**.

## <a name="see-also"></a>Ayrıca bkz.
- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
