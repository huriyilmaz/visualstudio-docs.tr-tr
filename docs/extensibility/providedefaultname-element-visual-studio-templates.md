---
title: ProvideDefaultName Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 192716198f605a5f6b4f62730e84dcf83b4229cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701711"
---
# <a name="providedefaultname-element-visual-studio-templates"></a>DefaultName öğesi sağlama (Visual Studio şablonları)
Proje sisteminin **Yeni Öğe Ekle** veya Yeni Proje iletişim kutusunda şablon için varsayılan bir ad oluşturup oluşturmayacağını belirtir. **New Project** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

 \<VSTemplate \<> ŞablonVeri> \<VarsayılanAd>

## <a name="syntax"></a>Sözdizimi

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Yeni Öğe Veya `true` `false` **Yeni Proje** **Ekle** iletişim kutusunda şablon için varsayılan bir ad oluşturup oluşturmayacağını belirten metin veya metin olmalıdır.

## <a name="remarks"></a>Açıklamalar
 `ProvideDefaultName`isteğe bağlı bir unsurdur. Varsayılan değer: `true`.

 `ProvideDefaultName` Öğe `false`ise, **Yeni Öğe Ekle** ve **Yeni Proje** iletişim kutularının `<Enter_name>` **Ad** kutuları değeri içerir.

 **Yeni Öğe Ekle** ve **Yeni Proje** iletişim kutularında projenin veya öğenin varsayılan adını belirtmek için Varsayılan [Ad](../extensibility/defaultname-element-visual-studio-templates.md) öğesini kullanın. `ProvideDefaultName` Öğenin değeri `true`olduğunda, projeler için `DefaultName` öğenin ihmal şablonun adı ile iletişim kutusu nu doldurur, yani [Ad](../extensibility/name-element-visual-studio-templates.md) öğesinden değer.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği `ProvideDefaultName` öğeyi `false`.

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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
