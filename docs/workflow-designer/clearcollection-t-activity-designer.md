---
title: İş Akışı Tasarımcısı - ClearCollection &lt; T &gt; Etkinlik Tasarımcısı
description: ClearCollection etkinliği oluşturmak ve yapılandırmak için ClearCollection <T> etkinlik tasarımcısını kullanmayı <T> öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: cca2dad48095d6c6282f05c8b2dc6d257826fcef
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963708"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T> Etkinlik Tasarımcısı

Etkinliği oluşturmak ve yapılandırmak için **ClearCollection \<T>** etkinlik tasarımcısı <xref:System.Activities.Statements.ClearCollection%601> kullanılır.

## <a name="the-clearcollectiont-activity"></a>ClearCollection \<T> Etkinliği

Etkinlik, <xref:System.Activities.Statements.ClearCollection%601> belirtilen tüm öğelerin koleksiyonunu temizler.

### <a name="using-the-clearcollectiont-activity-designer"></a>ClearCollection Etkinlik \<T> Tasarımcısını Kullanma

**ClearCollection \<T>** etkinlik tasarımcısı, araç kutusunun Araç Kutusu sekmesine tıklayarak erişilen  Araç Kutusu'İş Akışı Tasarımcısı.  Alternatif olarak Görünüm **menüsünden Araç** Kutusu'nı **seçin** veya **Ctrl** Alt X + **tuşlarına** + **basın.**

**ClearCollection \<T>** etkinlik tasarımcısı **Araç** Kutusundan sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildikten sonra bu alan yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Etkinlik tasarımcısını <xref:System.Activities.Statements.ClearCollection%601> <xref:System.Activities.Activity.DisplayName%2A> bırakarak, Varsayılan ClearCollection ve Int32<bir etkinlik \> oluşturur. *(TypeArgument* varsayılan olarak **Int32'dir.** TypeArgument, özellik kılavuzunda değiştirilebilir.) Değer, <xref:System.Activities.Activity.DisplayName%2A> **ClearCollection \>**<T etkinlik tasarımcısının üst bilgisinde veya özellik **kılavuzundaki DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenemez.

### <a name="the-clearcollectiont-properties"></a>ClearCollection \<T> Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.ClearCollection%601> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını <xref:System.Activities.Statements.ClearCollection%601> belirtir. Varsayılan değer ClearCollection ve Int32<'dır. \> Değer <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli değildir ancak bir değer kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Doğru|Öğelerden silinen koleksiyonu belirtir. Bu koleksiyon **ICollection \<TypeArgument> türündedir.** Koleksiyonu belirtmek için özellik kılavuzuna Visual Basic bir ifade yazın.|
|*TypeArgument*|Doğru|içinde yer alan öğelerin T türünü <xref:System.Collections.Generic.ICollection%601> belirtir. Varsayılan olarak, bu *TypeArgument* türü **Int32 olarak ayarlanır.** Türü değiştirmek için özellik kılavuzunda birleşik giriş kutusunda *TypeArgument* değerini değiştirebilirsiniz.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)