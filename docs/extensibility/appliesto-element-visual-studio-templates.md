---
title: AppliesTo öğesi (Visual Studio şablonları) | Microsoft Docs
description: AppliesTo öğesi ve bir veya daha fazla özellik eşleşmesi için isteğe bağlı bir ifade nasıl belirttiği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 340ac4db04b62abade9c6572335e28c9fb27b495
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725327"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo öğesi (Visual Studio şablonları)

Bir veya daha fazla özellik eşleşmesi için isteğe bağlı bir ifade belirtir (bkz <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher> .). Özellikler, hiyerarşi aracılığıyla proje türleri tarafından bir özellik __VSHPROPID5 olarak sunulur [. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). Bu sayede, şablon ortak uygulanabilir yeteneklere sahip birden fazla proje türü tarafından paylaşılabilir.

Bu öğe isteğe bağlıdır. Bir şablon dosyasında en fazla bir örnek olabilir. Bu öğe yalnızca, o anda seçili etkin projenin yeteneklerine göre bir öğe şablonunun uygulanabilir olarak tercih edilmesini sağlar. Bir öğe şablonunu uygulanamaz yapmak için kullanılamaz. Yoksa `AppliesTo` veya ifade başarılı bir şekilde kabul etmediğinde, `TemplateID` `TemplateGroupID` ürünün önceki sürümlerinde olduğu gibi, şablonu uygulanabilir hale getirmek için veya kullanılır.

Visual Studio 2013 güncelleştirme 2 ' de kullanıma sunulmuştur. doğru sürüme başvurmak için, bkz. [Visual Studio 2013 SDK güncelleştirme 2 ' de sunulan derlemelere başvuru](/previous-versions/dn632168(v=vs.120)).

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Syntax

```xml
<AppliesTo>Capability1</AppliesTo>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablon kategorilere ayırır.|

## <a name="text-value"></a>Metin değeri

Bir metin değeri gereklidir. Bu metin projenin yeteneklerini belirtir.

Geçerli ifade sözdizimi şu şekilde tanımlanır:

- "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)" gibi yetenek ifadesi.

- "&#124;", OR işleçtir.

- "&" ve "+" karakterleri hem hem de işleçleridir.

- "!" karakteri NOT işlecidir.

- Parantezler değerlendirme-öncelik sırasını zorlar.

- Null veya boş ifade bir eşleşme olarak değerlendirilir.

- Project özellikleri şu ayrılmış karakterler dışında herhangi bir karakter olabilir: "' ':;, +-*/ \\ ! ~&#124;&% $ @ ^ () = {} [] <>? \t\b\n\r

## <a name="example"></a>Örnek

Aşağıdaki örnek, üç farklı şablonu göstermektedir. `Template1` Tüm C# proje türlerine veya özelliğini destekleyen diğer proje türlerine uygulanır `WindowsAppContainer` . `Template2` her türlü C# projesi için geçerlidir. `Template3` Proje olmayan C# projelerine uygulanır `WindowsAppContainer` .

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
