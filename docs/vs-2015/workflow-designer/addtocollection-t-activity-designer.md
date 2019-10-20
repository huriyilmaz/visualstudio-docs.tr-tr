---
title: AddToCollection &lt;T &gt; etkinlik Tasarımcısı | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659202"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection &lt;T &gt; etkinlik Tasarımcısı
**AddToCollection \<T >** etkinlik tasarımcısı bir <xref:System.Activities.Statements.AddToCollection%601> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-addtocollectiont-activity"></a>AddToCollection \<T > etkinliği
 @No__t_0 etkinliği bir koleksiyona bir öğe ekler.

### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection \<T > etkinlik tasarımcısını kullanma
 **AddToCollection \<T >** etkinlik tasarımcısı, **[!INCLUDE[wfd2](../includes/wfd2-md.md)] araç** **kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir (alternatif olarak, **Görünüm** menüsü veya Ctrl + Alt + X.)

 **AddToCollection \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde yüzeyi üzerinde bırakılabilir. Bu, AddToCollection \<Int32 > Varsayılan <xref:System.Activities.Activity.DisplayName%2A> sahip <xref:System.Activities.Statements.AddToCollection%601> bir etkinlik oluşturur. (Varsayılan olarak, *TypeArgument* **Int32**' dir. Bu özellik kılavuzunda değiştirilebilir.) @No__t_0 değeri, **AddToCollection \<T >** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-addtocollectiont-properties"></a>AddToCollection \<T > Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.AddToCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer AddToCollection \<Int32 >. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|Doğru|Koleksiyona eklenecek öğe \<T >. Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ıcollection \<TypeArgument >** türünde. Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|@No__t_0 bulunan öğelerin T türü. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [addtocollection \<T > etkinlik tasarımcısı](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) var olan [tsınv \<T](../workflow-designer/existsincollection-t-activity-designer.md) > [RemoveFromCollection](../workflow-designer/removefromcollection-t-activity-designer.md) \<T >