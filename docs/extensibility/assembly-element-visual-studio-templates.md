---
title: Assembly öğesi (Visual Studio şablonları) | Microsoft Docs
titleSuffix: ''
description: Derleme öğesi hakkında bilgi edinin ve şablonun projelere Bu derlemenin bir başvurusunu eklemek için kullandığı bir derleme hakkındaki bilgileri nasıl belirttiği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 54fc5cfccde99776136f0cb904d02bf6a4971045
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725325"
---
# <a name="assembly-element-visual-studio-templates"></a>Assembly öğesi (Visual Studio şablonları)
Şablonun projelere Bu derlemenin bir başvurusunu eklemek için kullandığı bir derleme hakkındaki bilgileri belirtir.

 \<VSTemplate> \<TemplateContent>
 \<References>
 \<Reference>
 \<Assembly>

## <a name="syntax"></a>Syntax

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
|[Başvuru](../extensibility/reference-element-visual-studio-templates.md)|Öğe projeye eklendiğinde Eklenecek derleme başvurusunu belirtir.|

## <a name="text-value"></a>Metin değeri
 Bir metin değeri gereklidir.

 Bu metin, öğe şablonu örneği oluşturulduğunda bir projeye eklenecek derlemeyi belirtir. Bu derleme adı aşağıdaki yollarla belirtilmelidir:

- Tam derleme adı olarak. Örnek:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Basit metin başvurusu olarak. Örnek:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Açıklamalar
 `Assembly` , öğesinin gerekli bir alt öğesidir `Reference` .

 `Reference`, `References,` Ve `Assembly` öğeleri yalnızca özniteliği değeri olan *. vstemplate* dosyalarında kullanılabilir `Type` `Item` .

## <a name="example"></a>Örnek
 Aşağıdaki örnek `TemplateContent` bir öğe şablonunun öğesini gösterir. Bu XML *System.dll* ve *System.Data.dll* derlemelerine başvurular ekler.

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
- [Visual Studio şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
