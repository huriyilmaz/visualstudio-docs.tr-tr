---
title: İş Akışı Tasarımcısı-ForEach &lt;T &gt; etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: faf2f62c482deac963f597c9861fbf2acedc945c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650392"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt;T &gt; etkinlik Tasarımcısı

@No__t_0 etkinliği, belirtilen <xref:System.Activities.Statements.ForEach%601.Values%2A> koleksiyonundaki her öğe için <xref:System.Activities.Statements.ForEach%601.Body%2A> içerilen etkinliği yürütür.

## <a name="foreacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı < T \> özellikleri

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer ForEach < Int32 \>. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. @No__t_0 ayarlamak için, **ForEach < t \>** Etkinlik tasarımcısında veya özellik kılavuzunda **değerler** kutusuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|Genel parametre *t*tarafından belirtilen <xref:System.Activities.Statements.ForEach%601.Values%2A> koleksiyonundaki öğelerin türü. Varsayılan olarak, *TypeArgument* değeri **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzunda *TypeArgument* Birleşik giriş kutusunun değerini değiştirin.|

Varsayılan olarak, döngü yineleyicisi **öğe**olarak adlandırılır. @No__t_0 Etkinlik tasarımcısında Yineleyici değişkeninin adını değiştirebilirsiniz. Döngü yineleyicisi, <xref:System.Activities.Statements.ForEach%601> etkinliğinin alt öğelerindeki ifadelerde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)