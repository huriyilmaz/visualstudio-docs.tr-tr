---
title: İş Akışı Tasarımcısı AddToCollection<T> etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb00679001cc09b8fdfa68f898923ac208b32c4e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115321"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T > etkinlik Tasarımcısı

**AddToCollection\<t >** etkinlik Tasarımcısı, bir <xref:System.Activities.Statements.AddToCollection%601> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > etkinliği

<xref:System.Activities.Statements.AddToCollection%601> etkinliği bir koleksiyona bir öğe ekler.

### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection\<T > etkinlik tasarımcısını kullanma

**AddToCollection\<t >** etkinlik tasarımcısı, iş akışı Tasarımcısı **araç kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL**+**alt**+**X**tuşuna basın.

**AddToCollection\<t >** etkinlik Tasarımcısı **araç kutusundan** sürüklenebilir ve <xref:System.Activities.Statements.Sequence>içinde olduğu gibi etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. **Addtocollection\<t >** etkinlik Tasarımcısı, AddToCollection < Int32\>varsayılan <xref:System.Activities.Activity.DisplayName%2A> sahip bir <xref:System.Activities.Statements.AddToCollection%601> etkinliği oluşturur. (Varsayılan olarak, *TypeArgument* **Int32**' dir. TypeArgument özellik kılavuzunda değiştirilebilir.) <xref:System.Activities.Activity.DisplayName%2A> değeri, **AddToCollection < t\>** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.AddToCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> etkinliğinin kolay adı. Varsayılan değer AddToCollection < Int32\>' dir. <xref:System.Activities.Activity.DisplayName%2A> değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Doğru|Koleksiyona eklenecek öğe\<T >. Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ıcollection < TypeArgument\>** türünde. Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|<xref:System.Collections.Generic.ICollection%601>bulunan öğelerin T türü. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T > etkinlik Tasarımcısı](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
