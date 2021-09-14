---
title: Menü Komutlarını Yerelleştirme | Microsoft Docs
description: VSPackage'nız için yerelleştirilmiş .vsct dosyaları ve yerelleştirilmiş .resx dosyaları oluşturarak menü ve araç çubuğu komutları için yerelleştirilmiş metin sağlamayı öğrenin.
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
ms.openlocfilehash: 421072452214828560234aeb3a23128a38d0d515
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628892"
---
# <a name="localize-menu-commands"></a>Menü komutlarını yerelleştirme

VSPackage'nız için yerelleştirilmiş *.vsct* dosyaları ve *yerelleştirilmiş .resx* dosyaları oluşturarak ve ardından değişiklikleri birleştirmek için proje dosyalarını güncelleştirerek menü ve araç çubuğu komutları için yerelleştirilmiş metin sekleyebilirsiniz.

Yükleme deneyimini yerelleştirme hakkında bilgi için bkz. [VSIX paketlerini yerelleştirme.](../extensibility/localizing-vsix-packages.md)

## <a name="localize-command-names"></a>Komut adlarını yerelleştirme

VSPackage'larda menü komutları ve araç çubuğu düğmeleri *.vsct dosyasında* tanımlanır.

1. Dosya **Çözüm Gezgini** dosyasında *.vsct* dosyasının adını *filename.vsct* olarak *filename.en-US.vsct olarak değiştirir.*

2. Yerelleştirilmiş her dil *için filename.en-US.vsct* dosyasını kopyalayın.

    Her kopya dosya adını *adlandır.{ Locale}.vsct*; burada *{Locale}* belirli bir kültür adıdır. Kültür adı değerlerinin listesi için bkz. [Microsoft tarafından atanan yerel kimlikler.](/windows/uwp/publish/supported-languages)

    Bu *dosya adı. Locale.vsct* dosyaları, paketinizin yerelleştirilmiş menü metnini içerir.

3. Her dosya *adını açın. Metni yerelleştirmek için Locale.vsct* dosyası.

   1. [ButtonText öğesi değerlerini](../extensibility/buttontext-element.md) belirli bir dil için uygun şekilde değiştirme.

   2. Yerelleştirilmiş simgeler sağlayacaksanız Bit Eşlem [değerlerini](../extensibility/bitmap-element.md) hedef dosyaları işaret etmek için değiştirebilirsiniz.

      Aşağıdaki örnekte, Bir Aile Ağacı Gezgini araç penceresini açmak için bir komutun İngilizce ve İspanyolca düğme metni gösterilir.

      [*FamilyTree.en-US.vsct*]

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

    [*FamilyTree.es-ES.vsct*]

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

## <a name="localize-other-text-resources"></a>Diğer metin kaynaklarını yerelleştirme

Komut adları dışında metin kaynakları kaynak (*.resx*) dosyalarında tanımlanır.

1. *VSPackage.resx'i* *VSPackage.en-US.resx olarak yeniden adlandırın.*

2. Yerelleştirilmiş her dil *için VSPackage.en-US.resx* dosyasının bir kopyasını kopyalayın.

     Her kopyayı *VSPackage olarak adla.{ Locale}.resx*, burada *{Locale}* belirli bir kültür adıdır.

3. *Resources.resx'i* *Resources.en-US.resx olarak yeniden adlandırın.*

4. Yerelleştirilmiş her dil *için Resources.en-US.resx* dosyasının bir kopyasını kopyalayın.

     Her kopyayı Resources *olarak adla.{ Locale}.resx*, burada *{Locale}* belirli bir kültür adıdır.

5. Dize değerlerini belirli bir dil ve kültüre uygun şekilde değiştirmek için her *.resx* dosyasını açın. Aşağıdaki örnekte, bir araç penceresinin başlık çubuğu için yerelleştirilmiş kaynak tanımı gösterilir.

     [*Resources.en-US.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>Yerelleştirilmiş kaynakları projeye dahil etmek

*Assemblyinfo.cs dosyasını ve* proje dosyasını yerelleştirilmiş kaynakları birleştirmek için değiştirmeniz gerekir.

1. **Çözüm Gezgini'daki** Özellikler düğümünden *assemblyinfo.cs* veya *assemblyinfo.vb'yi* düzenleyicide açın. 

2. Aşağıdaki girdiyi ekleyin.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Bu, ABD İngilizce'lerini varsayılan dil olarak ayarlar.

3. Projeyi kaldırma.

4. Proje dosyasını düzenleyicide açın.

5. Kök `Project` öğesinde, varsayılan `PropertyGroup` dilinize eşleşen `UICulture` bir öğe ile bir öğesi ekleyin.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Bu, WINDOWS PRESENTATION FOUNDATION (WPF) denetimleri için varsayılan kullanıcı arabirimi kültürü olarak ABD İngilizcesi ayarlar.

6. Öğeleri `ItemGroup` içeren öğeyi `EmbeddedResource` bulun.

7. `EmbeddedResource` *VSPackage.en-US.resx* öğesini çağıran öğesinde öğesini aşağıdaki gibi olarak ayarlanmış `ManifestResourceName` `LogicalName` bir `VSPackage.en-US.Resources` öğeyle değiştirin:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Her yerelleştirilmiş dil için öğesini kopyalayın ve kopyanın Include özniteliğini ve LogicalName öğesini `EmbeddedResource` `VsPackage.en-US` hedef yerel ayara ayarlayın.  

9. Her yerelleştirilmiş `VSCTCompile` öğeye, aşağıdaki `ResourceName` örnekte gösterildiği gibi `Menus.ctmenu` öğesinin üzerine bir öğe ekleyin:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Proje dosyasını kaydedin ve projeyi yeniden yükleyin.

11. Projeyi derleyin.

     Bu, her dil için bir ana derleme ve kaynak derlemeleri oluşturur. Dağıtım işlemini yerelleştirme hakkında bilgi için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [Uygulamaları Genelleştirme ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)
