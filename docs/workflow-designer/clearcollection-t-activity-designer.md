---
title: İş Akışı Tasarımcısı-ClearCollection <T> etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4808c046c4da23bc5c95d3978965afd938962f5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650697"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection \<T > etkinlik Tasarımcısı

**ClearCollection \<T >** etkinlik Tasarımcısı <xref:System.Activities.Statements.ClearCollection%601> etkinliğini oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-clearcollectiont-activity"></a>ClearCollection \<T > etkinliği

@No__t_0 etkinliği tüm öğelerin belirtilen koleksiyonunu temizler.

### <a name="using-the-clearcollectiont-activity-designer"></a>ClearCollection \<T > etkinlik tasarımcısını kullanma

**ClearCollection \<T >** etkinlik tasarımcısı, iş akışı Tasarımcısı **araç kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** +**alt** +**X**tuşuna basın.

**ClearCollection \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, <xref:System.Activities.Statements.Sequence> içinde olduğu gibi etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. Etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Activity.DisplayName%2A> ClearCollection < Int32 \> varsayılan bir <xref:System.Activities.Statements.ClearCollection%601> etkinlik oluşturur. (Varsayılan olarak, *TypeArgument* **Int32**' dir. TypeArgument özellik kılavuzunda değiştirilebilir.) @No__t_0 değeri, **ClearCollection < t \>** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-clearcollectiont-properties"></a>ClearCollection \<T > Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.ClearCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer ClearCollection < Int32 \> ' dir. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Doğru|Öğelerin temizlenme koleksiyonunu belirtir. Bu koleksiyon **ıcollection \<TypeArgument > türünde.** Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|@No__t_0 yer alan öğelerin T türünü belirtir. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)