---
title: Diyagramların özellikleri
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 762c2acb6774d7eb4949087fdd91e85c86acd6bb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595429"
---
# <a name="properties-of-diagrams"></a>Diyagramların özellikleri
Diyagramların oluşturulan tasarımcıda nasıl görüneceğini belirten özellikler ayarlayabilirsiniz. Örneğin, diyagramdaki metin için varsayılan bir renk belirtebilirsiniz.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Aşağıdaki tabloda, diyagramların özellikleri listelenmektedir.

|Özellik|Açıklama|Varsayılan|
|-|-|-|
|Rengi doldur|Diyagram için doldur rengi.|Beyaz|
|Metin rengi|Diyagramda görüntülenen metnin rengi.|Siyah|
|Erişim değiştiricisi|Sınıfın erişim değiştiricisi (genel veya iç).|Ortak|
|Özel Öznitelikler|Oluşturulan kod sınıfına öznitelik eklemek için kullanılır.|\<yok >|
|Double türevi üretir|`True`, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları kullanarak özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel Oluşturucusu vardır|`True`, kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md)..|False|
|Devralma değiştiricisi|Diyagramdan oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract`veya `sealed`).|Yok.|
|Temel diyagram|Bu diyagramın temel sınıfı.|(yok)|
|Name|Bu diyagramın adı.|Geçerli ad|
|Ad alanı|Bu diyagramla ilişkili ad alanı.|Geçerli ad alanı|
|Temsil edilen sınıf|Bu diyagramın temsil ettiği kök etki alanı sınıfı.|Geçerliyse geçerli kök sınıfı|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar.|\<yok >|
|Dolgu rengini özellik olarak gösterir|`True`, Kullanıcı oluşturulan tasarımcının diyagramının Fill rengini ayarlayabilir. Bu özelliği ayarlamak için diyagram şekline sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|False|
|Metin rengini özellik olarak gösterir|`True`, Kullanıcı oluşturulan tasarımcıda diyagramın metin rengini ayarlayabilir. Bu özelliği ayarlamak için diyagram şekline sağ tıklayıp **gösterilen Ekle**' ye tıklayın.|False|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılan açıklama.|\<yok >|
|Görünen Ad|Bu diyagram için oluşturulan tasarımcıda görüntülenecek ad.|\<yok >|
|Help anahtar sözcüğü|Bu diyagram için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<yok >|

## <a name="see-also"></a>Ayrıca bkz.

[Etki alanına özgü dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
