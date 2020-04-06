---
title: CustomParameters Elemanı (Visual Studio Şablonları) | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739416"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParametreler öğesi (Visual Studio şablonları)
Sihirbaz parametre değiştirmeleri yaptığında şablon sihirbazına geçirilecek özel parametreleri gruplandırın.

## <a name="syntax"></a>Sözdizimi

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
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|İsteğe bağlı öğe.<br /><br /> Şablondan bir proje veya öğe oluşturulduğunda kullanılacak özel bir parametre adı ve değer içerir. Bir `CustomParameters` öğede sıfır `CustomParameter` veya daha fazla öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonun içeriğini belirtir.|

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Aşağıdaki örnek, şablonda birkaç özel parametrenin nasıl kullanılacağını gösterir. Bir proje veya öğe aşağıdaki özel parametrelere sahip bir şablondan `$color2$` oluşturulduğunda, şablon dosyalarının `Red` `$color1$` `Blue`tüm örnekleri sırasıyla ve şablon dosyalarıyla değiştirilir.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Ayrıca bkz.
- [CustomParameter öğesi (Visual Studio şablonları)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Şablon parametreleri](../ide/template-parameters.md)
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
