---
title: ProjectCollection Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12a22ca28c90ed1df69529ed3004b417b5e04276
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701972"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection öğesi (Visual Studio şablonları)
Birden fazla projeli şablonların içeriğini ve düzenini belirtir.

 \<VSTemplate \<> Şablonİçerik> \<ProjectCollection>

## <a name="syntax"></a>Sözdizimi

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
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Projeyi çok proje şablonunda belirtir.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Birden fazla projeli şablonlardaki projeleri gruplandırır.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonun içeriğini belirtir.|

## <a name="remarks"></a>Açıklamalar
 Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. Öğe, `ProjectCollection` şablonda yer alan projeleri belirtmek için kullanılır. Çoklu proje şablonları hakkında daha fazla bilgi için [bkz.](../ide/how-to-create-multi-project-templates.md)

## <a name="example"></a>Örnek
 Bu örnek, basit bir çok proje kökü *.vstemplate* dosyagösterir. Bu örnekte, şablon iki `My Windows Application` proje `My Class Library`içerir ve . Öğedeki `ProjectName` `ProjectTemplateLink` öznitelik, bu projeyi atamak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adı ayarlar. `ProjectName` Öznitelik yoksa, *.vstemplate* dosyasının adı proje adı olarak kullanılır.

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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl yapılı: Çoklu proje şablonları oluşturma](../ide/how-to-create-multi-project-templates.md)
