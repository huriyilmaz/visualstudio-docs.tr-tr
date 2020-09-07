---
title: Adlandırma Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45eb7442278d783b2663da2ba8587bea38632fa1
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509009"
---
# <a name="naming-warnings"></a>Adlandırma Uyarıları

Adlandırma uyarıları, .NET Tasarım Yönergelerinin adlandırma kurallarına uygunluğunu destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1700: Sabit listesi değerlerini 'Reserved' olarak adlandırmayın](../code-quality/ca1700.md)|Bu kural, "ayrılmış" içeren bir ada sahip numaralandırma üyesi şu anda kullanılmamaktadır ancak yeniden adlandırılabilir veya gelecekteki bir sürüme kaldırıldığını varsayar. Üye kaldırma veya yeniden adlandırma bölünmesi farklıdır.|
|[CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707.md)|Kural gereği, tanımlayıcı adlar alt çizgi (_) karakterini içermez. Bu kural ad alanlarını, türleri, üyeleri ve parametreleri denetler.|
|[CA1708: Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır](../code-quality/ca1708.md)|Ortak dil çalışma zamanı hedef dilleri büyük/küçük harf duyarlı olması gerekmediğinden ad alanları, türler, üyeler ve parametreler için tanımlayıcılar yalnızca büyük/küçük harfe göre farklılık göstermeyebilir.|
|[CA1710: Tanımlayıcılar doğru soneke sahip olmalıdır](../code-quality/ca1710.md)|Kural gereği, belirli temel türleri genişleten veya belirli arabirimleri ya da bu türlerden türetilmiş türleri uygulayan türlerin adları, temel tür veya arabirimle ilişkili bir soneke sahiptir.|
|[CA1711: Tanımlayıcılar yanlış sonek içermemelidir](../code-quality/ca1711.md)|Kural gereği, yalnızca, belirli temel türleri genişleten veya bazı arabirimleri ya da bu türlerinden türetilmiş türleri uygulayan tür adları belirli ayrılmış öneklerle bitmelidir. Diğer tür adları aşağıdaki ayrılmış sonekleri kullanmamalı.|
|[CA1712: Sabit listesi değerlerine tür adını önek olarak eklemeyin](../code-quality/ca1712.md)|Tür bilgilerinin geliştirme araçları tarafından sağlanması beklendiğinden, numaralandırma üyelerinin adlarına tür adı ön eki uygulanmaz.|
|[CA1713: Olaylar önce ya da sonra önekine sahip olmamalıdır](../code-quality/ca1713.md)|Olay adı "Önce" veya "Sonra" ile başlar. Belirli bir sırayla ilgili olayları adlandırmak için şimdiki veya geçmiş zamanı göreceli konumun sıralı eylemlerini belirtmek için kullanın.|
|[CA1714: Bayrak sabit listeleri çoğul adlara sahip olmalıdır](../code-quality/ca1714.md)|Genel numaralandırmanın System. FlagsAttribute özniteliği ve adı "s" ile bitmiyor. FlagsAttribute ile işaretlenen türlerin, öznitelik birden fazla değerin belirtibileceğini gösterdiği için çoğul olan adlara sahip olması gerekir.|
|[CA1715: Tanımlayıcılar doğru ön eke sahip olmalıdır](../code-quality/ca1715.md)|Dışarıdan görünen bir arabirimin adı, büyük bir "I" ile başlamıyor.  Dışarıdan görünen bir tür veya yöntemde genel tür parametresinin adı, büyük bir "T" ile başlamıyor.|
|[CA1716: Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir](../code-quality/ca1716.md)|Ad alanı adı veya tür adı ayrılmış anahtar sözcük bir programlama dili ile eşleşir. Tanımlayıcı adı ve türleri için ortak dil çalışma zamanı, hedef diller tarafından tanımlanan anahtar sözcüklerle aynı değildir.|
|[CA1717: Yalnızca FlagsAttribute sabit listeleri çoğul adlara sahip olmalıdır](../code-quality/ca1717.md)|Adlandırma kuralları numaralandırma için adlandırma aynı anda birden fazla numaralandırma değeri olduğunu gösterir.|
|[CA1720: Tanımlayıcılar tür adları içermemelidir](../code-quality/ca1720.md)|Parametre adı dışarıdan görünen üye, veri türü adını içerir ya da açıkça görünen üyenin adı dil özellikli veri türü adı içerir.|
|[CA1721: Özellik adları get metotları ile eşleşmemelidir](../code-quality/ca1721.md)|Ortak veya korumalı bir üye adı "Get" ile başlar ve aksi durumda ortak veya korumalı özellik adıyla eşleşir. "Get" yöntemlerinin ve özelliklerinin açıkça işlevlerinden ayırt edilebilen adları olması gerekir.|
|[CA1724: Tür adları ad alanları ile eşleşmemelidir](../code-quality/ca1724.md)|Tür adları .NET ad alanlarının adlarıyla eşleşmemelidir. Bu kuralın ihlali, kitaplığın kullanılabilirliğini azaltabilir.|
|[CA1725: Parametre adları temel bildirimle eşleşmemelidir](../code-quality/ca1725.md)|Parametreyi geçersiz kılma hiyerarşisinde tutarlı adlandırma yöntemini geçersiz kılmaları kullanılabilirliği artırır. Temel bildirim alanındaki addan farklı türetilmiş yöntem parametre adı taban yöntemini geçersiz kılma veya yeni aşırı yöntemin yöntem olup olmadığı hakkında karışıklığa neden olabilir.|
