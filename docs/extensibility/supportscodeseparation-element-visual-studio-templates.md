---
title: SupportsCodeSeparation Öğesi (Visual Studio Şablonları)
titleSuffix: ''
description: SupportsCodeSeparation öğesini ve Yeni Öğe Ekle iletişim kutusunda Kodu ayrı bir dosyaya ekle onay kutusunun etkinleştirildikten nasıl emin olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1f33f86722621b6c069363f3136a62b497ed5d31a78c2744f5432bea1c44832
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431454"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation Öğesi (Visual Studio Şablonları)
Yeni Öğe Ekle iletişim **kutusunda Kodu ayrı bir dosyaya ekle** onay kutusunun etkin olup **olmadığını** belirtir.

 \<VSTemplate> \<TemplateData>
 \<SupportsCodeSeparation>

## <a name="syntax"></a>Syntax

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırarak Yeni Görünüm'de veya **Yeni Project** iletişim **kutusunda nasıl görüntü** olduğunu tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metin, Yeni Öğe Ekle iletişim kutusunda Kodu ayrı bir dosyaya ekle onay kutusunun etkin olup olmadığını belirten `true` `false` **veya** olmalıdır. 

## <a name="remarks"></a>Açıklamalar
 `SupportsCodeSeparation` isteğe bağlı bir öğedir. `false` varsayılan değerdir.

 öğesi `SupportsCodeSeparation` yalnızca Web öğesi şablonları için kullanılabilir.

 Kod ayrımı veya arka arkasındaki kod sayfası modeli, işaretlemeyi bir dosyada ve programlama kodunu başka bir dosyada tutmanıza olanak sağlar. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ve diğer .NET dilleri bu modeli kullanır.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte Kodu ayrı bir dosyaya **yerle seçeneğinin görüntüleniyor olduğu gösterilir.**

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
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
