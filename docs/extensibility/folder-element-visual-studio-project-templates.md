---
title: Klasör Elemanı (Visual Studio Proje Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711462"
---
# <a name="folder-element-visual-studio-project-templates"></a>Klasör öğesi (Visual Studio proje şablonları)
Projeye eklenecek bir klasör belirtir.

 \<VSTemplate \<> Şablonİçerik \< \<> Proje> Klasör>

## <a name="syntax"></a>Sözdizimi

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
|`TargetFolderName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda klasöre verecek adı belirtir. Bu öznitelik, bir klasör adı oluşturmak için parametre değiştirme kullanmak veya doğrudan *.zip* dosyasında kullanılamayacak uluslararası bir dize içeren bir klasöre isim vermek için yararlıdır.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|`Folder`|Projeye eklemek için bir klasör belirtir. `Folder`öğeleri alt `Folder` öğeleri içerebilir.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Projeye eklemek için bir dosya belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent'in](../extensibility/templatecontent-element-visual-studio-templates.md)isteğe bağlı alt öğesi.|

## <a name="remarks"></a>Açıklamalar
 `Folder`isteğe bağlı `Project`bir çocuktur.

 Proje öğelerini şablondaki klasörlere düzenlemek için aşağıdaki yöntemlerden birini kullanabilirsiniz:

- Şablon *.zip* dosyasına klasörleri ekleyin ve `ProjectItem` öğelerde hiçbir `Folder` öğe olmadan dosyaya giden yolu belirterek *.vstemplate* dosyasındaki projeye ekleyin. Bu önerilen yöntemdir. Örnek:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Şablon *.zip* dosyasındaki klasörleri ekleyin ve öğeleri içeren `Folder` *.vstemplate* dosyasındaki projeye ekleyin. Örnek:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Şablon *.zip* dosyasına klasörler eklemeyin, `TargetFileName` `ProjectItem` ancak öğenin özniteliğini kullanarak klasörler ekleyin. Örnek:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows uygulaması için proje şablonu için meta veriler gösterilmiştir.

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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [ProjectItem öğesi (Visual Studio öğe şablonları)](../extensibility/projectitem-element-visual-studio-item-templates.md)
