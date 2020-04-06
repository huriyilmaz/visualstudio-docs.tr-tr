---
title: ProjectSubType Elemanı (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701829"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType öğesi (Visual Studio şablonları)
Şablonu öğede belirtilen değerin bir alt `ProjectType` kategorisine sınıflandırın.

 \<VSTemplate \<> ŞablonVeri> \<ProjectSubType>

## <a name="syntax"></a>Sözdizimi

```xml
<ProjectSubType> SubType </ProjectSubType>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu değer, şablonun alt kategorisini belirtir.

## <a name="remarks"></a>Açıklamalar
 `ProjectSubType`isteğe bağlı bir `TemplateData`alt öğedir.

 Öğe `ProjectSubType` [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) öğesine bir alt kategori sağlar. Bu değer şunları içerebilir:

- `SmartDevice-NETCFv1`: Şablonun sürüm 1.0'ı [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] hedef aldığını belirtir.

- `SmartDevice-NETCFv2`: Şablonun sürüm 2.0'ı [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] hedef aldığını belirtir.

  Şablon, `ProjectType` `Web`öğe değerine sahip bir `ProjectSubType` öğe içeriyorsa, öğe şablonun programlama dilini belirtir. Bu öğe aşağıdaki değerlere sahip olabilir:

- `CSharp`: Şablonun bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Web projesi veya öğesi oluşturduğunu belirtir.

- `VisualBasic`: Şablonun bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Web projesi veya öğesi oluşturduğunu belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, sürüm 2.0'ı [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] hedefleyen bir aygıt [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] uygulaması için proje şablonu meta verilerini gösterir.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [ProjectType öğesi (Visual Studio şablonları)](../extensibility/projecttype-element-visual-studio-templates.md)
