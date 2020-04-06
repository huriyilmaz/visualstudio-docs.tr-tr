---
title: GerekliFrameworkVersion Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701508"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>GerekliFrameworkVersion öğesi (Visual Studio şablonları)

Şablon tarafından gerekli olan .NET Framework'ün minimum sürümünü belirtir. **Hedef Çerçeve Sürümü** açılır listesinin Yeni **Proje** iletişim kutusunda görüntülenmesine neden olur. Öğe, `RequiredFrameworkVersion` açılır bırakmada bulunan en düşük değeri de belirler.

> [!IMPORTANT]
> Visual Studio 2017 sürüm 15.6'dan başlayarak, **Hedef Çerçeve Sürümü** açılır listesi artık Yeni **Proje** iletişim kutusunun **Şablonlar** bölümünde görüntülenen şablonlar için bir filtre değildir. Bunun yerine, açılır bırakma, seçili şablon için bir çerçeve seçici olarak işlev görür.

 \<VSTemplate \<> ŞablonVeri> \<GerekliFrameworkVersion>

## <a name="syntax"></a>Sözdizimi

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve **Yeni Proje** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleneceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, şablon için gerekli olan .NET Framework'ün minimum sürüm numarası olmalıdır.

## <a name="remarks"></a>Açıklamalar

`RequiredFrameworkVersion`isteğe bağlı bir unsurdur. Bu öğeyi yalnızca şablon .NET Framework'ün belirli bir minimum sürümünü (ve varsa sonraki sürümleri) destekliyorsa kullanın. Öğeyi `RequiredFrameworkVersion` belirtirseniz ve şablonunuzun .NET Framework'ün belirli bir minimum sürümünü desteklemezseniz, **hedef Çerçeve Sürümü** açılır açılır resmi geçerli olmadığında görüntülenir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, standart [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıf şablonu için meta veriler gösterilmektedir.

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

Bu örnekte, .NET Framework'ün şablon tarafından gerekli olan ve `RequiredFrameworkVersion`temsil ettiği minimum sürümü 3.0'dır. Bu şablonla oluşturulan bir proje 3.0'dan itibaren .NET Framework sürümlerini hedefleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Çerçeve hedeflemegenel bakış](../ide/visual-studio-multi-targeting-overview.md)
