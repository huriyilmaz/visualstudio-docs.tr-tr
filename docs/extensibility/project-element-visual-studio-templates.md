---
title: Project Element (Visual Studio Templates) | Microsoft Docs
description: Project hakkında bilgi ve projeye eklenecek dosyaları veya dizinleri nasıl belirtir?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 260b52b23be9857cc3850824b3eda8fe795abb701c21788df7b487ae6f5e111c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388558"
---
# <a name="project-element-visual-studio-templates"></a>Project öğesi (Visual Studio şablonları)
Projeye eklenecek dosyaları veya dizinleri belirtir.

 \<VSTemplate> \<TemplateContent>
 \<Project>

## <a name="syntax"></a>Syntax

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`File`|Gerekli öznitelik.<br /><br /> Şablon dosya dosyasında proje dosyasının adını *.zip* belirtir.|
|`ReplaceParameters`|İsteğe bağlı öznitelik.<br /><br /> Proje dosyasında şablondan proje oluşturulduğunda değiştirilmesi gereken parametre değerleri olup olmadığını belirten bir Boole değeri. Varsayılan değer `false` olarak belirlenmiştir.|
|`TargetFileName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan proje oluşturulduğunda proje dosyasının adını belirtir.|
|`IgnoreProjectParameter`|İsteğe bağlı öznitelik.<br /><br /> Projenin geçerli çözüme ekli olup olmadığını belirtir. Parametre değiştirme dosyasında "$*myCustomParameter*$" özel parametre değeri varsa, proje oluşturulur ancak o anda açık olan çözümün bir parçası olarak eklenmez.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Klasör](../extensibility/folder-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeye eklenecek klasörü belirtir.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeye eklenecek bir dosyayı belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.|

## <a name="remarks"></a>Açıklamalar
 `Project` isteğe bağlı bir alt `TemplateContent` öğesidir.

 `Project`öğesi bir projeyi tahmin etmek için kullanılır ve bu nedenle yalnızca proje şablonlarında geçerlidir.

 `Project` öğeleri Klasör [öğelerine](../extensibility/folder-element-visual-studio-project-templates.md) veya [ProjectItem öğelerine](../extensibility/projectitem-element-visual-studio-project-templates.md) sahip olabilir, ancak hem hem de öğelerinin `Folder` bir `ProjectItem` karışımına sahip değildir.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], yeni dosya adı iletişim kutusunda kullanıcı tarafından girilen ad temel alarak proje Project **yeniden** adlandırır. Şablonla `TargetFileName` oluşturulan proje dosyaları için alternatif bir dosya adı sağlamak için özniteliğini kullanın.

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
- [ProjectItem öğesi (Visual Studio şablonlarını oluşturma)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Klasör öğesi (Visual Studio proje şablonları)](../extensibility/folder-element-visual-studio-project-templates.md)
