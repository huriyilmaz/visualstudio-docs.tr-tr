---
title: DefaultName Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92bd29824cf1d3b91a7bdaa7220479c583ad0f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712313"
---
# <a name="defaultname-element-visual-studio-templates"></a>DefaultName öğesi (Visual Studio şablonları)
Visual Studio proje sisteminin proje veya öğe için oluşturulduğunda oluşturacağı adı belirtir.

 \<VSTemplate \<> ŞablonVeri> \<DefaultName>

## <a name="syntax"></a>Sözdizimi

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu metin, projenin veya öğenin varsayılan adını belirtir.

## <a name="remarks"></a>Açıklamalar
 `DefaultName`isteğe bağlı bir unsurdur.

 Projeler için bu öğe, projeyi diskte depolayan dizinin adını belirtir. Öğeler için, kaynak dosyanın dosya adını belirtir.

 Bir proje veya öğe oluşturduğunuzda, **Yeni Proje** iletişim kutusundan veya **Yeni Öğe Ekle** iletişim kutusundan kullanılabilen **Ad** seçeneğini kullanarak varsayılan adı değiştirebilirsiniz.

 Proje sisteminin proje veya öğe için varsayılan adı oluşturmasını istemiyorsanız, [AşağıdakiLeri Varsayılan Ad](../extensibility/providedefaultname-element-visual-studio-templates.md) öğesine `False`ayarlayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] sınıfın standart madde şablonu için meta veriler gösterilmektedir.

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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve madde şablonları oluşturma](../ide/creating-project-and-item-templates.md)
