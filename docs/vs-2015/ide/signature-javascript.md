---
title: '&lt;signature &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671125"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşırı yüklenmiş işlevlere yönelik belgeler sağlamak üzere bir işlev veya yöntem için ilgili öğelerin bir kümesini gruplandırır.

## <a name="syntax"></a>Sözdizimi

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>Parametreler
 Isteğe bağlı `externalid`. [@No__t_2loc >](../ide/loc-javascript.md) öğesi için `format` özniteliği `vsdoc` ise, bu öznitelik IMZAYLA ilişkili XML kodunu bulmak için kullanılan üye kimliğini belirtir. @No__t_0 özniteliğinin aksine, bu öznitelik, bu KIMLIĞE sahip olan üyenin tüm öğelerinin yüklü olması gerektiğini belirtir. XML kodunda bulunan ilişkili açıklama bilgileri de İmzada belirtilen öğelerle birleştirilir. Bu, `<capability>` gibi ek öğeleri kaynak dosyasında belirtmeden, sepet dosyasında belirtmenize olanak sağlar. `externalid`, isteğe bağlı bir özniteliktir.

 Isteğe bağlı `externalFile`. @No__t_0 bulunacak dosyanın adını belirtir. @No__t_0 yoksa bu öznitelik yoksayılır. Bu, isteğe bağlı bir özniteliktir. Varsayılan değer,. js yerine. xml dosya uzantısıyla geçerli dosyanın adıdır. Varsayılan olarak, yerelleştirme için yönetilen kaynak arama kuralları dosyayı bulmak için kullanılır.

 Isteğe bağlı `helpKeyword`. F1 Yardım anahtar sözcüğü.

 Isteğe bağlı `locid`. Alanla ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki `name` öznitelik değerine karşılık gelir. Tanımlayıcı türü, [\<loc >](../ide/loc-javascript.md) etiketinde belirtilen biçime bağlıdır.

## <a name="remarks"></a>Açıklamalar
 . Js dosyasındaki her bir aşırı yüklenmiş işlev açıklaması için bir `<signature>` öğesi kullanın veya belirtilen her dış üye KIMLIĞI için bir `<signature>` öğesi kullanın.

 @No__t_0 öğesi, hiçbir deyimden önce işlev gövdesine yerleştirilmelidir. @No__t_5returns öğesi ile [\<summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)veya [>](../ide/returns-javascript.md) öğelerini kullanırken, diğer öğeleri `<signature>` bloğunun içine yerleştirin.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `<signature>` öğesinin nasıl kullanılacağını gösterir.

```javascript
// Use of <signature> with externalid.
// Requires use of the <loc> tag to identify the external functions.
function illuminate(light) {
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>
    ///   <param name='light' type='Number' />
    /// </signature>
}

// Use of <signature> for overloads implemented in JavaScript.
function add(a, b) {
    /// <signature>
    /// <summary>function summary 1</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 2 – differ by number of params</summary>
    /// <param name="a" type="Number">Only 1 parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 3 – differ by parameter type</summary>
    /// <param name="a" type="Number">Number parameter</param>
    /// <param name="b" type="String">String parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 4 – differ by return type</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="String" />
    /// </signature>

    return a + b;
}
```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
