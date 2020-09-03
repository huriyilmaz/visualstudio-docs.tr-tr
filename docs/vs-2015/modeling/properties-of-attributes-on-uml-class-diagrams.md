---
title: UML sınıf diyagramlarındaki özniteliklerin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: de32eba5fc6e4afc21d62f4432d9317d85408ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652061"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>UML sınıf diyagramlarındaki özniteliklerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sınıf diyagramında *öznitelikleri* sınıflara ve arayüzlere ekleyebilirsiniz. Bir öznitelik, sınıfın veya arabirimin örneklerine iliştirilebilecek değerleri tanımlar.

 Bir öznitelik eklemek için, sınıfa veya arabirime sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **öznitelik**' e tıklayın.

 Diyagramdaki bir sınıfın öznitelikleri görünür değilse, sınıfın veya arabirimin en üstündeki köşeli çift ayraca tıklayarak genişletin. **Öznitelikler** başlığını göremiyorsanız, öznitelikler bölümünü genişletmek için **[+]** düğmesine tıklayın.

## <a name="signature-of-an-attribute"></a>Bir özniteliğin imzası
 Bir özniteliğin imzası, UML sınıf diyagramı üzerindeki bir sınıfta veya arabirimde temsil eden bir satırdır. Şu biçimdedir:

```
+ AttributeName : TypeName [*]
```

 \+ Genel görünürlüğü belirtir. İzin verilen diğer değerler-(özel), # (korumalı), ~ (paket).

 `AttributeName` özniteliği statikse altı çizilir.

 `: TypeName` özniteliğin türü yoksa, atlanır.

 `[*]` çeşitliliği gösterir. Çoğulluk 1 ise atlanır.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bir UML sınıf diyagramında bir sınıf veya arabirimdeki bir özniteliğin özellikleri açıklanmaktadır.

 Bir özniteliğin özelliklerini görmek için diyagramdaki sınıf veya arabirimdeki özniteliğe sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellikler Özellikler penceresi görüntülenir.

 Bir özniteliğin özelliklerini görüntülemek için, sağ tıklayın ve ardından **Özellikler**' e tıklayın.

|   **Özellik**    | **Varsayılanını**  |                                                                                                                                                                                                         Açıklama                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Varsayılan değer** |   olmamalıdır    |                                                                                                                                                                               Sınıflandırıcı örneği oluşturulurken özniteliğin değeri.                                                                                                                                                                                |
| **Salt okunurdur**  |    Yanlış     |                                                                                                                                                                                    True ise özniteliğin değeri değiştirilemez.                                                                                                                                                                                    |
|   **Is Static**   |    Yanlış     |                                                                                                                    True ise, bu öznitelik için tek bir değer bu türün tüm örnekleri arasında paylaşılır.<br /><br /> True ise özniteliğin adının diyagramda göründüğü yerde altı çizilir.                                                                                                                    |
|     **Ad**      | (yeni bir ad) |                                                                                                                                                                                        Sahip olan sınıflandırıcı içinde benzersiz olmalıdır.                                                                                                                                                                                        |
|     **Tür**      |    (yok)    |                                                **Tamsayı**veya modelde tanımlanan bir tür gibi temel bir tür. Değerin meta verilerde kodlanması gerektiğinden, **ondalık** gibi basit olmayan türler kullanamazsınız. Bu özellikte yeni bir tür için ad girerseniz, UML Model Gezgini 'nin **belirtilmeyen türler** bölümüne bir tür eklenecektir.                                                 |
|  **Görünürlük**   |    Genel    |                                     İzin verilen değerler ve İmzada görünen karakterler aşağıdaki gibidir:<br /><br /> **+ Genel** -genel görünür<br /><br /> **-Private** -sahip olan tür dışında görünür değil<br /><br /> **# Protected** -sahibinden türetilen türlere görünür<br /><br /> **~ Package** -aynı paket içindeki diğer türlere görünür.                                      |
|  **İş öğeleri**   | 0 ilişkili |                                                                                                                          İlişkili iş öğelerinin sayısı. Salt okunur.<br /><br /> Daha fazla bilgi için bkz. [model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Yaprak**    |    Yanlış     |                                                                                                                                                                    True ise, türetilmiş türlerde bu özniteliğin yeniden tanımlanması için tasarlanmamıştır.                                                                                                                                                                     |
|  **Türetilir**   |    Yanlış     |                                                                                                              True ise, bu öznitelik diğer özniteliklerden hesaplanır. Örneğin, diyagonal, genişlik ve yükseklikten hesaplanır. Ayrıntılar **açıklamasında** veya Iliştirilmiş bir açıklama biçiminde yazılmalıdır.                                                                                                              |
|  **Açıklama**  |   olmamalıdır    |                                                                                                                                                                        Genel notlar veya öznitelikteki değerlerde kısıtlamalar tanımlamak için.                                                                                                                                                                        |
| **Çokluk**  |      1       | **1** -bu özniteliğin belirtilen türde tek bir değeri vardır.<br /><br /> **0.. 1** -bu özniteliğin değeri olabilir `null` .<br /><br /> **\\**\* -Bu özniteliğin değeri bir değerler koleksiyonudur.<br /><br /> **1.. \\ ** \* -Bu özniteliğin değeri en az bir değer içeren bir koleksiyondur.<br /><br /> *n* **..** *d* -bu özniteliğin değeri *n* ile *d* arasında bir değer içeren bir koleksiyondur. |
|  **Sıralanmıştır**   |    Yanlış     |                                                                                                                                                                    True ise koleksiyon sıralı bir liste oluşturur. 1 ' den fazla **çokluk** için.                                                                                                                                                                     |
|   **Benzersizdir**   |    Yanlış     |                                                                                                                                                                True ise, koleksiyonda yinelenen değer yok. 1 ' den fazla **çokluk** için.                                                                                                                                                                |

## <a name="see-also"></a>Ayrıca Bkz.
 [UML sınıf diyagramları:](../modeling/uml-class-diagrams-reference.md) UML sınıf diyagramları ' [nın](../modeling/properties-of-operations-on-uml-class-diagrams.md) UML sınıf diyagramları 'ndaki başvuru [özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md) UML sınıf diyagramları [: yönergeler](../modeling/uml-class-diagrams-guidelines.md) [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)
