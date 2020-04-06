---
title: Proje Elemanı (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701999"
---
# <a name="project-element-visual-studio-templates"></a>Proje öğesi (Visual Studio şablonları)
Projeye eklenecek dosyaları veya dizinleri belirtir.

 \<VSTemplate \<> Şablonİçerik> \<Proje>

## <a name="syntax"></a>Sözdizimi

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
|`File`|Gerekli öznitelik.<br /><br /> Şablon *.zip* dosyasında proje dosyasının adını belirtir.|
|`ReplaceParameters`|İsteğe bağlı öznitelik.<br /><br /> Proje dosyasının şablondan bir proje oluşturulduğunda değiştirilmesi gereken parametre değerlerine sahip olup olmadığını belirten boolean değeri. Varsayılan değer. `false`|
|`TargetFileName`|İsteğe bağlı öznitelik.<br /><br /> Şablondan bir proje oluşturulduğunda proje dosyasının adını belirtir.|
|`IgnoreProjectParameter`|İsteğe bağlı öznitelik.<br /><br /> Projenin geçerli çözüme eklenip eklenmeyeceğini belirtir. Özel parametre değeri, "$*myCustomParameter*$" parametre değiştirme dosyasında varsa, proje oluşturulur, ancak şu anda açık çözümün bir parçası olarak eklenmez.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Klasör](../extensibility/folder-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeye eklemek için bir klasör belirtir.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeye eklemek için bir dosya belirtir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.|

## <a name="remarks"></a>Açıklamalar
 `Project`isteğe bağlı bir `TemplateContent`alt öğedir.

 Öğe `Project` bir projeyi belirtiretmek için kullanılır ve bu nedenle, yalnızca proje şablonlarında geçerlidir.

 `Project`öğeler [klasör](../extensibility/folder-element-visual-studio-project-templates.md) alt öğeleri veya [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) alt öğeleri olabilir, `ProjectItem` ancak hem de `Folder` alt öğelerin bir karışımı.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]kullanıcı tarafından **Yeni Proje** iletişim kutusunda girilen ada göre proje dosya adını otomatik olarak yeniden adlandırır. `TargetFileName` Şablonla oluşturulan proje dosyaları için alternatif bir dosya adı sağlamak istiyorsanız özniteliği kullanın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] uygulama için proje şablonu için meta verileri gösterir.

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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [ProjectItem öğesi (Visual Studio proje şablonları)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Klasör öğesi (Visual Studio proje şablonları)](../extensibility/folder-element-visual-studio-project-templates.md)
