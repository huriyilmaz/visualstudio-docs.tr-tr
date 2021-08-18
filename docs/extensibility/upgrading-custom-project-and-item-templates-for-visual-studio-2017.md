---
title: Visual Studio 2017 için özel proje ve öğe şablonlarını yükseltme
titleSuffix: ''
description: özel proje ve öğe şablonunuzu, Visual Studio 2017 ve sonraki sürümlerle kullanılmak üzere Visual Studio SDK 'sının önceki sürümlerinden nasıl güncelleştireceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b66b17a1ffdab71f7aa20a8bc9cc985b0b398838
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049304"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Visual Studio 2017 için özel Project ve öğe şablonlarını yükseltme

Visual Studio 2017 ' den başlayarak, Visual Studio bir. vsix veya .msi tarafından yüklenen proje ve öğe şablonlarını Visual Studio önceki sürümlerinden farklı bir şekilde bulur. Özel proje veya öğe şablonları kullanan uzantılara sahipseniz, uzantılarınızı güncelleştirmeniz gerekir. Bu makalede yapmanız gerekenler açıklanmaktadır.

bu değişiklik yalnızca Visual Studio 2017 ' i etkiler. Önceki Visual Studio sürümlerini etkilemez.

bir vsıx uzantısının parçası olarak bir proje veya öğe şablonu oluşturmak istiyorsanız bkz. [özel Project ve öğe şablonları oluşturma](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Şablon tarama

Visual Studio önceki sürümlerinde, **devenv/setup** veya **devenv/ınstallvstempsyonlar** , proje ve öğe şablonlarını bulmak için yerel disk taranacaktır. Visual Studio 2017 ' den başlayarak, tarama yalnızca kullanıcı düzeyi konum için gerçekleştirilir. varsayılan kullanıcı düzeyi konumu **%userprofile%\documents \\<Visual Studio sürüm \> \ şablonlar \\**' dır. bu konum,   >  sihirbazda, **şablonu otomatik olarak Visual Studio seçeneğine içeri aktar** **...** komutu Project tarafından oluşturulan şablonlar için kullanılır.

Diğer (Kullanıcı olmayanlar) konumları için, şablonun konumunu ve diğer özelliklerini belirten bir manifest (. vstman) dosyası eklemeniz gerekir. . Vstman dosyası, şablonlar için kullanılan. vstemplate dosyası ile birlikte oluşturulur. uzantınızı bir. vsix kullanarak yüklerseniz, uzantıyı Visual Studio 2017 ' de yeniden derleyerek bunu yapabilirsiniz. Ancak bir .msi kullanıyorsanız, değişiklikleri el ile yapmanız gerekir. Bu değişiklikleri yapmak için yapmanız gerekenler listesi için, bu sayfada daha sonra  **.MSIyüklenen uzantılar Için yükseltmeler** bölümüne bakın.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Project veya öğe şablonlarıyla vsıx uzantısını güncelleştirme

1. çözümü Visual Studio 2017 ' de açın. Kodu yükseltmeniz istenir. **Tamam**'a tıklayın.

2. Yükseltme tamamlandıktan sonra, Install Target sürümünü değiştirmeniz gerekebilir. VSıX projesinde, kaynak. Extension. valtmanifest dosyasını açın ve **hedefleri yüklensin** sekmesini seçin. **sürüm aralığı** alanı **[14,0]** ise, **düzenle** ' ye tıklayın ve Visual Studio 2017 ' i içerecek şekilde değiştirin. örneğin, uzantıyı Visual Studio 2015 veya Visual Studio 2017 ya da **[15,0]** Visual Studio yalnızca 2017 'e yüklemek için **[14.0, 15.0]** olarak ayarlayabilirsiniz.

3. Kodu yeniden derleyin.

4. Visual Studio’yu kapatın.

5. VSıX 'i yükler.

6. Güncelleştirmeyi aşağıdakileri yaparak test edebilirsiniz:

    1. Dosya tarama değişikliği aşağıdaki kayıt defteri anahtarı tarafından etkinleştirilir:

         **Reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg: 32**

    2. Anahtarı ekledikten sonra, **devenv/ınstallvstempsyonlar** komutunu çalıştırın.

    3. Visual Studio yeniden açın. Şablonunuzun beklenen konumda bulunması gerekir.

    > [!NOTE]
    > Visual Studio genişletilebilirlik proje şablonları, kayıt defteri anahtarı mevcut olduğunda kullanılamaz. Kayıt defteri anahtarını silmeniz (ve **devenv/ınstallvstemptısmaları**' nı yeniden çalıştırmanız) gerekir.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Project ve öğe şablonlarını dağıtmaya yönelik diğer Öneriler

- Daraltılmış şablon dosyalarını kullanmaktan kaçının. Kaynak ve içerik almak için sıkıştırılmış şablon dosyalarının sıkıştırılması gerekir, bu nedenle kullanım için maliyetlendirilir. Bunun yerine, şablon başlatma hızını hızlandırmak için proje ve öğe şablonlarını kendi dizinlerinden ayrı dosyalar olarak dağıtmanız gerekir. VSıX uzantıları için SDK derleme görevleri, VSıX dosyasını oluştururken tüm daraltılmış şablonları otomatik olarak sıkıştırmasını açılır.

- Şablon bulma sırasında gereksiz kaynak derleme yüklerini önlemek için şablon adı, açıklama, simge veya önizleme için paket/kaynak KIMLIĞI girdilerini kullanmaktan kaçının. Bunun yerine, yerelleştirilmiş Adlar veya özellikler kullanan her bir yerel ayar için bir şablon girişi oluşturmak üzere yerelleştirilmiş bildirimleri kullanabilirsiniz.

- Şablonları dosya öğeleri olarak dahil ediyorsanız, bildirim üretimi size beklenen sonuçları vermeyebilir. Bu durumda, VSıX projesine el ile oluşturulmuş bir bildirim eklemeniz gerekecektir.

## <a name="file-changes-in-project-and-item-templates"></a>Project ve öğe şablonlarındaki dosya değişiklikleri
yeni dosyaları doğru bir şekilde oluşturabilmeniz için, şablon dosyalarının Visual Studio 2015 ve Visual Studio 2017 sürümleri arasındaki fark noktalarını gösteririz.

 Visual Studio 2015 tarafından oluşturulan varsayılan proje. vstemplate dosyası aşağıda verilmiştir:

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

 . vstman dosyasının farklı öğeleri hakkında daha fazla bilgi için bkz. [Visual Studio şablonu bildirim şeması başvurusu](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>.MSI yüklenen uzantılar için yükseltmeler

Bazı MSI tabanlı uzantılar, şablonları aşağıdaki dizinler gibi ortak şablon konumlarına dağıtır:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<extensionname \> \\<Project/ıtemtemplates\>**

Uzantınız MSI tabanlı bir dağıtım gerçekleştirirse, şablon bildirimini el ile oluşturmanız ve uzantının uzantı kurulumuna eklendiğinden emin olmanız gerekir. yukarıda listelenen. vstman örneklerini ve [Visual Studio şablonu bildirim şeması başvurusunu](../extensibility/visual-studio-template-manifest-schema-reference.md)karşılaştırın.

Proje ve öğe şablonları için ayrı bildirimler oluşturun ve yukarıda belirtildiği gibi kök şablon dizinine işaret etmelidir. Uzantı ve yerel ayar başına bir bildirim oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablon bulma sorunlarını giderme](troubleshooting-template-discovery.md)
- [Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)
