---
title: CustomParameter öğesi (Visual Studio şablonları) | Microsoft Docs
description: CustomParameter öğesi hakkında bilgi edinin ve şablondan bir proje veya öğe oluşturulduğunda kullanılacak özel parametre adını ve değerini nasıl içerdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c118bbc85064beb10b99641f0803af7af12d56
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671955"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter öğesi (Visual Studio şablonları)
Şablondan bir proje veya öğe oluşturulduğunda kullanılacak özel bir parametre adı ve değeri içerir.

## <a name="syntax"></a>Syntax

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Parametrenin adı. Parametrelerin biçimi $*Name*$ olur.|
|`Value`|Gereklidir. Parametrenin değiştirme değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Sihirbaz parametre değişiklikleri yaptığında şablon sihirbazına geçirilecek özel parametreleri gruplandırır.|

## <a name="remarks"></a>Açıklamalar
 Şablon `CustomParameter` öğeleri içerdiğinde, her örnek `Name` özniteliği `Value` oluşturulan proje veya öğe dosyalarındaki özniteliğiyle değiştirilmiştir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir şablonda birkaç özel parametrenin nasıl kullanılacağını gösterir. Bir şablon veya öğe, aşağıdaki özel parametrelerle bir şablondan oluşturulduğunda, `$color1$` `$color2$` şablon dosyalarındaki ve içindeki tüm örnekleri sırasıyla ve ile yerine geçer `Red` `Blue` .

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Ayrıca bkz.
- [CustomParameters öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
