---
title: Visual Studio 2017 için özel proje ve öğe şablonlarını yükseltme
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698855"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Visual Studio 2017 Için Özel Proje ve Öğe Şablonlarını Yükselt

Visual Studio 2017'den itibaren Visual Studio,.vsix veya .msi tarafından yüklenen proje ve öğe şablonlarını Visual Studio'nun önceki sürümlerine göre farklı bir şekilde keşfeder. Özel proje veya öğe şablonları kullanan uzantılarınız varsa, uzantılarınızı güncelleştirmeniz gerekir. Bu makalede, ne yapmanız gerektiğini açıklar.

Bu değişiklik sadece Visual Studio 2017'yi etkiler. Visual Studio'nun önceki sürümlerini etkilemez.

VSIX uzantısı kapsamında bir proje veya öğe şablonu oluşturmak istiyorsanız, [bkz.](../extensibility/creating-custom-project-and-item-templates.md)

## <a name="template-scanning"></a>Şablon Tarama

Visual Studio'nun önceki sürümlerinde, **devenv /setup** veya **devenv /installvstemplates** proje ve öğe şablonlarını bulmak için yerel diski taradı. Visual Studio 2017'den itibaren tarama yalnızca kullanıcı düzeyindeki konum için gerçekleştirilir. Varsayılan kullanıcı düzeyindeki konum **%USERPROFILE%\Documents\\<\>Visual\\Studio sürümü \Templates'tir.** Bu konum, **şablonu Otomatik olarak Visual Studio'ya aktar** ın sihirbazı seçilirse, **Project** > **Export Templates...** komutu tarafından oluşturulan şablonlar için kullanılır.

Diğer (kullanıcı olmayan) konumlar için, şablonun konumunu ve diğer özelliklerini belirten bir bildirim (.vstman) dosyası eklemeniz gerekir. .vstman dosyası şablonlar için kullanılan .vstemplate dosyasıyla birlikte oluşturulur. Uzantınızı .vsix kullanarak yüklerseniz, uzantıyı Visual Studio 2017'de yeniden derleyerek bunu başarabilirsiniz. Ancak .msi kullanıyorsanız, değişiklikleri el ile yapmanız gerekir. Bu değişiklikleri yapmak için yapmanız gerekenlerin listesi **için, bir . MSI** daha sonra bu sayfada.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Proje veya Öğe Şablonları ile VSIX Uzantısı Nasıl Güncellenir?

1. Visual Studio 2017'de çözümü açın. Kodu yükseltmeniz istenir. **Tamam**'a tıklayın.

2. Yükseltme tamamlandıktan sonra yükleme hedefinin sürümünü değiştirmeniz gerekebilir. VSIX projesinde source.extension.vsixmanifest dosyasını açın ve **Hedefleri Yükle** sekmesini seçin. Sürüm **Aralığı** alanı **[14.0]** ise, **Edit'i** tıklatın ve Visual Studio 2017'yi içerecek şekilde değiştirin. Örneğin, uzantıyı Visual Studio 2015 veya Visual Studio 2017'ye yüklemek için **[14.0,15.0]** veya sadece Visual Studio 2017'ye yüklemek için **[15.0]** olarak ayarlayabilirsiniz.

3. Kodu yeniden derle.

4. Visual Studio’yu kapatın.

5. VSIX'yi yükleyin.

