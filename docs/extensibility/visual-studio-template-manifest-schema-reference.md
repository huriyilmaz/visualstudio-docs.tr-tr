---
title: Visual Studio şablon bildirimi şema başvurusu | Microsoft Docs
description: Bu şema başvurusu, Visual Studio projesi veya öğe şablonları için oluşturulan Visual Studio şablon bildirim dosyalarının biçimini açıklar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 259d2dd050f4681053f331bfd4ec39dd7b214059
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905390"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio şablon bildirim Şeması Başvurusu
Bu şema, Visual Studio projesi veya öğe şablonları için oluşturulan Visual Studio şablon bildirimi (*. vstman*) dosyalarının biçimini açıklar. Şema Ayrıca, bu şablonla ilgili konumu ve ilgili diğer bilgileri de açıklar.

 : Ayrı öğe ve proje şablonu dizinleri olduğundan, bir bildirimin öğe ve proje şablonlarının karışımı asla olmaması gerekir.

> [!IMPORTANT]
> Bu bildirim, Visual Studio 2017 ' den itibaren kullanılabilir.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest öğesi
 Bildirimin kök öğesi.

### <a name="attributes"></a>Öznitelikler

- **Sürüm**: şablon bildiriminin sürümünü temsil eden bir dize. Gereklidir.

- **Yerel ayar**: şablon bildiriminin yerel ayarlarını veya yerel ayarlarını temsil eden bir dize. Yerel ayar değeri tüm şablonlar için geçerlidir. Her yerel ayar için ayrı bir bildirim kullanmanız gerekir. İsteğe bağlı.

### <a name="child-elements"></a>Alt öğeleri

- **VSTemplateContainer** Seçim.

- **VSTemplateDir** Seçim.

### <a name="parent-element"></a>Üst öğe
 Yok.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Şablon bildirim öğelerinin kapsayıcısı. Bir bildirimin tanımladığı her şablon için bir şablon kapsayıcısı vardır.

### <a name="attributes"></a>Öznitelikler
 **VSTemplateType**: şablonun türünü belirten bir dize değeri ( `"Project"` , `"Item"` , veya `"ProjectGroup"` ). Gerekli

### <a name="child-elements"></a>Alt öğeleri

- **Relativepathondisk**: diskteki şablon dosyasının göreli yolu. Bu konum Ayrıca şablonun **Yeni proje** veya **Yeni öğe** iletişim kutusunda gösterilen şablon ağacında yerleşimini tanımlar. Dizin ve ayrı dosyalar olarak dağıtılan şablonlar için, bu yol şablon dosyalarını içeren dizine başvurur. *.zip* dosyası olarak dağıtılan şablonlar için, bu yol *.zip* dosyasının yolu olmalıdır.

- * * VSTemplateHeader: üstbilgiyi açıklayan bir [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) öğesi.

### <a name="parent-element"></a>Üst öğe
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Şablonun bulunduğu dizini açıklar. Bir bildirim, dizinler için yerelleştirilmiş ad ve sıralama düzeni sağlamak üzere, şablon Kategori ağacındaki görünümleri denetlemek için birden çok **VSTemplateDir** girişi içerebilir.

 **VSTemplateDir** girdileri, tasarımı nedeniyle yalnızca yerel ayar olmayan belirtilen bildirimlerde görünmelidir.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

- **RelativePath**: şablonun yolu. Yol başına yalnızca bir giriş olabilir, bu nedenle ilki tüm bildirimler için kazanacaktır.

- **LocalizedName**: yerelleştirilmiş adı belirten bir **namedescriptionıcon** öğesi. İsteğe bağlı.

- **SortOrder**: sıralama düzenini belirten bir dize. İsteğe bağlı.

- **Parentfolderoverdename**: üst klasörün geçersiz kılınan adı. İsteğe bağlı. Bu öğe, adı belirten bir dize değeri olan bir **Name** özniteliğine sahiptir.

### <a name="parent-element"></a>Üst öğe
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>Namedescriptionıcon
 Büyük olasılıkla yerelleştirilmiş şablonlar için ad ve açıklamayı belirtir. Yukarıdaki **LocalizedName** bölümüne bakın.

### <a name="attributes"></a>Öznitelikler

- **Paket**: paketi belirten bir dize değeri. İsteğe bağlı.

- **ID**: kimliği belirten bir dize değeri. İsteğe bağlı.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-element"></a>Üst öğe
 **LocalizedName**

## <a name="examples"></a>Örnekler
 Aşağıdaki kod proje şablonu *. vstman* dosyasına bir örnektir.

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

 Aşağıdaki kod bir öğe şablonu *. vstman* dosyası örneğidir.

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
