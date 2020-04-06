---
title: CustomParameter Element (Visual Studio Şablonları) | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739421"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter öğesi (Visual Studio şablonları)
Şablondan bir proje veya öğe oluşturulduğunda kullanılacak özel bir parametre adı ve değer içerir.

## <a name="syntax"></a>Sözdizimi

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Parametrenin adı. Parametrelerin biçimi $*adı*$'dır.|
|`Value`|Gereklidir. Parametrenin değiştirme değeri.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Sihirbaz parametre değiştirmeleri yaptığında şablon sihirbazına geçirilecek özel parametreleri gruplandırın.|

## <a name="remarks"></a>Açıklamalar
 Şablon öğeleri `CustomParameter` içeriyorsa, `Name` her örnekte öznitelik `Value` oluşturulan proje veya madde dosyalarındaki öznitelikile değiştirilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, şablonda birkaç özel parametrenin nasıl kullanılacağını gösterir. Bir proje veya öğe aşağıdaki özel parametrelere sahip bir şablondan `$color2$` oluşturulduğunda, şablon dosyalarının `Red` `$color1$` `Blue`tüm örnekleri sırasıyla ve şablon dosyalarıyla değiştirilir.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Ayrıca bkz.
- [CustomParametreler öğesi (Visual Studio şablonları)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
