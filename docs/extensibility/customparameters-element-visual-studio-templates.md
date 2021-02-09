---
title: CustomParameters öğesi (Visual Studio şablonları) | Microsoft Docs
description: CustomParameters öğesi ve sihirbaz parametre değişiklikleri yaptığında şablon sihirbazına geçirilecek özel parametreleri nasıl gruplayan hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a899790890bd299dcb77558d31499b0a61bcefe4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927138"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters öğesi (Visual Studio şablonları)
Sihirbaz parametre değişiklikleri yaptığında şablon sihirbazına geçirilecek özel parametreleri gruplandırır.

## <a name="syntax"></a>Syntax

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablondan bir proje veya öğe oluşturulduğunda kullanılacak özel bir parametre adı ve değeri içerir. Öğesinde sıfır veya daha fazla `CustomParameter` öğe olabilir `CustomParameters` .|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonun içeriğini belirtir.|

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir şablonda birkaç özel parametrenin nasıl kullanılacağını gösterir. Bir şablon veya öğe, aşağıdaki özel parametrelerle bir şablondan oluşturulduğunda, `$color1$` `$color2$` şablon dosyalarındaki ve içindeki tüm örnekleri sırasıyla ve ile yerine geçer `Red` `Blue` .

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Ayrıca bkz.
- [CustomParameter öğesi (Visual Studio şablonları)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
