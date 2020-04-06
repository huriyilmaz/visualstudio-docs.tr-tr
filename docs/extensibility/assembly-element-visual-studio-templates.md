---
title: Montaj Elemanı (Visual Studio Şablonları) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740039"
---
# <a name="assembly-element-visual-studio-templates"></a>Montaj öğesi (Visual Studio şablonları)
Şablonun bu derlemenin bir başvuruyu projelere eklemek için kullandığı bir derleme hakkındaki bilgileri belirtir.

 \<VSTemplate \<> Şablonİçerik \< \<> \<Referanslar> Başvuru> Montaj>

## <a name="syntax"></a>Sözdizimi

```
<Assembly> AssemblyName </Assembly>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler
 Yok.

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Başvuru](../extensibility/reference-element-visual-studio-templates.md)|Öğe projeye eklendiğinde eklemek için derleme başvuru belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu metin, öğe şablonu anında olduğunda projeye eklemek için derlemeyi belirtir. Bu derleme adı aşağıdaki yollardan biriyle belirtilmelidir:

- Tam montaj adı olarak. Örnek:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Basit metin referansı olarak. Örnek:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Açıklamalar
 `Assembly`gerekli bir alt `Reference`öğedir.

 `Reference`, `References,` ve `Assembly` öğeler yalnızca *.vstemplate* dosyalarında `Type` `Item`kullanılabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, `TemplateContent` bir öğe şablonunun öğesi gösterin. Bu XML *System.dll* ve *System.Data.dll* derlemelerine göndermeler ekler.

```
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
