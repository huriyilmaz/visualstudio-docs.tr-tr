---
title: MaxFrameworkVersion öğesi (Visual Studio şablonları) | Microsoft Docs
description: MaxFrameworkVersion öğesi hakkında bilgi edinin ve şablon için gereken .NET Framework en yüksek sürümünü nasıl belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 09ddccece8261a331277d1c143054305f0d08d7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943211"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion öğesi (Visual Studio şablonları)

Şablonun gerektirdiği .NET Framework en yüksek sürümünü belirtir. **Yeni proje** Iletişim kutusunun **hedef Framework sürümü** açılan menüsünde kullanılabilir en yüksek değeri belirler. Kullanıcıların bir çerçeve sürümü seçebilmeleri için, şablonun en düşük .NET Framework sürümü olarak [Requiredframeworkversion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) ' ı da belirtmeniz gerekir.

> [!IMPORTANT]
> Visual Studio 2017 sürüm 15,6 ' den başlayarak, **hedef Framework sürümü** açılan kutusu artık **Yeni proje** iletişim kutusunun **Şablonlar** bölümünde, görünen şablonlar için bir filtre değildir. Bunun yerine, **hedef Framework sürümü** açılan kutusu seçili şablon için bir çerçeve seçici olarak çalışır.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** ya da **Yeni öğe Ekle** iletişim kutusunda nasıl görüntüleneceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, şablon tarafından izin verilen .NET Framework en yüksek sürüm numarası olmalıdır.

## <a name="remarks"></a>Açıklamalar

`MaxFrameworkVersion` isteğe bağlı bir öğedir. `MaxFrameworkVersion`Şablon için desteklenen .NET Framework sürümlerinin yanlışlıkla sınırlandırımaması gibi, gerekli olmadığı sürece, öğe atlanmalıdır. .NET Framework şablon için geçerli değilse de atlanmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, standart sınıf şablonu için meta verileri gösterir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

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

Bu örnekte, şablonu için gereken .NET Framework en yüksek sürümü tarafından temsil edilir, `MaxFrameworkVersion` 4.7.1. Bu şablonla oluşturulan bir proje, 4.7.1 sürümüne kadar .NET Framework sürümlerini hedefleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
