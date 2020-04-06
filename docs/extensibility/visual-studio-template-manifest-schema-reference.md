---
title: Visual Studio Şablon Manifesto Şeması Referans | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697983"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio şablonu şema başvurusu tezahürü
Bu şema, Visual Studio projesi veya öğe şablonları için oluşturulan Visual Studio şablon*bildiriminin*biçimini açıklar. Şema da konumu ve şablon hakkında diğer ilgili bilgileri açıklar.

 : Ayrı öğe ve proje şablonu dizinleri olduğundan, bir bildirimin hiçbir zaman öğe ve proje şablonlarının bir karışımı olmamalıdır.

> [!IMPORTANT]
> Bu bildirim Visual Studio 2017'den itibaren mevcuttur.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest öğesi
 Bildirimin kök öğesi.

### <a name="attributes"></a>Öznitelikler

- **Sürüm**: Şablon bildiriminin sürümünü temsil eden dize. Gereklidir.

- **Yerel :** Şablon bildiriminin yerel veya yerel lerini temsil eden dize. Yerel değer tüm şablonlar için geçerlidir. Her yerel bölge için ayrı bir bildirim kullanmanız gerekir. İsteğe bağlı.

### <a name="child-elements"></a>Alt öğeleri

- **VSTemplateContainer** Isteğe bağlı.

- **VSTemplateDir** Isteğe bağlı.

### <a name="parent-element"></a>Üst öğe
 Yok.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Şablon un kapsayıcısı öğeleri gösterir. Bir bildirimde tanımladığı her şablon için bir şablon kapsayıcısı vardır.

### <a name="attributes"></a>Öznitelikler
 **VSTemplateType**: Şablonun türünü (`"Project"`, , `"Item"`veya ) `"ProjectGroup"`belirten bir dize değeridir. Gerekli

### <a name="child-elements"></a>Alt öğeleri

- **RelativePathOnDisk**: Diskteki şablon dosyasının göreli yolu. Bu konum, **Yeni Proje** veya **Yeni Öğe** iletişim kutusunda gösterilen şablon ağacındaki şablonun yerleşimini de tanımlar. Dizin ve tek tek dosyalar olarak dağıtılan şablonlar için bu yol, şablon dosyalarını içeren dizini ifade eder. *.zip* dosyası olarak dağıtılan şablonlar için bu yol *.zip* dosyasına giden yol olmalıdır.

- **VSTemplateHeader: Üstbilgi açıklayan bir [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) öğesi.

### <a name="parent-element"></a>Üst öğe
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Şablonun bulunduğu dizinaçıklanır. Bir bildirim, yerelleştirilmiş ad ve dizinlerin şablon kategorisi ağacındaki görünümlerini denetlemeleri için sıralama sıralaması sağlamak için birden çok **VSTemplateDir** girişi içerebilir.

 Tasarımları **nedeniyle, VSTemplateDir** girişleri yalnızca yerel olmayan belirtilen bildirimlerde görünmelidir.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

- **RelativePath**: Şablonun yolu. Yol başına sadece bir giriş olabilir, bu yüzden ilki tüm manifestolar için kazanır.

- **LocalizedName**: Yerelleştirilmiş adı belirten bir **NameDescriptionIcon** öğesi. İsteğe bağlı.

- **SortOrder**: Sıralama sırasını belirten dize. İsteğe bağlı.

- **ParentFolderOverrideName**: Üst klasörün geçersiz kılınan adı. İsteğe bağlı. Bu öğe, adı belirten bir dize değeri olan bir **Ad** özniteliği vardır.

### <a name="parent-element"></a>Üst öğe
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Büyük olasılıkla yerelleştirilmiş şablonlar için adı ve açıklamayı belirtir. Yukarıdaki **LocalizedName'e** bakın.

### <a name="attributes"></a>Öznitelikler

- **Paket**: Paketi belirten bir dize değeri. İsteğe bağlı.

- **ID**: Kimliği belirten bir dize değeri. İsteğe bağlı.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-element"></a>Üst öğe
 **Localizedname**

## <a name="examples"></a>Örnekler
 Aşağıdaki kod, bir proje şablonu *.vstman* dosyasına örnektir.

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

 Aşağıdaki kod bir öğe şablonu *.vstman* dosyasının bir örneğidir.

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
