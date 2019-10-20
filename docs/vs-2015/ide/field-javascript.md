---
title: '&lt;field &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663854"
---
# <a name="ltfieldgt-javascript"></a>&lt;field &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir nesne ya da bir nesnede tanımlı üye için bir açıklama dahil belge bilgilerini belirtir.

## <a name="syntax"></a>Sözdizimi

```
<field name="fieldName" static="true|false"
    type="FieldType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID"
    value="code">description
</field>
```

#### <a name="parameters"></a>Parametreler
 alanın veya üyenin adını `name`. Bir Oluşturucu işlevinde `<field>` öğesi kullanıldığında, `name` gereklidir ve etiketin geçerli olduğu üyeyi tanımlar. @No__t_0 öğesi bir alana doğrudan açıklama eklendiğinde, bu öznitelik yok sayılır ve Visual Studio tarafından kullanılan ad, kaynak kodundaki gerçek alanın adıdır.

 Isteğe bağlı `static`. Alanın Oluşturucu işlevinin bir üyesi mi yoksa Oluşturucu işlevi tarafından döndürülen nesnenin bir üyesi mi olduğunu belirtir. Alanı Oluşturucu işlevinin bir üyesi olarak değerlendirmek için `true` olarak ayarlayın. Alanı, Oluşturucu işlevinin döndürdüğü nesnenin bir üyesi olarak değerlendirmek için `false` olarak ayarlayın.

 Isteğe bağlı `type`. Alanın veri türü. Tür aşağıdakilerden biri olabilir:

- ECMAScript 5 belirtiminde `Number` ve `Object` gibi bir ECMAScript dil türü.

- @No__t_0, `Window` ve `Document` gibi bir DOM nesnesi.

- JavaScript Oluşturucu işlevi.

  Isteğe bağlı `integer`. @No__t_0 `Number`, alanın bir tamsayı olup olmadığını belirtir. Alanın bir tamsayı olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `domElement`. Bu öznitelik kullanım dışıdır; `type` özniteliği bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen alanın bir DOM öğesi olup olmadığını belirtir. Alanın bir DOM öğesi olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `domElement` `true` olarak ayarlandıysa, IntelliSense, ifade tamamlama gerçekleştirirken belgelenen alanı bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `mayBeNull`. Belgelenen alanın null olarak ayarlanamayacağını belirtir. Alanın null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementType`. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin türünü belirtir.

  Isteğe bağlı `elementInteger`. @No__t_0 `Array` ve `elementType` `Number` ise, bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. Dizideki öğelerin tamsayılar olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `elementDomElement`. Bu öznitelik kullanım dışıdır; `elementType` özniteliği bu özniteliğin üzerine gelir. @No__t_0 `Array` ise, bu öznitelik dizideki öğelerin DOM öğeleri olup olmadığını belirtir. Öğelerin DOM öğeleri olduğunu belirtmek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. @No__t_0 özniteliği ayarlanmamışsa ve `elementDomElement` `true` olarak ayarlandıysa, IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir `HTMLElement` olarak değerlendirir.

  Isteğe bağlı `elementMayBeNull`. @No__t_0 `Array`, dizideki öğelerin null olarak ayarlanamayacağını belirtir. Dizideki öğelerin null olarak ayarlanabileceği göstermek için `true` olarak ayarlayın; Aksi takdirde, `false` olarak ayarlayın. Varsayılan değer `false` şeklindedir. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  Isteğe bağlı `helpKeyword`. F1 Yardım anahtar sözcüğü.

  Isteğe bağlı `locid`. Alanla ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki `name` öznitelik değerine karşılık gelir. Tanımlayıcı türü, [\<loc >](../ide/loc-javascript.md) etiketinde belirtilen biçime bağlıdır.

  Isteğe bağlı `value`. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmesi gereken kodu belirtir. @No__t_0 için bu öznitelik, Oluşturucu işlevleri için desteklenir, ancak nesne değişmezleri için desteklenmez. Bu özniteliği, alan türü tanımsız olduğunda tür bilgilerini sağlamak için kullanabilirsiniz. Örneğin, `value=’1’` alan türünü sayı olarak değerlendirmek için kullanabilirsiniz.

  Isteğe bağlı `description`. Alan için bir açıklama.

## <a name="remarks"></a>Açıklamalar
 Bir Oluşturucu işlevindeki bir alanı belgeyorsanız `name` özniteliği gereklidir. Tüm diğer senaryolar için `<field>` öğesi için tüm öznitelikler isteğe bağlıdır.

 Bir Oluşturucu işlevini belgeliyoruz, `<field>` öğesi alan bildiriminden hemen önce görünmelidir. @No__t_0 özniteliği, kaynak kodunda kullanılan alan adıyla eşleşmelidir. Nesne üyeleri için, nesne üye bildiriminden hemen önce `<field>` öğesi görünürse `name` özniteliği atlanabilir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `<field>` öğesinin nasıl kullanılacağını gösterir.

```javascript
// Use of <field> in an object definition.
var Rectangle = {
    /// <field type='Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type='Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}

// Use of <field> in a constructor function.
// The name attribute is required.
function Engine() {
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
    this.HorsePower = 150;
}
```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `true` olarak ayarlanan `static` özniteliği ile `<field>` öğesinin nasıl kullanılacağını gösterir.

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `false` olarak ayarlanan `static` özniteliği ile `<field>` öğesinin nasıl kullanılacağını gösterir.

```javascript
function Engine() {
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>
}

Engine.HorsePower = 140;
var eng = new Engine();
// IntelliSense on the field is available here.
eng.

```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `value` özniteliğiyle `<field>` öğesinin nasıl kullanılacağını gösterir.

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
