---
title: References öğesi (Visual Studio şablonları) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef31c5e7550ec7c6e4570d156d364afcf4ad6819
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701610"
---
# <a name="references-element-visual-studio-templates"></a>References öğesi (Visual Studio şablonları)
Şablonun projelere eklediği derleme başvurularını gruplandırır.

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
|[Başvuru](../extensibility/reference-element-visual-studio-templates.md)|Gerekli öğe.<br /><br /> Öğe projeye eklendiğinde Eklenecek derleme başvurusunu belirtir. Öğesinde bir veya daha fazla `Reference` öğe olmalıdır `References` .|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Şablonun içeriğini belirtir.|

## <a name="remarks"></a>Açıklamalar
 `References` , öğesinin isteğe bağlı bir alt öğesidir `TemplateContent` .

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
