---
title: '&lt;returns &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669962"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlev veya yöntem çağrısının sonucu için belge bilgilerini belirtir.

## <a name="syntax"></a>Sözdizimi

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>Parametreler
 Isteğe bağlı `type`. Dönüş değerinin veri türü. Tür aşağıdakilerden biri olabilir:

- ECMAScript 5 belirtiminde `Number` ve `Object` gibi bir ECMAScript dil türü.

- @No__t_0, `Window` ve `Document` gibi bir DOM nesnesi.

- JavaScript Oluşturucu işlevi.

  Isteğe bağlı `integer`. @No__t_0 `Number`, dönüş değerinin bir tamsayı olup olmadığını belirtir. Dönüş değerinin bir tamsayı olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `domElement`. Bu öznitelik kullanım dışıdır; `type` özniteliği bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen dönüş değerinin bir DOM öğesi olup olmadığını belirtir. Dönüş değerinin bir DOM öğesi olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `domElement` `true` olarak ayarlanırsa, IntelliSense, ifade tamamlama gerçekleştirirken belgelenen dönüş değerini bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `mayBeNull`. Belgelenmiş dönüş değerinin null olarak ayarlanamayacağını belirtir. Dönüş değerinin null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementType`. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin türünü belirtir.

  Isteğe bağlı `elementInteger`. @No__t_0 `Array` ve `elementType` `Number` ise, bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. Dizideki öğelerin tamsayılar olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementDomElement`. Bu öznitelik kullanım dışıdır; `elementType` özniteliği bu özniteliğin üzerine gelir. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin DOM öğeleri olup olmadığını belirtir. Öğelerin DOM öğeleri olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `elementDomElement` `true` olarak ayarlandıysa, IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `elementMayBeNull`. @No__t_0 `Array`, dizideki öğelerin null olarak ayarlanamayacağını belirtir. Dizideki öğelerin null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `locid`. Dönüş değeri hakkındaki yerelleştirme bilgilerine yönelik tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki `name` öznitelik değerine karşılık gelir. Tanımlayıcı türü, [\<loc >](../ide/loc-javascript.md) etiketinde belirtilen biçime bağlıdır.

  Isteğe bağlı `value`. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmesi gereken kodu belirtir. Örneğin, `Promise` gibi zaman uyumsuz geri çağrılar için IntelliSense sağlamak üzere bu özniteliği kullanabilirsiniz. @No__t_1 öğesi ile `value` özniteliğini kullanmak, uzun kod yürütmeyi atlayarak IntelliSense performansını iyileştirebilir.

  Isteğe bağlı `description`. Dönüş değerinin açıklaması.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 öğesi, hiçbir deyimden önce işlev gövdesine yerleştirilmelidir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `<returns>` öğesinin nasıl kullanılacağını gösterir.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
