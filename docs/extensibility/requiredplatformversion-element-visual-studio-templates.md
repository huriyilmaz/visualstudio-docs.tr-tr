---
description: Proje şablonunun düzgün çalışması için gereken en düşük işletim sistemi sürümünü belirtir.
title: RequiredPlatformVersion Öğesi (Visual Studio Şablonları)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f5f72045fdfca073fbc740698c2eefe57a1a932f32751f9fe278e17c280fad9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388537"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion öğesi (Visual Studio şablonları)

Proje şablonunun düzgün çalışması için gereken en düşük işletim sistemi sürümünü belirtir. Bu öğe, uygulama oluşturan proje şablonları için [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] kullanılır.

 Değer `RequiredPlatformVersion` doğrudan işletim sisteminin sürümüyle karşılaştırıldı. işletim `RequiredPlatformVersion` sistemi sürümünden yüksekse, şablon Yeni Sürüm iletişim **Project** görünmez. veya daha yüksek bir şablon [!INCLUDE[win8](../debugger/includes/win8_md.md)] belirtmek için `RequiredPlatformVersion` 6.2.0 olarak ayarlayın. veya daha yüksek bir şablon [!INCLUDE[win81](../debugger/includes/win81_md.md)] belirtmek için `RequiredPlatformVersion` 6.3.0 olarak ayarlayın.

 `RequiredPlatformVersion`=8'i belirten şablonlar önceki müşteri [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] şablonlarıyla uyumludur.

 VSTemplate TemplateData ..... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Syntax

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Yok.

### <a name="attributes"></a>Öznitelikler

 Yok.

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Proje şablonunun hedefley olduğu platformu belirtir.|

## <a name="text-value"></a>Metin değeri

 Bir metin değeri gereklidir.

## <a name="remarks"></a>Açıklamalar

 Bu metin, şablon için gereken en düşük işletim sistemi sürümünü belirtir.

## <a name="example"></a>Örnek

 Bu örnek, proje şablonunun veya sonraki bir şablonu [!INCLUDE[win8](../debugger/includes/win8_md.md)] hedefle olduğunu belirtir.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.

- [TargetPlatformName öğesi (Visual Studio şablonları)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
