---
title: İş Akışı Tasarımcısı AddToCollection &lt; T &gt; etkinlik Tasarımcısı
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
ms.openlocfilehash: 1ffa24dce2691f061c5947e15d7fc7923d632b38
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88706548"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T> Etkinlik Tasarımcısı

**AddToCollection \<T> ** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.AddToCollection%601> .

## <a name="the-addtocollectiont-activity"></a>AddToCollection \<T> etkinliği

<xref:System.Activities.Statements.AddToCollection%601>Etkinlik bir koleksiyona bir öğe ekler.

### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection \<T> etkinlik tasarımcısını kullanma

**AddToCollection \<T> ** etkinlik Tasarımcısı, iş akışı Tasarımcısı araç **kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X**tuşlarına basın.

**AddToCollection \<T> ** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içindeki gibi etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . **AddToCollection \<T> ** etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.AddToCollection%601> varsayılan bir <xref:System.Activities.Activity.DisplayName%2A> AddToCollection<Int32 değeri olan bir etkinlik oluşturur \> . (Varsayılan olarak, *TypeArgument* **Int32**' dir. TypeArgument özellik kılavuzunda değiştirilebilir.) <xref:System.Activities.Activity.DisplayName%2A>Değer, **AddToCollection<\> T** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-addtocollectiont-properties"></a>AddToCollection \<T> Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.AddToCollection%601> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.AddToCollection%601> . Varsayılan değer, Int32<AddToCollection ' dur \> . <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Doğru|Koleksiyona eklenecek öğe \<T> . Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ıcollection<TypeArgument \> **türünde. Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|İçinde yer alan öğelerin T türü <xref:System.Collections.Generic.ICollection%601> . Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T> Etkinlik Tasarımcısı](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
