---
title: TargetPlatformName öğesi (Visual Studio şablonları) | Microsoft Docs
description: TargetPlatformName öğesi ve proje şablonunun hedeflediği platformu nasıl belirttiği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1f2b8903c99e5bd2f62587b7921be855e4ed6323
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938778"
---
# <a name="targetplatformname-element-visual-studio-templates"></a>TargetPlatformName Öğesi (Visual Studio Şablonları)
Proje şablonunun hedeflediği platformu belirtir. Bu öğe, uygulama oluşturmak için bir proje şablonu kullanılacağını belirtmek için kullanılır [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] .

## <a name="syntax"></a>Syntax

```xml
<VSTemplate>
    <TemplateData>
        <TargetPlatformName> OperatingSystem</TargetPlatformName>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|Proje şablonunun hedeflediği işlem sisteminin sürümünü belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırır ve **Yeni proje** veya **Yeni öğe Ekle** iletişim kutusunda nasıl görüntülediğini tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

## <a name="remarks"></a>Açıklamalar
 Metin **Windows** olmalıdır.

## <a name="example"></a>Örnek
 Bu örnek, proje şablonunun hedeflediği [!INCLUDE[win8](../debugger/includes/win8_md.md)] veya daha sonraki bir sürümünü belirtir.

```xml
<VSTemplate Type="Project" Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
        <RequiredPlatformVersion>8</RequiredPlatformVersion>
    </TemplateData>
    <TemplateContent> </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Proje ve Öğe Şablonları Oluşturma](../ide/creating-project-and-item-templates.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
