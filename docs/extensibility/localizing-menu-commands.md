---
title: Menü Komutlarını Yerelleştirme | Microsoft Dokümanlar
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702953"
---
# <a name="localize-menu-commands"></a>Menü komutlarını yerelleştir

VSPackage'ınız için yerelleştirilmiş *.vsct* dosyaları ve yerelleştirilmiş *.resx* dosyaları oluşturarak ve değişiklikleri birleştirmek için proje dosyalarını güncelleştirerek menü ve araç çubuğu komutları için yerelleştirilmiş metin sağlayabilirsiniz.

Yükleme deneyimini nasıl yerelleştirişize edin, [VSIX paketlerini yerelleştir'e](../extensibility/localizing-vsix-packages.md)bakın.

## <a name="localize-command-names"></a>Komut adlarını yerelleştir

VSPackages'ta *,.vsct* dosyasında menü komutları ve araç çubuğu düğmeleri tanımlanır.

1. **Çözüm Gezgini'nde** *,.vsct* dosyasının adını *filename.vsct'den* *filename.en-US.vsct*olarak değiştirin.

2. Her yerelleştirilmiş dil için *filename.en-US.vsct'nin* bir kopyasını yapın.

    Her kopya *dosya adını adlandırın.{ Locale}.vsct*, *{Locale}'ın* belirli bir kültür adı olduğu yer. Kültür adı değerlerinin listesi [için, Microsoft tarafından atanan Yerel ID'lere](/windows/uwp/publish/supported-languages)bakın.

    Bu *dosya adı. Locale.vsct* dosyaları, paketiniz için yerelleştirilmiş menü metnini içerir.

3. Her *dosya adını açın. *Metni yerelleştirmek için Locale.vsct dosyası.

   1. [ButtonText](../extensibility/buttontext-element.md) öğesi değerlerini belirli bir dile uygun şekilde değiştirin.

   2. Yerelleştirilmiş simgeler sağlayacaksanız, [Bitmap](../extensibility/bitmap-element.md) değerlerini hedef dosyaları işaret edecek şekilde değiştirin.

      Aşağıdaki örnekte, Bir Aile Ağacı Gezgini araç penceresi açmak için bir komut için İngilizce ve İspanyolca düğme metni gösterilmektedir.

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

(*.resx*) dosyalarında komut adları dışındaki metin kaynakları tanımlanır.

1. *VSPackage.resx* *vspackage.en-US.resx*için yeniden adlandırın.

2. Her yerelleştirilmiş dil için *VSPackage.en-US.resx* dosyasının bir kopyasını yapın.

     Her *kopyayı VSPackage olarak adlandırın.{ Locale}.resx*, *{Locale}* belirli bir kültür adıdır.

3. *Resources.resx'i* *Resources.en-US.resx*olarak yeniden adlandırın.

4. Yerelleştirilmiş her dil için *Resources.en-US.resx* dosyasının bir kopyasını yapın.

     Her kopyayı Kaynak olarak *adlandırın.{ Locale}.resx*, *{Locale}* belirli bir kültür adıdır.

5. Dize değerlerini belirli bir dil ve kültüre uygun şekilde değiştirmek için her *.resx* dosyasını açın. Aşağıdaki örnek, bir araç penceresinin başlık çubuğu için yerelleştirilmiş kaynak tanımını gösterir.

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

## <a name="incorporate-localized-resources-into-the-project"></a>Yerelleştirilmiş kaynakları projeye dahil edin

Yerelleştirilmiş kaynakları dahil etmek için *assemblyinfo.cs* dosyayı ve proje dosyasını değiştirmeniz gerekir.

1. **Solution Explorer'daki** **Özellikler** düğümünden, assemblyinfo.cs *veya* *assemblyinfo.vb'yi* düzenleyicide açın.

2. Aşağıdaki girişi ekleyin.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     Bu, VARSAYıLAN dil olarak ABD İngilizcesi ayarlar.

3. Projeyi boşaltın.

4. Proje dosyasını düzenleyicide açın.

5. Kök `Project` öğede, varsayılan `PropertyGroup` dilinizle `UICulture` eşleşen bir öğeiçeren bir öğe ekleyin.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     Bu, Windows Sunu Temeli (WPF) denetimleri için varsayılan Ara Birimi kültürü olarak ABD İngilizcesi'ni ayarlar.

6. Öğeleri `ItemGroup` içeren `EmbeddedResource` öğeyi bulun.

7. `EmbeddedResource` *VSPackage.en-US.resx*çağıran öğede, `ManifestResourceName` aşağıdaki gibi `LogicalName` ayarlanmış `VSPackage.en-US.Resources`bir öğe ile öğe değiştirin:

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. Her yerelleştirilmiş dil için `EmbeddedResource` `VsPackage.en-US`öğeyi kopyalayın ve kopyanın **Öznitelik** ve **Mantıksal Ad** öğesini hedef yerel ayarla'ya ayarlayın.

9. Her yerelleştirilmiş `VSCTCompile` öğeiçin, `ResourceName` `Menus.ctmenu`aşağıdaki örnekte gösterildiği gibi, işaret eden bir öğe ekleyin:

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. Proje dosyasını kaydedin ve projeyi yeniden yükleyin.

11. Projeyi derleyin.

     Bu, her dil için bir ana derleme ve kaynak derlemeleri oluşturur. Dağıtım işlemini yerelleştirme hakkında bilgi için [VSIX paketlerini Yerelleştir'e](../extensibility/localizing-vsix-packages.md) bakın

## <a name="see-also"></a>Ayrıca bkz.

- [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)
- [Uygulamaları küreselleştir in ve Yerelleştirme](../ide/globalizing-and-localizing-applications.md)
