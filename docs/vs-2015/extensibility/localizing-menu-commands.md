---
title: Menü komutlarını yerelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c879072b55729e249b1aecd665d6f470f4138a75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686130"
---
# <a name="localizing-menu-commands"></a>Menü Komutlarını Yerelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage için yerelleştirilmiş. vsct dosyaları ve yerelleştirilmiş. resx dosyaları oluşturarak ve sonra değişiklikleri içerecek proje dosyalarını güncelleştirerek menü ve araç çubuğu komutları için yerelleştirilmiş metin sağlayabilirsiniz.  
  
 Yükleme deneyiminin yerelleştirilmesi hakkında daha fazla bilgi için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md).  
  
## <a name="localizing-command-names"></a>Komut adlarını yerelleştirme  
 VSPackages 'de, menü komutları ve araç çubuğu düğmeleri. vsct dosyasında tanımlanmıştır.  
  
1. **Çözüm Gezgini**,. vsct dosyasının adını *filename*. vsct konumundan *filename*. en-US. vsct olarak değiştirin.  
  
2. Her yerelleştirilmiş dil için *filename*. en-US. vsct kopyasını oluşturun.  
  
    Her kopya *Dosya*adını adlandırın. *Locale*. vsct, burada *yerel ayar* belirli bir kültür adıdır. Kültür adı değerlerinin listesi için bkz. [Microsoft tarafından atanan yerel ayar kimlikleri](https://msdn.microsoft.com/library/windows/apps/jj657969.aspx).  
  
    Bu *dosya adı*. *Locale*. vsct dosyaları, paketiniz için yerelleştirilmiş menü metnini içerir.  
  
3. Her *dosya adını*açın. Metni yerelleştirmek için *locale*. vsct dosyası.  
  
   1. [ButtonText](../extensibility/buttontext-element.md) öğe değerlerini belirli bir dile uygun şekilde değiştirin.  
  
   2. Yerelleştirilmiş simgeler sağlayabiliyorsanız, [bit eşlem](../extensibility/bitmap-element.md) değerlerini hedef dosyalara işaret edecek şekilde değiştirin.  
  
      Aşağıdaki örnekte, bir komut için bir aile ağacı Gezgin araç penceresi açmak üzere Ingilizce ve Ispanyolca düğme metni gösterilmektedir.  
  
      [FamilyTree. en-US. vsct]  
  
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
  
    [FamilyTree.es-ES. vsct]  
  
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
  
## <a name="localizing-other-text-resources"></a>Diğer metin kaynaklarını yerelleştirme  
 Komut adlarından farklı metin kaynakları kaynak (. resx) dosyalarında tanımlanır.  
  
1. VSPackage. resx ' i VSPackage. en-US. resx olarak yeniden adlandırın.  
  
2. Her yerelleştirilmiş dil için VSPackage. en-US. resx dosyasının bir kopyasını oluşturun.  
  
     Her kopya VSPackage olarak adlandırın. *Locale*. resx, *yerel ayar* belirli bir kültür adıdır.  
  
3. Resources. resx ' i resources. en-US. resx olarak yeniden adlandırın.  
  
4. Her yerelleştirilmiş dil için resources. en-US. resx dosyasını bir kopyasını oluşturun.  
  
     Her kopyalama kaynağını adlandırın. *Locale*. resx, *yerel ayar* belirli bir kültür adıdır.  
  
5. Dize değerlerini belirli dile ve kültüre uygun şekilde değiştirmek için her. resx dosyasını açın. Aşağıdaki örnekte bir araç penceresinin başlık çubuğu için yerelleştirilmiş kaynak tanımı gösterilmektedir.  
  
     [Resources. en-US. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Family Tree Explorer</value>  
    </data>  
    ```  
  
     [Resources.es-ES. resx]  
  
    ```xml  
    <data name="ToolWindowTitle" xml:space="preserve">  
      <value>Explorador del arbol genealogico</value>  
    </data>  
  
    ```  
  
## <a name="incorporating-localized-resources-into-the-project"></a>Yerelleştirilmiş kaynakları projeye ekleme  
 Yerelleştirilmiş kaynakları birleştirmek için assemblyinfo.cs dosyasını ve proje dosyasını değiştirmeniz gerekir.  
  
1. **Çözüm Gezgini** **Özellikler** düğümünden, düzenleyicide Assemblyinfo.cs veya AssemblyInfo. vb dosyasını açın.  
  
2. Aşağıdaki girişi ekleyin.  
  
    ```csharp  
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]  
    ```  
  
     Bu, varsayılan dil olarak ABD Ingilizcesi 'ni ayarlar.  
  
3. Projeyi kaldırın.  
  
4. Proje dosyasını düzenleyicide açın.  
  
5. `ItemGroup`Öğeleri içeren öğeyi bulun `EmbeddedResource` .  
  
6. `EmbeddedResource`VSPackage. en-US. resx ' i çağıran öğede, öğesini `ManifestResourceName` aşağıdaki gibi olarak ayarlayın öğesi ile değiştirin `LogicalName` `VSPackage.en-US.Resources` .  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.en-US.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <LogicalName>VSPackage.en-US.Resources</LogicalName>  
    </EmbeddedResource>  
    ```  
  
7. Her yerelleştirilmiş dil için,  `EmbeddedResource` VsPackage. en-US için öğesini kopyalayın ve aşağıdaki örnekte gösterildiği gibi, kopyanın **Include** özniteliğini ve **LogicalName** öğesini hedef yerel ayara ayarlayın.  
  
8. Her yerelleştirilmiş `VSCTCompile` öğeye, `ResourceName` `Menus.ctmenu` Aşağıdaki örnekte gösterildiği gibi öğesine işaret eden bir öğesi ekleyin.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
    ```  
  
9. Proje dosyasını kaydedin ve projeyi yeniden yükleyin.  
  
10. Projeyi derleyin.  
  
     Bu, her dil için bir ana derleme ve kaynak derlemeleri oluşturur. Dağıtım işlemini yerelleştirme hakkında daha fazla bilgi için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Menüleri ve komutları genişletme](../extensibility/extending-menus-and-commands.md)   
 [MenuCommands ve OleMenuCommands karşılaştırması](../misc/menucommands-vs-olemenucommands.md)   
 [Genelleştirme ve yerelleştirme](https://msdn.microsoft.com/library/9a59696b-d89b-45bd-946d-c75da4732d02)
