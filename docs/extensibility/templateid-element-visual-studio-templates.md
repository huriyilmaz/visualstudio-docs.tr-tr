---
title: TemplateId öğesi (Visual Studio şablonları) | Microsoft Docs
description: TemplateId öğesi hakkında bilgi edinin ve TemplateGroupID öğesi tarafından bir öğe şablonları grubuna kategorilere ayrılmış bir öğe şablonu için bir tanımlayıcı belirtir.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 734af9de80da5f095f9ad7f0e52023659fea6b67
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903188"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID Öğesi (Visual Studio Şablonları)
[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) öğesi tarafından bir öğe şablonları grubuna kategorize edilmiş bir öğe şablonu için tanımlayıcıyı belirtir.

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Syntax

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Öğe `string` tarafından bir öğe şablonları grubuna kategorize edilmiş bir öğe şablonu için tanımlayıcıyı temsil eden bir `TemplateGroupID` .

## <a name="remarks"></a>Açıklamalar
 `TemplateID` isteğe bağlı bir öğedir.

 Bir. vstemplate dosyası öğesi atladığında `TemplateID` , [Name](../extensibility/name-element-visual-studio-templates.md) öğesi şablon için tanımlayıcı olarak kullanılır.

 Öğe değeri, `TemplateID` Proje sistem kaydı (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects) ile birlikte kullanıldığında \\ **Yeni öğe Ekle** iletişim kutusunda görünen şablonları filtreleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
