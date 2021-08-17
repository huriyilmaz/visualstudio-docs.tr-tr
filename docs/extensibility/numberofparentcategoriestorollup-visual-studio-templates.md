---
title: NumberOfParentCategoriesToRollUp öğesi (şablonlar)
description: numberofparentcategoriestorollup öğesi hakkında bilgi edinin ve yeni Project iletişim kutusunda şablonu görüntüleyecek üst kategori sayısını belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 899e5e991c998f26c46749875f3c10a7555136f89b95dc8d9c0351a734c0d722
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431675"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>numberofparentcategoriestorollup öğesi (Visual Studio şablonları)
**yeni Project** iletişim kutusunda şablonu görüntüleyecek üst kategori sayısını belirtir.

 \<VSTemplate> \<TemplateData>
 \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Syntax

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|şablonu kategorilere ayırır ve **yeni Project** ya da **yeni öğe ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 `integer`Değer gereklidir.

 bu değer, **yeni Project** iletişim kutusunda şablonu görüntüleyecek üst kategori sayısını belirtir.

## <a name="remarks"></a>Açıklamalar
 `NumberOfParentCategoriesToRollUp` isteğe bağlı bir öğedir.

## <a name="example"></a>Örnek
 bu örnek, bir Windows uygulamasının meta verilerini gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] . bu meta verilere sahip bir şablon en üst düzey düğümün altına iki klasör düzeyi yerleştirirse [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] , şablon **yeni Project** iletişim kutusundaki en üst düzey düğümünde görünür. `NumberOfParentCategoriesToRollUp`Ayarlanmamışsa, şablon yalnızca fiziksel olarak bulunduğu düğümde görüntülenir.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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
- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
