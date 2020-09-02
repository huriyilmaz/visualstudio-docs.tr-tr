---
title: 'Nasıl yapılır: oluşturma. Vsct dosyası | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158343"
---
# <a name="how-to-create-a-vsct-file"></a>Nasıl Yapılır: .Vsct Dosyası Oluşturma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

XML tabanlı Visual Studio komut tablosu yapılandırma (. vsct) dosyası oluşturmanın birkaç yolu vardır.  
  
- Paket şablonunda yeni bir VSPackage oluşturabilirsiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Var olan bir. CTC dosyasından bir dosya oluşturmak için, XML tabanlı komut tablosu yapılandırma derleyicisini Vsct.exe kullanabilirsiniz.  
  
- Var olan bir. CTO dosyasından bir. vsct dosyası oluşturmak için Vsct.exe kullanabilirsiniz.  
  
- El ile yeni bir. vsct dosyası oluşturabilirsiniz.  
  
  Bu konuda, yeni bir. vsct dosyasının el ile nasıl oluşturulacağı açıklanmaktadır.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>El ile yeni bir. vsct dosyası oluşturmak için  
  
1. Başlatın [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Dosya**' ya tıklayın.  
  
3. **Şablonlar** bölmesinde, **XML dosyası** ' na ve sonra **Aç**' a tıklayın.  
  
4. **Görünüm** menüsünde, **Özellikler penceresi** ' ne tıklayarak XML dosyasının özelliklerini görüntüleyin.  
  
5. **Özellikler** penceresinde, şemalar özelliğindeki (...) düğmesine tıklayın.  
  
6. XSD şemaları listesinde vsct. xsd şemasını seçin. Listede yoksa, **Ekle** ' ye tıklayın ve dosyayı yerel bir sürücüde bulun. İşiniz bittiğinde **Tamam** ' a tıklayın.  
  
7. XML dosyasında yazın `<CommandTable` ve ardından SEKME tuşuna basın. Yazarak etiketi kapatın `>` .  
  
     Bu, temel bir. vsct dosyası oluşturur.  
  
8. [Vsct şemasına](../../extensibility/vsct-xml-schema-reference.md)göre eklemek istediğiniz XML dosyasının öğelerini girin. Daha fazla bilgi için bkz [. yazma. Vsct dosyaları](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yalnızca bir. vsct dosyasını bir projeye eklemek, derlemeye neden olmaz. Yapı sürecinde bu dosyayı eklemeniz gerekir.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Proje derlemesine bir. vsct dosyası eklemek için  
  
1. Proje dosyanızı düzenleyicide açın. Proje yüklüyse, önce onu kaldırmanız gerekir.  
  
2. Aşağıdaki örnekte gösterildiği gibi, VSCTCompile öğesi içeren bir [ItemGroup öğesi](../../msbuild/itemgroup-element-msbuild.md) ekleyin.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     ResourceName öğesi her zaman olarak ayarlanmalıdır `Menus.ctmenu` .  
  
3. Projeniz bir. resx dosyası içeriyorsa, aşağıdaki örnekte gösterildiği gibi bir MergeWithCTO öğesi içeren bir EmbeddedResource öğesi ekleyin.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Bu biçimlendirme, gömülü kaynakları içeren ItemGroup öğesinin içine gitmelidir.  
  
4. Genellikle, düzenleyicide *projectname*Package.cs veya *ProjectName*Package. vb adlı paket dosyasını açın.  
  
5. Aşağıdaki örnekte gösterildiği gibi, Package sınıfına bir ProvideMenuResource özniteliği ekleyin.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     İlk parametre değeri, proje dosyasında tanımladığınız ResourceName özniteliğinin değeriyle eşleşmelidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özgün. Vsct dosyaları](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Nasıl yapılır: oluşturma. Varolan bir dosyadan vsct dosyası. CTC dosyası](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [Nasıl yapılır: oluşturma. Varolan bir dosyadan vsct dosyası. CTO dosyası](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
