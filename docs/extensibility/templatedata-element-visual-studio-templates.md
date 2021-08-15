---
title: templatedata öğesi (Visual Studio şablonları) | Microsoft Docs
description: templatedata öğesi hakkında bilgi edinin ve şablonu kategorilere ayırır ve yeni Project ya da yeni öğe ekle iletişim kutusunda nasıl görüntülediğini tanımlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fbbc43ec169f48e13e55d397b6290482a93a6b2167712df8970deef747cc70cd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238508"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData Öğesi (Visual Studio Şablonları)
şablonu kategorilere ayırır ve **yeni Project** ya da **yeni öğe ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.

 \<VSTemplate> \<TemplateData>

## <a name="syntax"></a>Syntax

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt Öğeler

| Öğe | Açıklama |
| - | - |
| [Ad](../extensibility/name-element-visual-studio-templates.md) | Gerekli öğe.<br /><br /> **yeni Project** veya **yeni öğe ekle** iletişim kutusunda göründüğü gibi şablonun adını belirtir. |
| [Açıklama](../extensibility/description-element-visual-studio-templates.md) | Gerekli öğe.<br /><br /> **yeni Project** veya **yeni öğe ekle** iletişim kutusunda göründüğü gibi şablonun açıklamasını belirtir. |
| [Simge](../extensibility/icon-element-visual-studio-templates.md) | Gerekli öğe.<br /><br /> şablon için **yeni Project** veya **yeni öğe ekle** iletişim kutusunda görünen simge olarak hizmet gören görüntü dosyasının yolunu ve dosya adını belirtir. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Gerekli öğe.<br /><br /> proje şablonunu, **yeni Project** iletişim kutusunda belirtilen grubun altında görünecek şekilde kategorilere ayırır. |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> proje şablonunu, **yeni Project** iletişim kutusunda belirtilen alt kategori altında görünecek şekilde sınıflandırır. |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablon KIMLIĞINI belirtir. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablon grubu KIMLIĞINI belirtir. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> **yeni Project** veya **yeni öğe ekle** iletişim kutusunda göründüğü gibi, şablonu düzenlemek için kullanılan bir değeri belirtir. |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Projenin örneklenmesi sırasında içeren bir klasörün oluşturulup oluşturulmayacağını belirtir. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Visual Studio proje sisteminin oluşturulduğu sırada proje veya öğe için üretecektir adı belirtir. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Visual Studio proje sisteminin oluşturulduğu sırada proje veya öğe için varsayılan adı oluşturup üretmeyeceğini belirtir. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> projenin geçici bir proje olarak oluşturulup oluşturuamayacağını belirtir (yalnızca Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> kullanıcıların yeni bir projenin kaydedildiği varsayılan dizini kolayca değiştirebilmeleri için **yeni Project** iletişim kutusunda, **tarayıcı** düğmesinin kullanılabilir olup olmadığını belirtir. |
| [Gizli](../extensibility/hidden-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> şablonun **yeni Project** veya **yeni öğe ekle** iletişim kutusunda görünüp başlatılmayacağını belirtir. |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> **yeni Project** iletişim kutusunda şablonu görüntüleyecek üst kategori sayısını belirtir. |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | İsteğe bağlı öğe. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | İsteğe bağlı öğe.<br /><br /> **yeni Project** iletişim kutusunda **konum** metin kutusunun etkin, devre dışı ya da proje şablonu için gizli olup olmadığını belirtir. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablon yalnızca belirli bir minimum sürümü ve varsa .NET Framework daha sonraki sürümlerini destekliyorsa bu öğeyi kullanın. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablonun Web projeleri için ana sayfayı destekleyip desteklemediğini belirtir. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablonun kod ayrımını veya Web projeleri için arka plan kod modeli ' ni destekleyip desteklemediğini belirtir. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> şablonun birden çok dil için özdeş olup olmadığını ve **dil** seçeneğinin **yeni Project** iletişim kutusunda kullanılıp kullanılamayacağını belirtir. |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Proje şablonunun hedeflediği platformu belirtir. Bu öğe, uygulama oluşturmak için bir proje şablonu kullanıldığını belirtir [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] . |

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Proje şablonu, öğe şablonu veya başlangıç seti için tüm meta verileri içerir.|

## <a name="remarks"></a>Açıklamalar
 `TemplateData` gerekli bir öğedir.

 İsteğe bağlı bir öğe eklemezseniz, bu öğe için varsayılan değer kullanılır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulama için bir proje şablonu meta verilerini gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
