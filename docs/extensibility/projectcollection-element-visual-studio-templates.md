---
title: ProjectCollection öğesi (Visual Studio şablonları) | Microsoft Docs
description: ProjectCollection öğesi hakkında bilgi edinin ve çoklu proje şablonlarının organizasyonunu ve içeriğini nasıl belirtir.
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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 29a73f1e0c7a39bb5ffaa1877cbaff7aa54c3930
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959408"
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
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Çoklu Proje şablonundaki bir projeyi belirtir.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Birden fazla projeli şablonlardaki projeleri gruplandırır.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonun içeriğini belirtir.|

## <a name="remarks"></a>Açıklamalar
 Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. `ProjectCollection`Öğesi şablonda yer almak üzere projeleri belirtmek için kullanılır. Çoklu proje şablonları hakkında daha fazla bilgi için bkz. [nasıl yapılır: çoklu proje şablonları oluşturma](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Örnek
 Bu örnekte basit bir çoklu proje root *. vstemplate* dosyası gösterilmektedir. Bu örnekte, şablon iki proje içerir `My Windows Application` ve `My Class Library` . `ProjectName`Öğesi üzerindeki özniteliği, `ProjectTemplateLink` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Bu projeyi atamak için adını ayarlar. `ProjectName`Özniteliği yoksa, *. vstemplate* dosyasının adı proje adı olarak kullanılır.

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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılır: birden çok proje şablonu oluşturma](../ide/how-to-create-multi-project-templates.md)
