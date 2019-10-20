---
title: '&lt;value &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656393"
---
# <a name="ltvaluegt-javascript"></a>&lt;value &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ECMAScript 3 özellikleri için `get` ve `set` işlevleriyle ilgili belge bilgilerini belirtir.

## <a name="syntax"></a>Sözdizimi

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>Parametreler
 Isteğe bağlı `type`. Özelliğin veri türü. Tür aşağıdakilerden biri olabilir:

- @No__t_0 ve `Object` gibi ECMAScript 5 belirtiminde bir ECMAScript dil türü.

- @No__t_0, `Window` ve `Document` gibi bir DOM nesnesi.

- JavaScript Oluşturucu işlevi.

  Isteğe bağlı `integer`. @No__t_0 `Number`, özelliğin bir tamsayı olup olmadığını belirtir. Özelliğin bir tamsayı olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `domElement`. Bu öznitelik kullanım dışıdır; `type` özniteliği bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen özelliğin bir DOM öğesi olup olmadığını belirtir. Özelliğin bir DOM öğesi olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `domElement` `true` olarak ayarlandıysa, IntelliSense, deyimin tamamlanmasını gerçekleştirirken belgelenen özelliği bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `mayBeNull`. Belgelenmiş özelliğin NULL olarak ayarlanamayacağını belirtir. Özelliğin NULL olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementType`. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin türünü belirtir.

  Isteğe bağlı `elementInteger`. @No__t_0 `Array` ve `elementType` `Number` ise, bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. Dizideki öğelerin tamsayılar olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementDomElement`. Bu öznitelik kullanım dışıdır; `elementType` özniteliği bu özniteliğin üzerine gelir. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin DOM öğeleri olup olmadığını belirtir. Öğelerin DOM öğeleri olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `elementDomElement` `true` olarak ayarlandıysa, IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `elementMayBeNull`. @No__t_0 `Array`, dizideki öğelerin null olarak ayarlanamayacağını belirtir. Dizideki öğelerin null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `locid`. Özelliği ile ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki `name` öznitelik değerine karşılık gelir. Tanımlayıcı türü [\<loc >](../ide/loc-javascript.md) öğesinde belirtilen biçime bağlıdır.

  Isteğe bağlı `description`. Özelliğin açıklaması.

## <a name="remarks"></a>Açıklamalar
 ECMAScript 5 özellikleri [\<summary >](../ide/summary-javascript.md) öğesini kullanır.

 @No__t_1 veya `set` işlevinden hemen önce `<value>` öğesini kullanın.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir `get` işlevinde `<value>` öğesinin nasıl kullanılacağını gösterir.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
