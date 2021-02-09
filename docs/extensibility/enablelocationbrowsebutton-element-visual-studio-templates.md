---
title: EnableLocationBrowseButton Öğesi (Visual Studio Şablonları)
description: EnableLocationBrowseButton öğesi hakkında bilgi edinin ve yeni proje iletişim kutusunda, gezinme düğmesinin kullanılabilir olup olmadığını nasıl belirtir.
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d909e70f38800bdbeb873ad3fd9bff1d55132825
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883434"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton öğesi (Visual Studio şablonları)
Kullanıcıların yeni bir projenin kaydedildiği varsayılan dizini kolayca değiştirebilmeleri için **Yeni proje** iletişim kutusunda, **tarayıcı** düğmesinin kullanılabilir olup olmadığını belirtir.

 \<VSTemplate> \<TemplateData>
 \<EnableLocationBrowseButton>

## <a name="syntax"></a>Syntax

```xml
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
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

 Metin `true` veya `false` **Yeni proje** iletişim kutusunda **tarama** düğmesinin görüntülenip görüntülenmeyeceğini belirten bir ya da olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `EnableLocationBrowseButton` isteğe bağlı bir öğedir. Varsayılan değer `true` , **Yeni proje** iletişim kutusundaki **tarayıcı** düğmesini görüntüleyen ' dir.

 **Yeni proje** Iletişim kutusunda **konum** metin kutusu yeni projenin kaydedildiği dizini belirtir. Git **düğmesi,** bilgisayarınızda bulunan farklı bir dizine kolayca gidebilmenizi sağlayan **Proje konumu** iletişim kutusunu görüntüleyerek bu dizini değiştirmenize yardımcı olur ve sonra bunu yeni projenin kaydedildiği dizin olarak seçebilirsiniz.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir Windows uygulaması için meta verileri gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
