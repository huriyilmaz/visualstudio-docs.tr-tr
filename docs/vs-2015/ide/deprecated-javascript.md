---
title: '&lt;kullanım dışı &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665813"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;kullanım dışı &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım dışı bırakılan bir işlevi veya yöntemi belirtir.

## <a name="syntax"></a>Söz dizimi

```
<deprecated
    type="deprecate|remove"
    locid="descriptionID">description
</deprecated>
```

#### <a name="parameters"></a>Parametreler
 `type` Seçim. İşlevin veya yöntemin gelecekteki bir sürümde kaldırılıp kaldırılameyeceğini veya işlevin ya da yöntemin zaten kaldırılıp kaldırılmadığını ve bunun bir hatayla sonuçlanabileceğini belirtir. `deprecate`İşlevin veya yöntemin sonraki bir sürümde kaldırılacağını belirtmek için olarak ayarlayın. `remove`İşlev veya metodun zaten kaldırılmış olduğunu belirtmek için olarak ayarlayın.

 `locid` Seçim. İşlev veya yöntem hakkında yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da `name` OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki öznitelik değerine karşılık gelir. Tanımlayıcı türü, öğesinde belirtilen biçime bağlıdır [\<loc>](../ide/loc-javascript.md) .

 `description` Seçim. Kullanım dışı bırakılan işlev veya metodun açıklaması.

## <a name="remarks"></a>Açıklamalar
 Dahil olmak üzere işlevleri Not eklemek için kullanılan öğelerin, `<deprecated>` herhangi bir deyimden önce işlev gövdesine yerleştirilmesi gerekir. Bir işlevi kullanım dışı olarak işaretlediğinizde öğesini öğesiyle değiştirmeniz önerilir [\<summary>](../ide/summary-javascript.md) `<deprecated>` .

## <a name="example"></a>Örnek
 Aşağıdaki kod öğesinin nasıl kullanılacağını gösterir `<deprecated>` .

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
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
