---
title: Diyagramların özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31fb06512457f919b67d41c3fb4096e4c3477426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652024"
---
# <a name="properties-of-diagrams"></a>Diyagramların Özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diyagramların oluşturulan tasarımcıda nasıl görüneceğini belirten özellikler ayarlayabilirsiniz. Örneğin, diyagramdaki metin için varsayılan bir renk belirtebilirsiniz.

 Daha fazla bilgi için bkz. [etki alanına özgü dil tanımlama](../modeling/how-to-define-a-domain-specific-language.md). Bu özelliklerin nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [etki alanına özgü dili özelleştirme ve genişletme](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Aşağıdaki tabloda, diyagramların özellikleri listelenmektedir.

|Özellik|Açıklama|Varsayılan|
|--------------|-----------------|-------------|
|Rengi doldur|Diyagram için doldur rengi.|be|
|Metin rengi|Diyagramda görüntülenen metnin rengi.|siyah|
|Erişim değiştiricisi|Sınıfın erişim değiştiricisi (genel veya iç).|Ortak|
|Özel Öznitelikler|Oluşturulan kod sınıfına öznitelik eklemek için kullanılır.|\<none >|
|Double türevi üretir|@No__t_0, hem temel sınıf hem de kısmi bir sınıf (geçersiz kılmaları kullanarak özelleştirmeyi desteklemek için) oluşturulur. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Özel Oluşturucusu vardır|@No__t_0, kaynak kodda özel bir Oluşturucu sağlanacaktır. Daha fazla bilgi için bkz. [oluşturulan sınıfları geçersiz kılma ve genişletme](../modeling/overriding-and-extending-the-generated-classes.md)..|False|
|Devralma değiştiricisi|Diyagramdan oluşturulan kaynak kodu sınıfının devralım türünü açıklar (`none`, `abstract` veya `sealed`).|Yok.|
|Temel diyagram|Bu diyagramın temel sınıfı.|seçim|
|Name|Bu diyagramın adı.|Geçerli ad|
|Ad Alanı|Bu diyagramla ilişkili ad alanı.|Geçerli ad alanı|
|Temsil edilen sınıf|Bu diyagramın temsil ettiği kök etki alanı sınıfı.|Geçerliyse geçerli kök sınıfı|
|Notlar|Bu öğeyle ilişkili resmi olmayan notlar.|\<none >|
|Dolgu rengini özellik olarak gösterir|@No__t_0, Kullanıcı oluşturulan tasarımcının diyagramının Fill rengini ayarlayabilir. Bunu ayarlamak için diyagram şekline sağ tıklayın ve **Açılım Ekle**' ye tıklayın.|False|
|Metin rengini özellik olarak gösterir|@No__t_0, Kullanıcı oluşturulan tasarımcıda diyagramın metin rengini ayarlayabilir. Bunu ayarlamak için diyagram şekline sağ tıklayın ve **Açılım Ekle**' ye tıklayın.|False|
|Açıklama|Oluşturulan tasarımcıyı belgelemek için kullanılan açıklama.|\<none >|
|Görünen ad|Bu diyagram için oluşturulan tasarımcıda görüntülenecek ad.|\<none >|
|Help anahtar sözcüğü|Bu diyagram için F1 yardımını dizine eklemek için kullanılan anahtar sözcük.|\<none >|

## <a name="see-also"></a>Ayrıca Bkz.
 [Alana Özgü Dil Araçları sözlüğü](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
