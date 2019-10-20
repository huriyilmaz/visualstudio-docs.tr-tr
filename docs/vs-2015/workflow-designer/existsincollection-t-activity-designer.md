---
title: Mevcut Tsıncollection &lt;T &gt; etkinlik Tasarımcısı | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656729"
---
# <a name="existsincollectionlttgt-activity-designer"></a>Mevcut Tsincollection &lt;T &gt; etkinlik Tasarımcısı
**Mevcut Tsincollection \<T >** etkinlik Tasarımcısı <xref:System.Activities.Statements.ExistsInCollection%601> etkinliğini oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-existsincollectiont-activity"></a>Mevcut Tsincollection \<T > etkinliği
 @No__t_0 etkinliği belirli bir koleksiyonda belirtilen öğenin mevcut olup olmadığını belirler.

### <a name="using-the-existsincollectiont-activity-designer"></a>Mevcut Tsıncollection \<T > etkinlik tasarımcısını kullanma
 **Mevcut Tsincollection \<T >** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] **araç kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir (alternatif olarak, **Görünüm** menüsü veya Ctrl + Alt + X.)

 Var olan **Tsıncollection \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyi bir <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde yer alan yüzeyine bırakılabilir. Bu, var olan \<Int32 > Varsayılan <xref:System.Activities.Activity.DisplayName%2A> sahip <xref:System.Activities.Statements.ExistsInCollection%601> bir etkinlik oluşturur. (Varsayılan olarak, *TypeArgument* **Int32**' dir. Özellik kılavuzunda değiştirilebilir.)  @No__t_0 değeri, var olan **Tsıncollection \<T >** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-existsincollectiont-properties"></a>Mevcut Tsincollection \<T > Özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.ExistsInCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer, \<Int32 > var Tsıncollection. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Doğru|Koleksiyona eklenecek öğe \<T >. Bu öğe, *TypeArgument*türünde *T* türündedir. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Doğru|Öğenin eklenmesi gereken koleksiyon. Bu koleksiyon **ıcollection \<TypeArgument > türünde.** Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|@No__t_0 bulunan öğelerin T türü. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Koleksiyonda belirtilen öğenin var olup olmadığını gösteren bir değer. Sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir Visual Basic değişkeni yazın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Koleksiyon](../workflow-designer/collection-activity-designers.md) [addtocollection \<T >](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T >](../workflow-designer/clearcollection-t-activity-designer.md) [RemoveFromCollection \<T >](../workflow-designer/removefromcollection-t-activity-designer.md)