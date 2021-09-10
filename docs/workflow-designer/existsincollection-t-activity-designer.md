---
title: Mevcut Tsıncollection &lt; T &gt; etkinlik Tasarımcısı
description: <T>Mevcut bir Tsıncollection etkinliği oluşturmak ve yapılandırmak için iş akışı Tasarımcısı ' de var olan bulunan Tsıncollection etkinlik tasarımcısını nasıl kullanabileceğinizi öğrenin <T> .
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 1b5110a28dd46acff895a52d0e3c05f3f53b7700
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963712"
---
# <a name="existsincollectiont-activity-designer"></a>ExistsInCollection\<T> Etkinlik Tasarımcısı

Var olan **Tsıncollection \<T>** etkinlik Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.ExistsInCollection%601> .

## <a name="the-existsincollectiont-activity"></a>Varolan Tsıncollection \<T> etkinliği

<xref:System.Activities.Statements.ExistsInCollection%601>Etkinlik belirli bir koleksiyonda belirtilen öğenin mevcut olup olmadığını belirler.

### <a name="using-the-existsincollectiont-activity-designer"></a>Mevcut Tsıncollection \<T> etkinlik tasarımcısını kullanma

**\<T> Mevcut Tsıncollection** etkinlik Tasarımcısı, iş akışı Tasarımcısı **araç kutusu** sekmesine tıklanarak erişilen **araç kutusu** **koleksiyon** kategorisinde bulunabilir. Alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu seçin veya **CTRL** + **alt** + **X** tuşlarına basın.

Var olan **Tsıncollection \<T>** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.ExistsInCollection%601> , varsayılan değeri var olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A><Int32 \> . (Varsayılan olarak, *TypeArgument* **Int32**' dir. Özellik kılavuzunda değiştirilebilir.)  Değer, var <xref:System.Activities.Activity.DisplayName%2A> olan **Tsıncollection<\> T** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir. Diğer özellikler, özellik kılavuzunda düzenlenmelidir.

### <a name="the-existsincollectiont-properties"></a>Mevcut Tsıncollection \<T> Özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.ExistsInCollection%601> Özellikler gösterilmektedir ve tasarımcıda nasıl kullanıldıkları açıklanmıştır:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.ExistsInCollection%601> . Varsayılan değer, Int32<Vartsincollection ' dur \> . <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|Doğru|Koleksiyonda aranacak öğe \<T> . Bu öğe, *TypeArgument* türünde *T* türünde. öğeyi belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|Doğru|Öğenin bulunup bulunmadığını kontrol edilecek koleksiyon. Bu koleksiyon **ıcollection<TypeArgument türünde \> .** koleksiyonu belirtmek için, özellik kılavuzuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|İçinde yer alan öğelerin T türü <xref:System.Collections.Generic.ICollection%601> . Varsayılan olarak, bu *TypeArgument* türü **Int32** olarak ayarlanır. Türü değiştirmek için, özellik kılavuzundaki Birleşik giriş kutusunda *TypeArgument* değerini değiştirin.|
|<xref:System.Activities.Activity%601.Result%2A>|Yanlış|Koleksiyonda belirtilen öğenin var olup olmadığını gösteren bir değer. sonuca bağlanacak bir değişken belirtmek için, özellik kılavuzuna bir Visual Basic değişkeni yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyon](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)