---
title: LocationField Öğesi (Visual Studio Proje Şablonları)
titleSuffix: ''
description: LocationField öğesini ve Yeni Dosya iletişim kutusunun Konum metin kutusunun proje şablonu için Project, devre dışı bırakılmıştır veya gizlenir olduğunu nasıl belirtir hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0610ab1e24b4f6de2052b45d52882ff7c9e88c2a402d1b7c96e5e0f4a5e4afe
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121290927"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField öğesi (Visual Studio proje şablonları)
Yeni Oturum Açma iletişim kutusundaki **Konum** metin kutusunun **proje şablonu için Project,** devre dışı veya gizli olup olmadığını belirtir.

 \<VSTemplate> \<TemplateData>
 \<LocationField>

## <a name="syntax"></a>Syntax

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırarak New Project **.**|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Geçerli metin değerleri:

- `Enabled`, Yeni Uygulama iletişim **kutusunun** Konum **kutusunun Project** belirtir.

- `Disabled`, Yeni Uygulama iletişim **kutusunun** Konum kutusunun **Project** olduğunu belirtir.

- `Hidden`, Yeni Uygulama iletişim **kutusunun** Konum **kutusunun Project** olduğunu belirtir.

## <a name="remarks"></a>Açıklamalar
 `Enabled` varsayılan değerdir.

 Yeni **Dizin** iletişim kutusundaki **Konum Project** kutusu, kullanıcıların yeni projelerin kayded olduğu varsayılan dizini değiştirmesini sağlar.

 Öğesinde belirtilen değer yalnızca temel proje sistemi tarafından `Location` destek alıyorsa iletişim kutusu tarafından kabul edildi.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir şablonun meta verilerini [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] göstermektedir.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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
