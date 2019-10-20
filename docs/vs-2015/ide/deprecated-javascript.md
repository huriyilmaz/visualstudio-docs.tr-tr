---
title: '&lt;deprecated &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 343f3ebe4bea7ee999f60741c189f35defb0ac7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665813"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım dışı bırakılan bir işlevi veya yöntemi belirtir.

## <a name="syntax"></a>Sözdizimi

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Parametreler
 Isteğe bağlı `type`. İşlevin veya yöntemin gelecekteki bir sürümde kaldırılıp kaldırılameyeceğini veya işlevin ya da yöntemin zaten kaldırılıp kaldırılmadığını ve bunun bir hatayla sonuçlanabileceğini belirtir. İşlevin veya yöntemin gelecekteki bir sürümde kaldırılacağını belirtmek için `deprecate` olarak ayarlayın. İşlevin veya metodun zaten kaldırılmış olduğunu belirtmek için `remove` olarak ayarlayın.

 Isteğe bağlı `locid`. İşlev veya yöntem hakkında yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki `name` öznitelik değerine karşılık gelir. Tanımlayıcı türü [\<loc >](../ide/loc-javascript.md) öğesinde belirtilen biçime bağlıdır.

 Isteğe bağlı `description`. Kullanım dışı bırakılan işlev veya metodun açıklaması.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 içeren işlevlere Not eklemek için kullanılan öğeler, herhangi bir deyimden önce işlev gövdesine yerleştirilmelidir. Bir işlevi kullanım dışı olarak işaretlediğinizde, [\<summary >](../ide/summary-javascript.md) öğesini `<deprecated>` öğesiyle değiştirmenizi öneririz.

## <a name="example"></a>Örnek
 Aşağıdaki kod `<deprecated>` öğesinin nasıl kullanılacağını gösterir.

```javascript
function areaFunction(radiusParam) {
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
