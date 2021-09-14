---
title: Diyagramların özellikleri
description: Diyagramlar hakkında bilgi edinin ve diyagramların oluşturulan tasarımcıda nasıl görüneceğini belirten özellikleri nasıl ayarlayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 5128befb2460a364758a692cfe5cac0a30732f1e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637569"
---
# <a name="properties-of-diagrams"></a>Diyagramların özellikleri
Diyagramların oluşturulan tasarımcıda nasıl görüneceğini belirten özellikler ayarlayabilirsiniz. Örneğin, diyagramdaki metin için varsayılan bir renk belirtebilirsiniz.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Aşağıdaki tabloda, diyagramların özellikleri listelenmektedir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu Rengi|Diyagram için doldur rengi.|Beyaz|
|Metin rengi|Diyagramda görüntülenen metnin rengi.|Siyahi|
|Erişim değiştiricisi|Sınıfın erişim değiştiricisi (genel veya iç).|Genel|
|Özel Öznitelikler|Oluşturulan kod sınıfına öznitelik eklemek için kullanılır.|\<none>|
|Double türevi üretir|Eğer `True` bir temel sınıf ve kısmi bir sınıf (geçersiz kılmaları özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|Yanlış|
|Özel Oluşturucusu vardır|İse `True` , kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md)..|Yanlış|
|Devralma değiştiricisi|Diyagramdan oluşturulan kaynak kodu sınıfının devralım türünü açıklar ( `none` , `abstract` , veya `sealed` ).|Hiçbiri|
|Temel diyagram|Bu diyagramın temel sınıfı.|(yok)|
|Name|Bu diyagramın adı.|Geçerli ad|
|Ad Alanı|Bu diyagramla ilişkili ad alanı.|Geçerli ad alanı|
|Temsil edilen sınıf|Bu diyagramın temsil ettiği kök etki alanı sınıfı.|Geçerliyse geçerli kök sınıfı|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar.|\<none>|
|Dolgu rengini özellik olarak gösterir|İse `True` , Kullanıcı oluşturulan tasarımcının diyagramının Fill rengini ayarlayabilir. Bu özelliği ayarlamak için diyagram şekline sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|Yanlış|
|Metin rengini özellik olarak gösterir|Eğer `True` Kullanıcı, oluşturulan tasarımcıda diyagramın metin rengini ayarlayabilir. Bu özelliği ayarlamak için diyagram şekline sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|Yanlış|
|Description|Oluşturulan tasarımcıyı belgelemek için kullanılan açıklama.|\<none>|
|Görünen Ad|Bu diyagram için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Help anahtar sözcüğü|Bu diyagram için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

[Etki alanına özgü dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))