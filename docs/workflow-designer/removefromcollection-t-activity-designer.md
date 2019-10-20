---
title: İş Akışı Tasarımcısı-RemoveFromCollection &lt;T &gt; etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a8885505607d654327ad9dc36ab88708ab708c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649996"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection \<T > etkinlik Tasarımcısı

**RemoveFromCollection \<T >** etkinlik Tasarımcısı <xref:System.Activities.Statements.RemoveFromCollection%601> etkinliğini oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection \<T > etkinliği

@No__t_0 etkinliği belirli bir koleksiyondan belirtilen öğeyi kaldırır.

### <a name="using-the-removefromcollectiont-activity-designer"></a>RemoveFromCollection \<T > etkinlik tasarımcısını kullanma

**Toolbox**'ın **koleksiyon** kategorisindeki **RemoveFromCollection \<T >** etkinlik tasarımcısına erişin.
**RemoveFromCollection \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip iş akışı Tasarımcısı yüzeyi bir <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde yer alan yüzeyine bırakılabilir. Bu, <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection < Int32 \> için varsayılan bir <xref:System.Activities.Statements.RemoveFromCollection%601> etkinlik oluşturur. @No__t_0 değeri, **RemoveFromCollection < t \>** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T \> özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.RemoveFromCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır:

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer, < Int32 \> RemoveFromCollection ' dur.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Doğru|Koleksiyondan kaldırılacak öğe **\<T >** . Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Doğru|Öğenin kaldırılması gereken koleksiyon. Bu koleksiyon **ıcollection < TypeArgument \> türünde.** Koleksiyonu belirtmek için, özellik kılavuzunda bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|@No__t_0 bulunan öğelerin T türü. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Belirtilen öğenin koleksiyondan kaldırılıp kaldırılmadığını gösteren bir değer. Sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir değişken yazın|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)