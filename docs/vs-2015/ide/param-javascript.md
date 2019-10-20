---
title: '&lt;param &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670354"
---
# <a name="ltparamgt-javascript"></a>&lt;param &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlev veya yöntemdeki bir parametre için belge bilgilerini belirtir.

## <a name="syntax"></a>Sözdizimi

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>Parametreler
 `name` gerekiyor. Parametrenin adı.

 Isteğe bağlı `type`. Parametrenin veri türü. Tür aşağıdakilerden biri olabilir:

- ECMAScript 5 belirtiminde `Number` ve `Object` gibi bir ECMAScript dil türü.

- @No__t_0, `Window` ve `Document` gibi bir DOM nesnesi.

- JavaScript Oluşturucu işlevi.

  Isteğe bağlı `integer`. @No__t_0 `Number`, parametrenin bir tamsayı olup olmadığını belirtir. Parametrenin bir tamsayı olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `domElement`. Bu öznitelik kullanım dışıdır; `type` özniteliği bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen parametrenin bir DOM öğesi olup olmadığını belirtir. Parametrenin bir DOM öğesi olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `domElement` `true` olarak ayarlandıysa, IntelliSense, deyimin tamamlanmasını gerçekleştirirken belgelenen parametreyi bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `mayBeNull`. Belgelenmiş parametrenin null olarak ayarlanamayacağını belirtir. Parametrenin null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementType`. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin türünü belirtir.

  Isteğe bağlı `elementInteger`. @No__t_0 `Array` ve `elementType` `Number` ise, bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. Dizideki öğelerin tamsayılar olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementDomElement`. Bu öznitelik kullanım dışıdır; `elementType` özniteliği bu özniteliğin üzerine gelir. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin DOM öğeleri olup olmadığını belirtir. Öğelerin DOM öğeleri olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `elementDomElement` `true` olarak ayarlandıysa, IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `elementMayBeNull`. @No__t_0 `Array`, dizideki öğelerin null olarak ayarlanamayacağını belirtir. Dizideki öğelerin null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `locid`. Parametresiyle ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki `name` öznitelik değerine karşılık gelir. Tanımlayıcı türü [\<loc >](../ide/loc-javascript.md) öğesinde belirtilen biçime bağlıdır.

  Isteğe bağlı `parameterArray`. @No__t_0 işlevinde desteklenen yinelenen parametrelere benzer şekilde, belgelenen parametrenin işlev çağrısında tekrarlanıp tekrarlanamayacağını belirtir. Parametrenin tekrarlanabilir olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `optional`. Çağıran işlevde belgelenen parametrenin isteğe bağlı olup olmadığını belirtir. Parametrenin isteğe bağlı olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın.

  Isteğe bağlı `value`. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmesi gereken kodu belirtir. Parametre türü tanımsız olduğunda tür bilgilerini sağlamak için bu özniteliği kullanabilirsiniz. Örneğin, parametre türünü sayı olarak değerlendirmek için `value=’1’` kullanabilirsiniz.

  Isteğe bağlı `description`. Parametrenin açıklaması.

## <a name="remarks"></a>Açıklamalar
 Tek gerekli öznitelik `name`. Diğer tüm öznitelikler isteğe bağlıdır.

 [@No__t_1summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)ve [\<returns >](../ide/returns-javascript.md)gibi işlevlere açıklama eklemek için kullanılan öğeler, herhangi bir deyimden önce işlev gövdesine yerleştirilmelidir.

 Aynı ada sahip birden çok `<param>` öğesi varsa, `<param>` öğelerinden biri kullanılır ve gereksiz öğeler yok sayılır. Hangi öğenin kullanıldığını belirleyen davranış tanımlı değildir. @No__t_0 varolmayan bir parametreye başvuruyorsa, öğe yok sayılır.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `<param>` öğesinin nasıl kullanılacağını gösterir.

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

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
