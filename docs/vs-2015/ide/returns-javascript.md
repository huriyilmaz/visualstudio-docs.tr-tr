---
title: '&lt;döndürür &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669962"
---
# <a name="ltreturnsgt-javascript"></a>&lt;döndürür &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlev veya yöntem çağrısının sonucu için belge bilgilerini belirtir.

## <a name="syntax"></a>Söz dizimi

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>Parametreler
 `type` Seçim. Dönüş değerinin veri türü. Tür aşağıdakilerden biri olabilir:

- ECMAScript 5 belirtiminde, ve gibi bir ECMAScript dil türü `Number` `Object` .

- , Ve gibi bir DOM nesnesi `HTMLElement` `Window` `Document` .

- JavaScript Oluşturucu işlevi.

  `integer` Seçim. `type`İse, `Number` dönüş değerinin bir tamsayı olup olmadığını belirtir. `true`Dönüş değerinin bir tamsayı olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `domElement` Seçim. Bu öznitelik kullanım dışıdır; `type` öznitelik bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen dönüş değerinin bir DOM öğesi olup olmadığını belirtir. `true`Dönüş değerinin BIR DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `type`Özniteliği ayarlanmamışsa ve `domElement` olarak ayarlanırsa `true` , IntelliSense, `HTMLElement` ifade tamamlama gerçekleştirirken belgelenen dönüş değerini bir olarak değerlendirir.

  `mayBeNull` Seçim. Belgelenmiş dönüş değerinin null olarak ayarlanamayacağını belirtir. `true`Dönüş değerinin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementType` Seçim. `type`İse `Array` , bu öznitelik dizideki öğelerin türünü belirtir.

  `elementInteger` Seçim. , `type` Ve ise, `Array` `elementType` `Number` Bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. `true`Dizideki öğelerin tamsayılar olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementDomElement` Seçim. Bu öznitelik kullanım dışıdır; `elementType` öznitelik bu özniteliğin üzerine gelir. `type`İse `Array` , bu öznitelik DIZIDEKI öğelerin DOM öğeleri olup olmadığını belirtir. `true`ÖĞELERIN DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `elementType`Özniteliği ayarlanmamışsa ve `elementDomElement` olarak ayarlandıysa `true` , IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir olarak değerlendirir `HTMLElement` .

  `elementMayBeNull` Seçim. `type`İse, `Array` dizideki öğelerin null olarak ayarlanamayacağını belirtir. `true`Dizideki öğelerin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `locid` Seçim. Dönüş değeri hakkındaki yerelleştirme bilgilerine yönelik tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da `name` OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki öznitelik değerine karşılık gelir. Tanımlayıcı türü, etiketinde belirtilen biçime bağlıdır [\<loc>](../ide/loc-javascript.md) .

  `value` Seçim. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmesi gereken kodu belirtir. Örneğin, gibi zaman uyumsuz geri çağrılar için IntelliSense sağlamak üzere bu özniteliği kullanabilirsiniz `Promise` . `value`Özniteliği öğesi ile kullanmak, `<returns>` uzun kod yürütmeyi atlayarak IntelliSense performansını iyileştirebilir.

  `description` Seçim. Dönüş değerinin açıklaması.

## <a name="remarks"></a>Açıklamalar
 `<returns>`Öğe, hiçbir deyimden önce işlev gövdesine yerleştirilmelidir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, öğesinin nasıl kullanılacağını gösterir `<returns>` .

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
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
