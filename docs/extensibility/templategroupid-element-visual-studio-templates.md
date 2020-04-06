---
title: TemplateGroupID Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: affc324418e3745f85fb0b91a0ef7abda0ab28b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699072"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID Öğesi (Visual Studio Şablonları)
Bir öğe şablonunun ne tür bir projede görüneceğini belirtir. [ShowByDefault (Visual Studio Templates)](../extensibility/showbydefault-visual-studio-templates.md) olarak ayarlandığında `false`bu öğe önemlidir. [ShowByDefault (Visual Studio Şablonları)](../extensibility/showbydefault-visual-studio-templates.md) `true`ayarlandığında, tüm proje türlerinde bir öğe şablonu kullanılabilir.

 \<VSTemplate \<> ŞablonVeri> \<ŞablonGroupID>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırın ve Yeni **Proje'de** veya **Yeni Öğe Ekle** iletişim kutusunda nasıl görüntüleyeceğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metin, öğe şablonları kategorisi için bir tanımlayıcı belirtir.

## <a name="remarks"></a>Açıklamalar
 `TemplateGroupID`bir unsurdur.

 Öğenin `TemplateGroupID` değeri, **Yeni Öğe Ekle** iletişim kutusunda görünen şablonları\\filtrelemek için proje sistem kaydı (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*\<sürüm numarası>* \Projeler)\\ile birlikte kullanılır.

|Görsel C++ Değeri|Anlamı|
|------------------------|-------------|
|VC-Yerli|Yerel projeler için kullanılır. Proje türü belirlenemezse de varsayılan değerdir.|
|VC Yönetilen|Yönetilen (/clr) projeler için kullanılır|
|VC-Windows|Windows platformlarını hedefleyen tüm projeler için kullanılır (yerel/yönetilen/depo)|
|WinRT-Yerli-UAP|Windows 10 mağaza projeleri için kullanılır|
|KodPaylaşımı-Yerel|Paylaşılan öğe projeleri için kullanılır|
|WinRT-Yerli-6.3|Windows 8.1 Store projeleri için kullanılır|
|WinRT-Yerli-Telefon-6.3|Windows Phone 8.1 projeleri için kullanılır|
|WinRT-Yerli|Windows 8.0 Store projeleri için kullanılır|
|VC-Android|Android projeleri için kullanılır|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
