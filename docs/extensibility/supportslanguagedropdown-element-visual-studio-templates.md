---
title: SupportsLanguageDropDown Öğesi (Visual Studio Şablonları)
titleSuffix: ''
description: SupportsLanguageDropDown öğesini ve Web öğesi şablonunun birden çok dil için aynı olup olmadığını ve Dil seçeneğinin etkin olup olmadığını nasıl belirtir hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f02b7b70e3caedca11a41fd399ec80e84c4c8a39ccfc8eb98db795a4d49fa58b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121413823"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown Öğesi (Visual Studio Şablonları)

Web öğesi şablonunun birden çok dil için aynı  olup olmadığını ve Yeni Öğe Ekle iletişim kutusunda Dil seçeneğinin etkin **olup** olmadığını belirtir.

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Syntax

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

 Yok.

### <a name="child-elements"></a>Alt Öğeler

 Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırarak Yeni Öğe Ekle iletişim kutusunda **Project** **nasıl görüntü olduğunu** tanımlar.|

## <a name="text-value"></a>Metin Değeri

 Bir metin değeri gereklidir.

 Metin, Yeni Öğe Ekle iletişim kutusunda Dil seçeneğinin kullanılabilir olup olmadığını `true` `false` belirten **veya** olması gerekir. 

## <a name="remarks"></a>Açıklamalar

 `SupportsLanguageDropDown` isteğe bağlı bir öğedir. `false` varsayılan değerdir.

 öğesi `SupportsLanguageDropDown` yalnızca Web öğesi şablonları için kullanılabilir.

 Bu öğenin değeri olarak ayarlanırsa, öğe şablonu tüm programlama dilleri için aynıdır ve Dil seçeneği Yeni Öğe Ekle `true` **iletişim kutusunda** etkinleştirilir.  Bu seçenek, şablondan oluşturmak istediğiniz yeni öğenin programlama dilini seçmenize olanak sağlar.

## <a name="example"></a>Örnek

 Aşağıdaki örnekte Dil açılan **seçeneğinin görüntüleniyor** olduğu gösterilir.

```xml
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
