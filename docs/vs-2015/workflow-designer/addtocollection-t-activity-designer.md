---
title: AddToCollection &lt; T &gt; etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 50deab447b3dcb93d352e73fc4765d913b4d24bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659202"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection &lt; T &gt; etkinlik Tasarımcısı
**AddToCollection \<T> ** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.AddToCollection%601> .

## <a name="the-addtocollectiont-activity"></a>AddToCollection \<T> etkinliği
 <xref:System.Activities.Statements.AddToCollection%601>Etkinlik bir koleksiyona bir öğe ekler.

### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection \<T> etkinlik tasarımcısını kullanma
 **AddToCollection \<T> ** etkinlik Tasarımcısı, araç **kutusu** sekmesine tıklanarak erişilen **Toolbox**'ın **koleksiyon** kategorisinde bulunabilir [!INCLUDE[wfd2](../includes/wfd2-md.md)] (ALTERNATIF olarak, **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.)

 **AddToCollection \<T> ** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, [!INCLUDE[wfd2](../includes/wfd2-md.md)] bir içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.AddToCollection%601> , varsayılan AddToCollection adlı bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> \<Int32> . (Varsayılan olarak, *TypeArgument* **Int32**' dir. Bu özellik kılavuzunda değiştirilebilir.) <xref:System.Activities.Activity.DisplayName%2A>Değer, ** \<T> AddToCollection** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-addtocollectiont-properties"></a>AddToCollection \<T> Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.AddToCollection%601> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.AddToCollection%601> . Varsayılan değer AddToCollection ' dur \<Int32> . <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Doğru|Koleksiyona eklenecek öğe \<T> . Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ICollection \<TypeArgument> **türünde. Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|İçinde yer alan öğelerin T türü <xref:System.Collections.Generic.ICollection%601> . Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> etkinlik Tasarımcısı](../workflow-designer/addtocollection-t-activity-designer.md) [ \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ \<T> ](../workflow-designer/existsincollection-t-activity-designer.md) ClearCollection var tsınv [RemoveFromCollection \<T> ](../workflow-designer/removefromcollection-t-activity-designer.md) var