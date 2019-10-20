---
title: UML sınıf diyagramlarındaki işlemlerin özellikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671344"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>UML sınıf diyagramlarındaki işlemlerin özellikleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML sınıf diyagramında, sınıflara ve arabirimlere *işlemler* ekleyebilirsiniz. İşlem, bir sınıf veya arabirim örneği tarafından gerçekleştirilebilecek bir yöntem veya işlevdir.

 Bir işlem eklemek için sınıfa veya arabirime sağ tıklayın, **Ekle**' nin üzerine gelin ve sonra **işlem**' e tıklayın.

 Diyagramdaki bir sınıfın işlemleri görünür değilse, sınıfın veya arabirimin en üstündeki köşeli çift ayraca tıklayın. **İşlem** üst bilgisini görebiliyorsanız, işlemler bölümünü genişletmek için **[+]** öğesine tıklayın.

## <a name="signature-of-an-operation"></a>Bir Işlemin imzası
 Bir işlemin imzası, UML sınıf diyagramı üzerindeki bir sınıfta veya arabirimde bunu temsil eden metin satırıdır. Aşağıdaki biçimdedir:

 \+ OperationName (parametre1: Type1 [*],...): ReturnType [\*]

 \+ genel görünürlüğü gösterir. İzin verilen diğer değerler-(özel), # (korumalı), ~ (paket).

 `OperationName` **static** özelliği true ise altı çizili olur ve **abstract** özelliği true ise italik olur.

 hiçbir dönüş türü tanımlanmamışsa `: ReturnType` atlanır.

 `[*]` bir parametre veya dönüş türünün çokluğunu gösterir. Çoğulluk 1 ise atlanır.

 Bu özelliklerin tam açıklaması için sonraki bölüme bakın.

## <a name="properties"></a>Özellikler
 Bunlar bir sınıf veya arabirim içindeki bir işlemin Özellikler UML sınıf diyagramı üzerinde bulunur.

 Bir işlemin özelliklerini görmek için diyagramdaki sınıf veya arabirimdeki işleme sağ tıklayın ve ardından **Özellikler**' e tıklayın. Özellikler **, Özellikler penceresinde görünür** .

|      Özellik       |   Varsayılan    |                                                                                                                                                                                 Açıklama                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Ad**       | (yeni bir ad) |                                                                                                                                                                Kapsayan tür içinde benzersiz olmalıdır.                                                                                                                                                                 |
|   **Parametreler**    |    seçim    |      Şu form adına sahip bir liste **:** <em>tür</em> **,** <em>ad</em> **:** <em>tür</em> **,....** Listeyi düzenlemek için **[...]** düğmesine tıklayın.<br /><br /> Türler, temel türler veya modelde tanımlanan türler olabilir. Bu özellikte yeni bir tür için ad girerseniz, UML Model Gezgini 'nin **belirtilmeyen türler** bölümüne bir tür eklenecektir.      |
|   **Dönüş Türü**   |    seçim    |                                                                               **(yok)** veya temel bir tür ya da modelde tanımlı bir tür. Bu özellikte yeni bir tür için ad girerseniz, UML Model Gezgini 'nin **belirtilmeyen türler** bölümüne bir tür eklenecektir.                                                                                |
| **Sonkoşulları**  |    seçim    |                                                                                                                         İşlemin yürütmeden önce ve sonra sistemin durumu arasındaki ilişkiyi belirten isteğe bağlı bir koşul.                                                                                                                         |
|  **Üstbilgisinde**  |    seçim    |                                                                                                                            İşlem yürütülmeye başlamadan önce sistemin durumu hakkındaki varsayımları belirten isteğe bağlı bir durumdur.                                                                                                                            |
| **Gövde koşulları** |    seçim    |                                                                                                                                                       İşlemin döndürdüğü değerler üzerinde isteğe bağlı bir kısıtlama.                                                                                                                                                       |
|   **Görünürlük**    |    Ortak    |                  İzin verilen değerler ve İmzada görünen karakterler şunlardır:<br /><br /> **+ Genel** -genel görünür<br /><br /> **-Private** -sahip olan tür dışında görünür değil<br /><br /> **# Protected** -sahibinden türetilen türlere görünür<br /><br /> **~ Package** -aynı paket içindeki diğer türlere görünür.                   |
|    **İmza**    |  +*adı*()   |                                                                                      Bu işlemin görünürlüğünü, adını, parametrelerini ve dönüş türünü özetler. Diyagramdaki imzayı düzenleyerek veya tek tek özellikleri düzenleyerek bu özellikleri değiştirebilirsiniz.                                                                                      |
|   **İş öğeleri**    | 0 ilişkili |                                                                                                  İlişkili iş öğelerinin sayısı. Salt okunur.<br /><br /> Daha fazla bilgi için bkz. [model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Eşzamanlılık**   |  Sıralı  | **Sıralı** -işlem Eşzamanlılık denetimi olmadan tasarlanacaktır. Bu işlemi eşzamanlı olarak çağırmak hatalara yol açabilir.<br /><br /> **Korunuyor** -işlem, diğer örnekleri tamamlanana kadar otomatik olarak engellenir.<br /><br /> **Eşzamanlı** -işlem, birden çok çağrısının eşzamanlı yürütebilmesi için tasarlanmıştır. |
|    **Statiktir**    |    False     |                                                                                                  True ise, bu işlem bu türün tüm örnekleri arasında paylaşılır.<br /><br /> True ise işlemin adı diyagramda göründüğü yerde Altıçizili olacaktır.                                                                                                   |
|   **Soyut**   |    False     |                                                                                                                                        True ise, bu işlemle ilişkili kod yok. Bu nedenle, sahip olan sınıf soyuttur.                                                                                                                                         |
|     **Yaprak**     |    False     |                                                                                                                                              Tasarımcı, bu işlemin türetilmiş sınıflarda geçersiz kılınamayacağını size amaçlamaktadır.                                                                                                                                              |
|    **Sorgu**     |    False     |                                                                                                 True ise, bu işlem tarafından sistem durumunda önemli bir değişiklik yapılmaz. Bu nedenle, örneğin, sistemin durumunu denetlemek için bir testte kullanılabilir.                                                                                                  |
|  **Ğunun**   |      1\.       |                                 **1** -belirtilen türde tek bir değer.<br /><br /> **0.. 1** -`null` olabilir.<br /><br /> \*-belirtilen türdeki değerlerin bir koleksiyonu.<br /><br /> **1.. \\** \*-en az bir değer içeren bir koleksiyon.<br /><br /> *n* `..` *d* -`n` ve `m` değerleri içeren bir koleksiyon.                                  |
|   **Sıralanmıştır**    |    False     |                                                                                                                                             True ise koleksiyon sıralı bir liste oluşturur. 1 ' den fazla **çokluk** için.                                                                                                                                              |
|    **Benzersizdir**    |    False     |                                                                                                                                         True ise, koleksiyonda yinelenen değer yok. 1 ' den fazla **çokluk** için.                                                                                                                                         |

## <a name="see-also"></a>Ayrıca Bkz.
 [UML sınıf diyagramları:](../modeling/uml-class-diagrams-reference.md) UML sınıf çizenekleri UML sınıf diyagramları üzerindeki [ilişkilerin](../modeling/properties-of-associations-on-uml-class-diagrams.md) UML sınıf diyagramları [özelliklerindeki](../modeling/properties-of-attributes-on-uml-class-diagrams.md) başvuru [özellikleri](../modeling/properties-of-types-on-uml-class-diagrams.md) UML sınıf diyagramları [: yönergeler](../modeling/uml-class-diagrams-guidelines.md)
