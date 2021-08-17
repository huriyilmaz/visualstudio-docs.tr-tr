---
title: TargetPlatformName Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: TargetPlatformName öğesini ve proje şablonunun hedeflemektedir platformunu nasıl belirtir hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 3a6b1f45-b5d6-418e-add1-87ee8f15033d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d888b393f669305b03379e0d138ecfa5e75305981a0bec03f53424b95ad6ec0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358901"
---
# <a name="targetplatformname-element-visual-studio-templates"></a>TargetPlatformName Öğesi (Visual Studio Şablonları)
Proje şablonunun hedefley olduğu platformu belirtir. Bu öğe, uygulama oluşturmak için bir proje şablonu kullanmak için [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] kullanılır.

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
|[RequiredPlatformVersion](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|Proje şablonu tarafından hedeflenen işlem sisteminin sürümünü belirtir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Şablonu kategorilere ayırarak Yeni Öğe Ekle iletişim kutusunda **Project** **şekilde** tanımlar.|

## <a name="text-value"></a>Metin Değeri
 Bir metin değeri gereklidir.

## <a name="remarks"></a>Açıklamalar
 Metin, olarak **Windows.**

## <a name="example"></a>Örnek
 Bu örnek, proje şablonunun veya sonraki bir şablonu [!INCLUDE[win8](../debugger/includes/win8_md.md)] hedefle olduğunu belirtir.

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
