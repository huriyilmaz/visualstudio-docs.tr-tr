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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670354"
---
# <a name="ltparamgt-javascript"></a>&lt;param &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlev veya yöntemdeki bir parametre için belge bilgilerini belirtir.

## <a name="syntax"></a>Söz dizimi

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
 `name` Gerekli. Parametrenin adı.

 `type` Seçim. Parametrenin veri türü. Tür aşağıdakilerden biri olabilir:

- ECMAScript 5 belirtiminde, ve gibi bir ECMAScript dil türü `Number` `Object` .

- , Ve gibi bir DOM nesnesi `HTMLElement` `Window` `Document` .

- JavaScript Oluşturucu işlevi.

  `integer` Seçim. İse `type` , `Number` parametrenin bir tamsayı olup olmadığını belirtir. `true`Parametresinin bir tamsayı olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `domElement` Seçim. Bu öznitelik kullanım dışıdır; `type` öznitelik bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen parametrenin bir DOM öğesi olup olmadığını belirtir. `true`Parametresinin BIR DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `type`Özniteliği ayarlanmamışsa ve `domElement` olarak ayarlanırsa `true` , IntelliSense, ifade tamamlama gerçekleştirirken belgelenen parametreyi bir olarak değerlendirir `HTMLElement` .

  `mayBeNull` Seçim. Belgelenmiş parametrenin null olarak ayarlanamayacağını belirtir. `true`Parametresinin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementType` Seçim. `type`İse `Array` , bu öznitelik dizideki öğelerin türünü belirtir.

  `elementInteger` Seçim. , `type` Ve ise, `Array` `elementType` `Number` Bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. `true`Dizideki öğelerin tamsayılar olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementDomElement` Seçim. Bu öznitelik kullanım dışıdır; `elementType` öznitelik bu özniteliğin üzerine gelir. `type`İse `Array` , bu öznitelik DIZIDEKI öğelerin DOM öğeleri olup olmadığını belirtir. `true`ÖĞELERIN DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `elementType`Özniteliği ayarlanmamışsa ve `elementDomElement` olarak ayarlandıysa `true` , IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir olarak değerlendirir `HTMLElement` .

  `elementMayBeNull` Seçim. `type`İse, `Array` dizideki öğelerin null olarak ayarlanamayacağını belirtir. `true`Dizideki öğelerin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `locid` Seçim. Parametresiyle ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da `name` OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki öznitelik değerine karşılık gelir. Tanımlayıcı türü, öğesinde belirtilen biçime bağlıdır [\<loc>](../ide/loc-javascript.md) .

  `parameterArray` Seçim. İşlev çağrısında belgelenmiş parametrenin yinelenemeyeceğini, işlevde desteklenen yinelenen parametrelere benzer şekilde belirtir `String.format` . `true`Parametresinin tekrarlanabilir olduğunu belirtmek için olarak ayarlayın; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `optional` Seçim. Çağıran işlevde belgelenen parametrenin isteğe bağlı olup olmadığını belirtir. `true`Parametresinin isteğe bağlı olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` .

  `value` Seçim. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmesi gereken kodu belirtir. Parametre türü tanımsız olduğunda tür bilgilerini sağlamak için bu özniteliği kullanabilirsiniz. Örneğin, `value=’1’` parametre türünü sayı olarak değerlendirmek için kullanabilirsiniz.

  `description` Seçim. Parametrenin açıklaması.

## <a name="remarks"></a>Açıklamalar
 Yalnızca gerekli olan öznitelik `name` . Diğer tüm öznitelikler isteğe bağlıdır.

 , Ve gibi işlevleri Not eklemek için kullanılan öğelerin, [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) [\<returns>](../ide/returns-javascript.md) herhangi bir deyimden önce işlev gövdesine yerleştirilmesi gerekir.

 `<param>`Aynı ada sahip birden fazla öğe varsa, `<param>` öğelerinden biri kullanılır ve gereksiz öğeler yok sayılır. Hangi öğenin kullanıldığını belirleyen davranış tanımlı değildir. `name`Varolmayan bir parametreye başvuruyorsa, öğe yok sayılır.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, öğesinin nasıl kullanılacağını gösterir `<param>` .

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
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
