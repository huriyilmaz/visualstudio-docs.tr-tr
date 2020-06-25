---
title: Konu arayın (Yardım Görüntüleyicisi)
ms.date: 11/02/2017
ms.topic: how-to
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4581d7ea0b40e2b6b519f0beafaee8744e0b46c1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284925"
---
# <a name="how-to-search-for-topics"></a>Nasıl yapılır: konu arama

Tam metin arama özelliğini kullanarak belirli bir sözcüğü içeren tüm konuları bulabilirsiniz. Ayrıca joker karakter ifadeleri, mantıksal işleçler ve gelişmiş arama işleçlerini kullanarak aramanızı iyileştirebilirsiniz ve özelleştirebilirsiniz.

**Arama** sekmesini açmak için **Yardım Görüntüleyicisi** penceresinde **Ara** sekmesini seçin veya bir klavye kullanıcısı kullanıyorsanız **CTRL** + **E**' yi seçin.

## <a name="to-perform-a-full-text-search"></a>Tam metin araması gerçekleştirmek için

1. Arama kutusuna bulmak istediğiniz sözcüğü yazın.

2. Arama sorgusunda, arama için hangi mantıksal veya Gelişmiş arama işleçlerinin uygulanacağını belirtin. Tüm kullanılabilir yardımı aramak için işleçleri kullanmayın.

    > [!NOTE]
    > **Görüntüleyici seçenekleri** iletişim kutusunda, bir kerede görüntülenecek en fazla arama sonucu sayısı ve birincil yerel ayarınız İngilizce değilse, İngilizce içerik eklenip eklenmeyeceğini gibi ek tercihleri belirtebilirsiniz.

3. **ENTER** tuşunu seçin.

     Arama, varsayılan olarak en fazla 200 isabet döndürür ve bunları arama sonuçları alanında görüntüler. İçeriğe bağlı olarak her bir sonuç için ek sürüm bilgileri görünebilir.

4. Bir konuyu görüntülemek için, sonuç listesinden başlığını seçin.

## <a name="full-text-search-tips"></a>Tam metin arama ipuçları

Sözdiziminin sorgunuzu nasıl etkilediğini anladıysanız, yalnızca ilgilendiğiniz konuları döndüren daha hedefli aramalar oluşturabilirsiniz. Söz dizimi özel karakterler, ayrılmış sözcükler ve filtreler içerir. Bu konuda, sorgularınızı daha iyi hale getirmenize yardımcı olmak için ipuçları, yordamlar ve ayrıntılı sözdizimi bilgileri sağlanmaktadır.

### <a name="general-guidelines"></a>Genel yönergeler

Aşağıdaki tablo, yardım 'da arama sorguları geliştirmeye yönelik bazı temel kuralları ve yönergeleri içerir.

|Syntax|Description|
|------------|-----------------|
|Büyük/küçük harf duyarlılığı|Aramalar büyük/küçük harfe duyarlı değildir. Büyük veya küçük harfli karakterler kullanarak arama ölçütlerinizi geliştirin. Örneğin, "OLE" ve "OLE" aynı sonuçları döndürür.|
|Karakter birleşimleri|Yalnızca tek harf (a-z) veya sayı (0-9) için arama yapamazsınız. "And", "from" ve "with" gibi belirli ayrılmış kelimeleri aramaya çalışırsanız, bunlar yok sayılır. Daha fazla bilgi için, bu konunun ilerleyen kısımlarında [bulunan aramalardaki kelimelerin yoksayılan sözcükleri](#stopwords) inceleyin.|
|Değerlendirme sırası|Arama sorguları soldan sağa değerlendirilir.|

### <a name="search-syntax"></a>Arama söz dizimi

"Word1 word2" gibi birden çok sözcük içeren bir arama dizesi belirtirseniz, bu dize "word1 ve word2" yazmakla eşdeğerdir, bu da yalnızca arama dizesindeki tek tek sözcüklerin bulunduğu konuları döndürür.

> [!IMPORTANT]
> - Tümcecik aramaları desteklenmez. Bir arama dizesinde birden fazla sözcük belirtirseniz, döndürülen konular belirttiğiniz tüm kelimeleri içerir ancak belirttiğiniz tam ifade değildir.
> - Arama tümceciğinin kelimeleri arasındaki ilişkiyi belirtmek için mantıksal işleçleri kullanın. Aramanızı daha da belirginleştirmek için ve, veya gibi mantıksal işleçleri dahil edebilirsiniz. Örneğin, "yakın birleşim bildirme" araması yaparsanız, arama sonuçları birbirleriyle "bildirme" ve "Union" sözcüklerini içeren konuları içerir. Daha fazla bilgi için bkz. [arama Ifadelerinde mantıksal işleçler](../help-viewer/logical-operators-search-expressions.md).

### <a name="filters"></a>Filtreler

Gelişmiş arama işleçlerini kullanarak arama sonuçlarını daha da kısıtlayabilirsiniz. Yardım, tam metin aramasının sonuçlarını filtrelemek için kullanabileceğiniz üç kategori içerir: Başlık, kod ve anahtar sözcük.

### <a name="ranking-of-search-results"></a>Arama sonuçlarının derecelendirmesi

Arama algoritması, arama sonuçlarının sonuçlar listesinde daha yüksek veya daha düşük bir şekilde derecelendirmesine yardımcı olmak için belirli kriterleri uygular. Genel olarak:

1. Başlıktaki arama sözcüklerini içeren içerik, olmayan içerikten daha yüksek olarak derecelendirilir.

2. Yakın yakınlık içinde arama sözcüklerini içeren içerik, olmayan içerikten daha yüksek bir şekilde derecelendirilir.

3. Arama sözcüklerinin daha yüksek bir yoğunluğunu içeren içerik, arama sözcüklerini daha düşük bir yoğunlukta olan içerikten daha yüksek olarak derecelendirilir.

### <a name=""></a><a name="stopwords">Aramalardaki sözcükler yoksayıldı (sözcükleri Durdur)</a>

Genellikle durdurma kelimeleri olarak adlandırılan yaygın olarak oluşan sözcükler veya sayılar, tam metin araması sırasında otomatik olarak yoksayılır. Örneğin, "pass through" ifadesini arıyorsanız, arama sonuçları "pass" sözcüğünü içeren, ancak "Through" sözcüğünü içeren konuları görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal ve gelişmiş işleçler](../help-viewer/logical-operators-search-expressions.md)
- [Nasıl yapılır: dizinde konu bulma](../help-viewer/find-topics-index.md)
- [Nasıl yapılır: TOC 'de konu bulma](../help-viewer/find-topics-toc.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)