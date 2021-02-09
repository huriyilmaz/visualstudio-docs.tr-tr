---
title: Visual Studio 2017 için özel proje ve öğe şablonlarını yükseltme
titleSuffix: ''
description: Visual Studio 2017 ve sonraki sürümlerle kullanılmak üzere Visual Studio SDK 'sının önceki sürümlerinden özel proje ve öğe şablonunuzu güncelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 84e9b08350cf5977269bfbcf28ca5335e17f024d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893411"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Yükseltme özel Visual Studio için Proje ve Öğe Şablonları 2017

Visual Studio 2017 ' den başlayarak Visual Studio, Visual Studio 'nun önceki sürümlerine farklı bir şekilde bir. vsix veya. msi tarafından yüklenen proje ve öğe şablonlarını bulur. Özel proje veya öğe şablonları kullanan uzantılara sahipseniz, uzantılarınızı güncelleştirmeniz gerekir. Bu makalede yapmanız gerekenler açıklanmaktadır.

Bu değişiklik yalnızca Visual Studio 2017 ' i etkiler. Visual Studio 'nun önceki sürümlerini etkilemez.

Bir VSıX uzantısının parçası olarak bir proje veya öğe şablonu oluşturmak istiyorsanız bkz. [özel proje ve öğe şablonları oluşturma](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Şablon tarama

Visual Studio 'nun önceki sürümlerinde, **devenv/setup** veya **devenv/ınstallvstempsyonlar** proje ve öğe şablonlarını bulmak için yerel disk tarandı. Visual Studio 2017 ' den başlayarak, tarama yalnızca Kullanıcı düzeyinde konum için gerçekleştirilir. Varsayılan Kullanıcı düzeyi konumu, **\\ Visual Studio Sürüm \> \ şablonları \\<%UserProfile%\Documents dizinidir**. Bu konum,   >  sihirbazda **şablonu Visual Studio 'ya otomatik olarak içeri aktar** seçeneği belirlenmişse proje **dışarı aktarma şablonları...** komutu tarafından oluşturulan şablonlar için kullanılır.

Diğer (Kullanıcı olmayanlar) konumları için, şablonun konumunu ve diğer özelliklerini belirten bir manifest (. vstman) dosyası eklemeniz gerekir. . Vstman dosyası, şablonlar için kullanılan. vstemplate dosyası ile birlikte oluşturulur. Uzantınızı bir. vsix kullanarak yüklerseniz, uzantıyı Visual Studio 2017 ' de yeniden derleyerek bunu yapabilirsiniz. Ancak. msi kullanıyorsanız, değişiklikleri el ile yapmanız gerekir. Bu değişiklikleri yapmak için yapmanız gerekenler listesi için, bkz  **. Ile yüklenen uzantılar Için yükseltmeler.** Daha sonra bu sayfada MSI.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Proje veya öğe şablonlarıyla VSıX uzantısını güncelleştirme

1. Visual Studio 2017 ' de çözümü açın. Kodu yükseltmeniz istenir. **Tamam**'a tıklayın.

2. Yükseltme tamamlandıktan sonra, Install Target sürümünü değiştirmeniz gerekebilir. VSıX projesinde, kaynak. Extension. valtmanifest dosyasını açın ve **hedefleri yüklensin** sekmesini seçin. **Sürüm aralığı** alanı **[14,0]** ise, **Düzenle** ' ye tıklayın ve Visual Studio 2017 ' i içerecek şekilde değiştirin. Örneğin, uzantıyı Visual Studio 2015 veya Visual Studio 2017 ya da yalnızca Visual Studio 2017 ' e yüklemek için [ **15,0] veya []** için [ **14.0, 15.0]** olarak ayarlayabilirsiniz.

3. Kodu yeniden derleyin.

4. Visual Studio’yu kapatın.

5. VSıX 'i yükler.

6. Güncelleştirmeyi aşağıdakileri yaparak test edebilirsiniz:

    1. Dosya tarama değişikliği aşağıdaki kayıt defteri anahtarı tarafından etkinleştirilir:

         **Reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg: 32**

    2. Anahtarı ekledikten sonra, **devenv/ınstallvstempsyonlar** komutunu çalıştırın.

    3. Visual Studio 'Yu yeniden açın. Şablonunuzun beklenen konumda bulunması gerekir.

    > [!NOTE]
    > Kayıt defteri anahtarı mevcut olduğunda Visual Studio genişletilebilirlik proje şablonları kullanılamaz. Kayıt defteri anahtarını silmeniz (ve **devenv/ınstallvstemptısmaları**' nı yeniden çalıştırmanız) gerekir.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Proje ve öğe şablonları dağıtmaya yönelik diğer öneriler

- Daraltılmış şablon dosyalarını kullanmaktan kaçının. Kaynak ve içerik almak için sıkıştırılmış şablon dosyalarının sıkıştırılması gerekir, bu nedenle kullanım için maliyetlendirilir. Bunun yerine, şablon başlatma hızını hızlandırmak için proje ve öğe şablonlarını kendi dizinlerinden ayrı dosyalar olarak dağıtmanız gerekir. VSıX uzantıları için SDK derleme görevleri, VSıX dosyasını oluştururken tüm daraltılmış şablonları otomatik olarak sıkıştırmasını açılır.

- Şablon bulma sırasında gereksiz kaynak derleme yüklerini önlemek için şablon adı, açıklama, simge veya önizleme için paket/kaynak KIMLIĞI girdilerini kullanmaktan kaçının. Bunun yerine, yerelleştirilmiş Adlar veya özellikler kullanan her bir yerel ayar için bir şablon girişi oluşturmak üzere yerelleştirilmiş bildirimleri kullanabilirsiniz.

- Şablonları dosya öğeleri olarak dahil ediyorsanız, bildirim üretimi size beklenen sonuçları vermeyebilir. Bu durumda, VSıX projesine el ile oluşturulmuş bir bildirim eklemeniz gerekecektir.

## <a name="file-changes-in-project-and-item-templates"></a>Proje ve öğe şablonlarındaki dosya değişiklikleri
Yeni dosyaları doğru bir şekilde oluşturabilmeniz için, Visual Studio 2015 ve şablon dosyalarının Visual Studio 2017 sürümleri arasındaki fark noktalarını gösteririz.

 Visual Studio 2015 tarafından oluşturulan varsayılan Project. vstemplate dosyası aşağıda verilmiştir:

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

 Burada, VSıX projesinin yeniden oluşturulması sonucunda elde edilen. vstman dosyası (VSıX projesinin manifest dizininde bulabilirsiniz):

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

 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) öğesi tarafından belirtilen bilgiler aynı kalır. **\<VSTemplateContainer>** Öğesi ilişkili şablon için. vstemplate dosyasını işaret eder.

 Visual Studio 2015 tarafından oluşturulan varsayılan item. vstemplate dosyası aşağıda verilmiştir:

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

 Burada, VSıX projesinin yeniden oluşturulması sonucunda elde edilen. vstman dosyası (VSıX projesinin manifest dizininde bulabilirsiniz):

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

 Öğesi tarafından belirtilen bilgiler **\<TemplateData>** aynı kalır. **\<VSTemplateContainer>** Öğesi ilişkili şablon için. vstemplate dosyasını işaret eder

 . Vstman dosyasının farklı öğeleri hakkında daha fazla bilgi için bkz. [Visual Studio şablon bildirim şeması başvurusu](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>İle yüklenen uzantılar için yükseltmeler. DEFTERI

Bazı MSI tabanlı uzantılar, şablonları aşağıdaki dizinler gibi ortak şablon konumlarına dağıtır:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<Project/ItemTemplates\>**

Uzantınız MSI tabanlı bir dağıtım gerçekleştirirse, şablon bildirimini el ile oluşturmanız ve uzantının uzantı kurulumuna eklendiğinden emin olmanız gerekir. Yukarıda listelenen. vstman örneklerini ve [Visual Studio şablon bildirim şeması başvurusunu](../extensibility/visual-studio-template-manifest-schema-reference.md)karşılaştırın.

Proje ve öğe şablonları için ayrı bildirimler oluşturun ve yukarıda belirtildiği gibi kök şablon dizinine işaret etmelidir. Uzantı ve yerel ayar başına bir bildirim oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablon bulma sorunlarını giderme](troubleshooting-template-discovery.md)
- [Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)
