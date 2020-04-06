---
title: SupportsLanguageDropDown Element (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1230b493fe746a272cf4ca4cffe9d197afd8ba1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699464"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown Öğesi (Visual Studio Şablonları)
Web öğesi şablonu birden çok dil için aynı olup olmadığını ve **Yeni Öğe Ekle** iletişim kutusunda **Dil** seçeneğinin etkin olup olmadığını belirtir.

 \<VSTemplate \<> ŞablonVeri> \<DesteklerLanguageDropDown>

## <a name="syntax"></a>Sözdizimi

```
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metin, `true` Yeni Öğe `false` **Ekle** iletişim **kutusundan Dil** seçeneğinin kullanılabilir olup olmadığını belirten metin olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `SupportsLanguageDropDown`isteğe bağlı bir unsurdur. Varsayılan değer: `false`.

 Öğe `SupportsLanguageDropDown` yalnızca Web öğesi şablonları için kullanılabilir.

 Bu öğenin değeri `true`,, öğe şablonu tüm programlama dilleri için aynıdır ve **Dil** seçeneği Yeni Öğe **Ekle** iletişim kutusunda etkinleştirilir. Bu seçenek, şablondan oluşturmak istediğiniz yeni öğenin programlama dilini seçmenize olanak tanır.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte **Dil** açılır seçeneğini görüntülemek için belirtilir.

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
