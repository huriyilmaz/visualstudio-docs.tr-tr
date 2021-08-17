---
title: VSCT XML şeması Koşullu öznitelikleri | Microsoft Docs
description: VSCT XML şema listelerine ve öğelerine koşullu öznitelikler uygulamayı öğrenin. Öznitelikler doğru veya yanlış olarak değerlendirilir ve sonuçta elde edilen çıktıyı kontrol edin.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c56f3cd8929d9ca17b01df2e78ab6a1b8354558445450137bd2e68aa1a8785d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121335283"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML şeması Koşullu öznitelikleri
Koşullu öznitelikleri tüm listelerine ve öğelere uygulayabilirsiniz. Mantıksal işleçler ve sembol genişletme ifadeleri true veya false olarak değerlendirilir. True ise, ilişkili liste veya öğe ortaya çıkan çıktıya dahil edilir.

 Belirteç genişletmeleri diğer belirteç genişletmeleri veya sabitlerine karşı test edebilirsiniz. İşlevi, `Defined()` bir değer olmasa bile belirli bir adın tanımlanıp tanımlanmadığını sınar.

 Bir koşul özniteliği bir listeye uygulandığında, koşul listedeki her alt öğeye uygulanır. Bir alt öğenin kendisi bir koşul özniteliği içeriyorsa, koşulu bir ve işlemi tarafından üst ifadeyle birleştirilir.

 1, ' 1 ' ve ' true ' değerleri true olarak değerlendirilir ve 0, ' 0 ' ve ' false ' yanlış olarak değerlendirilir.

## <a name="operators"></a>İşleçler
 Koşullu ifadeleri değerlendirmek için aşağıdaki işleçleri kullanın.

|Operatör|Tanım|
|--------------|----------------|
|(,)|Gruplandırma|
|!|Mantıksal değil|
|\<, >, \<=, >=, ==, !=|İlişkisel ve eşitlik|
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
- [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
