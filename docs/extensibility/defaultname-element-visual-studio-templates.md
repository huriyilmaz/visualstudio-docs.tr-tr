---
title: defaultname öğesi (Visual Studio şablonları) | Microsoft Docs
description: defaultname öğesi hakkında bilgi edinin ve Visual Studio proje sisteminin oluşturulduğu sırada proje veya öğe için oluşturduğu adı nasıl belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b26eced0849ebd4551c0f91f3ba2b7040022312c0e8007dc0a2cf54decc24788
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377034"
---
# <a name="defaultname-element-visual-studio-templates"></a>defaultname öğesi (Visual Studio şablonları)
Visual Studio proje sisteminin oluşturulduğu sırada proje veya öğe için üretecektir adı belirtir.

 \<VSTemplate> \<TemplateData>
 \<DefaultName>

## <a name="syntax"></a>Syntax

```
<DefaultName>
    Default Project Name
</DefaultName>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> şablonu kategorilere ayırır ve **yeni Project** ya da **yeni öğe ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu metin projenin veya öğenin varsayılan adını belirtir.

## <a name="remarks"></a>Açıklamalar
 `DefaultName` isteğe bağlı bir öğedir.

 Projeler için bu öğe, projeyi diskte depolayan dizinin adını belirtir. Öğeler için kaynak dosyanın dosya adını belirtir.

 bir proje veya öğe oluşturduğunuzda, varsayılan adı, **yeni Project** iletişim kutusundan veya **yeni öğe ekle** iletişim kutusundan erişilebilen **ad** seçeneğini kullanarak değiştirebilirsiniz.

 Proje sisteminin proje veya öğe için varsayılan adı oluşturmasını istemiyorsanız, [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) öğesini olarak ayarlayın `False` .

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir sınıf için standart öğe şablonu meta verilerini gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
