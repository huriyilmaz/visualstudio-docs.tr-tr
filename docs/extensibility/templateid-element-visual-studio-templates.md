---
title: TemplateID Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699068"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID Öğesi (Visual Studio Şablonları)
[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) öğesi tarafından madde şablonları grubuna kategorize edilen bir madde şablonu için tanımlayıcı belirtir.

 \<VSTemplate \<> ŞablonVeri> \<TemplateID>

## <a name="syntax"></a>Sözdizimi

```
<TemplateID> ... </TemplateID>
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
 Öğe `string` tarafından madde şablonları grubuna kategorize edilen bir öğe şablonu için `TemplateGroupID` tanımlayıcıyı temsil eden bir tanım.

## <a name="remarks"></a>Açıklamalar
 `TemplateID`isteğe bağlı bir unsurdur.

 Bir .vstemplate dosyası öğeyi `TemplateID` atlarsa, [Ad](../extensibility/name-element-visual-studio-templates.md) öğesi şabloniçin tanımlayıcı olarak kullanılır.

 Öğenin `TemplateID` değeri, **Yeni Öğe Ekle** iletişim kutusunda görünen şablonları filtrelemek için proje\\sistem kaydı (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects) ile birlikte kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
