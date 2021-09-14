---
title: MaxFrameworkVersion Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: MaxFrameworkVersion öğesini ve şablonun gerekli olduğu en yüksek .NET Framework nasıl belirtir hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05d61e298c666d22df1af8d426cb0671feb8b9c5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724955"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion öğesi (Visual Studio şablonları)

Şablon için gereken en .NET Framework sürümünü belirtir. Yeni Çerçeve Sürümü iletişim kutusunun **Hedef Çerçeve Sürümü** açılan listesinde kullanılabilen en yüksek **Project** belirler. Kullanıcıların bir çerçeve sürümü seçeb için, şablonun en düşük sürüm olarak [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) .NET Framework belirtmeniz gerekir.

> [!IMPORTANT]
> Visual Studio 2017 sürüm 15.6'dan başlayarak, **Hedef Çerçeve** Sürümü açılan listesinde artık Yeni  Çerçeve Sürümü iletişim kutusunun Şablonlar bölümünde görüntülenen şablonlar için bir **filtre Project** yoktur. Bunun yerine, **Hedef Çerçeve Sürümü** açılan listesinde seçilen şablon için çerçeve seçici işlevi kullanılır.

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırarak Yeni Öğe Ekle iletişim kutusunda **Project** **görüntülenen şablonu** tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, şablon tarafından izin verilen .NET Framework en yüksek sürüm numarasına sahip olması gerekir.

## <a name="remarks"></a>Açıklamalar

`MaxFrameworkVersion` isteğe bağlı bir öğedir. Öğe gerekli olmadığı sürece atlanır, bu nedenle şablon için desteklenen .NET Framework aralıklarını yanlışlıkla `MaxFrameworkVersion` sınırlamamalıdır. Şablon için geçerli .NET Framework de atlanır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, standart bir sınıf şablonunun meta [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] verilerini göstermektedir.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

Bu örnekte, tarafından temsil edilen .NET Framework için gereken en yüksek sürüm `MaxFrameworkVersion` 4.7.1'tir. Bu şablonla oluşturulan bir proje, 4.7.1.NET Framework e kadar olan tüm sürümleri hedefleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
