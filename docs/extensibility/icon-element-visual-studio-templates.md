---
title: Icon öğesi (Visual Studio şablonları) | Microsoft Docs
description: Simge öğesi hakkında bilgi edinin ve simge olarak hizmet gören görüntü dosyasının dosya adını ve yolunu belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fced03b190ab46885c5d786b8374a05c3bd043b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883304"
---
# <a name="icon-element-visual-studio-templates"></a>Icon öğesi (Visual Studio şablonları)
Şablon için **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda görünen simge olarak hizmet gören görüntü dosyasının yolunu ve dosya adını belirtir.

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
|`Package`|Gelişmiş Kullanıcı senaryoları için isteğe bağlı öznitelik.<br /><br /> Visual Studio paket KIMLIĞINI belirten bir GUID.|
|`ID`|Gelişmiş Kullanıcı senaryoları için isteğe bağlı öznitelik.<br /><br /> Visual Studio kaynak KIMLIĞINI belirtir.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 `Package`Ve `ID` öznitelikleri kullanılmamışsa metin değeri gereklidir.

 Metin, **Yeni proje** iletişim kutusunda görünecek şablon simgesinin yolunu ve dosya adını sağlar.

## <a name="remarks"></a>Açıklamalar
 `Icon` , öğesinin gerekli bir alt öğesidir `TemplateData` .

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
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
