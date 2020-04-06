---
title: BuildOnLoad öznitelik ve öğe (Visual Studio Şablonları)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3be4016822ccaaae2f1352f91ecc10f09273a889
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739962"
---
# <a name="buildonload-attribute-and-element"></a>BuildOnLoad özniteliği ve öğesi

Proje oluşturulduktan hemen sonra oluşturulup oluşturulmayacağını belirtir. **BuildOnLoad** hem bir öznitelik hem de bir öğedir.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri

**BuildOnLoad** öğesi için bir metin değeri gereklidir. Metin, proje `true` oluşturulduktan hemen sonra oluşturulup oluşturulmayacağını belirten bir metin olmalıdır. `false`

## <a name="remarks"></a>Açıklamalar

**BuildOnLoad** isteğe bağlı bir özelliktir. Varsayılan değer: `false`.

## <a name="example"></a>Örnek

Aşağıdaki örnek, **BuildOnLoad** öğesi olarak kullanıldığında C# şablonu için meta verileri göstermektedir:

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
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
