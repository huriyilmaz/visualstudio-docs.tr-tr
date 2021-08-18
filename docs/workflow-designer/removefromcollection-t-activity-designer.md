---
title: RemoveFromCollection &lt; T &gt; Etkinlik Tasarımcısı
description: Bu İş Akışı Tasarımcısı RemoveFromCollection etkinlik tasarımcısını kullanarak bir <T> RemoveFromCollection etkinliği oluşturma ve yapılandırma hakkında bilgi <T> edinmek için.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135356"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T> Etkinlik Tasarımcısı

Bir etkinlik oluşturmak ve yapılandırmak için **\<T> RemoveFromCollection** etkinlik tasarımcısı <xref:System.Activities.Statements.RemoveFromCollection%601> kullanılır.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection \<T> Etkinliği

Etkinlik <xref:System.Activities.Statements.RemoveFromCollection%601> belirli bir koleksiyondan belirtilen öğeyi kaldırır.

### <a name="using-the-removefromcollectiont-activity-designer"></a>RemoveFromCollection Etkinlik \<T> Tasarımcısını Kullanma

Araç Kutusunun **Koleksiyon kategorisinde \<T> RemoveFromCollection** **etkinlik** tasarımcısına **erişin.**
**RemoveFromCollection \<T>** etkinlik tasarımcısı **Araç** Kutusundan sürüklenip, etkinlikler genellikle yerleştirildikten sonra İş Akışı Tasarımcısı yüzeyine (örneğin bir içinde) <xref:System.Activities.Statements.Sequence> bırakılır. Bu, <xref:System.Activities.Statements.RemoveFromCollection%601> <xref:System.Activities.Activity.DisplayName%2A> Varsayılan RemoveFromCollection ve Int32<bir etkinlik \> oluşturur. Değer, <xref:System.Activities.Activity.DisplayName%2A> **\> RemoveFromCollection** üst bilgisinde<T etkinlik tasarımcısında veya özellik **kılavuzundaki DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenemez.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection<T \> Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.RemoveFromCollection%601> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay <xref:System.Activities.Statements.RemoveFromCollection%601> adı. Varsayılan değer, Int32'de<RemoveFromCollection'dır. \><br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Doğru|Koleksiyonundan **kaldırıla \<T> öğe.** Bu öğe T *türündedir* ve *TypeArgument türündedir.* Öğeyi belirtmek için, özellik kılavuzunda Visual Basic bir ifade yazın.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Doğru|Öğenin kaldırılması gereken koleksiyon. Bu koleksiyon **ICollection ve TypeArgument<\> türündedir.** Koleksiyonu belirtmek için, özellik kılavuzunda Visual Basic bir ifade yazın.|
|*TypeArgument*|Doğru|içinde yer alan öğelerin T <xref:System.Collections.Generic.ICollection%601> türü. Varsayılan olarak, bu *TypeArgument* türü **Int32 olarak ayarlanır.** Türü değiştirmek için özellik kılavuzunda birleşik giriş kutusunda *TypeArgument* değerini değiştirebilirsiniz.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Belirtilen öğenin koleksiyondan kaldırılmış olup olmadığını gösteren bir değer. Sonucu bağlamak için bir değişken belirtmek için özellik kılavuzuna bir değişken yazın|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)