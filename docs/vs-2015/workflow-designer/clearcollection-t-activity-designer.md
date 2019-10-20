---
title: ClearCollection &lt;T &gt; etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2f1e0264d39c65601a70e8c24b51c7eceadf4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657018"
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection &lt;T &gt; etkinlik Tasarımcısı
**ClearCollection \<T >** etkinlik Tasarımcısı <xref:System.Activities.Statements.ClearCollection%601> etkinliğini oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-clearcollectiont-activity"></a>ClearCollection \<T > etkinliği
 @No__t_0 etkinliği tüm öğelerin belirtilen koleksiyonunu temizler.

### <a name="using-the-clearcollectiont-activity-designer"></a>ClearCollection \<T > etkinlik tasarımcısını kullanma
 **Clearcollection \<T >** etkinlik tasarımcısı, **[!INCLUDE[wfd2](../includes/wfd2-md.md)] araç** **kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir (alternatif olarak, **Görünüm** menüsü veya Ctrl + Alt + X.)

 **ClearCollection \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde yüzeyi üzerinde bırakılabilir. Bu, ClearCollection \<Int32 > Varsayılan <xref:System.Activities.Activity.DisplayName%2A> sahip <xref:System.Activities.Statements.ClearCollection%601> bir etkinlik oluşturur. (Varsayılan olarak, *TypeArgument* **Int32**' dir. Bu özellik kılavuzunda değiştirilebilir.) @No__t_0 değeri, **ClearCollection \<T >** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-clearcollectiont-properties"></a>ClearCollection \<T > Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.ClearCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adını belirtir. Varsayılan değer ClearCollection \<Int32 >. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|Doğru|Öğelerin temizlenme koleksiyonunu belirtir. Bu koleksiyon **ıcollection \<TypeArgument > türünde.** Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|@No__t_0 yer alan öğelerin T türünü belirtir. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [addtocollection \<T](../workflow-designer/addtocollection-t-activity-designer.md) var olan > var [tsıncollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)