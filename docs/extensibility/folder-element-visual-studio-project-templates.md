---
title: Folder öğesi (Visual Studio proje şablonları) | Microsoft Docs
description: Klasör öğesi ve projenin projeye eklenecek bir klasörü nasıl belirttiği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40e1df1d5efeab17adf60a8e1732991cb2cac02a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070134"
---
# <a name="folder-element-visual-studio-project-templates"></a>Folder öğesi (Visual Studio proje şablonları)
Projeye eklenecek klasörü belirtir.

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<Folder>

## <a name="syntax"></a>Syntax

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gerekli öznitelik.<br /><br /> Proje klasörünün adı.|
|`TargetFolderName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda klasöre verilecek adı belirtir. Bu öznitelik, bir klasör adı oluşturmak veya bir klasörü doğrudan *. zip* dosyasında kullanılamayan uluslararası bir dizeyle adlandırmak üzere parametre değişimini kullanmak için yararlıdır.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|`Folder`|Projeye eklenecek klasörü belirtir. `Folder` öğeler, alt `Folder` öğeleri içerebilir.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Projeye eklenecek bir dosya belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)öğesinin isteğe bağlı alt öğesi.|

## <a name="remarks"></a>Açıklamalar
 `Folder` , öğesinin isteğe bağlı bir alt öğesidir `Project` .

 Bir şablondaki klasörler halinde proje öğelerini düzenlemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz:

- Klasörleri template *. zip* dosyasına dahil edin ve öğe içinde dosya yolunu belirterek *. vstemplate* dosyasındaki projeye ekleyin ( `ProjectItem` hiçbir öğesi olmadan) `Folder` . Önerilen yöntem budur. Örnek:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Klasörleri template *. zip* dosyasına dahil edin ve *. vstemplate* dosyasındaki öğeleri öğeleriyle birlikte bu klasöre ekleyin `Folder` . Örnek:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Şablon *. zip* dosyasına klasörler eklemeyin, ancak öğesinin özniteliğini kullanarak klasörler ekleyin `TargetFileName` `ProjectItem` . Örnek:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir Windows uygulaması için bir proje şablonu meta verilerini gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
