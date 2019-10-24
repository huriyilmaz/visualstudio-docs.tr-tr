---
title: TemplateId öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0e404921d1ed74db2a1f23117242f49a07206c2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718735"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID Öğesi (Visual Studio Şablonları)
[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) öğesi tarafından bir öğe şablonları grubuna kategorize edilmiş bir öğe şablonu için tanımlayıcıyı belirtir.

 \<VSTemplate > \<TemplateData > \<TemplateId >

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 `TemplateGroupID` öğesi tarafından bir öğe şablonları grubuna kategorize edilen bir öğe şablonu için tanımlayıcıyı temsil eden bir `string`.

## <a name="remarks"></a>Açıklamalar
 `TemplateID`, isteğe bağlı bir öğedir.

 Bir. vstemplate dosyası `TemplateID` öğesini atladığında, [Name](../extensibility/name-element-visual-studio-templates.md) öğesi şablon için tanımlayıcı olarak kullanılır.

 `TemplateID` öğesinin değeri, **Yeni öğe Ekle** iletişim kutusunda görünen şablonları filtrelemek için proje sistem kaydı (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) ile birlikte kullanılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)