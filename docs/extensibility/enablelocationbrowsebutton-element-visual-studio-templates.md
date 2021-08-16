---
title: EnableLocationBrowseButton Öğesi (Visual Studio Şablonları)
description: EnableLocationBrowseButton öğesini ve Yeni Giriş iletişim kutusunda Gözat düğmesinin kullanılabilir olup olmadığını nasıl Project öğrenin.
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b6f25154015790919577d7fc32daffe21c0e69d90c10675c98dd2ad5d1314eed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388727"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>EnableLocationBrowseButton öğesi (Visual Studio şablonları)
Kullanıcıların yeni projenin **kayded** olduğu varsayılan dizini **kolayca değiştire** Project için Gözat düğmesinin Yeni Dizin iletişim kutusunda kullanılabilir olup olmadığını belirtir.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırarak Yeni Öğe Ekle iletişim kutusunda **Project** **şekilde** tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, Yeni Giriş `true` iletişim `false` kutusunda Gözat düğmesinin  görüntüleniyor olup olmadığını belirten **veya Project** gerekir.

## <a name="remarks"></a>Açıklamalar
 `EnableLocationBrowseButton` isteğe bağlı bir öğedir. Varsayılan değer, `true` Yeni Giriş iletişim **kutusunda** Gözat düğmesini **Project** değeridir.

 Yeni **Project** iletişim kutusunda, **Konum** metin kutusu yeni projenin kayded olduğu dizini belirtir. Gözat **düğmesi,** **Project Konumu** iletişim kutusunu görüntüleyerek bu dizini değiştirmenize yardımcı olur. Bu iletişim kutusu bilgisayarınızdan kullanılabilen farklı bir dizine kolayca gidin ve yeni projenin kayded olduğu dizin olarak seçin.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir uygulamanın meta [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] verilerini Windows göstermektedir.

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
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
