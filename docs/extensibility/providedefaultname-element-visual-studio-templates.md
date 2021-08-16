---
title: providedefaultname öğesi (Visual Studio şablonları) | Microsoft Docs
description: providedefaultname öğesi hakkında bilgi edinin ve Visual Studio yeni öğe veya yeni Project ekle iletişim kutusunda varsayılan bir Visual Studio adı oluşturup üretmeyeceğinizi nasıl belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0415e44f891b78908c27ef14627582ca7c217bdcf6382ffc6185db310c556b49
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400926"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>providedefaultname öğesi (Visual Studio şablonları)
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]proje sisteminin **yeni öğe ekle** veya **yeni Project** iletişim kutusunda şablon için varsayılan bir ad oluşturup üretmeyeceğini belirtir.

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>Syntax

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt Öğeler
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> şablonu kategorilere ayırır ve **yeni Project** ya da **yeni öğe ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 metin ya da ya da `true` `false` **yeni öğe ekle** veya **yeni Project** iletişim kutusunda şablon için varsayılan bir ad oluşturulup oluşturulmayacağını belirten bir değer olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `ProvideDefaultName` isteğe bağlı bir öğedir. `true` varsayılan değerdir.

 `ProvideDefaultName`öğesi ise `false` , **yeni öğe ekle** ve **yeni Project** iletişim kutularının **ad** kutuları değeri içerir `<Enter_name>` .

 **yeni öğe ekle** ve **yeni Project** iletişim kutularında varsayılan proje veya öğe adını belirtmek için [defaultname](../extensibility/defaultname-element-visual-studio-templates.md) öğesini kullanın. Öğesinin değeri olduğunda `ProvideDefaultName` `true` , `DefaultName` projeler için öğesinin atlanması, iletişim kutusunu şablon adı, diğer bir deyişle, [ad](../extensibility/name-element-visual-studio-templates.md) öğesinden doldurur.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği `ProvideDefaultName` öğesini olarak ayarlar `false` .

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
