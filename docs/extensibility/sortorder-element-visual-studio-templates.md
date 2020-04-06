---
title: Sıralama Elemanı (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699962"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder Öğesi (Visual Studio Şablonları)
**Yeni Proje** veya **Yeni Öğe Ekle** iletişim kutusunda göründüğü gibi, şablonu düzenlemek için kullanılan değeri, aynı kategorideki diğer şablonlar arasında belirtir.

 \<VSTemplate \<> ŞablonVeri> \<SortOrder>

## <a name="syntax"></a>Sözdizimi

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt Öğeler
 Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Sıra `integer` değerini temsil eden bir değer.

## <a name="remarks"></a>Açıklamalar
 `SortOrder`isteğe bağlı bir unsurdur. Varsayılan değer 100'dür ve tüm değerler 10'un katları olmalıdır.

 Öğe, `SortOrder` kullanıcı tarafından oluşturulan şablonlar için yoksayılır. Kullanıcı tarafından oluşturulan tüm şablonlar alfabetik olarak sıralanır.

 Düşük sıralama sırası değerlerine sahip şablonlar, yüksek sıralama sırası değerlerine sahip şablonlardan önce **Yeni Proje** veya **Yeni Öğe Ekle** iletişim kutusunda görünür.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, standart [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıf şablonu için meta veriler gösterilmektedir.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 Bu örnekte, `SortOrder` öğe nispeten yüksektir. Diğer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] öğe şablonlarının, **Yeni Öğe** iletişim `290` kutusundaki bu şablondan daha düşük bir `SortOrder` değere sahip olması ve bu şablondan önce görünmesi olasıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
