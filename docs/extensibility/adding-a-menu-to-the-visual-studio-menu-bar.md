---
title: Visual Studio Menü Çubuğuna Menü Ekleme | Microsoft Dokümanlar
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740315"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Visual Studio menü çubuğuna menü ekleme

Bu gözden geçirme, Visual Studio tümleşik geliştirme ortamının (IDE) menü çubuğuna nasıl bir menü ekleyeceğinigösterir. IDE menü **çubuğu, Dosya**, **Edit**, **Görünüm**, **Pencere**ve **Yardım**gibi menü kategorileri içerir.

Visual Studio menü çubuğuna yeni bir menü eklemeden önce, komutlarınızın varolan bir menüye yerleştirilip yerleştirilmeyeceğini göz önünde bulundurun. Komut yerleşimi hakkında daha fazla bilgi için [Visual Studio için Menüler ve komutlara](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)bakın.

Menüler projenin *.vsct* dosyasında bildirilir. Menüler ve *.vsct* dosyaları hakkında daha fazla bilgi için [Komutlar, menüler ve araç çubuklarına](../extensibility/internals/commands-menus-and-toolbars.md)bakın.

Bu izbiyi tamamlayarak, **testmenüsü** adında tek bir komut içeren bir menü oluşturabilirsiniz.

> [!NOTE]
> VS 2019'da uzantıların katkıda olduğu üst düzey menüler **Uzanlar** menüsünün altına yerleştirilir.

## <a name="prerequisites"></a>Ön koşullar

Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleyin.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Özel komut öğesi şablonu olan bir VSIX projesi oluşturma

1. Adlı `TopLevelMenu`bir VSIX projesi oluşturun. "vsix" aramasını yaparak **VSIX** proje şablonunu Yeni Proje iletişim kutusunda bulabilirsiniz.  Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Proje açıldığında, **TestCommand**adlı özel bir komut öğesi şablonu ekleyin. Çözüm **Gezgini'nde**proje düğümüne sağ tıklayın ve**Yeni Öğe** **Ekle'yi** >  seçin. Yeni **Öğe Ekle** iletişim kutusunda Visual **C# / Genişletilebilirlik'e** gidin ve **Özel Komut'u**seçin. Pencerenin altındaki **Ad** alanında, komut dosyası adını *TestCommand.cs*olarak değiştirin.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>IDE menü çubuğunda menü oluşturma

::: moniker range="vs-2017"

1. **Solution**Explorer'da, *TestCommandPackage.vsct'i*açın.

    Dosyanın sonunda, birkaç \< \<GuidSymbol> düğümü içeren bir Semboller> düğümü vardır. guidTestCommandPackageCmdSet adlı düğümde, aşağıdaki gibi yeni bir simge ekleyin:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Gruplar>'den \< \<hemen önce, \<düğüm> komutlarda boş bir Menü> düğüm oluşturun. Menüler \<düğümü>, aşağıdaki \<gibi bir Menü> düğümü ekleyin:

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid` Menünün `id` ve değerleri komut kümesini ve komut kümesindeki belirli menüyü belirtir.

    Üst `guid` `id` öğenin ve değerlerinin ve menüyü Visual Studio menü çubuğunun Araçlar ve Eklentiler menülerini içeren bölümünde konumlandırın.

    Dize `CommandName` değeri, metnin menü öğesinde görünmesi gerektiğini belirtir.

3. \<> Gruplar bölümünde, Grup \<>'ni \<bulun ve Üst> öğesini az önce eklediğimiz menüye işaret etmek üzere değiştirin:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Bu, grubu yeni menünün bir parçası haline getirir.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Solution**Explorer'da, *TopLevelMenuPackage.vsct'i*açın.

    Dosyanın sonunda, birkaç \< \<GuidSymbol> düğümü içeren bir Semboller> düğümü vardır. GuidTopLevelMenuPackageCmdSet adlı düğümde, aşağıdaki gibi yeni bir simge ekleyin:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Gruplar>'den \< \<hemen önce, \<düğüm> komutlarda boş bir Menü> düğüm oluşturun. Menüler \<düğümü>, aşağıdaki \<gibi bir Menü> düğümü ekleyin:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid` Menünün `id` ve değerleri komut kümesini ve komut kümesindeki belirli menüyü belirtir.

    Üst `guid` `id` öğenin ve değerlerinin ve menüyü Visual Studio menü çubuğunun Araçlar ve Eklentiler menülerini içeren bölümünde konumlandırın.

    Dize `CommandName` değeri, metnin menü öğesinde görünmesi gerektiğini belirtir.

3. \<> Gruplar bölümünde, Grup \<>'ni \<bulun ve Üst> öğesini az önce eklediğimiz menüye işaret etmek üzere değiştirin:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Bu, grubu yeni menünün bir parçası haline getirir.

::: moniker-end

4. `Buttons` Bölümü bulun. Paket şablonunüst [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] öğesini `Button` '' olarak ayarlayan bir öğe oluşturduğuna `MyMenuGroup`dikkat edin. Sonuç olarak, bu komut menünüzde görünür.

## <a name="build-and-test-the-extension"></a>Uzantıyı oluşturma ve test edin

1. Projeyi oluşturun ve hata ayıklamaya başlayın. Deneysel örneğin bir örneği görünmelidir.

::: moniker range="vs-2017"

2. Deneme örneğindeki menü çubuğu bir **TestMenu** menüsü içermelidir.

::: moniker-end

::: moniker range=">=vs-2019"

2. Deneme örneğindeki **Uzantılar** menüsü bir **TestMenu** menüsü içermelidir.

::: moniker-end

3. **TestMenüsü** menüsünde, **Test Komutunu Çağır'ı**tıklatın.

     İleti kutusu görünmeli ve "TestKomut Paketi Inside TopLevelMenu.TestCommand.MenuItemCallback()" iletisini görüntülemelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