6. Güncelleştirmeyi aşağıdakileri yaparak test edebilirsiniz:

    1. Dosya tarama değişikliği aşağıdaki kayıt defteri anahtarı tarafından etkinleştirilir:

         **reg ekle hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Anahtarı ekledikten sonra **devenv /installvstemplates çalıştırın.**

    3. Visual Studio'yı yeniden açın. Şablonunuzu beklenen konumda bulmanız gerekir.

    > [!NOTE]
    > Kayıt defteri anahtarı bulunduğunda Visual Studio Genişletilebilirlik proje şablonları kullanılamaz. Bunları kullanmak için kayıt defteri anahtarını silmeniz (ve **devenv /installvstemplates'i**yeniden çalıştırmanız gerekir).

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Proje ve Madde Şablonlarını Dağıtmak için Diğer Öneriler

- Sıkıştırılmış şablon dosyalarını kullanmaktan kaçının. Kaynak ve içerik almak için sıkıştırılmış şablon dosyalarının sıkıştırılmamış olması gerekir, bu nedenle kullanımı daha maliyetli olacaktır. Bunun yerine, şablon başlatmayı hızlandırmak için proje ve öğe şablonlarını kendi dizinleri altında tek tek dosyalar olarak dağıtmanız gerekir. VSIX uzantıları için, SDK yapı görevleri, VSIX dosyasını oluştururken herhangi bir sıkıştırılmış şablonun zip'ini otomatik olarak açar.

- Şablon bulma sırasında gereksiz kaynak derleme yüklerinden kaçınmak için şablon adı, açıklama, simge veya önizleme için paket/kaynak kimliği girişlerini kullanmaktan kaçının. Bunun yerine, yerelleştirilmiş adlar veya özellikler kullanan her yerel bölge için bir şablon girişi oluşturmak için yerelleştirilmiş bildirimleri kullanabilirsiniz.

- Şablonları dosya öğesi olarak dahil ediyorsanız, bildirim oluşturma size beklenen sonuçları vermeyebilir. Bu durumda, VSIX projesine el ile oluşturulmuş bir bildirim eklemeniz gerekir.

## <a name="file-changes-in-project-and-item-templates"></a>Proje ve Madde Şablonlarında Dosya Değişiklikleri
Yeni dosyaları doğru bir şekilde oluşturabilmeniz için şablon dosyalarının Visual Studio 2015 ve Visual Studio 2017 sürümleri arasındaki fark noktalarını gösteriyoruz.

 Visual Studio 2015 tarafından oluşturulan varsayılan proje .vstemplate dosyası aşağıda verilmiştir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 VSIX projesinin yeniden oluşturulmasından kaynaklanan .vstman dosyası (VSIX projesinin manifesto dizininde bulabilirsiniz) :

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) öğesi tarafından sağlanan bilgiler aynı kalır. VSTemplateContainer>öğesi, ilişkili şablon için .vstemplate dosyasını gösterir. ** \<**

 Visual Studio 2015 tarafından oluşturulan varsayılan öğe .vstemplate dosyası aşağıda verilmiştir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 VSIX projesinin yeniden oluşturulmasından kaynaklanan .vstman dosyası (VSIX projesinin manifesto dizininde bulabilirsiniz) :

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 TemplateData>öğesi tarafından sağlanan bilgiler aynı kalır. ** \<** VSTemplateContainer>öğesi ilişkili şablon için .vstemplate dosyasını işaret ediyor ** \<**

 .vstman dosyasının farklı öğeleri hakkında daha fazla bilgi için [Visual Studio Template Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md)bölümüne bakın.

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Bir ile yüklenen Uzantılar için yükseltmeleri . Msı

Bazı MSI tabanlı uzantılar şablonları aşağıdaki dizinler gibi yaygın şablon konumlarına dağıtır:

- **\<Visual Studio yükleme dizini>\Common7\IDE\\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio kurulum dizini>\Common7\IDE\Extensions\\<ExtensionName\> \\<Project/ItemTemplates\>**

Uzantınız MSI tabanlı bir dağıtım gerçekleştiriyorsa, şablon bildirimini el ile oluşturmanız ve uzantı kurulumuna dahil edilmesini sağlamanız gerekir. Yukarıda listelenen .vstman örneklerini ve [Visual Studio Template Manifest Schema Reference'ı](../extensibility/visual-studio-template-manifest-schema-reference.md)karşılaştırın.

Proje ve madde şablonları için ayrı bildirimler oluşturun ve bunlar yukarıda belirtildiği gibi kök şablon dizinine işaret etmelidir. Uzantı ve yerel olarak bir bildirim oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorun giderme şablonu bulma](troubleshooting-template-discovery.md)
- [Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)
