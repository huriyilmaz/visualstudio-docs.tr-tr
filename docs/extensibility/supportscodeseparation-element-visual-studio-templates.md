---
title: Supportscodeayrım öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e68516a798bcd4d1437ab504c09b4cc529eb889
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719423"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation Öğesi (Visual Studio Şablonları)
**Yeni öğe Ekle** iletişim kutusunda **farklı dosya yerleştir** onay kutusunun etkin olup olmadığını belirtir.

 \<VSTemplate > \<TemplateData > \<SupportsCodeSeparation >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** ya da **Yeni öğe** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metnin, **Yeni öğe Ekle** iletişim kutusunda **ayrı dosya olarak Yerleştir** onay kutusunun etkin olup olmadığını gösteren `true` veya `false` olması gerekir.

## <a name="remarks"></a>Açıklamalar
 `SupportsCodeSeparation`, isteğe bağlı bir öğedir. Varsayılan değer `false` şeklindedir.

 @No__t_0 öğesi yalnızca Web öğesi şablonları için kullanılabilir.

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