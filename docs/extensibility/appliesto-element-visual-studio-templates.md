---
title: AapplyTo Element (Visual Studio Templates) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b5ee1e3cad0b4d8ddbe0fc2dfa1c2d478ec063
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740079"
---
# <a name="appliesto-element-visual-studio-templates"></a>AapplyTo öğesi (Visual Studio şablonları)

Bir veya daha fazla özelliği eşleştirmek için <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>isteğe bağlı bir ifade belirtir (bkz. Özellikler, bir özellik __VSHPROPID5 olarak hiyerarşi aracılığıyla proje türlerine göre açığa [alınır. VSHPROPID_ProjectCapabilities.](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>) Bu sayede, şablon ortak uygulanabilir yeteneklere sahip birden fazla proje türü tarafından paylaşılabilir.

Bu öğe isteğe bağlıdır. Bir şablon dosyasında en fazla bir örnek olabilir. Bu öğe yalnızca, o anda seçili etkin projenin yeteneklerine göre bir öğe şablonunun uygulanabilir olarak tercih edilmesini sağlar. Bir öğe şablonunu uygulanamaz yapmak için kullanılamaz. `AppliesTo` Yoksa veya ifade başarılı bir şekilde kabul `TemplateID` etmiyorsa, `TemplateGroupID` şablonu ürünün önceki sürümlerinde olduğu gibi geçerli kılmak için kullanılır.

Visual Studio 2013 Güncelleme 2 tanıtıldı. Doğru sürüme başvurmak için Visual [Studio 2013 SDK Update 2'de teslim edilen Başvuru derlemelerine](/previous-versions/dn632168(v=vs.120))bakın.

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Sözdizimi

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

- "&#124;" OR işlecidir.

- "&" ve "+" karakterleri hem AND işleçleridir.

- "!" karakteri NOT işlecidir.

- Parantezler değerlendirme-öncelik sırasını zorlar.

- Null veya boş ifade bir eşleşme olarak değerlendirilir.

- Proje yetenekleri bu ayrılmış karakterler dışında herhangi bir karakter olabilir: "''::,+-*/\\!~&#124;&%$@^()={}[]<>? \t\b\n\r

## <a name="example"></a>Örnek

Aşağıdaki örnek, üç farklı şablonu göstermektedir. `Template1`tüm C# proje türleri veya `WindowsAppContainer` yeteneği destekleyen diğer proje türleri için geçerlidir. `Template2`her türlü c# projeleri için geçerlidir. `Template3`proje olmayan `WindowsAppContainer` C# projeleri için geçerlidir.

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

- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
