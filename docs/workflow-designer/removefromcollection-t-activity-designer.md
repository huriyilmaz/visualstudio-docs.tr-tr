---
title: İş Akışı Tasarımcısı-RemoveFromCollection &lt; T &gt; etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8af0a0bf8bdf60c8ae9911ef0926cb9e395989a
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875585"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T> Etkinlik Tasarımcısı

**RemoveFromCollection \<T> ** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.RemoveFromCollection%601> .

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection \<T> etkinliği

<xref:System.Activities.Statements.RemoveFromCollection%601>Etkinlik belirli bir koleksiyondan belirtilen öğeyi kaldırır.

### <a name="using-the-removefromcollectiont-activity-designer"></a>RemoveFromCollection \<T> etkinlik tasarımcısını kullanma

**Toolbox**'ın **koleksiyon** kategorisindeki ** \<T> RemoveFromCollection** etkinlik tasarımcısına erişin.
**RemoveFromCollection \<T> ** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içindeki gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.RemoveFromCollection%601> , varsayılan bir <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection<Int32 ile bir etkinlik oluşturur \> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **RemoveFromCollection<\> T** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection<T \> Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.RemoveFromCollection%601> Özellikler gösterilmektedir ve tasarımcıda nasıl kullanıldıkları açıklanmıştır:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.RemoveFromCollection%601> . Varsayılan değer, varsayılan olarak RemoveFromCollection<\> .<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Doğru|**Koleksiyondan \<T> **kaldırılacak öğe. Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Doğru|Öğenin kaldırılması gereken koleksiyon. Bu koleksiyon **ıcollection<TypeArgument türünde \> .** Koleksiyonu belirtmek için, özellik kılavuzunda bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|İçinde yer alan öğelerin T türü <xref:System.Collections.Generic.ICollection%601> . Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Belirtilen öğenin koleksiyondan kaldırılıp kaldırılmadığını gösteren bir değer. Sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir değişken yazın|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)