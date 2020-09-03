---
title: Uyarıları adlandırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03bc20d4bf39aa31865007e46e7ad3615f4b95bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655962"
---
# <a name="naming-warnings"></a>Adlandırma Uyarıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Adlandırma uyarıları, Tasarım Yönergelerinin adlandırma kurallarına uygunluğunu destekler [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Description|
|----------|-----------------|
|[CA1700: Sabit listesi değerlerini 'Reserved' olarak adlandırmayın](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Bu kural, "ayrılmış" içeren bir ada sahip numaralandırma üyesi şu anda kullanılmamaktadır ancak yeniden adlandırılabilir veya gelecekteki bir sürüme kaldırıldığını varsayar. Üye kaldırma veya yeniden adlandırma bölünmesi farklıdır.|
|[CA1713: Olaylar önce ya da sonra önekine sahip olmamalıdır](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Olay adı "Önce" veya "Sonra" ile başlar. Belirli bir sırayla ilgili olayları adlandırmak için şimdiki veya geçmiş zamanı göreceli konumun sıralı eylemlerini belirtmek için kullanın.|
|[CA1714: Bayrak sabit listeleri çoğul adlara sahip olmalıdır](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Genel numaralandırmanın System. FlagsAttribute özniteliği ve adı "s" ile bitmiyor. FlagsAttribute ile işaretlenen türlerin, öznitelik birden fazla değerin belirtibileceğini gösterdiği için çoğul olan adlara sahip olması gerekir.|
|[CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Dışarıdan görünen bir tanımlayıcı ad Microsoft yazım denetimi kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir.|
|[CA1708: Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Ortak dil çalışma zamanı hedef dilleri büyük/küçük harf duyarlı olması gerekmediğinden ad alanları, türler, üyeler ve parametreler için tanımlayıcılar yalnızca büyük/küçük harfe göre farklılık göstermeyebilir.|
|[CA1715: Tanımlayıcılar doğru ön eke sahip olmalıdır](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Dışarıdan görünen bir arabirimin adı, büyük bir "I" ile başlamıyor.  Dışarıdan görünen bir tür veya yöntemde genel tür parametresinin adı, büyük bir "T" ile başlamıyor.|
|[CA1720: Tanımlayıcılar tür adları içermemelidir](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Parametre adı dışarıdan görünen üye, veri türü adını içerir ya da açıkça görünen üyenin adı dil özellikli veri türü adı içerir.|
|[CA1722: Tanımlayıcılar yanlış ön ek içermemelidir](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Kural gereği, programlama öğelerinin belirli bir önek ile başlayan adları vardır.|
|[CA1711: Tanımlayıcılar yanlış sonek içermemelidir](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Kural gereği, yalnızca, belirli temel türleri genişleten veya bazı arabirimleri ya da bu türlerinden türetilmiş türleri uygulayan tür adları belirli ayrılmış öneklerle bitmelidir. Diğer tür adları aşağıdaki ayrılmış sonekleri kullanmamalı.|
|[CA1717: Yalnızca FlagsAttribute sabit listeleri çoğul adlara sahip olmalıdır](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Adlandırma kuralları numaralandırma için adlandırma aynı anda birden fazla numaralandırma değeri olduğunu gösterir.|
|[CA1725: Parametre adları temel bildirimle eşleşmemelidir](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Parametreyi geçersiz kılma hiyerarşisinde tutarlı adlandırma yöntemini geçersiz kılmaları kullanılabilirliği artırır. Temel bildirim alanındaki addan farklı türetilmiş yöntem parametre adı taban yöntemini geçersiz kılma veya yeni aşırı yöntemin yöntem olup olmadığı hakkında karışıklığa neden olabilir.|
|[CA1719: Parametre adları üye adları ile eşleşmemelidir](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Bir parametre adı bir parametrenin anlamını iletmeli ve üye adı bir üyenin anlamını iletmelidir. Bunların aynı olduğu yerlerde nadir bir tasarım olur. Aynı üye adıyla parametreyi adlandırma sezgisel değildir ve kütüphane kullanımını zorlaştırır.|
|[CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Kaynak dizesindeki her sözcük büyük küçük harfe dayalı belirteçlere bölünür. Her bir bitişik ikili-işaret kombinasyonu Microsoft yazım kitaplığı tarafından denetlenir. Tanınırsa, kelime kural ihlali üretir.|
|[CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Kaynak dizesi, Microsoft Yazım kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir.|
|[CA1724: Tür adları ad alanları ile eşleşmemelidir](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Tür adları, sınıf kitaplığında tanımlanan ad alanlarının adlarıyla eşleşmemelidir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Bu kuralın ihlali, kitaplığın kullanılabilirliğini azaltabilir.|
|[CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Kural gereği, tanımlayıcı adlar alt çizgi (_) karakterini içermez. Bu kural ad alanlarını, türleri, üyeleri ve parametreleri denetler.|
|[CA1721: Özellik adları get metotları ile eşleşmemelidir](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Ortak veya korumalı bir üye adı "Get" ile başlar ve aksi durumda ortak veya korumalı özellik adıyla eşleşir. "Get" yöntemlerinin ve özelliklerinin açıkça işlevlerinden ayırt edilebilen adları olması gerekir.|
|[CA1716: Tanımlayıcılar anahtar sözcükler ile eşleşmemelidir](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Ad alanı adı veya tür adı ayrılmış anahtar sözcük bir programlama dili ile eşleşir. Tanımlayıcı adı ve türleri için ortak dil çalışma zamanı, hedef diller tarafından tanımlanan anahtar sözcüklerle aynı değildir.|
|[CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)|Dışarıdan görünen bir tanımlayıcının adı, tercih edilen terim varolduğunda alternatif olarak bir terim içerir. Alternatif olarak ad, "Bayrak" veya "Bayraklar" terimini içerir.|
|[CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Kural gereği, parametre adları ortası büyük harfleri, ad alanı, tür ve üye adları, Pascal büyük harfleri kullanır.|
|[CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Tanımlayıcının adı birden çok sözcük içerir ve bu sözcüklerden en az biri büyük harf kullanımı hatasına maruz kalmış birleşik kelime olarak görülür.|
|[CA1712: Sabit listesi değerlerine tür adını önek olarak eklemeyin](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Tür bilgilerinin geliştirme araçları tarafından sağlanması beklendiğinden, numaralandırma üyelerinin adlarına tür adı ön eki uygulanmaz.|
|[CA1710: Tanımlayıcılar doğru soneke sahip olmalıdır](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Kural gereği, belirli temel türleri genişleten veya belirli arabirimleri ya da bu türlerden türetilmiş türleri uygulayan türlerin adları, temel tür veya arabirimle ilişkili bir soneke sahiptir.|
