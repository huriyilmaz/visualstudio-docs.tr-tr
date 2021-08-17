---
title: ProjectType Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: ProjectType öğesini ve proje şablonunu Yeni Öğe Ekle iletişim kutusunda Project kategorilere ayırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92fa66c122d441ed50e4ab83a4e0bfcce5c2e411372e97b45f747663cfc457c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400939"
---
# <a name="projecttype-element-visual-studio-templates"></a>ProjectType öğesi (Visual Studio şablonları)
Proje şablonunu, Yeni Uygulama veya Yeni Öğe Ekle iletişim kutusunda belirtilen grubun **Project** **şekilde kategorilere** ayırıyor.

> [!WARNING]
> Project 2012'den başlayarak C++ Visual Studio destekle. 2010 ve önceki sürümlerde C++ Visual Studio desteklanmaz.

 \<VSTemplate> \<TemplateData>
 \<ProjectType>

## <a name="syntax"></a>Syntax

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırarak Yeni Öğe Ekle iletişim kutusunda **Project** **şekilde** tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu değer, şablonun oluşturacağız projesinin türünü belirtir ve aşağıdaki değerlerden birini içermesi gerekir:

- `CSharp`: Şablonun bir proje veya öğe [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oluşturduğuna belirtir.

- `VisualBasic`: Şablonun bir proje veya öğe [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oluşturduğuna belirtir.

- `Web`: Şablonun bir Web projesi veya öğesi oluşturduğuna belirtir. Öğesi bu değeri içeriyorsa, proje veya öğenin dili `ProjectType` [ProjectSubType Öğesinde (Visual Studio Şablonları) tanımlanır.](../extensibility/projectsubtype-element-visual-studio-templates.md)

## <a name="remarks"></a>Açıklamalar
 `ProjectType` , öğesinin gerekli bir alt `TemplateData` öğesidir.

 öğesinin değeri, şablonun New Project veya Add New Item (Yeni Öğe `ProjectType` **Ekle)** **iletişim kutusunda bulunduğu** yeri belirtir. Örneğin, Değerine sahip bir şablon, Yeni Uygulama iletişim kutusundaki `ProjectType` `CSharp` Visual **C#** düğümü **altında Project** görünür.

 [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) öğesi kullanılarak bir şablon alt türü belirtilebilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulama için proje şablonu meta verilerini [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] gösterir.

```
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
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [ProjectSubType öğesi (Visual Studio şablonları)](../extensibility/projectsubtype-element-visual-studio-templates.md)
