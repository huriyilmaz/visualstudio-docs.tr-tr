---
title: MaxFrameworkVersion Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702630"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion öğesi (Visual Studio şablonları)

Şablon tarafından gerekli olan .NET Framework'ün en büyük sürümünü belirtir. **Yeni Proje** iletişim kutusunun **Hedef Çerçeve Sürümü** açılır düşüşünde bulunan en yüksek değeri belirler. Kullanıcıların bir çerçeve sürümünü seçebilmeleri için, Şablon için en az .NET Framework sürümü olarak [GerekliFrameworkVersion'u](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) belirtmeniz gerekir.

> [!IMPORTANT]
> Visual Studio 2017 sürüm 15.6'dan başlayarak, **Hedef Çerçeve Sürümü** açılır listesi artık Yeni **Proje** iletişim kutusunun **Şablonlar** bölümünde görüntülenen şablonlar için bir filtre değildir. Bunun yerine, **Hedef Framework Version** açılır bırakma, seçili şablon için bir çerçeve seçici olarak işlev görür.

 \<VSTemplate \<> ŞablonVeri> \<MaxFrameworkVersion>

## <a name="syntax"></a>Sözdizimi

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve **Yeni Proje** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleneceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Metin, şablon tarafından izin verilen .NET Framework'ün en yüksek sürüm numarası olmalıdır.

## <a name="remarks"></a>Açıklamalar

`MaxFrameworkVersion`isteğe bağlı bir unsurdur. Şablon `MaxFrameworkVersion` için desteklenen .NET Framework sürümlerinin yanlışlıkla sınırlandırılmaması için, öğe gerekli olmadıkça atlanmalıdır. .NET Framework şabloniçin geçerli değilse de atlanmalıdır.

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

Bu örnekte, .NET Framework'ün şablon tarafından gerekli olan ve `MaxFrameworkVersion`temsil ettiği maksimum sürümü 4.7.1'dir. Bu şablonla oluşturulan bir proje .NET Framework sürümlerini 4.7.1'e kadar hedefleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
