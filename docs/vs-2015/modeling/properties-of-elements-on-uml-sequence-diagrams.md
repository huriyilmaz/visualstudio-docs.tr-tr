---
title: UML sıralı diyagramlarındaki öğelerin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671423"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>UML sıralı diyagramlarındaki öğelerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sıralı diyagramında, diyagramdaki her bir öğenin özellikleri vardır. Bir öğenin özelliklerini görmek için diyagramda veya **UML Model Gezgini** ' nde öğeye sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellikler **, Özellikler penceresinde görünür** .

> [!NOTE]
> Bu konu, UML sıralı diyagramlarındaki öğelerin özellikleri hakkındadır. UML sıralı diyagramlarını okuma hakkında daha fazla bilgi için bkz. [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md). UML sıralı diyagramları çizme hakkında daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Öğelerin özellikleri

|Özellik|Varsayılan|Öğe|Açıklama|
|--------------|-------------|-------------|-----------------|
|**Ad**|Varsayılan ad|Tümü|Öğesi tanımlar.|
|**Tam ad**|Paket:: Name|Tümü|Öğeyi benzersiz bir şekilde tanımlar. Ön eki içeren paketin tam adı.|
|**İş öğeleri**|0 ilişkili|Tümü|Bu öğeyle ilişkili iş öğelerinin sayısı. İş öğelerini ilişkilendirmek için bkz. [bağlantı modeli öğeleri ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).|
|**Açıklama**|adet|Tümü|Öğe hakkında genel notları buradan yapabilirsiniz.|
|**Color**|(öğe türü için varsayılan)|Yaşam çizgisi, Ileti|Şeklin rengi. Bu, gösterdiği öğe yerine şeklin bir özelliğidir.|
|**Tür**|adet|Yaşam|Yaşam çizgisinin temsil ettiği örnek türü.<br /><br /> Yaşam çizgisinin üstbilgisinde bir başvuru sembolü varsa, bu sınıf veya arabirim UML Model Gezgini 'nde ayrı olarak bulunur ve bir sınıf diyagramında görüntülenebilir.|
|**Actor** (Oyuncu)|Yanlış|Yaşam|Yaşam çizgisinin, diyagramın ilgili olduğu bileşenin dışında bir Kullanıcı, cihaz veya yazılım bileşenini temsil ettiğini belirtir.|
|**Tip**|**Tam** -gönderici ve alıcıya sahip bir ileti.<br /><br /> **Bulundu** -belirlenemeyen bir göndereni olan ileti.<br /><br /> **Kayıp** -belirtilmeyen bir alıcıya sahip bir ileti.|İleti|Bir iletinin hangi uçlarını bir yaşam çizgisine iliştirildiğini gösterir.<br /><br /> Bu özelliği değiştiremezsiniz. İletiyi oluşturduğunuzda ayarlanır.|
|**Sırala**|**AsynchCall** -zaman uyumsuz bir ileti.<br /><br /> **Eşlenmiş çağrı** -zaman uyumlu bir ileti.<br /><br /> **Yanıtla** -zaman uyumlu bir iletinin dönüş bölümü.<br /><br /> **CreateMessage** -bir örnek oluşturma iletisi.|İleti|İleti türü. Bu özelliği değiştiremezsiniz. İletiyi oluşturmak için kullandığınız araç tarafından belirlenir.|
|**İşlem**|olmamalıdır|İleti|Alıcı yaşam çizgisinde ileti tarafından çağrılan bir yöntem.<br /><br /> Yalnızca alıcı yaşam çizgisi bir arabirime veya sınıfa bağlıysa görünür.|
|**Başvurduğu yer**|Sıralı diyagram|Etkileşim kullanımı|Bu etkileşim kullanımı tarafından çağrılan sıralı diyagram.|
|**Etkileşim operatörü**|Komutu **Ile çevrelemeyi** kullandığınızda ayarlayın|Birleşik parça|Bu parça veya parçalar koleksiyonu tarafından temsil edilen işleç.|
|**Guard**|olmamalıdır|Birleşik bir parçadaki etkileşim Işleneni|Koruyucu true olmadığı takdirde parçadaki sıra gerçekleşmeyecektir.<br /><br /> Birleşik parçaların en üst parçasını seçmek için parça başlığının altına tıklayın.|
|**En az, en fazla**|(kısıtlama yok)|Birleşik parçayı döngüye ın|Döngünün en düşük ve en fazla kaç kez yürütüldüğü.|
|**İletiler**|olmamalıdır|Göz önünde bulundurun<br /><br /> Birleşik parçaları yoksay|Bu parçada kabul edilen veya yoksayılan iletiler.|

## <a name="see-also"></a>Ayrıca Bkz.
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md) [UML sıralı diyagramları: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md) [, denetim akışını UML sıralı diyagramlarında parçalar ile anlatmaktadır](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
