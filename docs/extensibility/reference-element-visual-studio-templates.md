---
title: Reference öğesi (Visual Studio şablonları) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701621"
---
# <a name="reference-element-visual-studio-templates"></a>Reference öğesi (Visual Studio şablonları)
Öğe projeye eklendiğinde Eklenecek derleme başvurusunu belirtir.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>

## <a name="syntax"></a>Syntax

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
|[Bütünleştirilmiş Kod](../extensibility/assembly-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Şablonun projelere Bu derlemenin bir başvurusunu eklemek için kullandığı bir derleme hakkındaki bilgileri belirtir. `Assembly`Her öğede bir öğe olmalıdır `Reference` .|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Başvurular](../extensibility/references-element-visual-studio-templates.md)|Şablonun projelere eklediği derleme başvurularını gruplandırır.|

## <a name="remarks"></a>Açıklamalar
 `Reference` , öğesinin gerekli bir alt öğesidir `References` .

 `Reference`Ve `References` öğeleri yalnızca özniteliği değeri olan *. vstemplate* dosyalarında kullanılabilir `Type` `Item` .

## <a name="example"></a>Örnek
 Aşağıdaki örnek `TemplateContent` bir öğe şablonunun öğesini gösterir. Bu XML *System.dll* ve *System.Data.dll* derlemelerine başvurular ekler.

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
- [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
