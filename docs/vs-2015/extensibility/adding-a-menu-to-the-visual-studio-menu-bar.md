---
title: Menü çubuğuna menü ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184933"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Visual Studio Menü Çubuğuna Menü Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, Visual Studio tümleşik geliştirme ortamının (IDE) menü çubuğuna bir menünün nasıl ekleneceğini gösterir. IDE menü çubuğu, **Dosya**, **düzenleme**, **görüntüleme**, **pencere**ve **Yardım**gibi menü kategorilerini içerir.

 Visual Studio menü çubuğuna yeni bir menü eklemeden önce, komutlarınızın mevcut bir menü içine yerleştirilmesi gerekip gerekmediğini göz önünde bulundurun. Komut yerleşimi hakkında daha fazla bilgi için bkz. [Visual Studio Için menüler ve komutlar](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Menüler, projenin. vsct dosyasında bildirilmiştir. Menüler ve. vsct dosyaları hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).

 Bu yönergeyi tamamlayarak, bir komut içeren **TestMenu** adlı bir menü oluşturabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Özel bir komut öğesi şablonu olan bir VSıX projesi oluşturma

1. Adlı bir VSıX projesi oluşturun `TopLevelMenu` . VSIX proje şablonunu, **Visual C#** genişletilebilirliği altında **Yeni proje** iletişim kutusunda bulabilirsiniz  /  **Extensibility**.  Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Proje açıldığında, **TestCommand**adlı özel bir komut öğesi şablonu ekleyin. **Çözüm Gezgini**, proje düğümüne sağ tıklayın ve **Ekle/yeni öğe**' yi seçin. **Yeni öğe Ekle** iletişim kutusunda, **Visual C#/genişletilebilirlik** ' e gidin ve **özel komut**' yi seçin. Pencerenin alt kısmındaki **ad** alanında, komut dosyası adını **TestCommand.cs**olarak değiştirin.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>IDE menü çubuğunda bir menü oluşturma

#### <a name="to-create-a-menu"></a>Bir menü oluşturmak için

1. **Çözüm Gezgini**' de TestCommandPackage. vsct öğesini açın.

     Dosyanın sonunda, \<Symbols> birkaç düğüm içeren bir düğüm vardır \<GuidSymbol> . GuidTestCommandPackageCmdSet adlı düğümde aşağıdaki şekilde yeni bir sembol ekleyin:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. \<Menus> \<Commands> Düğümde yalnızca daha önce boş bir düğüm oluşturun \<Groups> . Düğümünde, \<Menus> \<Menu> aşağıdaki gibi bir düğüm ekleyin:

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

     `guid`Menünün ve `id` değerleri komut kümesindeki komut kümesini ve belirli menüyü belirler.

     `guid` `id` Üst öğesi ve değerleri, Visual Studio menü çubuğunun araç ve eklenti menülerini içeren bölümündeki menüyü konumlandırır.

     Dizenin değeri, `CommandName` metnin menü öğesinde görünmesi gerektiğini belirtir.

3. \<Groups>Bölümünde \<Group> öğesini bulun ve \<Parent> öğesini yeni eklediğimiz menüye işaret etmek üzere değiştirin:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Bu, grubun yeni menünün bir parçasını oluşturur.

4. Bölümünü bulun `Buttons` . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Paket şablonunun üst öğesi olarak ayarlanmış bir öğe ürettiğine dikkat edin `Button` `MyMenuGroup` . Sonuç olarak, bu komut menüde görünür.

## <a name="building-and-testing-the-extension"></a>Uzantıyı derleme ve test etme

1. Projeyi derleyin ve hata ayıklamayı başlatın. Deneysel örneğin bir örneği görünmelidir.

2. Deneysel örnekteki menü çubuğu bir **TestMenu** menüsü içermelidir.

3. **TestMenu** menüsünde **test komutunu çağır**' a tıklayın.

     İleti kutusu görünmelidir ve "TestCommand paketini TopLevelMenu. TestCommand. Menuıitemcallback ()" Içinde görüntüler. Bu, yeni komutun çalışıp çalışmadığını gösterir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
