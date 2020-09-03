---
title: RequiredPlatformVersion öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701491"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion öğesi (Visual Studio şablonları)
Proje şablonunun doğru çalışması için gereken en düşük işletim sistemi sürümünü belirtir. Bu öğe, uygulama oluşturan proje şablonları için kullanılır [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .

 `RequiredPlatformVersion`Değer, işletim sisteminin sürümü ile doğrudan karşılaştırılır. , `RequiredPlatformVersion` İşletim sistemi sürümünden daha yüksekse, şablon **Yeni proje** iletişim kutusunda görünmez. Veya üzeri bir şablon belirtmek için [!INCLUDE[win8](../debugger/includes/win8_md.md)] , `RequiredPlatformVersion` 6.2.0 olarak ayarlayın. Veya üzeri bir şablon belirtmek için [!INCLUDE[win81](../debugger/includes/win81_md.md)] , `RequiredPlatformVersion` 6.3.0 olarak ayarlayın.

 = 8 ' i belirten şablonlar `RequiredPlatformVersion` önceki müşteri şablonlarıyla uyumludur [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .

 VSTemplate TemplateData..... TargetPlatformName RequiredPlatformVersion

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
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Proje şablonunun hedeflediği platformu belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

## <a name="remarks"></a>Açıklamalar
 Bu metin, şablonun gerektirdiği en düşük işletim sistemi sürümünü belirtir.

## <a name="example"></a>Örnek
 Bu örnek, proje şablonunun hedeflediği [!INCLUDE[win8](../debugger/includes/win8_md.md)] veya daha sonraki bir sürümünü belirtir.

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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
