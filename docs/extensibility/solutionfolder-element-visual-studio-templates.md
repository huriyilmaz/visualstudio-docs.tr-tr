---
title: solutionfolder öğesi (Visual Studio şablonları) | Microsoft Docs
description: SolutionFolder öğesi hakkında bilgi edinin ve birden çok projeli şablonlarda projeleri nasıl gruplandırır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c8865456b5b25b2f65a839bd947f558e803803533c7aa58f51f6bf01aa0a679
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121273610"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder Öğesi (Visual Studio Şablonları)
Birden fazla projeli şablonlardaki projeleri gruplandırır.

 \<VSTemplate> \<TemplateContent>
 \<ProjectCollection>
 \<SolutionFolder>

## <a name="syntax"></a>Syntax

```
<SolutionFolder Name="DirectoryName">
    ...
</SolutionFolder>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gerekli öznitelik.<br /><br /> Çözüm klasörünün adı.|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Birden fazla projeli bir şablonda, tek bir projenin .vstemplate dosyasının yolunu belirtir.|
|`SolutionFolder`|İsteğe bağlı öğe.<br /><br /> Birden fazla projeli şablonlardaki projeleri gruplandırır.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Birden fazla projeli şablonların içeriğini ve düzenini belirtir.|
|`SolutionFolder`|Birden fazla projeli şablonlardaki projeleri gruplandırır.|

## <a name="remarks"></a>Açıklamalar
 Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. `SolutionFolder`Öğesi şablondaki projeleri gruplar halinde düzenlemek için kullanılır. Öğeleri tarafından belirtilen klasörler, `SolutionFolder` içindeki projede çözüm klasörleri olarak oluşturulur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . çoklu proje şablonları hakkında daha fazla bilgi için bkz. [nasıl yapılır: çoklu Project şablonları oluşturma](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Örnek
 Bu örnek, `SolutionFolder` Çoklu proje şablonunu iki gruba bölmek için öğesini kullanır `Math Classes` ve `Graphics Classes` . Şablon, her bir çözüm klasörüne yerleştirilmiş dört proje içerir.

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
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
- [Nasıl Yapılır: Birden Çok Proje Şablonu Oluşturma](../ide/how-to-create-multi-project-templates.md)
