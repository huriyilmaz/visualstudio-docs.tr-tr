---
title: VSCT XML Şeması Koşullu Öznitelikleri | Microsoft Docs
description: VSCT XML şema listelerine ve öğelerine koşullu öznitelikler uygulama hakkında bilgi. Öznitelikler, elde edilen çıkışı denetleyerek true veya false olarak değerlendirilir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e91207016ed6e1baab80b323680d10a40e0331d8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905260"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML şeması koşullu öznitelikleri
Koşullu öznitelikleri tüm listelere ve öğelere uygulayabilirsiniz. Mantıksal işleçler ve sembol genişletme ifadeleri true veya false olarak değerlendirilir. True ise, ilişkili liste veya öğe sonuçta elde edilen çıkışa dahil edilir.

 Belirteç genişletmelerini diğer belirteç genişletmelerine veya sabitlerine karşı test etmek için kullanabilirsiniz. İşlev, `Defined()` değere sahip olsa bile belirli bir adın tanımlanmamış olup olmadığını sıyr.

 Bir listeye Condition özniteliği uygulandığında koşul, listede yer alan her alt öğeye uygulanır. Bir alt öğenin kendisi bir Condition özniteliği içeriyorsa, koşulu bir AND işlemi tarafından üst ifadeyle birleştirilmiş olur.

 1, '1' ve 'true' değerleri true, 0, '0' ve 'false' değerleri false olarak değerlendirilir.

## <a name="operators"></a>İşleçler
 Koşullu ifadeleri değerlendirmek için aşağıdaki işleçleri kullanın.

|Operatör|Tanım|
|--------------|----------------|
|(,)|Gruplandırma|
|!|Mantıksal değil|
|\<, >, \<=, >=, ==, !=|İlişkisel ve Eşitlik|
|ve|Boole|
|veya|Boole|

## <a name="examples"></a>Örnekler

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tablosu () seçin. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
