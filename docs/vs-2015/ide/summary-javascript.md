---
title: '&lt;summary &gt; (JavaScript) | Microsoft Docs'
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646844"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary &gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir işlev veya yöntem için açıklama belirtir.

## <a name="syntax"></a>Sözdizimi

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Parametreler
 Isteğe bağlı `locid`. İşlev veya yöntem hakkında yerelleştirme bilgileri için tanımlayıcı. Tanımlayıcı, bir üye KIMLIĞI ya da OpenAjax meta verileri tarafından tanımlanan bir ileti grubundaki `name` öznitelik değerine karşılık gelir. Tanımlayıcı türü [\<loc >](../ide/loc-javascript.md) öğesinde belirtilen biçime bağlıdır.

 Isteğe bağlı `description`. İşlevin veya metodun açıklaması.

## <a name="remarks"></a>Açıklamalar
 [@No__t_1summary >](../ide/summary-javascript.md), [\<param >](../ide/param-javascript.md)ve [\<returns >](../ide/returns-javascript.md)dahil olmak üzere işlevleri Not eklemek için kullanılan öğeler, hiçbir deyimden önce işlev gövdesine yerleştirilmelidir.

## <a name="example"></a>Örnek
 Aşağıdaki kod `<summary>` öğesinin nasıl kullanılacağını gösterir.

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
 [XML Belge Açıklamaları](../ide/xml-documentation-comments-javascript.md)
