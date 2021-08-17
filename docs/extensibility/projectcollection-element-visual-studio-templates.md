---
title: ProjectCollection Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: ProjectCollection öğesini ve çok projeli şablonların kuruluş ve içeriklerini nasıl belirtir hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1e6d37b55837b0a069148f7bd6c74da0da3511e664d253fdaa7c0de0b80ab7dc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431584"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection öğesi (Visual Studio şablonları)
Birden fazla projeli şablonların içeriğini ve düzenini belirtir.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>

## <a name="syntax"></a>Syntax

```xml
<ProjectCollection>
    <ProjectTemplateLink> ... </ProjectTemplateLink>
    <SolutionFolder> ... </SolutionFolder>
</ProjectCollection>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Çok projeli bir şablonda bir proje belirtir.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Birden fazla projeli şablonlardaki projeleri gruplandırır.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonun içeriğini belirtir.|

## <a name="remarks"></a>Açıklamalar
 Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. `ProjectCollection`öğesi, şablonda yer alan projeleri belirtmek için kullanılır. Birden çok projeli şablonlar hakkında daha fazla bilgi için [bkz. Nasıl 2012:](../ide/how-to-create-multi-project-templates.md)Birden çok proje şablonu oluşturma.

## <a name="example"></a>Örnek
 Bu örnekte basit bir çok projeli kök *.vstemplate dosyası* gösterir. Bu örnekte şablon iki proje içerir: `My Windows Application` ve `My Class Library` . öğesinde `ProjectName` `ProjectTemplateLink` özniteliği, bu projeyi atamak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] için için adını ayarlar. Öznitelik `ProjectName` yoksa proje adı olarak *.vstemplate* dosyasının adı kullanılır.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılanlar: Çok projeli şablonlar oluşturma](../ide/how-to-create-multi-project-templates.md)
