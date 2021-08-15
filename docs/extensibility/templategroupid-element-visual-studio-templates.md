---
title: TemplateGroupID Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: TemplateGroupID öğesi hakkında bilgi ve öğe şablonlarının ne tür bir projede gösterüleceklerini nasıl belirtir?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 582723ede99b0644688abd62d644e6aaf05220c8224dae82dd6eace39c904f63
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121237741"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID Öğesi (Visual Studio Şablonları)
Bir öğe şablonlarının ne tür bir projede göster göster olduğunu belirtir. [ShowByDefault (Visual Studio Templates) olarak ayarlanırken bu](../extensibility/showbydefault-visual-studio-templates.md) öğe `false` önemlidir. [ShowByDefault (Visual Studio Şablonları)](../extensibility/showbydefault-visual-studio-templates.md) olarak ayarlanırsa, tüm proje `true` türlerinde bir öğe şablonu kullanılabilir.

 \<VSTemplate> \<TemplateData>
 \<TemplateGroupID>

## <a name="syntax"></a>Syntax

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırarak Yeni Öğe Ekle iletişim kutusunda **Project** **nasıl görüntü olduğunu** tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

 Metin, öğe şablonları kategorisi için bir tanımlayıcı belirtir.

## <a name="remarks"></a>Açıklamalar
 `TemplateGroupID` bir öğedir.

 öğesinin `TemplateGroupID` değeri, Yeni Öğe Ekle iletişim kutusunda görünen şablonları filtrelemek için proje sistemi kaydıyla (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<version number>* \Projects \\ ) birlikte kullanılır. 

|Visual C++ Değeri|Anlamı|
|------------------------|-------------|
|VC-Native|Yerel projeler için kullanılır. Ayrıca, bir proje türü belirlenenine kadar varsayılan değerdir.|
|VC-Managed|Yönetilen (/clr) projeler için kullanılır|
|VC-Windows|Windows platformunu (yerel/yönetilen/depo) hedef alan tüm projeler için kullanılır|
|WinRT-Native-UAP|Depolama projeleri Windows 10 için kullanılır|
|CodeSharing-Native|Paylaşılan öğe projeleri için kullanılır|
|WinRT-Native-6.3|Windows 8.1 Store projeleri için kullanılır|
|WinRT-Native-Telefon-6.3|8.1 Windows Phone için kullanılır|
|WinRT-Native|Windows 8.0 Store projeleri için kullanılır|
|VC-Android|Android projeleri için kullanılır|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
