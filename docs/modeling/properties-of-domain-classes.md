---
title: Etki Alanı Sınıflarının Özellikleri
description: Erişim değiştiricisi ve özel öznitelikler gibi etki alanı sınıflarının çeşitli özellikleri hakkında bilgi edinin ve çift türetilmiş bir üretir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eaaae0028d574a521319ae045cdb4f7f1bdafaa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390014"
---
# <a name="properties-of-domain-classes"></a>Etki Alanı Sınıflarının Özellikleri
Etki alanı sınıfları aşağıdaki tabloda yer alan özelliklere sahiptir. Etki alanı sınıfları hakkında daha fazla bilgi için bkz. [modelleri, sınıfları ve Ilişkileri anlama](../modeling/understanding-models-classes-and-relationships.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Domain-Specific dilini özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Erişim değiştiricisi|Etki alanı sınıfına erişim düzeyi ( `public` veya `internal` ).|`public`|
|Özel Öznitelikler|Bu etki alanı sınıfından oluşturulan kaynak kodu sınıfına öznitelikler eklemek için kullanılır.|\<none>|
|Double türevi üretir|Eğer `True` bir temel sınıf ve kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Özel Oluşturucusu vardır|İse `True` , kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Devralma değiştiricisi|Etki alanı sınıfından (veya) oluşturulan kaynak kodu sınıfının devralım türünü açıklar `none` `abstract` `sealed` .|`none`|
|Temel sınıf|Bu alan sınıfı türetildiyse, taban sınıfın adı.|\<none>|
|Name|Bu alan sınıfının adı.|Geçerli ad|
|Ad Alanı|Bu alan sınıfının ad alanı.|Geçerli ad alanı|
|Notlar|Bu alan sınıfıyla ilişkili resmi olmayan notlar.|\<none>|
|Açıklama|Oluşturulan tasarımcının Kullanıcı arabirimini belgelemek için kullanılan açıklama.|\<none>|
|Görünen Ad|Bu alan sınıfı için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Help anahtar sözcüğü|Bu etki alanı sınıfına yönelik F1 yardımını indekslemek için kullanılan isteğe bağlı anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))