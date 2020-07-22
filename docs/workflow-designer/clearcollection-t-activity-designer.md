---
title: İş Akışı Tasarımcısı-ClearCollection <T> etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a96f0b56172684c5c82910b34f40aa44fd6aec81
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876183"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T> Etkinlik Tasarımcısı

**ClearCollection \<T> ** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.ClearCollection%601> .

## <a name="the-clearcollectiont-activity"></a>ClearCollection \<T> etkinliği

<xref:System.Activities.Statements.ClearCollection%601>Etkinlik, tüm öğelerin belirtilen koleksiyonunu temizler.

### <a name="using-the-clearcollectiont-activity-designer"></a>ClearCollection \<T> etkinlik tasarımcısını kullanma

**ClearCollection \<T> ** etkinlik Tasarımcısı, iş akışı Tasarımcısı araç **kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X**tuşlarına basın.

**ClearCollection \<T> ** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, içindeki gibi etkinliklerin yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Etkinlik Tasarımcısı ' nın atılması, <xref:System.Activities.Statements.ClearCollection%601> varsayılan <xref:System.Activities.Activity.DisplayName%2A> clearcollection<Int32 ile bir etkinlik oluşturur \> . (Varsayılan olarak, *TypeArgument* **Int32**' dir. TypeArgument özellik kılavuzunda değiştirilebilir.) <xref:System.Activities.Activity.DisplayName%2A>Değer, **clearcollection \><T** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-clearcollectiont-properties"></a>ClearCollection \<T> Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.ClearCollection%601> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adını belirtir <xref:System.Activities.Statements.ClearCollection%601> . Varsayılan değer ClearCollection<Int32 'dir \> . <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Doğru|Öğelerin temizlenme koleksiyonunu belirtir. Bu koleksiyon **ICollection türünde \<TypeArgument> .** Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|İçinde yer alan öğelerin T türünü belirtir <xref:System.Collections.Generic.ICollection%601> . Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)