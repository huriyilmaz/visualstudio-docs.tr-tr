---
title: Diyagramların özellikleri
description: Diyagramlar hakkında bilgi ve diyagramların oluşturulan tasarımcıda nasıl görüneceklerini belirten özellikleri nasıl ayarlayabilirsiniz?
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
ms.workload:
- multiple
ms.openlocfilehash: 8a060c79866d1746135f8a29aef15ca96dd51f63
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390678"
---
# <a name="properties-of-diagrams"></a>Diyagramların özellikleri
Diyagramların oluşturulan tasarımcıda nasıl görüneceklerini belirten özellikler belirtebilirsiniz. Örneğin, diyagramda metin için varsayılan bir renk belirtebilirsiniz.

 Daha fazla bilgi için [bkz. Etki alanına özgü bir dil tanımlama.](../modeling/how-to-define-a-domain-specific-language.md) Bu özellikleri kullanma hakkında daha fazla bilgi için [bkz. Etki alanına özgü bir dili özelleştirme ve genişletme.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 Aşağıdaki tabloda diyagramların özellikleri liste almaktadır.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Dolgu Rengi|Diyagram için dolgu rengi.|Beyaz|
|Metin Rengi|Diyagramda görüntülenen metnin rengi.|Siyahi|
|Erişim Değiştiricisi|Sınıfın erişim değiştiricisi (genel veya iç).|Genel|
|Özel Öznitelikler|Oluşturulan kod sınıfına öznitelik eklemek için kullanılır.|\<none>|
|Çift Türetilen|ise, `True` hem temel bir sınıf hem de kısmi bir sınıf (geçersiz kılmalar aracılığıyla özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için [bkz. Oluşturulan sınıfları geçersiz kılma ve genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Özel Oluşturucuya Sahip|ise, `True` kaynak kodunda özel bir oluşturucu sağlanır. Daha fazla bilgi için [bkz. Oluşturulan sınıfları geçersiz kılma ve genişletme.](../modeling/overriding-and-extending-the-generated-classes.md)|Yanlış|
|Devralma Değiştiricisi|Diyagramdan ( , veya ) oluşturulan kaynak kod sınıfının `none` `abstract` devralmanın nasıl olduğunu `sealed` açıklar.|Hiçbiri|
|Temel Diyagram|Bu diyagramın temel sınıfı.|(yok)|
|Name|Bu diyagramın adı.|Geçerli ad|
|Ad Alanı|Bu diyagrama bağlı olan ad alanı.|Geçerli ad alanı|
|Temsil Edilen Sınıf|Bu diyagramın temsil ettiği kök etki alanı sınıfı.|Varsa geçerli kök sınıfı|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar.|\<none>|
|Dolgu Rengini Farklı Görüntüler Özelliği|ise, `True` kullanıcı oluşturulan tasarımcı diyagramının dolgu rengini ayarlayın. Bu özelliği ayarlamak için diyagram şekline sağ tıklayın ve Maruz **Ekle'ye tıklayın.**|Yanlış|
|Metin Rengini Farklı Görüntüler Özelliği|ise, `True` kullanıcı, oluşturulan tasarımcıda diyagramın metin rengini ayarlayın. Bu özelliği ayarlamak için diyagram şekline sağ tıklayın ve Maruz **Ekle'ye tıklayın.**|Yanlış|
|Açıklama|Oluşturulan tasarımcıyı belgeley etmek için kullanılan açıklama.|\<none>|
|Görünen Ad|Bu diyagram için oluşturulan tasarımcıda görüntülenecek ad.|\<none>|
|Help Anahtar Sözcüğü|Bu diyagram için F1 yardım dizinini dizine eklemek için kullanılan anahtar sözcük.|\<none>|

## <a name="see-also"></a>Ayrıca bkz.

[Etki alanına özgü dil araçları sözlüğü](/previous-versions/bb126564(v=vs.100))