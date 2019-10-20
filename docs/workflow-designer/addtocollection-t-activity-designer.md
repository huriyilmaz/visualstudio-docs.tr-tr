---
title: İş Akışı Tasarımcısı AddToCollection <T> etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8aa11f93b702f48d93710b9993769289ebc8ffa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650740"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection \<T > etkinlik Tasarımcısı

**AddToCollection \<T >** etkinlik tasarımcısı bir <xref:System.Activities.Statements.AddToCollection%601> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-addtocollectiont-activity"></a>AddToCollection \<T > etkinliği

@No__t_0 etkinliği bir koleksiyona bir öğe ekler.

### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection \<T > etkinlik tasarımcısını kullanma

**AddToCollection \<T >** etkinlik tasarımcısı, iş akışı Tasarımcısı **araç kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** +**alt** +**X**tuşuna basın.

**AddToCollection \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, <xref:System.Activities.Statements.Sequence> içinde olduğu gibi etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. **Addtocollection \<T >** etkinlik Tasarımcısı, AddToCollection < Int32 \> varsayılan <xref:System.Activities.Activity.DisplayName%2A> sahip bir <xref:System.Activities.Statements.AddToCollection%601> etkinliği oluşturur. (Varsayılan olarak, *TypeArgument* **Int32**' dir. TypeArgument özellik kılavuzunda değiştirilebilir.) @No__t_0 değeri, **AddToCollection < t \>** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-addtocollectiont-properties"></a>AddToCollection \<T > Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.AddToCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer AddToCollection < Int32 \> ' dir. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Doğru|Koleksiyona eklenecek öğe \<T >. Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ıcollection < TypeArgument \>** türünde. Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|@No__t_0 bulunan öğelerin T türü. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection \<T > etkinlik Tasarımcısı](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)