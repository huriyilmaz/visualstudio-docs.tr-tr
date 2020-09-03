---
title: '&lt;imza &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671125"
---
# <a name="ltsignaturegt-javascript"></a>&lt;imza &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aşırı yüklenmiş işlevlere yönelik belgeler sağlamak üzere bir işlev veya yöntem için ilgili öğelerin bir kümesini gruplandırır.

## <a name="syntax"></a>Söz dizimi

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>Parametreler
 `externalid` Seçim. `format`Öğesi için özniteliği [\<loc>](../ide/loc-javascript.md) ise `vsdoc` , bu ÖZNITELIK imzayla ilişkili XML kodunu bulmak IÇIN kullanılan üye kimliğini belirtir. Özniteliğin aksine `locid` , bu öznitelik bu kimliğe sahip olan üyenin tüm öğelerinin yüklü olması gerektiğini belirtir. XML kodunda bulunan ilişkili açıklama bilgileri de İmzada belirtilen öğelerle birleştirilir. Bu, `<capability>` kaynak dosyada belirtmeden, gibi ek öğeler belirtmenize olanak sağlar. `externalid` isteğe bağlı bir özniteliktir.

 `externalFile` Seçim. İçinde bulunacak dosyanın adını belirtir `externalid` . Bu öznitelik, yoksa yok sayılır `externalid` . Bu, isteğe bağlı bir özniteliktir. Varsayılan değer,. js yerine. xml dosya uzantısıyla geçerli dosyanın adıdır. Varsayılan olarak, yerelleştirme için yönetilen kaynak arama kuralları dosyayı bulmak için kullanılır.

 `helpKeyword` Seçim. F1 Yardım anahtar sözcüğü.

 `locid` Seçim. Alanla ilgili yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da `name` OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki öznitelik değerine karşılık gelir. Tanımlayıcı türü, etiketinde belirtilen biçime bağlıdır [\<loc>](../ide/loc-javascript.md) .

## <a name="remarks"></a>Açıklamalar
 `<signature>`. Js dosyasındaki her bir aşırı yüklenmiş işlev açıklaması için bir öğe kullanın veya `<signature>` belirtilen her dış üye kimliği için bir öğe kullanın.

 `<signature>`Öğe, hiçbir deyimden önce işlev gövdesine yerleştirilmelidir. [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) [\<returns>](../ide/returns-javascript.md) Öğesi ile, veya öğelerini kullanırken `<signature>` , diğer öğeleri bloğunun içine yerleştirin `<signature>` .

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, öğesinin nasıl kullanılacağını gösterir `<signature>` .

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
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
