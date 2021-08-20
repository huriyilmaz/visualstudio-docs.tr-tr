---
title: Visual Studio menü çubuğuna menü ekleme | Microsoft Docs
description: Visual Studio tümleşik geliştirme ortamının (ıde) menü çubuğuna bir menü eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f622200066192304b2d066ad3bd3839ab2cbc0c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112015"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Visual Studio menü çubuğuna bir menü ekleyin

bu izlenecek yol, Visual Studio tümleşik geliştirme ortamının (ıde) menü çubuğuna bir menünün nasıl ekleneceğini gösterir. IDE menü çubuğu, **Dosya**, **düzenleme**, **görüntüleme**, **pencere** ve **Yardım** gibi menü kategorilerini içerir.

Visual Studio menü çubuğuna yeni bir menü eklemeden önce, komutlarınızın mevcut bir menü içine yerleştirilmesi gerekip gerekmediğini göz önünde bulundurun. Komut yerleşimi hakkında daha fazla bilgi için bkz. [Visual Studio menüleri ve komutları](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Menüler, projenin *. vsct* dosyasında bildirilmiştir. Menüler ve *. vsct* dosyaları hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).

Bu yönergeyi tamamlayarak, bir komut içeren **Test menüsü** adlı bir menü oluşturabilirsiniz.

:::moniker range=">=vs-2019"
> [!NOTE]
> Visual Studio 2019 ' den başlayarak, uzantılara göre katkıda bulunulan üst düzey menüler **uzantılar** menüsünün altına yerleştirilir.
:::moniker-end

## <a name="prerequisites"></a>Önkoşullar

Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezi ' nden yüklemeyin. Visual Studio kurulum 'da isteğe bağlı bir özellik olarak eklenmiştir. VS SDK ' yı daha sonra da yükleyebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SDK 'yı ınstall](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Özel bir komut öğesi şablonu olan bir VSıX projesi oluşturma

1. Adlı bir VSıX projesi oluşturun `TopLevelMenu` . vsıx proje şablonunu, **yeni Project** iletişim kutusunda "vsıx" arayarak bulabilirsiniz.  Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

::: moniker range="vs-2017"

2. Proje açıldığında, **TestCommand** adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >   **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#/genişletilebilirlik** ' e gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *TestCommand. cs* olarak değiştirin.

::: moniker-end

::: moniker range=">=vs-2019"

2. Proje açıldığında, **TestCommand** adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve   >   **Yeni öğe** Ekle ' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#/genişletilebilirlik** ' e gidin ve **komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını *TestCommand. cs* olarak değiştirin.

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>IDE menü çubuğunda bir menü oluşturun

::: moniker range="vs-2017"

1. **Çözüm Gezgini**' de *TestCommandPackage. vsct* öğesini açın.

    Dosyanın sonunda, `<Symbols>` birkaç düğüm içeren bir düğüm vardır `<GuidSymbol>` . Adlı düğümde, `guidTestCommandPackageCmdSet` aşağıdaki gibi yeni bir sembol ekleyin:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. `<Menus>` `<Commands>` Düğümde yalnızca daha önce boş bir düğüm oluşturun `<Groups>` . Düğümünde, `<Menus>` `<Menu>` aşağıdaki gibi bir düğüm ekleyin:

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`Menünün ve `id` değerleri komut kümesindeki komut kümesini ve belirli menüyü belirler.

    `guid` `id` üst öğesi ve değerleri, araç ve eklenti menülerini içeren Visual Studio menü çubuğunun bölümünde yer alan menüyü konumlandırır.

    `<ButtonText>`Öğesi, metnin menü öğesinde görünmesi gerektiğini belirtir.

3. `<Groups>`Bölümünde `<Group>` öğesini bulun ve `<Parent>` öğesini yeni eklediğimiz menüye işaret etmek üzere değiştirin:

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Bu, grubun yeni menünün bir parçasını oluşturur.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini** içinde *TopLevelMenuPackage. vsct* öğesini açın.

    Dosyanın sonunda, `<Symbols>` birkaç düğüm içeren bir düğüm vardır `<GuidSymbol>` . Adlı düğümde, `guidTopLevelMenuPackageCmdSet` aşağıdaki gibi yeni bir sembol ekleyin:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. `<Menus>` `<Commands>` Düğümde yalnızca daha önce boş bir düğüm oluşturun `<Groups>` . Düğümünde, `<Menus>` `<Menu>` aşağıdaki gibi bir düğüm ekleyin:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`Menünün ve `id` değerleri komut kümesindeki komut kümesini ve belirli menüyü belirler.

    `guid` `id` üst öğesi ve değerleri, araç ve eklenti menülerini içeren Visual Studio menü çubuğunun bölümünde yer alan menüyü konumlandırır.

    `<ButtonText>`Öğesi, metnin menü öğesinde görünmesi gerektiğini belirtir.

3. `<Groups>`Bölümünde `<Group>` öğesini bulun ve `<Parent>` öğesini yeni eklediğimiz menüye işaret etmek üzere değiştirin:

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Bu, grubun yeni menünün bir parçasını oluşturur.

::: moniker-end

4. `<Buttons>`Bölümünde `<Button>` düğümünü bulun. Ardından, `<Strings>` düğümünde `<ButtonText>` öğesini olarak değiştirin `Test Command` .

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Paket şablonunun üst öğesi olarak ayarlanmış bir öğe ürettiğine dikkat edin `Button` `MyMenuGroup` . Sonuç olarak, bu komut menüde görünür.

## <a name="build-and-test-the-extension"></a>Uzantıyı derleme ve test etme

1. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örneğin bir örneği görünmelidir.

::: moniker range="vs-2017"

2. Deneysel örnekteki menü çubuğu bir **Test menü** menüsü içermelidir.

::: moniker-end

::: moniker range=">=vs-2019"

2. Deneysel örnekteki **Uzantılar** menüsü bir **Test menü** menüsü içermelidir.

::: moniker-end

3. **Test menüsü** menüsünde, **test komutu**' nı seçin.

    İleti kutusu görünmelidir ve "TestCommand. TestCommand. Menuıitemcallback ()" iletisinin "Testkomutu" iletisini görüntülemesi gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
