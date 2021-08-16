---
title: References Öğesi (Visual Studio Şablonları) | Microsoft Docs
description: References öğesini ve şablonun projelere ekleyen derleme başvurularını nasıl gruplay olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9cf14c207d7ffb560612d963571fc11cca6d55e68ac4418afa8ec71bb69c0920
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359019"
---
# <a name="references-element-visual-studio-templates"></a>References öğesi (Visual Studio şablonları)
Şablonun projelere ekleyen derleme başvurularını gruplar.

 \<VSTemplate> \<TemplateContent>
 \<References>

## <a name="syntax"></a>Syntax

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Başvuru](../extensibility/reference-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Öğe bir projeye ekleniyorken eklenecek derleme başvurularını belirtir. Bir öğede bir veya daha `Reference` fazla öğe `References` olması gerekir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonun içeriğini belirtir.|

## <a name="remarks"></a>Açıklamalar
 `References` isteğe bağlı bir alt `TemplateContent` öğesidir.

 ve öğeleri yalnızca öznitelik değerine sahip `Reference` `References` *.vstemplate* `Type` dosyalarında `Item` kullanılabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir `TemplateContent` öğe şablonunun öğesini gösterir. Bu XML,System.dll *veSystem.Data.dll* ekler. 

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio şablonu şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
