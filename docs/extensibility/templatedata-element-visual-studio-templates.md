---
title: TemplateData Element (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699189"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData Öğesi (Visual Studio Şablonları)
Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.

 \<VSTemplate \<> ŞablonVeri>

## <a name="syntax"></a>Sözdizimi

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
| [Adı](../extensibility/name-element-visual-studio-templates.md) | Gerekli öğe.<br /><br /> **Yeni Proje** veya **Yeni Öğe Ekle** iletişim kutusunda göründüğü gibi şablonun adını belirtir. |
| [Açıklama](../extensibility/description-element-visual-studio-templates.md) | Gerekli öğe.<br /><br /> **Yeni Proje** veya **Yeni Öğe Ekle** iletişim kutusunda görünen şablonun açıklamasını belirtir. |
| [Simge](../extensibility/icon-element-visual-studio-templates.md) | Gerekli öğe.<br /><br /> Şablon için **Yeni Proje** veya **Yeni Öğe Ekle** iletişim kutusunda görünen simge olarak hizmet veren resim dosyasının yolunu ve dosya adını belirtir. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Gerekli öğe.<br /><br /> Proje şablonu, **Yeni Proje** iletişim kutusunda belirtilen grubun altında görünecek şekilde kategorilere ayırıyor. |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Proje şablonu, **Yeni Proje** iletişim kutusunda belirtilen alt kategorialtında görünecek şekilde sınıflandırın. |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablon kimliğini belirtir. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablon grubu kimliğini belirtir. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> **Yeni Proje** veya **Yeni Öğe Ekle** iletişim kutusunda göründüğü gibi, şablonu düzenlemek için kullanılan değeri, aynı kategorideki diğer şablonlar arasında belirtir. |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Projenin anında oluşturulup oluşturulmadığını belirtir. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Visual Studio proje sisteminin proje veya öğe için oluşturulduğunda oluşturacağı adı belirtir. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Visual Studio proje sisteminin oluşturulduğunda bir proje veya öğe için varsayılan adı oluşturup oluşturmayacağını belirtir. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Projenin geçici bir proje olarak oluşturulup oluşturulamayacağını belirtir (yalnızca Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> **Gözat** düğmesinin **Yeni Proje** iletişim kutusunda kullanılabilir olup olmadığını belirtir, böylece kullanıcılar yeni bir proje kaydedilirken varsayılan dizini kolayca değiştirebilir. |
| [Gizli](../extensibility/hidden-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablonun Yeni Proje'de veya **Yeni** **Öğe Ekle** iletişim kutusunda görünüp görünmediğini belirtir. |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> **Şablonu Yeni Proje** iletişim kutusunda görüntüleyecek üst kategorilerin sayısını belirtir. |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | İsteğe bağlı öğe. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | İsteğe bağlı öğe.<br /><br /> **Yeni Proje** iletişim kutusundaki **Konum** metin kutusunun etkin, devre dışı veya proje şablonu için gizli olup olmadığını belirtir. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablon yalnızca belirli bir minimum sürümü destekliyorsa bu öğeyi ve varsa .NET Framework'ün sonraki sürümlerini kullanın. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablonun web projeleri için bir ana sayfayı destekleyip desteklemediğini belirtir. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablonun web projeleri için kod ayrımını mı yoksa sayfa arkasındaki kod arkasındaki modeli mi desteklediğini belirtir. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Şablonun birden çok dil için aynı olup olmadığını ve **Dil** seçeneğinin **Yeni Proje** iletişim kutusundan kullanılabilir olup olmadığını belirtir. |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | İsteğe bağlı öğe.<br /><br /> Proje şablonunun hedeflenebilen platformu belirtir. Bu öğe, uygulama oluşturmak [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] için bir proje şablonu kullanıldığını belirtir. |

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Proje şablonu, öğe şablonu veya başlangıç kiti için tüm meta verileri içerir.|

## <a name="remarks"></a>Açıklamalar
 `TemplateData`gerekli bir unsurdur.

 İsteğe bağlı bir öğe eklemezseniz, bu öğeiçin varsayılan değer kullanılır.

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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
