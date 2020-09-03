---
title: '&lt;var &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f72b403d4c6c9cc71bc2a3fdbff8f778a44b3b55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663069"
---
# <a name="ltvargt-javascript"></a>&lt;var &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir değişken için belge bilgilerini belirtir.

## <a name="syntax"></a>Söz dizimi

```
<var type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID">description
</var>
```

#### <a name="parameters"></a>Parametreler
 `type` Seçim. Değişkenin veri türü. Tür aşağıdakilerden biri olabilir:

- ECMAScript 5 belirtiminde, ve gibi bir ECMAScript dil türü `Number` `Object` .

- , Ve gibi bir DOM nesnesi `HTMLElement` `Window` `Document` .

- JavaScript Oluşturucu işlevi.

  `integer` Seçim. İse `type` , `Number` değişkenin bir tamsayı olup olmadığını belirtir. `true`Değişkenin bir tamsayı olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `domElement` Seçim. Bu öznitelik kullanım dışıdır; `type` öznitelik bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen değişkenin bir DOM öğesi olup olmadığını belirtir. `true`Değişkenin BIR DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `type`Özniteliği ayarlanmamışsa ve `domElement` olarak ayarlanırsa `true` , IntelliSense, ifade tamamlama gerçekleştirirken belgelenen değişkeni bir olarak değerlendirir `HTMLElement` .

  `mayBeNull` Seçim. Belgelenmiş değişkenin null olarak ayarlanamayacağını belirtir. `true`Değişkenin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementType` Seçim. `type`İse `Array` , bu öznitelik dizideki öğelerin türünü belirtir.

  `elementInteger` Seçim. , `type` Ve ise, `Array` `elementType` `Number` Bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. `true`Dizideki öğelerin tamsayılar olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementDomElement` Seçim. Bu öznitelik kullanım dışıdır; `elementType` öznitelik bu özniteliğin üzerine gelir. `type`İse `Array` , bu öznitelik DIZIDEKI öğelerin DOM öğeleri olup olmadığını belirtir. `true`ÖĞELERIN DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `elementType`Özniteliği ayarlanmamışsa ve `elementDomElement` olarak ayarlandıysa `true` , IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir olarak değerlendirir `HTMLElement` .

  `elementMayBeNull` Seçim. `type`İse, `Array` dizideki öğelerin null olarak ayarlanamayacağını belirtir. `true`Dizideki öğelerin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `helpKeyword` Seçim. F1 Yardım anahtar sözcüğü.

  `locid` Seçim. Değişkenle ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da `name` OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki öznitelik değerine karşılık gelir. Tanımlayıcı türü, etiketinde belirtilen biçime bağlıdır [\<loc>](../ide/loc-javascript.md) .

  `description` Seçim. Değişkenin açıklaması.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, öğesinin nasıl kullanılacağını gösterir `<var>` .

```javascript
/// <var>A rectangle that has a width of 5.</var>
var Rectangle = {
    /// <field type = 'Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type = 'Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
