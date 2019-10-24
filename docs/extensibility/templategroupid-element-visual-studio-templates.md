---
title: TemplateGroupID öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f710a73d8b9c4e31c8189d3322c518f20def5bb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718665"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID Öğesi (Visual Studio Şablonları)
Öğe şablonlarının ne tür projenin gösterileceğini belirtir. Bu öğe, [ShowByDefault (Visual Studio şablonları)](../extensibility/showbydefault-visual-studio-templates.md) `false` olarak ayarlandığında önemlidir. [ShowByDefault (Visual Studio şablonları)](../extensibility/showbydefault-visual-studio-templates.md) `true` olarak ayarlandığında, tüm proje türlerinde bir öğe şablonu kullanılabilir.

 \<VSTemplate > \<TemplateData > \<TemplateGroupID >

## <a name="syntax"></a>Sözdizimi

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metin bir öğe şablonları kategorisi için tanımlayıcıyı belirtir.

## <a name="remarks"></a>Açıklamalar
 `TemplateGroupID` öğesidir.

 @No__t_0 öğesinin değeri proje sistem kaydıyla birlikte kullanılır (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<version numarası >* \projects \\) ve **Yeni öğe Ekle ' de görüntülenen şablonları filtrelemek için** iletişim kutusu.

|Görsel C++ değer|Açıklama|
|------------------------|-------------|
|VC-yerel|Yerel projeler için kullanılır. Ayrıca, bir proje türü belirlenemiyorsa varsayılan değer.|
|VC tarafından yönetilen|Yönetilen (/CLR) projeler için kullanılır|
|VC-Windows|Windows platformunu hedefleyen tüm projeler için kullanılır (Yerel/yönetilen/mağaza)|
|WinRT-yerel-UAP|Windows 10 mağazası projeleri için kullanılır|
|CodeSharing-yerel|Paylaşılan öğe projeleri için kullanılır|
|WinRT-yerel-6,3|Windows 8.1 mağaza projeleri için kullanılır|
|WinRT-yerel-telefon-6,3|Windows Phone 8,1 projeleri için kullanılır|
|WinRT-yerel|Windows 8,0 mağaza projeleri için kullanılır|
|VC-Android|Android projeleri için kullanılır|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)