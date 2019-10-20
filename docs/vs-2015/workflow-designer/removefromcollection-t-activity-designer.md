---
title: RemoveFromCollection &lt;T &gt; etkinlik Tasarımcısı | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672569"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection &lt;T &gt; etkinlik Tasarımcısı
**RemoveFromCollection \<T >** etkinlik Tasarımcısı <xref:System.Activities.Statements.RemoveFromCollection%601> etkinliğini oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection \<T > etkinliği
 @No__t_0 etkinliği belirli bir koleksiyondan belirtilen öğeyi kaldırır.

### <a name="using-the-removefromcollectiont-activity-designer"></a>RemoveFromCollection \<T > etkinlik tasarımcısını kullanma
 **RemoveFromCollection \<T >** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] araç **kutusu** sekmesine tıklanarak erişilen **Toolbox**'ın **koleksiyon** kategorisinde bulunabilir (alternatif olarak, **araç çubuğunu** seçin **Görünüm** menüsü veya Ctrl + Alt + X.)

 **RemoveFromCollection \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyi bir <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde yer alan yüzeyine bırakılabilir. Bu, <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection \<Int32 > için varsayılan bir <xref:System.Activities.Statements.RemoveFromCollection%601> etkinlik oluşturur. @No__t_0 değeri, **RemoveFromCollection \<T >** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection \<T > Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.RemoveFromCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin isteğe bağlı kolay adı. Varsayılan değer RemoveFromCollection \<Int32 >.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Doğru|Koleksiyona eklenecek öğe **\<T >** . Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ıcollection \<TypeArgument > türünde.** Koleksiyonu belirtmek için, özellik kılavuzunda bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|@No__t_0 bulunan öğelerin T türü. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Belirtilen öğenin koleksiyondan kaldırılıp kaldırılmadığını gösteren bir değer. Sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir değişken yazın|

## <a name="see-also"></a>Ayrıca Bkz.
 {1 & gt; [koleksiyon](../workflow-designer/collection-activity-designers.md) [addtocollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection > \<T](../workflow-designer/clearcollection-t-activity-designer.md) var olan [tsıncollection \<T >](../workflow-designer/existsincollection-t-activity-designer.md)