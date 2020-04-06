---
title: CreateNewFolder Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 860f4df3e69a568a3e391da4d7437d9a5fd83f15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739677"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder öğesi (Visual Studio şablonları)
Projenin oluşturulacağı hedef dizinin var olup olmadığını denetleyip denetlemeyeceğini belirler. Dizin varsa, proje için yeni bir dizin oluşturulabilir. Bu ayar genellikle `NewProjectRequiresNewFolder(VsTemplate)` tüm yaygın proje türlerinin`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`yeni bir dizinde yeni bir proje oluşturup oluşturmayacağını belirlemek için kullandığı kayıt defteri bayrağı ( ) tarafından geçersiz kılınan bir ayardır.

 \<VSTemplate \<> ŞablonVeri> \<CreateNewFolder>

## <a name="syntax"></a>Sözdizimi

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>Tür
 `Boolean`

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, `true` `false`şablondan bir proje oluşturulduğunda yeni bir kapsayıcı klasörü oluşturulup oluşturulmaması gerektiğini belirten metin olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `CreateNewFolder`isteğe bağlı bir unsurdur. Varsayılan değer: `true`.

 `CreateNewFolder` Öğede belirtilen değer, yalnızca temel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proje sistemi destekliyorsa onurlanır.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, şablondan bir proje oluşturulduğunda yeni bir klasör oluşturmamayı belirtir.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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
