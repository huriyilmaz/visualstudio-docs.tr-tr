---
title: ProjectTemplateLink Elemanı (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701816"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink öğesi (Visual Studio şablonları)
Çok projeli şablonda bir projenin *.vstemplate* dosyasına giden yolu belirtir.

 \<VSTemplate \<> \<TemplateContent> \<ProjectCollection> ProjectTemplateLink> \<-or- VSTemplate> \<TemplateContent> \<ProjectCollection> \<SolutionFolder> \<ProjectTemplateLink>

## <a name="syntax"></a>Sözdizimi

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`ProjectName`|İsteğe bağlı öznitelik.<br /><br /> Birden fazla projeli bir şablonda, her bir proje için adı belirtir. **Yeni Proje** iletişim kutusu tek tek projelere ad atayamaz.|
|`CopyParameters`|Ana grup şablonundaki tüm değişkenlerin bağlı şablonların her birine kopyalanmasını sağlar.<br /><br /> Bağlı şablonlarda parametrelerin bir önek `"$ext_*$"`var. Örneğin, ana grup şablonunda `$projectname$` parametrenin bir değeri varsa **ExampleProject1**, bağlı şablon yürütülmek üzere `$ext_projectname$`sırasını aldığında, `$projectname$` ana grup şablonundan parametrenin bir kopyası olan bir parametre alır.<br /><br /> Bu durum, bağlı şablonların, yalnızca üst grup şablonunda rahatlıkla oluşturulabilecek bazı ortak parametreleri paylaşmasına olanak sağlar.<br /><br /> Bu öznitelik isteğe bağlıdır ve dahil `false` olmadığında otomatik olarak varsayılandır.<br /><br /> Visual Studio 2013 Güncelleme 2 tanıtıldı. Doğru ürün sürümüne başvurmak için Visual [Studio 2013 SDK Update 2'de teslim edilen Başvuru derlemelerine](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb)bakın.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Birden fazla projeli şablonların içeriğini ve düzenini belirtir.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Birden fazla projeli şablonlardaki projeleri gruplandırır.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu metin, şablonun *.vstemplate* dosyasına giden yolu belirtir.

## <a name="remarks"></a>Açıklamalar
 Birden fazla projeli şablonlar, iki veya daha fazla proje için kapsayıcı olarak davranır. Öğe, `ProjectTemplateLink` şablondaki projelerden biri için *.vstemplate* dosyasının konumunu belirtmek için kullanılır. Çoklu proje şablonunun *.vstemplate* dosyası, `ProjectTemplateLink` şablondaki her proje için bir öğe içerir. Çoklu proje şablonları hakkında daha fazla bilgi için [bkz.](../ide/how-to-create-multi-project-templates.md)

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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
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
