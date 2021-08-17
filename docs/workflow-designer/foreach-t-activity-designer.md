---
title: İş Akışı Tasarımcısı-ForEach &lt; &gt; etkinlik Tasarımcısı
description: ForEach <T> etkinliğinin, belirtilen değerler koleksiyonundaki her öğe Için gövdesinde içerilen etkinliği nasıl yürüttüğünü öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 22ab21d25420296ba800ccecbc09257f67f8834e79813169d1e4c06a02d682dd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394036"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt; &gt; etkinlik Tasarımcısı

<xref:System.Activities.Statements.ForEach%601>Etkinlik, <xref:System.Activities.Statements.ForEach%601.Body%2A> belirtilen koleksiyondaki her öğe için içinde bulunan etkinliği yürütür <xref:System.Activities.Statements.ForEach%601.Values%2A> .

## <a name="foreacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı<T \> Özellikleri

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.ForEach%601> . Varsayılan değer ForEach ' dir<\> . <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. ayarlamak için <xref:System.Activities.Statements.ForEach%601.Values%2A> , **ForEach<T \>** etkinlik tasarımcısında veya özellik kılavuzunda **değerler** kutusuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|<xref:System.Activities.Statements.ForEach%601.Values%2A>Genel parametre *T* tarafından belirtilen koleksiyondaki öğelerin türü. Varsayılan olarak, *TypeArgument* değeri **Int32** olarak ayarlanır. Türü değiştirmek için, özellik kılavuzunda *TypeArgument* Birleşik giriş kutusunun değerini değiştirin.|

Varsayılan olarak, döngü yineleyicisi **öğe** olarak adlandırılır. Etkinlik tasarımcısında Yineleyici değişkeninin adını değiştirebilirsiniz <xref:System.Activities.Statements.ForEach%601> . Döngü yineleyicisi etkinliğin alt öğelerindeki ifadelerde kullanılabilir <xref:System.Activities.Statements.ForEach%601> .

## <a name="see-also"></a>Ayrıca bkz.

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
