---
title: ExistsInCollection &lt; T &gt; Etkinlik Tasarımcısı
description: ExistsInCollection etkinliği oluşturmak ve yapılandırmak için <T> İş Akışı Tasarımcısı'da ExistsInCollection etkinlik tasarımcısını kullanmayı <T> öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: ac03ddce895b18c95d74fd41a0ab2692fe92ccd750b95611fda0caf950384b8b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408024"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T> Etkinlik Tasarımcısı

Bir etkinlik oluşturmak ve yapılandırmak için **\<T> ExistsInCollection** etkinlik tasarımcısı <xref:System.Activities.Statements.ExistsInCollection%601> kullanılır.

## <a name="the-existsincollectiont-activity"></a>ExistsInCollection \<T> Etkinliği

Etkinlik, <xref:System.Activities.Statements.ExistsInCollection%601> belirtilen bir öğenin belirli bir koleksiyonda var olup olmadığını belirler.

### <a name="using-the-existsincollectiont-activity-designer"></a>ExistsInCollection Etkinlik \<T> Tasarımcısını Kullanma

**ExistsInCollection \<T>** etkinlik tasarımcısı, araç kutusunun Araç Kutusu sekmesine tıklayarak erişilen  Araç Kutusu'İş Akışı Tasarımcısı.  Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**ExistsInCollection \<T>** etkinlik **tasarımcısı, Araç** Kutusundan sürüklenerek İş Akışı Tasarımcısı bir içinde olduğu gibi genellikle her yerde bu etkinlik yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Bu, <xref:System.Activities.Statements.ExistsInCollection%601> <xref:System.Activities.Activity.DisplayName%2A> Varsayılan ExistsInCollection ve Int32<bir etkinlik \> oluşturur. *(TypeArgument* varsayılan olarak **Int32'dir.** Özellik kılavuzunda değiştirilebilir.)  Değer, <xref:System.Activities.Activity.DisplayName%2A> **\> ExistsInCollection** üst bilgisinde veya T<tasarımcısında veya özellik **kılavuzundaki DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenemez.

### <a name="the-existsincollectiont-properties"></a>ExistsInCollection \<T> Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.ExistsInCollection%601> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.ExistsInCollection%601> adı. Varsayılan değer, Int32'<ExistsInCollection'dır. \> Değer <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir ancak bir değer kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Doğru|Koleksiyonunda bakıla \<T> öğe. Bu öğe T *türündedir* ve *TypeArgument türündedir.* Öğeyi belirtmek için özellik kılavuzuna Visual Basic bir ifade yazın.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Doğru|Öğenin var olup olamayacakları kontrol etmek için koleksiyon. Bu koleksiyon, **TypeArgument için ICollection<\> türündedir.** Koleksiyonu belirtmek için özellik kılavuzuna Visual Basic bir ifade yazın.|
|*TypeArgument*|Doğru|içinde yer alan öğelerin T <xref:System.Collections.Generic.ICollection%601> türü. Varsayılan olarak, bu *TypeArgument* türü **Int32 olarak ayarlanır.** Türü değiştirmek için özellik kılavuzunda birleşik giriş kutusunda *TypeArgument* değerini değiştirebilirsiniz.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Belirtilen öğenin koleksiyonda mevcut olup olmadığını belirten bir değer. Sonucu bağlamak için bir değişken belirtmek için, özellik kılavuzunda Visual Basic değişken yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)