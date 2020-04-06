---
title: VSCT XML Şema Koşullu Öznitelikler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697940"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML şema koşullu öznitelikleri
Koşullu öznitelikleri tüm listelere ve öğelere uygulayabilirsiniz. Mantıksal işleçler ve sembol genişletme ifadeleri doğru veya yanlış olarak değerlendirilir. Doğruysa, ilişkili liste veya öğe elde edilen çıktıya dahil edilir.

 Belirteç genişletmelerini diğer belirteç genişletmelerine veya sabitlere karşı test edebilirsiniz. İşlev, `Defined()` değeri olmasa bile belirli bir adın tanımlanıp tanımlanmadığını sınar.

 Bir Koşul özniteliği bir listeye uygulandığında, koşul listedeki her alt öğeye uygulanır. Bir alt öğenin kendisi bir Durum özniteliği içeriyorsa, durumu bir AND işlemi ile üst ifade ile birleştirilir.

 1, '1' ve 'true' değerleri doğru, 0, '0' ve 'yanlış' değerleri yanlış olarak değerlendirilir.

## <a name="operators"></a>İşleçler
 Koşullu ifadeleri değerlendirmek için aşağıdaki işleçleri kullanın.

|İşleç|Tanım|
|--------------|----------------|
|(,)|Gruplandırma|
|!|Mantıksal değil|
|\<, >, \<=, >=, ==, !=|İlişkisel ve Eşitlik|
|ve|Boole|
|or|Boole|

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
- [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
