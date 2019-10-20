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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663069"
---
# <a name="ltvargt-javascript"></a>&lt;var &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir değişken için belge bilgilerini belirtir.

## <a name="syntax"></a>Sözdizimi

```
<var type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID">description
</var>
```

#### <a name="parameters"></a>Parametreler
 Isteğe bağlı `type`. Değişkenin veri türü. Tür aşağıdakilerden biri olabilir:

- @No__t_0 ve `Object` gibi ECMAScript 5 belirtiminde bir ECMAScript dil türü.

- @No__t_0, `Window` ve `Document` gibi bir DOM nesnesi.

- JavaScript Oluşturucu işlevi.

  Isteğe bağlı `integer`. @No__t_0 `Number`, değişkenin bir tamsayı olup olmadığını belirtir. Değişkenin bir tamsayı olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `domElement`. Bu öznitelik kullanım dışıdır; `type` özniteliği bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen değişkenin bir DOM öğesi olup olmadığını belirtir. Değişkenin bir DOM öğesi olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `domElement` `true` olarak ayarlandıysa, IntelliSense, deyimin tamamlanmasını gerçekleştirirken belgelenen değişkeni bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `mayBeNull`. Belgelenmiş değişkenin null olarak ayarlanamayacağını belirtir. Değişkenin null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementType`. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin türünü belirtir.

  Isteğe bağlı `elementInteger`. @No__t_0 `Array` ve `elementType` `Number` ise, bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. Dizideki öğelerin tamsayılar olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementDomElement`. Bu öznitelik kullanım dışıdır; `elementType` özniteliği bu özniteliğin üzerine gelir. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin DOM öğeleri olup olmadığını belirtir. Öğelerin DOM öğeleri olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `elementDomElement` `true` olarak ayarlandıysa, IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `elementMayBeNull`. @No__t_0 `Array`, dizideki öğelerin null olarak ayarlanamayacağını belirtir. Dizideki öğelerin null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `helpKeyword`. F1 Yardım anahtar sözcüğü.

  Isteğe bağlı `locid`. Değişkenle ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki `name` öznitelik değerine karşılık gelir. Tanımlayıcı türü, [\<loc >](../ide/loc-javascript.md) etiketinde belirtilen biçime bağlıdır.

  Isteğe bağlı `description`. Değişkenin açıklaması.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `<var>` öğesinin nasıl kullanılacağını gösterir.

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
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
