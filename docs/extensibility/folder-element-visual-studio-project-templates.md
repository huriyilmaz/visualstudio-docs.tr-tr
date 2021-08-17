---
title: Klasör Öğesi (Visual Studio Project Şablonları) | Microsoft Docs
description: Klasör öğesi ve projeye eklenecek klasörü nasıl belirtir hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: f06f0a5323073304bda5126351ad07373be66ae39a3947e5fb95c553f827b674
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432637"
---
# <a name="folder-element-visual-studio-project-templates"></a>Klasör öğesi (Visual Studio proje şablonları)
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
|`TargetFolderName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan proje oluşturulduğunda klasöre eklenecek adı belirtir. Bu öznitelik, bir klasör adı oluşturmak veya bir klasörü doğrudan.zipdosyasında kullanılam bir uluslararası dizeyle *adlandırmak için parametre değiştirme kullanmak için* yararlıdır.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|`Folder`|Projeye eklenecek klasörü belirtir. `Folder` öğeleri alt öğeleri `Folder` içerebilir.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Projeye eklenecek bir dosyayı belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent öğesinin isteğe bağlı alt öğesi.](../extensibility/templatecontent-element-visual-studio-templates.md)|

## <a name="remarks"></a>Açıklamalar
 `Folder` isteğe bağlı bir alt alt `Project` veridir.

 Proje öğelerini bir şablondaki klasörlerde düzenlemek için aşağıdaki yöntemlerden herhangi birini kullanabilirsiniz:

- Klasörlerini şablon *.zip* dosyasına ekleyin ve öğelerinde öğe içermeden dosyanın yolunu belirterek *.vstemplate* dosyasındaki `ProjectItem` projeye `Folder` ekleyin. Bu önerilen yöntemdir. Örnek:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Klasörlerini şablon.zip *ekleyin* ve *öğeleriyle .vstemplate* dosyasındaki projeye `Folder` ekleyin. Örnek:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Şablona klasör ekleme *.zip,* ancak öğesinin özniteliğini kullanarak `TargetFileName` klasörler `ProjectItem` ekleyin. Örnek:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulamanın proje şablonunun meta [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] verilerini Windows göstermektedir.

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
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
