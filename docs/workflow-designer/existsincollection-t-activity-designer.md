---
title: İş Akışı Tasarımcısı-mevcut Tsincollection &lt;T &gt; etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9dc1f6a3694b6164fe4f2187fa4c6e2b42751e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650481"
---
# <a name="existsincollectiont-activity-designer"></a>Mevcut Tsincollection \<T > etkinlik Tasarımcısı

**Mevcut Tsincollection \<T >** etkinlik Tasarımcısı <xref:System.Activities.Statements.ExistsInCollection%601> etkinliğini oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-existsincollectiont-activity"></a>Mevcut Tsincollection \<T > etkinliği

@No__t_0 etkinliği belirli bir koleksiyonda belirtilen öğenin mevcut olup olmadığını belirler.

### <a name="using-the-existsincollectiont-activity-designer"></a>Mevcut Tsıncollection \<T > etkinlik tasarımcısını kullanma

**Mevcut Tsincollection \<T >** etkinlik tasarımcısı, iş akışı Tasarımcısı **araç kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** +**alt** +**X**tuşuna basın.

Var olan **Tsıncollection \<T >** etkinlik Tasarımcısı **araç kutusundan** sürüklenip iş akışı Tasarımcısı yüzeyi bir <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde yer alan yüzeyine bırakılabilir. Bu, var olan < Int32 \> varsayılan <xref:System.Activities.Activity.DisplayName%2A> sahip bir <xref:System.Activities.Statements.ExistsInCollection%601> etkinlik oluşturur. (Varsayılan olarak, *TypeArgument* **Int32**' dir. Özellik kılavuzunda değiştirilebilir.)  @No__t_0 değeri, var olan **Tsincollection < t \>** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-existsincollectiont-properties"></a>Mevcut Tsincollection \<T > Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.ExistsInCollection%601> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır:

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer < Int32 \> var Tsıncollection. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Doğru|Koleksiyonda aranacak öğe \<T >. Bu öğe, *TypeArgument*türünde *T*türünde. Öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Doğru|Öğenin bulunup bulunmadığını kontrol edilecek koleksiyon. Bu koleksiyon **ıcollection < TypeArgument \> türünde.** Koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|@No__t_0 bulunan öğelerin T türü. Varsayılan olarak, bu *TypeArgument* türü **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Koleksiyonda belirtilen öğenin var olup olmadığını gösteren bir değer. Sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir Visual Basic değişkeni yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)