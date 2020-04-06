---
title: Referans Öğesi (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701621"
---
# <a name="reference-element-visual-studio-templates"></a>Başvuru öğesi (Visual Studio şablonları)
Öğe projeye eklendiğinde eklemek için derleme başvuru belirtir.

 \<VSTemplate \<> Şablonİçerik \< \<> Referanslar> Referans>

## <a name="syntax"></a>Sözdizimi

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Aşağıdaki bölümlerde öznitelik, alt öğeler ve üst öğeler açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Derleme](../extensibility/assembly-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonun bu derlemenin bir başvuruyu projelere eklemek için kullandığı bir derleme hakkındaki bilgileri belirtir. Her `Reference` elementte `Assembly` bir element olmalı.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Başvurular](../extensibility/references-element-visual-studio-templates.md)|Şablonun projelere eklediği derleme başvurularını gruplandırın.|

## <a name="remarks"></a>Açıklamalar
 `Reference`gerekli bir alt `References`öğedir.

 Ve `Reference` `References` öğeleri yalnızca öznitelik değeri olan `Type` *.vstemplate* dosyalarında `Item`kullanılabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `TemplateContent` bir öğe şablonunun öğesi gösterin. Bu XML *System.dll* ve *System.Data.dll* derlemelerine göndermeler ekler.

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
- [Visual Studio şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
