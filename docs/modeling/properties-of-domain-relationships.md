---
title: Etki Alanı İlişkilerinin Özellikleri
description: Erişim Değiştiricisi, Özel Öznitelikler ve İki Kez Türetilen Oluşturma gibi bir etki alanı relationshop ile ilişkili özellikler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8972722c0f65f4d007db7173ef41b7a40dba1208
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637553"
---
# <a name="properties-of-domain-relationships"></a>Etki Alanı İlişkilerinin Özellikleri
Aşağıdaki tablodaki özellikler bir etki alanı ilişkisiyle ilişkilendirildi. Etki alanı ilişkileri hakkında bilgi için [bkz. Modelleri, Sınıfları ve İlişkileri Anlama.](../modeling/understanding-models-classes-and-relationships.md) Bu özellikleri kullanma hakkında daha fazla bilgi için, [bkz. Domain-Specific Dili Özelleştirme ve Genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Erişim Değiştiricisi|Etki alanı ilişkisinin erişim düzeyi ( `public` veya `internal` ).|`public`|
|Özel Öznitelikler|Etki alanı ilişkisinden oluşturulan kaynak kod sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Çift Türetilen|ise, `True` hem temel bir sınıf hem de kısmi bir sınıf (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|Özel Oluşturucuya Sahip|ise, `True` kaynak kodda özel bir oluşturucu sağlanmıştır gösterir. Daha fazla bilgi için [bkz. Oluşturulan Sınıfları Geçersiz Kılma ve Genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|Devralma Değiştiricisi|Etki alanı ilişkisinden ( veya ) oluşturulan kaynak kod sınıfının `none` devralmanın nasıl olduğunu `abstract` `sealed` açıklar.|\<none>|
|Yinelenenlere Izin Verir|ise, `True` etki alanı ilişkisinin yinelenen bağlantıları aynı iki öğe arasında oluşturulabilir.|`False`|
|Temel İlişkiler|Etki alanı ilişkisi türetilmişse, etki alanı ilişkisinin temel ilişkisi.|\<none>|
|Ekleme|ise, `True` etki alanı ilişkisi bir ekleme ilişkisidir. ise, `False` ilişki bir başvuru ilişkisidir.|\<both>|
|Name|Etki alanı ilişkisinin adı.|Geçerli ad|
|Ad Alanı|Etki alanı ilişkisine bağlı olan ad alanı.|Geçerli ad alanı|
|Notlar|Etki alanı ilişkisiyle ilişkili resmi olmayan notlar.|\<none>|
|Description|Kodu belgeley için kullanılan ve oluşturulan tasarımcının kullanıcı arabiriminde kullanılan açıklama.|\<none>|
|Görünen Ad|Etki alanı ilişkisi için oluşturulan tasarımcıda görüntülenen ad.|\<none>|
|Yardım Anahtar Sözcüğü|Etki alanı ilişkisi için F1 yardım dizinini dizine eklemek için kullanılan isteğe bağlı anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))