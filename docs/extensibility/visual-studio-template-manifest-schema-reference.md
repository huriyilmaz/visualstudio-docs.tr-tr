---
title: Visual Studio Şablon Bildirimi Şema Başvurusu | Microsoft Docs
description: Bu şema başvurusu, proje veya Visual Studio için oluşturulan şablon bildirim Visual Studio biçimini açıklar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4e0cb5372340bfd3ca624d3c9844bd34ef1e0914
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109948"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio şablonu bildirim şeması başvurusu
Bu şema, proje veya Visual Studio şablonları için oluşturulan Visual Studio şablon bildirimi (*.vstman*) dosyalarının biçimini açıklar. Şema ayrıca konumu ve şablonla ilgili diğer bilgileri de açıklar.

 : Ayrı öğe ve proje şablonu dizinleri olduğundan, bir bildirim hiçbir zaman öğe ve proje şablonlarının bir karışımına sahip olması gerekir.

> [!IMPORTANT]
> Bu bildirim, 2017'Visual Studio kullanılabilir.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest öğesi
 Bildirimin kök öğesi.

### <a name="attributes"></a>Öznitelikler

- **Sürüm:** Şablon bildiriminin sürümünü temsil eden bir dize. Gereklidir.

- **Yerel seçim:** Şablon bildiriminin yerel veya yerel bölgelerini temsil eden bir dize. Yerel ayar değeri tüm şablonlar için geçerlidir. Her yerel seçim için ayrı bir bildirim kullan gerekir. İsteğe bağlı.

### <a name="child-elements"></a>Alt öğeleri

- **VSTemplateContainer** Isteğe bağlı.

- **VSTemplateDir** Isteğe bağlı.

### <a name="parent-element"></a>Üst öğe
 Yok.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Şablon bildirimi öğelerinin kapsayıcısı. Bir bildirim, tanımladığı her şablon için bir şablon kapsayıcısı içerir.

### <a name="attributes"></a>Öznitelikler
 **VSTemplateType:** Şablonun türünü belirten bir dize değeri ( `"Project"` , `"Item"` veya `"ProjectGroup"` ). Gerekli

### <a name="child-elements"></a>Alt öğeleri

- **RelativePathOnDisk:** Diskte şablon dosyasının göreli yolu. Bu konum, şablonun Yeni Kaynak veya Yeni Öğe iletişim kutusunda gösterilen şablon **Project** **yerleşimini de** tanımlar. Bu yol, bir dizin ve tek tek dosyalar olarak dağıtılan şablonlar için şablon dosyalarını içeren dizine başvurur. .zipdosyası *olarak dağıtılan* şablonlar için bu yol, dosyanın *.zip* gerekir.

- **VSTemplateHeader: Üst bilgiyi açıklayan [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) öğesi.

### <a name="parent-element"></a>Üst öğe
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Şablonun bulunduğu dizini açıklar. Bir bildirim, dizinlerin şablon kategorisi ağacında görünümünü denetlemesi için yerelleştirilmiş ad ve sıralama düzeni sağlamak için birden çok **VSTemplateDir** girdisi içerebilir.

 Tasarımı nedeniyle **VSTemplateDir** girişleri yalnızca yerel olarak belirtilmeyen bildirimlerde görünilmelidir.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

- **RelativePath:** Şablonun yolu. Yol başına yalnızca bir giriş olabilir, bu nedenle ilk giriş tüm bildirimlerde kazanır.

- **LocalizedName:** **Yerelleştirilmiş adı belirten nameDescriptionIcon** öğesi. İsteğe bağlı.

- **SortOrder:** Sıralama sırasını belirten bir dize. İsteğe bağlı.

- **ParentFolderOverrideName:** Üst klasörün geçersiz kılınan adı. İsteğe bağlı. Bu **öğenin, adı** belirten bir dize değeri olan Name özniteliği vardır.

### <a name="parent-element"></a>Üst öğe
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Büyük olasılıkla yerelleştirilmiş şablonlar için adı ve açıklamayı belirtir. Yukarıdaki **LocalizedName'e** bakın.

### <a name="attributes"></a>Öznitelikler

- **Paket:** Paketi belirten bir dize değeri. İsteğe bağlı.

- **ID:** Kimliği belirten bir dize değeri. İsteğe bağlı.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-element"></a>Üst öğe
 **Localizedname**

## <a name="examples"></a>Örnekler
 Aşağıdaki kod, proje şablonu *.vstman dosyasının bir örneğidir.*

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Aşağıdaki kod, bir öğe şablonu *.vstman dosyası örneğidir.*

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
