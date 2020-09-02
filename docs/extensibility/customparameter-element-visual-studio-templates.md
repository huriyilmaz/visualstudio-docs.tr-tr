---
title: CustomParameter öğesi (Visual Studio şablonları) | Microsoft Docs
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
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739421"
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
