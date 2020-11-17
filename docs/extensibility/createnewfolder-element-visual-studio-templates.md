---
title: CreateNewFolder öğesi (Visual Studio şablonları) | Microsoft Docs
description: CreateNewFolder öğesi hakkında bilgi edinin ve projenin oluşturulacağı hedef dizinin mevcut olmadığını denetleyip denetmeyeceğini nasıl belirlediğini öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 15633c2f701c813ca24c5484fd4108a86c57b05b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671585"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder öğesi (Visual Studio şablonları)
Projenin oluşturulacağı hedef dizinin mevcut olmadığını denetleyip denetmeyeceğini belirler. Dizin varsa, proje için yeni bir dizin oluşturulabilir. Bu ayar genellikle, `NewProjectRequiresNewFolder(VsTemplate)` `HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>` tüm ortak proje türlerinin yeni bir dizinde yeni bir proje oluşturulup oluşturulmayacağını belirlemede kullanılan kayıt defteri bayrağı () tarafından geçersiz kılınır.

 \<VSTemplate> \<TemplateData>
 \<CreateNewFolder>

## <a name="syntax"></a>Syntax

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin `true` veya `false` şablondan bir proje oluşturulduğunda yeni bir kapsayıcı klasörünün oluşturulup oluşturulmayacağını belirten bir değer olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `CreateNewFolder` isteğe bağlı bir öğedir. `true` varsayılan değerdir.

 Öğesinde belirtilen değer `CreateNewFolder` yalnızca [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] temel alınan proje sistemi tarafından destekliyorsa kabul edilir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, şablondan bir proje oluşturulduğunda yeni bir klasör oluşturmamalıdır.

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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
