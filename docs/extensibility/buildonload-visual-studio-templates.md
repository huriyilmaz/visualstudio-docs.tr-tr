---
title: buildonload özniteliği ve öğesi (Visual Studio şablonları)
titleSuffix: ''
description: BuildOnLoad özniteliği ve öğesi hakkında bilgi edinin ve oluşturulduktan sonra projenin oluşturulup derlenmeyeceğini nasıl belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 912616d180d732d987a2ff5aa16fbd522458cafc5b4250ca89fd53bd36867977
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452660"
---
# <a name="buildonload-attribute-and-element"></a>BuildOnLoad özniteliği ve öğesi

Oluşturulduktan sonra projenin hemen oluşturulup derlenmeyeceğini belirtir. **Buildonload** özniteliği ve bir öğesidir.

Öğe hiyerarşisi:

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Öğe sözdizimi

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|şablonu kategorilere ayırır ve **yeni Project** ya da **yeni öğe ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri

**Buildonload** öğesi için bir metin değeri gereklidir. Metin `true` veya oluşturulduktan `false` sonra projenin hemen oluşturulup derlenmeyeceğini belirten olmalıdır.

## <a name="remarks"></a>Açıklamalar

**Buildonload** , isteğe bağlı bir özniteliktir. `false` varsayılan değerdir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, **Buildonload** bir öğe olarak kullanıldığında bir C# şablonu meta verilerini gösterir:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildOnLoad>true</BuildOnLoad>
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

- [BuildProjectOnload öğesi](buildprojectonload-element-visual-studio-templates.md)
- [TemplateContent öğesi](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
