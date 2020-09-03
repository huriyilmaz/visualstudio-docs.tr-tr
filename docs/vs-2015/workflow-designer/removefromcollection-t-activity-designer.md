---
title: RemoveFromCollection &lt; T &gt; etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672569"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection &lt; T &gt; etkinlik Tasarımcısı
**RemoveFromCollection \<T> ** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.RemoveFromCollection%601> .

## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection \<T> etkinliği
 <xref:System.Activities.Statements.RemoveFromCollection%601>Etkinlik belirli bir koleksiyondan belirtilen öğeyi kaldırır.

### <a name="using-the-removefromcollectiont-activity-designer"></a>RemoveFromCollection \<T> etkinlik tasarımcısını kullanma
 **RemoveFromCollection \<T> ** etkinlik Tasarımcısı **, araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak **Collection** , **Toolbox** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçerek) araç kutusu koleksiyon kategorisinde bulunabilir.

 **RemoveFromCollection \<T> ** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.RemoveFromCollection%601> <xref:System.Activities.Activity.DisplayName%2A> , varsayılan olarak RemoveFromCollection olan bir etkinlik oluşturur \<Int32> . <xref:System.Activities.Activity.DisplayName%2A>Değer, ** \<T> RemoveFromCollection** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection \<T> Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.RemoveFromCollection%601> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin isteğe bağlı kolay adı <xref:System.Activities.Statements.RemoveFromCollection%601> . Varsayılan değer RemoveFromCollection ' dur \<Int32> .<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Doğru|**Koleksiyona \<T> **eklenecek öğe. Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ICollection türünde \<TypeArgument> .** Koleksiyonu belirtmek için, özellik kılavuzunda bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|İçinde yer alan öğelerin T türü <xref:System.Collections.Generic.ICollection%601> . Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Belirtilen öğenin koleksiyondan kaldırılıp kaldırılmadığını gösteren bir değer. Sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir değişken yazın|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) var [tsıncollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) var