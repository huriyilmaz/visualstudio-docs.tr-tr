---
title: SupportsCodeSeparation Element (Visual Studio Şablonları) | Microsoft Dokümanlar
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
ms.openlocfilehash: bd52ae47f47f3ca1fce23f7cf8d37260ec86fb0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699504"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation Öğesi (Visual Studio Şablonları)
**Yeni Öğe Ekle** iletişim kutusunda ayrı dosya onay **kutusundaki Yer kodunun** etkin olup olmadığını belirtir.

 \<VSTemplate \<> ŞablonVeri> \<DesteklerCodeSeparation>

## <a name="syntax"></a>Sözdizimi

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve Yeni **Proje** veya **Yeni Öğe** iletişim kutusunda nasıl görüntülenebildiğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Yeni **Öğe Ekle** `false`iletişim kutusunda ayrı dosya onay **kutusundaki Yer kodunun** etkin olup olmadığını belirten metin veya `true` metin olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `SupportsCodeSeparation`isteğe bağlı bir unsurdur. Varsayılan değer: `false`.

 Öğe `SupportsCodeSeparation` yalnızca Web öğesi şablonları için kullanılabilir.

 Kod ayırma veya kod arkası sayfa modeli, biçimlendirmeyi bir dosyada, programlama kodunu başka bir dosyada tutmanızı sağlar. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]ve diğer .NET dilleri bu modeli kullanır.

## <a name="example"></a>Örnek
 Aşağıdaki **örnekte, Yer kodunu ayrı bir dosya seçeneğinde** görüntülemek için belirtin.

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
