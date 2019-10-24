---
title: Etki Alanı İlişkilerinin Özellikleri
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d08f453c3c52f8520dacc26f9b636fd8c8bcafde
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747467"
---
# <a name="properties-of-domain-relationships"></a>Etki Alanı İlişkilerinin Özellikleri
Aşağıdaki tabloda yer alan Özellikler bir etki alanı ilişkisiyle ilişkilendirilir. Etki alanı ilişkileri hakkında daha fazla bilgi için bkz. [modelleri, sınıfları ve Ilişkileri anlama](../modeling/understanding-models-classes-and-relationships.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Erişim değiştiricisi|Etki alanı ilişkisine erişim düzeyi (`public` veya `internal`).|`public`|
|Özel Öznitelikler|Etki alanı ilişkisinden oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none >|
|Double türevi üretir|@No__t_0, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Özel Oluşturucusu vardır|@No__t_0, kaynak kodda özel bir oluşturucunun sağlandığını gösterir. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Devralma değiştiricisi|Etki alanı ilişkisinden oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract` veya `sealed`).|\<none >|
|Yinelemelere izin verir|@No__t_0, aynı iki öğe arasında etki alanı ilişkisinin Yinelenen bağlantıları oluşturulabilir.|`False`|
|Temel Ilişkiler|Etki alanı ilişkisi türetildiyse, etki alanı ilişkisinin temel ilişkisi.|\<none >|
|Ekleniyor|@No__t_0, etki alanı ilişkisi bir katıştırma ilişkisidir. @No__t_0, ilişki bir başvuru ilişkisidir.|\<both >|
|Name|Etki alanı ilişkisinin adı.|Geçerli ad|
|Ad Alanı|Etki alanı ilişkisiyle bağlantılı olan ad alanı.|Geçerli ad alanı|
|Notlar|Etki alanı ilişkisiyle ilişkili resmi olmayan notlar.|\<none >|
|Açıklama|Kodu belgelemek için kullanılan açıklama ve oluşturulan tasarımcının Kullanıcı arabiriminde kullanılır.|\<none >|
|Görünen ad|Etki alanı ilişkisi için oluşturulan tasarımcıda görüntülenen ad.|\<none >|
|Help anahtar sözcüğü|Etki alanı ilişkisi için F1 yardımını dizine eklemek üzere kullanılan isteğe bağlı anahtar sözcük.|\<none >|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)