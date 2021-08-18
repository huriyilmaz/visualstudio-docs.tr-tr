---
title: AddToCollection &lt; T &gt; etkinlik tasarımcısı
description: AddToCollection etkinlik tasarımcısının bir AddToCollection etkinliği oluşturmak ve yapılandırmak için nasıl <T> <T> İş Akışı Tasarımcısı.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: a204e6147b18938d20a94c0a41c06e8983d4026e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068157"
---
# <a name="addtocollectiont-activity-designer"></a>AddToCollection\<T> Etkinlik Tasarımcısı

Etkinlik oluşturmak ve yapılandırmak için **\<T> AddToCollection** etkinlik tasarımcısı <xref:System.Activities.Statements.AddToCollection%601> kullanılır.

## <a name="the-addtocollectiont-activity"></a>AddToCollection \<T> Etkinliği

Etkinlik <xref:System.Activities.Statements.AddToCollection%601> bir koleksiyona öğe ekler.

### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection Etkinlik \<T> Tasarımcısını Kullanma

**AddToCollection \<T>** etkinlik tasarımcısı, araç kutusunun Araç Kutusu sekmesine tıklayarak erişilen  Araç Kutusu'nun Koleksiyon İş Akışı Tasarımcısı.  Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**AddToCollection \<T>** etkinlik tasarımcısı **Toolbox'tan** sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra bu veri yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. **AddToCollection etkinlik \<T> tasarımcısı bırakarak,** <xref:System.Activities.Statements.AddToCollection%601> <xref:System.Activities.Activity.DisplayName%2A> Int32'de varsayılan AddToCollection<bir etkinlik \> oluşturur. *(TypeArgument* varsayılan olarak **Int32'dir.** TypeArgument, özellik kılavuzunda değiştirilebilir.) Değer, <xref:System.Activities.Activity.DisplayName%2A> **\> AddToCollection** üst bilgisinde veya T<tasarımcısında veya özellik **kılavuzundaki DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenemez.

### <a name="the-addtocollectiont-properties"></a>AddToCollection \<T> Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.AddToCollection%601> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.AddToCollection%601> adı. Varsayılan değer, Int32'<AddToCollection'dır. \> Değer <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir ancak bir değer kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Doğru|Koleksiyonuna ek olarak \<T> öğesi. Bu öğe T *türündedir* ve *TypeArgument türündedir.* Öğeyi belirtmek için, özellik kılavuzunda Visual Basic bir ifade yazın.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Doğru|Öğenin ekleniyor olması gereken koleksiyon. Bu koleksiyon, **TypeArgument için ICollection \><türündedir.** Koleksiyonu belirtmek için özellik kılavuzuna Visual Basic bir ifade yazın.|
|*TypeArgument*|Doğru|içinde yer alan öğelerin T <xref:System.Collections.Generic.ICollection%601> türü. Varsayılan olarak, bu *TypeArgument* türü **Int32 olarak ayarlanır.** Türü değiştirmek için özellik kılavuzunda birleşik giriş kutusunda *TypeArgument* değerini değiştirebilirsiniz.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T> Etkinlik Tasarımcısı](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
