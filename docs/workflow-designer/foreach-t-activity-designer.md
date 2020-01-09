---
title: İş Akışı Tasarımcısı-ForEach&lt;T&gt; etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30d43351211a6ff857630b47f05be77e27bd7951
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593921"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt; etkinlik Tasarımcısı

<xref:System.Activities.Statements.ForEach%601> etkinliği, belirtilen <xref:System.Activities.Statements.ForEach%601.Values%2A> koleksiyonundaki her öğe için <xref:System.Activities.Statements.ForEach%601.Body%2A> içerilen etkinliği yürütür.

## <a name="foreacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı < T\> özellikleri

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> etkinliğinin kolay adı. Varsayılan değer ForEach < Int32\>. <xref:System.Activities.Activity.DisplayName%2A> değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. <xref:System.Activities.Statements.ForEach%601.Values%2A>ayarlamak için, **ForEach < t\>** Etkinlik tasarımcısında veya özellik kılavuzunda **değerler** kutusuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|Genel parametre *t*tarafından belirtilen <xref:System.Activities.Statements.ForEach%601.Values%2A> koleksiyonundaki öğelerin türü. Varsayılan olarak, *TypeArgument* değeri **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzunda *TypeArgument* Birleşik giriş kutusunun değerini değiştirin.|

Varsayılan olarak, döngü yineleyicisi **öğe**olarak adlandırılır. <xref:System.Activities.Statements.ForEach%601> Etkinlik tasarımcısında Yineleyici değişkeninin adını değiştirebilirsiniz. Döngü yineleyicisi, <xref:System.Activities.Statements.ForEach%601> etkinliğinin alt öğelerindeki ifadelerde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)
