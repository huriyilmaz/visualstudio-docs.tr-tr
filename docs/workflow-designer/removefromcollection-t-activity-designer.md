---
title: RemoveFromCollection &lt; T &gt; etkinlik Tasarımcısı
description: İş Akışı Tasarımcısı, RemoveFromCollection <T> etkinlik Tasarımcısı 'nı kullanarak bir RemoveFromCollection etkinliği oluşturma ve yapılandırma hakkında bilgi edinin <T> .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: bcf44bbb8db921307137b2d953ecbc085b666e3d
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963713"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T> Etkinlik Tasarımcısı

**RemoveFromCollection \<T>** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.RemoveFromCollection%601> .

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection \<T> etkinliği

<xref:System.Activities.Statements.RemoveFromCollection%601>Etkinlik belirli bir koleksiyondan belirtilen öğeyi kaldırır.

### <a name="using-the-removefromcollectiont-activity-designer"></a>RemoveFromCollection \<T> etkinlik tasarımcısını kullanma

**Toolbox**'ın **koleksiyon** kategorisindeki **\<T> RemoveFromCollection** etkinlik tasarımcısına erişin.
**RemoveFromCollection \<T>** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içindeki gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.RemoveFromCollection%601> , varsayılan bir <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection<Int32 ile bir etkinlik oluşturur \> . <xref:System.Activities.Activity.DisplayName%2A>Değer, **RemoveFromCollection<\> T** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection<T \> Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.RemoveFromCollection%601> Özellikler gösterilmektedir ve tasarımcıda nasıl kullanıldıkları açıklanmıştır:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.RemoveFromCollection%601> . Varsayılan değer, varsayılan olarak RemoveFromCollection<\> .<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Doğru|**Koleksiyondan \<T>** kaldırılacak öğe. Bu öğe, *TypeArgument* türünde *T* türünde. öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Doğru|Öğenin kaldırılması gereken koleksiyon. Bu koleksiyon **ıcollection<TypeArgument türünde \> .** koleksiyonu belirtmek için, özellik kılavuzunda bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|İçinde yer alan öğelerin T türü <xref:System.Collections.Generic.ICollection%601> . Varsayılan olarak, bu *TypeArgument* türü **Int32** olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Belirtilen öğenin koleksiyondan kaldırılıp kaldırılmadığını gösteren bir değer. Sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir değişken yazın|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)