---
title: SolutionFolder Element (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder
helpviewer_keywords:
- <SolutionFolder> element [Visual Studio Templates]
- SolutionFolder element [Visual Studio Templates]
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3262a5dcc0f226a0ac1b3aa08219fb89dbf70e83
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699998"
---
# <a name="solutionfolder-element-visual-studio-templates"></a>SolutionFolder Öğesi (Visual Studio Şablonları)
Birden fazla projeli şablonlardaki projeleri gruplandırır.

 \<VSTemplate \<> TemplateContent \<> \<ProjectCollection> SolutionFolder>

## <a name="syntax"></a>Sözdizimi

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
 Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. Öğe, `SolutionFolder` şablondaki projeleri gruplar halinde düzenlemek için kullanılır. Öğeler tarafından `SolutionFolder` belirtilen klasörler projede çözüm klasörleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]olarak oluşturulur. Çoklu proje şablonları hakkında daha fazla bilgi için [bkz.](../ide/how-to-create-multi-project-templates.md)

## <a name="example"></a>Örnek
 Bu örnek, `SolutionFolder` çoklu proje şablonu iki gruba `Math Classes` bölmek `Graphics Classes`için öğeyi kullanır ve. Şablon, ikisi her çözüm klasörüne yerleştirilen dört proje içerir.

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
