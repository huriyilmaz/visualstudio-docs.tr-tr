---
title: Mevcut Tsıncollection &lt; T &gt; etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 08aabbcb7dbef2df9a3affa8589a9c6d4205ac58
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656729"
---
# <a name="existsincollectionlttgt-activity-designer"></a>Mevcut Tsıncollection &lt; T &gt; etkinlik Tasarımcısı
Var olan **Tsıncollection \<T> ** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.ExistsInCollection%601> .

## <a name="the-existsincollectiont-activity"></a>Varolan Tsıncollection \<T> etkinliği
 <xref:System.Activities.Statements.ExistsInCollection%601>Etkinlik belirli bir koleksiyonda belirtilen öğenin mevcut olup olmadığını belirler.

### <a name="using-the-existsincollectiont-activity-designer"></a>Mevcut Tsıncollection \<T> etkinlik tasarımcısını kullanma
 Var olan **Tsıncollection \<T> ** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ALTERNATIF olarak, **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.)

 Var olan **Tsıncollection \<T> ** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyde yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.ExistsInCollection%601> , varsayılan olarak var olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> \<Int32> . (Varsayılan olarak, *TypeArgument* **Int32**' dir. Özellik kılavuzunda değiştirilebilir.)  Değer, var olan <xref:System.Activities.Activity.DisplayName%2A> **Tsıncollection \<T> ** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-existsincollectiont-properties"></a>Mevcut Tsıncollection \<T> Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.ExistsInCollection%601> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.ExistsInCollection%601> . Varsayılan değer Vartsıncollection ' dır \<Int32> . <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Doğru|Koleksiyona eklenecek öğe \<T> . Bu öğe, *TypeArgument*türünde *T* türündedir. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ICollection türünde \<TypeArgument> .** Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|İçinde yer alan öğelerin T türü <xref:System.Collections.Generic.ICollection%601> . Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Koleksiyonda belirtilen öğenin var olup olmadığını gösteren bir değer. Sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir Visual Basic değişkeni yazın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md)