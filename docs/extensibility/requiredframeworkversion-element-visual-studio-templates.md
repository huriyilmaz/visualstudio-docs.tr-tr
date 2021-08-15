---
description: şablonun gerektirdiği .NET Framework en düşük sürümünü belirtir.
title: RequiredFrameworkVersion Öğesi (Visual Studio Şablonları)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5164202c10008112b6072b1a45aed7d52c3ddf0598c97f6b69b32ba1cb9aadf4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305197"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>requiredframeworkversion öğesi (Visual Studio şablonları)

şablonun gerektirdiği .NET Framework en düşük sürümünü belirtir. **hedef Framework sürümü** açılan listesinin **yeni Project** iletişim kutusunda görüntülenmesine neden olur. `RequiredFrameworkVersion`Öğe ayrıca açılan listede bulunan en düşük değeri de belirler.

> [!IMPORTANT]
> Visual Studio 2017 sürüm 15,6 ' den başlayarak, **hedef Framework sürümü** açılan menüsü artık **yeni Project** iletişim kutusunun **şablonlar** bölümünde, görünen şablonlar için bir filtre değildir. Bunun yerine, açılan menü seçili şablon için bir çerçeve seçici olarak çalışır.

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> şablonu kategorilere ayırır ve **yeni Project** ya da **yeni öğe ekle** iletişim kutusunda nasıl görüntüleneceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 metin, şablon için gerekli .NET Framework en düşük sürüm numarası olmalıdır.

## <a name="remarks"></a>Açıklamalar

`RequiredFrameworkVersion` isteğe bağlı bir öğedir. Bu öğeyi yalnızca şablon, .NET Framework için belirli bir minimum sürümü (ve varsa sonraki sürümleri) destekliyorsa kullanın. `RequiredFrameworkVersion`öğesini belirtirseniz ve şablonunuz .NET Framework en düşük sürümü desteklemiyorsa, **hedef Framework sürümü** açılan kutusu uygulanabilir olmadığında görüntülenir.

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

bu örnekte, şablon için gereken .NET Framework en düşük sürümü, tarafından temsil edilir `RequiredFrameworkVersion` 3,0. bu şablonla oluşturulan bir proje, 3,0 'den başlayarak .NET Framework sürümleri hedefleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md)
