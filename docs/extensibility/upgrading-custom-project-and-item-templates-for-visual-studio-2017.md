---
title: Visual Studio 2017 için özel proje ve öğe şablonlarını yükseltme
titleSuffix: ''
description: Visual Studio SDK'nın önceki sürümlerinden özel projenizi ve öğe şablonlarınızı Visual Studio 2017 ve sonraki sürümlerle kullanmak üzere nasıl güncelleştirebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0d07af0a00ab840df8a9af437bcddc427f606948
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903066"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Özel Sürüm Visual Studio için Proje ve Öğe Şablonları 2017'ye Yükseltme

Visual Studio 2017'den başlayarak Visual Studio, bir .vsix veya .msi tarafından önceki Visual Studio sürümlerinden farklı bir şekilde yüklenmiş proje ve öğe şablonlarını Visual Studio. Özel proje veya öğe şablonları kullanan uzantılarınız varsa, uzantılarınızı güncelleştirmeniz gerekir. Bu makalede neleri yapmaları gerektiğini açıklanmıştır.

Bu değişiklik yalnızca 2017 Visual Studio etkiler. Bu, uygulamanın önceki sürümlerini Visual Studio.

VSIX uzantısının bir parçası olarak proje veya öğe şablonu oluşturmak için bkz. [Özel Proje ve Öğe Şablonları Oluşturma.](../extensibility/creating-custom-project-and-item-templates.md)

## <a name="template-scanning"></a>Şablon Tarama

önceki Visual Studio sürümlerinde proje ve öğe şablonlarını bulmak için **devenv /setup** veya **devenv /installvstemplates** yerel diski taradı. 2017'Visual Studio başlayarak tarama yalnızca kullanıcı düzeyinde konum için gerçekleştirilir. Varsayılan kullanıcı düzeyinde konum **%USERPROFILE%\Documents \\<Visual Studio \> \Templates \\ sürümüdür.** Sihirbazda Şablonu Otomatik olarak Visual Studio aktar seçeneği seçiliyse, bu konum Proje Dışarı  >  **Aktarma** **Şablonları...** komutu tarafından oluşturulan şablonlar için kullanılır.

Diğer (kullanıcı olmayan) konumlar için, şablonun konumunu ve diğer özelliklerini belirten bir manifest(.vstman) dosyası dahil etmek gerekir. .vstman dosyası, şablonlar için kullanılan .vstemplate dosyasıyla birlikte oluşturulur. Uzantınızı bir .vsix kullanarak yüklürsanız, uzantıyı 2017'de yeniden Visual Studio yapabilirsiniz. Ancak bir uygulama .msi değişiklikleri el ile yapmak gerekir. Bu değişiklikleri yapmak için neleri ihtiyacınız olduğunu  görmek için bu sayfanın ilerleyen sayfalarındaki .MSIYükseltmeleri'ne bakın.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Proje veya Öğe Şablonlarıyla VSIX Uzantısını Güncelleştirme

1. 2017'de Visual Studio açın. Kodu yükseltmeniz istenecek. **Tamam**'a tıklayın.

2. Yükseltme tamamlandıktan sonra yükleme hedefinin sürümünü değiştirmeniz gerekir. VSIX projesinde source.extension.vsixmanifest dosyasını açın ve Hedefleri Yükle **sekmesini** seçin. Sürüm Aralığı alanı **[14.0]** ise  Düzenle'ye tıklayın ve bunu 2017'ye dahil Visual Studio.  Örneğin, uzantıyı yalnızca **Visual Studio 2017'ye** yüklemek için uzantıyı Visual Studio 2015 veya Visual Studio 2017'ye yüklemek için **[14.0.15.0] olarak veya [15.0]** olarak Visual Studio.

3. Kodu yeniden derleme.

4. Visual Studio’yu kapatın.

5. VSIX'i yükleyin.

6. Güncelleştirmeyi test etmek için şunları yapabilirsiniz:

    1. Dosya tarama değişikliği aşağıdaki kayıt defteri anahtarıyla etkinleştirilir:

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Anahtarı ekledikten sonra **devenv /installvstemplates çalıştırın.**

    3. Yeniden Visual Studio. Şablonlarınızı beklenen konumda bulmanız gerekir.

    > [!NOTE]
    > Visual Studio Genişletilebilirlik proje şablonları, kayıt defteri anahtarı mevcut olduğunda kullanılamaz. Bunları kullanmak için kayıt defteri anahtarını silmeniz (ve **devenv /installvstemplates)** yeniden çalıştırması gerekir.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Proje ve Öğe Şablonlarını Dağıtmak için Diğer Öneriler

