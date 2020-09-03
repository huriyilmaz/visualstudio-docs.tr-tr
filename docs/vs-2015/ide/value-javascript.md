---
title: '&lt;değer &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656393"
---
# <a name="ltvaluegt-javascript"></a>&lt;değer &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`get`ECMAScript 3 özelliklerine yönelik belge bilgilerini ve `set` işlevleri belirtir.

## <a name="syntax"></a>Söz dizimi

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>Parametreler
 `type` Seçim. Özelliğin veri türü. Tür aşağıdakilerden biri olabilir:

- ECMAScript 5 belirtiminde, ve gibi bir ECMAScript dil türü `Number` `Object` .

- , Ve gibi bir DOM nesnesi `HTMLElement` `Window` `Document` .

- JavaScript Oluşturucu işlevi.

  `integer` Seçim. İse `type` , `Number` özelliğin bir tamsayı olup olmadığını belirtir. `true`Özelliğin bir tamsayı olduğunu göstermek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `domElement` Seçim. Bu öznitelik kullanım dışıdır; `type` öznitelik bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen özelliğin bir DOM öğesi olup olmadığını belirtir. `true`Özelliğin BIR DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `type`Özniteliği ayarlanmamışsa ve `domElement` olarak ayarlanırsa `true` , IntelliSense, `HTMLElement` ifade tamamlama gerçekleştirirken belgelenen özelliği olarak değerlendirir.

  `mayBeNull` Seçim. Belgelenmiş özelliğin NULL olarak ayarlanamayacağını belirtir. `true`Özelliğinin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementType` Seçim. `type`İse `Array` , bu öznitelik dizideki öğelerin türünü belirtir.

  `elementInteger` Seçim. , `type` Ve ise, `Array` `elementType` `Number` Bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. `true`Dizideki öğelerin tamsayılar olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementDomElement` Seçim. Bu öznitelik kullanım dışıdır; `elementType` öznitelik bu özniteliğin üzerine gelir. `type`İse `Array` , bu öznitelik DIZIDEKI öğelerin DOM öğeleri olup olmadığını belirtir. `true`ÖĞELERIN DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `elementType`Özniteliği ayarlanmamışsa ve `elementDomElement` olarak ayarlandıysa `true` , IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir olarak değerlendirir `HTMLElement` .

  `elementMayBeNull` Seçim. `type`İse, `Array` dizideki öğelerin null olarak ayarlanamayacağını belirtir. `true`Dizideki öğelerin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `locid` Seçim. Özelliği ile ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da `name` OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki öznitelik değerine karşılık gelir. Tanımlayıcı türü, öğesinde belirtilen biçime bağlıdır [\<loc>](../ide/loc-javascript.md) .

  `description` Seçim. Özelliğin açıklaması.

## <a name="remarks"></a>Açıklamalar
 ECMAScript 5 özellikleri öğesini kullanır [\<summary>](../ide/summary-javascript.md) .

 `<value>`Veya işlevinden hemen önce öğesini kullanın `get` `set` .

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `<value>` bir işlev üzerinde öğesinin nasıl kullanılacağını gösterir `get` .

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
