---
title: Tam metin arama Ipuçları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac683ff6e7079478d5b4e642918df4e281a53f0b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645647"
---
# <a name="full-text-search-tips"></a>Tam Metin Araması İpuçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yardım 'da bilgi bulmanın daha kullanışlı yöntemlerinden biri tam metin araması gerçekleştirmekten biridir. Sonuçlarınızı iyileştirmek ve özelleştirmek için sözdiziminin sorgunuzu nasıl etkileyeceğini anlamanız gerekir. Bu konuda, sorgularınızı daha iyi hale getirmenize yardımcı olmak için ipuçları, yordamlar ve ayrıntılı sözdizimi bilgileri sağlanmaktadır.

## <a name="full-text-search-tips"></a>Tam Metin Araması İpuçları
 Sorgularda kullandığınız biçimlendirmeyi nasıl yorumlayacağınızı anladıysanız, yalnızca ilgilendiğiniz konuları döndüren daha hedefli aramalar oluşturabilirsiniz. Bu biçimler özel karakterler, ayrılmış sözcükler ve filtreler içerir.

### <a name="general-guidelines"></a>Genel Yönergeler
 Aşağıdaki tablo, yardım 'da arama sorguları geliştirmeye yönelik bazı temel kuralları ve yönergeleri içerir.

|Sözdizimi|Açıklama|
|------------|-----------------|
|Büyük/küçük harf duyarlılığı|Aramalar büyük/küçük harfe duyarlı değildir. Büyük veya küçük harfli karakterler kullanarak arama ölçütlerinizi geliştirin. Örneğin, "OLE" ve "OLE" aynı sonuçları döndürür.|
|Karakter birleşimleri|Yalnızca tek harf (a – z) veya sayı (0 – 9) için arama yapamazsınız. "And", "from" ve "with" gibi belirli ayrılmış kelimeleri aramaya çalışırsanız, bunlar yok sayılır. Daha fazla bilgi için, bu konunun ilerleyen kısımlarında "aramalardaki (sözcükleri Durdur) sözcükler yoksayıldı" başlığına bakın.|
|Değerlendirme sırası|Arama sorguları soldan sağa değerlendirilir.|

### <a name="search-syntax"></a>Arama söz dizimi
 "Word1 word2" gibi birden çok sözcük içeren bir arama dizesi belirtirseniz, bu dize "word1 ve word2" yazmakla eşdeğerdir, bu da yalnızca arama dizesindeki tek tek sözcüklerin bulunduğu konuları döndürür.

> [!IMPORTANT]
> 1. Tümcecik aramaları desteklenmez. Bir arama dizesinde birden fazla sözcük belirtirseniz, döndürülen konular belirttiğiniz tüm kelimeleri içerir ancak belirttiğiniz tam ifade değildir.
>    2. Arama tümceciğinin kelimeleri arasındaki ilişkiyi belirtmek için mantıksal işleçleri kullanın. Aramanızı daha da belirginleştirmek için ve, veya gibi mantıksal işleçleri dahil edebilirsiniz. Örneğin, "yakın birleşim bildirme" araması yaparsanız, arama sonuçları birbirleriyle "bildirme" ve "Union" sözcüklerini içeren konuları içerir. Daha fazla bilgi için bkz. [arama Ifadelerinde mantıksal işleçler](../ide/logical-operators-in-search-expressions.md).

### <a name="filters"></a>FilTReleri
 Gelişmiş arama işleçlerini kullanarak arama sonuçlarını daha da kısıtlayabilirsiniz. Yardım, tam metin aramasının sonuçlarını filtrelemek için kullanabileceğiniz üç kategori içerir: Başlık, kod ve anahtar sözcük. Daha fazla bilgi için bkz. [arama Ifadelerinde gelişmiş arama işleçleri](../ide/advanced-search-operators-in-search-expressions.md).

### <a name="ranking-of-search-results"></a>Arama sonuçlarının derecelendirmesi
 Arama algoritması, arama sonuçlarının sonuçlar listesinde daha yüksek veya daha düşük bir şekilde derecelendirmesine yardımcı olmak için belirli kriterleri uygular. Genel olarak:

1. Başlıktaki arama sözcüklerini içeren içerik, olmayan içerikten daha yüksek olarak derecelendirilir.

2. Yakın yakınlık içinde arama sözcüklerini içeren içerik, olmayan içerikten daha yüksek bir şekilde derecelendirilir.

3. Arama sözcüklerinin daha yüksek bir yoğunluğunu içeren içerik, arama sözcüklerini daha düşük bir yoğunlukta olan içerikten daha yüksek olarak derecelendirilir.

### <a name="words-ignored-in-searches-stop-words"></a>Aramalardaki sözcükler yoksayıldı (sözcükleri Durdur)
 Genellikle durdurma kelimeleri olarak adlandırılan yaygın olarak oluşan sözcükler veya sayılar, tam metin araması sırasında otomatik olarak yoksayılır. Örneğin, "pass through" ifadesini arıyorsanız, arama sonuçları "pass" sözcüğünü içeren, ancak "Through" sözcüğünü içeren konuları görüntüler.

## <a name="see-also"></a>Ayrıca Bkz.
 [](../ide/locate-information.md) [Arama Ifadelerinde bilgi mantıksal işleçlerini](../ide/logical-operators-in-search-expressions.md) bulma
