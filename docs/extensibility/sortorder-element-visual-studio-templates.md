---
title: SortOrder öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719919"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder Öğesi (Visual Studio Şablonları)
**Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda göründüğü gibi, şablonu düzenlemek için kullanılan bir değeri belirtir.

 \<VSTemplate > \<TemplateData > \<SortOrder >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Sıralama düzeni değerini temsil eden bir `integer`.

## <a name="remarks"></a>Açıklamalar
 `SortOrder`, isteğe bağlı bir öğedir. Varsayılan değer 100 ' dir ve tüm değerler 10 ' un katları olmalıdır.

 @No__t_0 öğesi, Kullanıcı tarafından oluşturulan şablonlar için yok sayılır. Kullanıcı tarafından oluşturulan tüm şablonlar alfabetik olarak sıralanır.

 Düşük sıralama düzeni değerleri olan şablonlar, yüksek sıralama düzeni değerlerine sahip şablonlardan önce **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda görünür.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir standart [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıf şablonu için meta verileri gösterir.

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

 Bu örnekte `SortOrder` öğesi nispeten yüksektir. Diğer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] öğesi şablonlarının `290` daha düşük bir `SortOrder` değeri olabilir ve **Yeni öğe** iletişim kutusunda Bu şablondan önce görünecektir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)