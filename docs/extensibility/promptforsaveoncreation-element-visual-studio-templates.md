---
title: PromptForSaveOnCreation Öğesi (Visual Studio Şablonları)
titleSuffix: ''
description: Promptforsaveonoluşturma öğesi hakkında bilgi edinin ve yeni proje iletişim kutusu aracılığıyla kullanıcının bir proje kaydetme konumu isteyip istemediğiniz sorulur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5bc3c28bcfa35dac23c96d9a566b9767f8db9c1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068654"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>Promptforsaveonoluşturma öğesi (Visual Studio şablonları)

Proje oluştururken, kullanıcıdan **Yeni proje** iletişim kutusu aracılığıyla bir proje kaydetme konumu istenip istenmediğini belirtir. Bu öğe olarak ayarlandıysa `true` , kullanıcıdan bir kayıt konumu istenir. Varsa `false` , bunlar istenmez (Yani geçici bir proje oluşturulur).

```xml
\<VSTemplate>
\<TemplateData>
\<PromptForSaveOnCreation>
```

## <a name="syntax"></a>Syntax

```xml
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>
```

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

 Metin ya da ya da `true` `false` `true` Yeni bir proje oluştururken kullanıcıdan kaydetme konumu istenmeyeceğini belirten bir olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `PromptForSaveOnCreation` isteğe bağlı bir öğedir. `false` varsayılan değerdir.

 Geçici projeler, bu projenin içeriğini diskte kaydetmeden oluşturabileceğiniz ve değiştirebileceğiniz projelerdir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek `PromptForSaveOnCreation` `false` , projenin geçici bir proje olarak oluşturulmasını izin vermeyi belirten değerine eşit değer olarak ayarlar.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>
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
