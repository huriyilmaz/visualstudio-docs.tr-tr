---
title: Menü komutlarını yerelleştirme | Microsoft Docs
description: VSPackage için yerelleştirilmiş. vsct dosyaları ve yerelleştirilmiş. resx dosyaları oluşturarak menü ve araç çubuğu komutları için yerelleştirilmiş metin sağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/08/2019
ms.topic: how-to
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 12a8801e9629de97bed6e35dbdcc3bc8d14a1653f0692aca3a46f4deddd91430
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121401095"
---
# <a name="localize-menu-commands"></a>Yerelleştirmek menü komutları

VSPackage için yerelleştirilmiş *. vsct* dosyaları ve yerelleştirilmiş *. resx* dosyaları oluşturarak ve sonra değişiklikleri içerecek proje dosyalarını güncelleştirerek menü ve araç çubuğu komutları için yerelleştirilmiş metin sağlayabilirsiniz.

Yükleme deneyiminin yerelleştirilmesi hakkında daha fazla bilgi için bkz. [Yerel VSIX paketleri](../extensibility/localizing-vsix-packages.md).

## <a name="localize-command-names"></a>Komut adlarını yerelleştirin

VSPackages 'de, menü komutları ve araç çubuğu düğmeleri *. vsct* dosyasında tanımlanmıştır.

1. **Çözüm Gezgini**, *. vsct* dosyasının adını *filename. vsct* konumundan *filename. en-US. vsct* olarak değiştirin.

2. Her yerelleştirilmiş dil için *filename. en-US. vsct* kopyasını oluşturun.

    Her kopya dosya adını adlandırın *. { Locale}. vsct*, burada *{locale}* belirli bir kültür adıdır. Kültür adı değerlerinin listesi için bkz. [Microsoft tarafından atanan yerel ayar kimlikleri](/windows/uwp/publish/supported-languages).

    Bu *dosya adı. Locale. vsct* dosyaları, paketiniz için yerelleştirilmiş menü metnini içerir.

3. Her *dosya adını açın. Metni yerelleştirmek için locale. vsct* dosyası.

   1. [ButtonText](../extensibility/buttontext-element.md) öğe değerlerini belirli bir dile uygun şekilde değiştirin.

   2. Yerelleştirilmiş simgeler sağlayabiliyorsanız, [bit eşlem](../extensibility/bitmap-element.md) değerlerini hedef dosyalara işaret edecek şekilde değiştirin.

      Aşağıdaki örnekte, bir komut için bir aile ağacı Gezgin araç penceresi açmak üzere Ingilizce ve Ispanyolca düğme metni gösterilmektedir.

      [*FamilyTree. en-US. vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-es. vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>Diğer metin kaynaklarını yerelleştirin

Komut adlarından farklı metin kaynakları kaynak (*. resx*) dosyalarında tanımlanır.

1. *VSPackage. resx* ' i *VSPackage. en-US. resx* olarak yeniden adlandırın.

2. Her yerelleştirilmiş dil için *VSPackage. en-US. resx* dosyasının bir kopyasını oluşturun.

     Her kopya *VSPackage olarak adlandırın. { Locale}. resx*, burada *{locale}* belirli bir kültür adıdır.

3. *Resources. resx* ' i *Resources. en-US. resx* olarak yeniden adlandırın.

4. Her yerelleştirilmiş dil için *Resources. en-US. resx* dosyasını bir kopyasını oluşturun.

     Her kopya *kaynağını adlandırın. { Locale}. resx*, burada *{locale}* belirli bir kültür adıdır.

5. Dize değerlerini belirli dile ve kültüre uygun şekilde değiştirmek için her *. resx* dosyasını açın. Aşağıdaki örnekte bir araç penceresinin başlık çubuğu için yerelleştirilmiş kaynak tanımı gösterilmektedir.

     [*Resources. en-US. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-es. resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Yerelleştirilmiş kaynakları projeye ekleyin

Yerelleştirilmiş kaynakları birleştirmek için *AssemblyInfo. cs* dosyasını ve proje dosyasını değiştirmeniz gerekir.

1. **Çözüm Gezgini** **Özellikler** düğümünden, düzenleyicide *AssemblyInfo. cs* veya *AssemblyInfo. vb* dosyasını açın.

2. Aşağıdaki girişi ekleyin.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Bu, varsayılan dil olarak ABD Ingilizcesi 'ni ayarlar.

3. Projeyi kaldırın.

4. Proje dosyasını düzenleyicide açın.

5. Kök `Project` öğesinde, `PropertyGroup` varsayılan diliniz ile eşleşen bir öğesi olan bir öğesi ekleyin `UICulture` .

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     bu, Windows Presentation Foundation (WPF) denetimleri için varsayılan uı kültürü olarak ingilizce 'yi ayarlar.

6. `ItemGroup`Öğeleri içeren öğeyi bulun `EmbeddedResource` .

7. `EmbeddedResource` *VSPackage. en-US. resx* öğesini çağıran öğede, `ManifestResourceName` öğesini `LogicalName` şöyle ayarlanmış bir öğeyle değiştirin `VSPackage.en-US.Resources` :

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Her yerelleştirilmiş dil için, öğesini kopyalayın  `EmbeddedResource` `VsPackage.en-US` ve kopyanın **Include** özniteliğini ve **LogicalName** öğesini hedef yerel ayara ayarlayın.

9. Her yerelleştirilmiş `VSCTCompile` öğeye, `ResourceName` `Menus.ctmenu` Aşağıdaki örnekte gösterildiği gibi öğesine işaret eden bir öğesi ekleyin:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Proje dosyasını kaydedin ve projeyi yeniden yükleyin.

11. Projeyi derleyin.

     Bu, her dil için bir ana derleme ve kaynak derlemeleri oluşturur. Dağıtım işlemini yerelleştirme hakkında daha fazla bilgi için bkz. [Yerel VSIX paketleri](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Menüleri ve komutları Genişlet](../extensibility/extending-menus-and-commands.md)
- [Uygulamaları globalize ve yerelleştirme](../ide/globalizing-and-localizing-applications.md)
