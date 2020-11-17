---
title: ProjectSubType öğesi (Visual Studio şablonları) | Microsoft Docs
description: ProjectSubType öğesi ve şablonu, ProjectType öğesinde belirtilen değerin bir alt kategorisine nasıl sınıflandırdığı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9ceecbf1bfb750244a13c641906f7a8712d01d69
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672326"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType öğesi (Visual Studio şablonları)
Şablonu, öğesinde belirtilen değerin bir alt kategorisine sınıflandırır `ProjectType` .

 \<VSTemplate> \<TemplateData>
 \<ProjectSubType>

## <a name="syntax"></a>Syntax

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu değer, şablonun alt kategorisini belirtir.

## <a name="remarks"></a>Açıklamalar
 `ProjectSubType` , öğesinin isteğe bağlı bir alt öğesidir `TemplateData` .

 `ProjectSubType`Öğesi [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) öğesine bir alt kategori sağlar. Bu değer şunlar olabilir:

- `SmartDevice-NETCFv1`: Şablonun 1,0 sürümünü hedeflediğini belirtir [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] .

- `SmartDevice-NETCFv2`: Şablonun 2,0 sürümünü hedeflediğini belirtir [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] .

  Bir şablon `ProjectType` değeri olan bir öğesi içeriyorsa `Web` , `ProjectSubType` öğesi şablonun programlama dilini belirtir. Bu öğe aşağıdaki değerlere sahip olabilir:

- `CSharp`: Şablonun bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Web projesi veya öğe oluşturduğunu belirtir.

- `VisualBasic`: Şablonun bir [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Web projesi veya öğe oluşturduğunu belirtir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 2,0 sürümünü hedefleyen bir cihaz uygulaması için bir proje şablonu meta verilerini gösterir [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] .

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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [ProjectType öğesi (Visual Studio şablonları)](../extensibility/projecttype-element-visual-studio-templates.md)
