---
title: vstemplate öğesi (Visual Studio şablonları) | Microsoft Docs
description: VSTemplate öğesi hakkında bilgi edinin ve proje şablonu, öğe şablonu veya Starter Kit hakkında tüm meta verileri nasıl içerdiğini öğrenin.
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
ms.openlocfilehash: b57965d7b59ca921c0b3831c24413709f85f0ff5ee8a394f357629ea66992357
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121335218"
---
# <a name="vstemplate-element-visual-studio-templates"></a>vstemplate öğesi (Visual Studio şablonları)
Proje şablonu, öğe şablonu veya Starter Kit ile ilgili tüm meta verileri içerir.

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
| `Type` | Şablonu bir proje şablonu veya bir öğe şablonu olarak tanımlar. Bu öznitelik veya değerine sahip olabilir `Project` `Item` . |
| `Version` | Şablon için sürüm numarasını belirtir. Ve içindeki [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] Şablonlar [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] `Version` özniteliği değeri `3.0.0` . |

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> şablonu sınıflandırmakta olan verileri belirtir ve **yeni Project** veya **yeni öğe ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonun içeriğini belirtir.|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|İsteğe bağlı öğe.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|İsteğe bağlı öğe.|

### <a name="parent-elements"></a>Üst öğeler
 Yok.

## <a name="remarks"></a>Açıklamalar
 `VSTemplate`Öğesi *. vstemplate* dosyalarının kök öğesidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulama için bir proje şablonu meta verilerini gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

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
- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
