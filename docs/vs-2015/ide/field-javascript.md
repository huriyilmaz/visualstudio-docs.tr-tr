---
title: '&lt;alan &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663854"
---
# <a name="ltfieldgt-javascript"></a>&lt;alan &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir nesne ya da bir nesnede tanımlı üye için bir açıklama dahil belge bilgilerini belirtir.

## <a name="syntax"></a>Söz dizimi

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
 `name` Alanın veya üyenin adı. `<field>`Öğesi bir Oluşturucu işlevinde kullanıldığında, `name` gereklidir ve etiketin geçerli olduğu üyeyi tanımlar. `<field>`Öğe bir alana doğrudan açıklama eklendiğinde, bu öznitelik yok sayılır ve Visual Studio tarafından kullanılan ad, kaynak kodundaki gerçek alanın adıdır.

 `static` Seçim. Alanın Oluşturucu işlevinin bir üyesi mi yoksa Oluşturucu işlevi tarafından döndürülen nesnenin bir üyesi mi olduğunu belirtir. `true`Alanı Oluşturucu işlevinin bir üyesi olarak değerlendirmek için olarak ayarlayın. Alanı, `false` Oluşturucu işlevinin döndürdüğü nesnenin bir üyesi olarak değerlendirmek için olarak ayarlayın.

 `type` Seçim. Alanın veri türü. Tür aşağıdakilerden biri olabilir:

- ECMAScript 5 belirtiminde, ve gibi bir ECMAScript dil türü `Number` `Object` .

- , Ve gibi bir DOM nesnesi `HTMLElement` `Window` `Document` .

- JavaScript Oluşturucu işlevi.

  `integer` Seçim. `type`İse `Number` alanın bir tamsayı olup olmadığını belirtir. `true`Alanın bir tamsayı olduğunu göstermek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `domElement` Seçim. Bu öznitelik kullanım dışıdır; `type` öznitelik bu özniteliğin üzerine gelir. Bu öznitelik, belgelenen alanın bir DOM öğesi olup olmadığını belirtir. `true`Alanın BIR DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `type`Özniteliği ayarlanmamışsa ve `domElement` olarak ayarlanırsa `true` , IntelliSense, ifade tamamlama gerçekleştirirken belgelenen alanı bir olarak değerlendirir `HTMLElement` .

  `mayBeNull` Seçim. Belgelenen alanın null olarak ayarlanamayacağını belirtir. `true`Alanın null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementType` Seçim. `type`İse `Array` , bu öznitelik dizideki öğelerin türünü belirtir.

  `elementInteger` Seçim. , `type` Ve ise, `Array` `elementType` `Number` Bu öznitelik dizideki öğelerin tamsayı olup olmadığını belirtir. `true`Dizideki öğelerin tamsayılar olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `elementDomElement` Seçim. Bu öznitelik kullanım dışıdır; `elementType` öznitelik bu özniteliğin üzerine gelir. `type`İse `Array` , bu öznitelik DIZIDEKI öğelerin DOM öğeleri olup olmadığını belirtir. `true`ÖĞELERIN DOM öğesi olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . `elementType`Özniteliği ayarlanmamışsa ve `elementDomElement` olarak ayarlandıysa `true` , IntelliSense deyimin tamamlanma sırasında dizideki her öğeyi bir olarak değerlendirir `HTMLElement` .

  `elementMayBeNull` Seçim. `type`İse, `Array` dizideki öğelerin null olarak ayarlanamayacağını belirtir. `true`Dizideki öğelerin null olarak ayarlanabileceği belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` . Varsayılan değer: `false`. Bu öznitelik, Visual Studio tarafından IntelliSense bilgilerini sağlamak için kullanılmaz.

  `helpKeyword` Seçim. F1 Yardım anahtar sözcüğü.

  `locid` Seçim. Alanla ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da `name` OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki öznitelik değerine karşılık gelir. Tanımlayıcı türü, etiketinde belirtilen biçime bağlıdır [\<loc>](../ide/loc-javascript.md) .

  `value` Seçim. İşlev kodunun kendisi yerine IntelliSense tarafından kullanılmak üzere değerlendirilmesi gereken kodu belirtir. İçin `<field>` , bu öznitelik Oluşturucu işlevleri için desteklenir, ancak nesne değişmezleri için desteklenmez. Bu özniteliği, alan türü tanımsız olduğunda tür bilgilerini sağlamak için kullanabilirsiniz. Örneğin, `value=’1’` alan türünü sayı olarak değerlendirmek için kullanabilirsiniz.

  `description` Seçim. Alan için bir açıklama.

## <a name="remarks"></a>Açıklamalar
 `name`Bir Oluşturucu işlevindeki bir alanı belgeyorsanız öznitelik gereklidir. Tüm diğer senaryolar için, öğe için tüm öznitelikler `<field>` isteğe bağlıdır.

 Bir Oluşturucu işlevini belgeliyoruz, `<field>` öğe, alan bildiriminden hemen önce gelmelidir. `name`Öznitelik, kaynak kodunda kullanılan alan adıyla eşleşmelidir. Nesne üyeleri için öğe, `name` `<field>` nesne üye bildiriminden hemen önce görünürse özniteliği atlanabilir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, öğesinin nasıl kullanılacağını gösterir `<field>` .

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
 Aşağıdaki örnek, `<field>` öğesinin `static` olarak ayarlanan özniteliğiyle birlikte nasıl kullanılacağını gösterir `true` .

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `<field>` öğesinin `static` olarak ayarlanan özniteliğiyle birlikte nasıl kullanılacağını gösterir `false` .

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
 Aşağıdaki örnek, öğesinin özniteliğiyle nasıl kullanılacağını gösterir `<field>` `value` .

```javascript
function calculator(a) {
    /// <field name='f' value='1'/>
}
new calculator().f.   // Completion list for a Number.

```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