- Sıkıştırılmış şablon dosyalarını kullanmaktan kaçının. Kaynakları ve içeriği almak için sıkıştırılmış şablon dosyalarının sıkıştırılmamış olması gerekir, bu nedenle bunların kullanımı daha maliyetli olur. Bunun yerine, şablon başlatmayı hızlandırmak için proje ve öğe şablonlarını kendi dizinlerinde ayrı dosyalar olarak dağıtmalısınız. VSIX uzantıları için SDK derleme görevleri, VSIX dosyasını oluştururken sıkıştırılmış şablonların sıkıştırmalarını otomatik olarak açar.

- Şablon bulma sırasında gereksiz kaynak derlemesi yüklemelerini önlemek için şablon adı, açıklama, simge veya önizleme için paket/kaynak kimliği girdilerini kullanmaktan kaçının. Bunun yerine, yerelleştirilmiş adları veya özellikleri kullanan her yerel seçim için bir şablon girişi oluşturmak üzere yerelleştirilmiş bildirimleri kullanabilirsiniz.

- Şablonları dosya öğeleri olarak dahil ediyorsanız, bildirim oluşturma size beklenen sonuçları vermeyebilirsiniz. Bu durumda, VSIX projesine el ile oluşturulan bir bildirim eklemeniz gerekir.

## <a name="file-changes-in-project-and-item-templates"></a>Proje ve Öğe Şablonlarında Dosya Değişiklikleri
Şablon dosyalarının Visual Studio 2015 ve Visual Studio 2017 sürümleri arasındaki fark noktalarını gösteririz, böylece yeni dosyaları doğru şekilde oluşturabilirsiniz.

 2015'te oluşturulan varsayılan proje .vstemplate Visual Studio:

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

 VsIX projesinin yeniden oluşturma sonucunda elde edilen .vstman dosyası (vsIX projesinin bildirim dizininde bulabilirsiniz) şöyledir:

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

 TemplateData öğesi [tarafından sağlanan](../extensibility/templatedata-element-visual-studio-templates.md) bilgiler aynı kalır. öğesi, **\<VSTemplateContainer>** ilişkili şablon için .vstemplate dosyasını belirtir.

 2015'te tarafından oluşturulan varsayılan .vstemplate Visual Studio:

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

 VsIX projesinin yeniden oluşturma sonucunda elde edilen .vstman dosyası (vsIX projesinin bildirim dizininde bulabilirsiniz) şöyledir:

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

 öğesi tarafından sağlanan **\<TemplateData>** bilgiler aynı kalır. öğesi, **\<VSTemplateContainer>** ilişkili şablon için .vstemplate dosyasını belirtir

 .vstman dosyasının farklı öğeleri hakkında daha fazla bilgi için [bkz. Visual Studio Şablon Bildirimi Şema Başvurusu.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Bir .MSI ile Yüklü Uzantılar için Yükseltmeler

Bazı MSI tabanlı uzantılar, şablonları aşağıdaki dizinler gibi ortak şablon konumlarına dağıtır:

- **\<Visual Studio installation directory>\Common7\IDE \\<ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<\> \\ Project/ItemTemplates<ExtensionName\>**

Uzantınız MSI tabanlı bir dağıtım gerçekleştiriyorsa şablon bildirimini el ile oluşturmalı ve uzantı kurulumuna dahil olduğundan emin olun. Yukarıda listelenen .vstman örneklerini ve şablon [Visual Studio Şema Başvurusu'Visual Studio karşılaştırma.](../extensibility/visual-studio-template-manifest-schema-reference.md)

Proje ve öğe şablonları için ayrı bildirim oluşturun ve yukarıda belirtildiği gibi kök şablon dizinine işaret ediyor olmalıdır. Uzantı ve yerel değer başına bir bildirim oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablon bulma sorunlarını giderme](troubleshooting-template-discovery.md)
- [Özel proje ve öğe şablonları oluşturma](creating-custom-project-and-item-templates.md)
