---
title: SupportsCodeSeparation Öğesi (Visual Studio Şablonları)
titleSuffix: ''
description: Supportscodeayrım öğesi ve yeni öğe Ekle iletişim kutusunda farklı dosya Yerleştir onay kutusunun etkin olup olmadığını nasıl belirttiği hakkında bilgi edinin.
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1847d5f0a0fa77b1dd0ddd0d74eeba84326d0205
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901862"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation Öğesi (Visual Studio Şablonları)
**Yeni öğe Ekle** iletişim kutusunda **farklı dosya yerleştir** onay kutusunun etkin olup olmadığını belirtir.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** ya da **Yeni öğe** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metin `true` , ya da `false` **Yeni öğe Ekle** Iletişim kutusunda **farklı dosya yerleştir** onay kutusunun etkin olup olmadığını belirten bir değer olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `SupportsCodeSeparation` isteğe bağlı bir öğedir. `false` varsayılan değerdir.

 `SupportsCodeSeparation`Öğesi yalnızca Web öğesi şablonları için kullanılabilir.

 Kod ayrımı veya arka plan kod modeli, biçimlendirmeyi bir dosyada ve diğer bir dosyadaki programlama kodunda tutmanıza olanak sağlar. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ve diğer .NET dilleri bu modeli kullanır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, **yer kodunu ayrı dosya** seçeneğinde göstermek için belirtir.

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
