---
title: VSTemplate Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: VSTemplate öğesini ve proje şablonu, öğe şablonu veya başlangıç seti ile ilgili tüm meta verileri nasıl içerdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7509614613ac80bc4f697f7f93358819eb9ecde4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726893"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate öğesi (Visual Studio Şablonları)
Proje şablonu, öğe şablonu veya başlangıç seti ile ilgili tüm meta verileri içerir.

## <a name="syntax"></a>Syntax

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
|-----------| - |
| `Type` | Şablonu proje şablonu veya öğe şablonu olarak tanımlar. Bu öznitelik veya değerine `Project` sahip `Item` olabilir. |
| `Version` | Şablon için bir sürüm numarası belirtir. ve [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] şablonlarının [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] öznitelik değeri `Version` `3.0.0` vardır. |

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayıran verileri belirtir ve yeni şablonun Yeni Project veya **Yeni Öğe Ekle** iletişim kutusunda nasıl **görüntü** olduğunu tanımlar.|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonun içeriğini belirtir.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|İsteğe bağlı öğe.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|İsteğe bağlı öğe.|

### <a name="parent-elements"></a>Üst öğeler
 Yok.

## <a name="remarks"></a>Açıklamalar
 öğesi `VSTemplate` , *.vstemplate dosyalarının kök öğesidir.*

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulama için proje şablonu meta verilerini [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] gösterir.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
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
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
