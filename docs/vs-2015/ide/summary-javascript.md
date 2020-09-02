---
title: '&lt;Özet &gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646844"
---
# <a name="ltsummarygt-javascript"></a>&lt;Özet &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlev veya yöntem için açıklama belirtir.

## <a name="syntax"></a>Söz dizimi

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Parametreler
 `locid` Seçim. İşlev veya yöntem hakkında yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da `name` OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki öznitelik değerine karşılık gelir. Tanımlayıcı türü, öğesinde belirtilen biçime bağlıdır [\<loc>](../ide/loc-javascript.md) .

 `description` Seçim. İşlevin veya metodun açıklaması.

## <a name="remarks"></a>Açıklamalar
 , Ve içeren işlevleri Not eklemek için kullanılan öğelerin [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) [\<returns>](../ide/returns-javascript.md) herhangi bir deyimden önce işlev gövdesine yerleştirilmesi gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki kod öğesinin nasıl kullanılacağını gösterir `<summary>` .

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Ayrıca Bkz.
 [XML belge açıklamaları](../ide/xml-documentation-comments-javascript.md)
