---
title: CreateNewFolder Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: CreateNewFolder öğesini ve projenin oluşturulacak olduğu hedef dizinin mevcut olup olmadığını denetlemeyi nasıl belirleyip belirlemeyeceklerini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dd332fe32044cb66f24418be016cdf75c9683d0ace936417cfecd8cf246a7e8c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403521"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder öğesi (Visual Studio şablonları)
Projenin oluşturulacak hedef dizinin mevcut olup olmadığını denetlemeyi belirler. Dizin varsa proje için yeni bir dizin oluşturulabilir. Bu ayar genellikle tüm ortak proje türlerinin yeni bir dizinde yeni proje oluşturulıp oluşturul olmadığını belirlemek için kullanılan kayıt defteri bayrağı `NewProjectRequiresNewFolder(VsTemplate)` ( ) tarafından geçersiz `HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>` kılınır.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırarak Yeni Öğe Ekle iletişim kutusunda **Project** **şekilde** tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, şablondan proje oluşturulduğunda yeni bir kapsayıcı klasörünün oluşturulıp oluşturulmay gerektiğini belirten `true` `false` veya olması gerekir.

## <a name="remarks"></a>Açıklamalar
 `CreateNewFolder` isteğe bağlı bir öğedir. `true` varsayılan değerdir.

 öğesinde belirtilen `CreateNewFolder` değer, yalnızca temel proje sistemi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tarafından destekiliyorsa tarafından kabul edildi.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, şablondan proje oluşturulduğunda yeni bir klasör oluşturmamanızı belirtir.

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
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
