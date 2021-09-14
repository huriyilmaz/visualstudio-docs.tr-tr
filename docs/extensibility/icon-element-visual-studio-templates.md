---
title: Icon Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: Icon öğesini ve simge olarak görev alan görüntü dosyasının yolunu ve dosya adını nasıl ifade ettiği hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3241457fc23a0df369c1ebc78546a5045e89975
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626229"
---
# <a name="icon-element-visual-studio-templates"></a>Icon öğesi (Visual Studio şablonları)
Şablon için Yeni Dosya veya Yeni Öğe Ekle iletişim kutusunda görünen simge olarak görev alan  görüntü **dosyasının yolunu ve Project dosya** adını belirtir.

 \<VSTemplate> \<TemplateData>
 \<Icon>

## <a name="syntax"></a>Syntax

```
<Icon>
    IconFileName
</Icon>
```

```
<Icon Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Package`|Gelişmiş kullanıcı senaryoları için isteğe bağlı öznitelik.<br /><br /> Paket kimliğini belirten Visual Studio GUID.|
|`ID`|Gelişmiş kullanıcı senaryoları için isteğe bağlı öznitelik.<br /><br /> Kaynak kimliğini Visual Studio belirtir.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırarak Yeni Öğe Ekle iletişim kutusunda **Project** **nasıl görüntü olduğunu** tanımlar.|

## <a name="text-value"></a>Metin değeri
 ve öznitelikleri kullanılmadıkça metin `Package` `ID` değeri gereklidir.

 Metin, Yeni Uygulama iletişim kutusunda görünecek şablon simgesinin yolunu **ve Project** sağlar.

## <a name="remarks"></a>Açıklamalar
 `Icon` , öğesinin gerekli bir alt `TemplateData` öğesidir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulama için proje şablonu meta verilerini [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] gösterir.

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
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
