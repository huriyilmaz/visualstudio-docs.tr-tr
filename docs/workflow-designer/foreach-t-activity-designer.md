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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fd81377ca24dfbeaf4a25f2af00fb69f4821d73
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437989"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt; &gt; etkinlik Tasarımcısı

<xref:System.Activities.Statements.ForEach%601>Etkinlik, <xref:System.Activities.Statements.ForEach%601.Body%2A> belirtilen koleksiyondaki her öğe için içinde bulunan etkinliği yürütür <xref:System.Activities.Statements.ForEach%601.Values%2A> .

## <a name="foreacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı<T \> Özellikleri

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.ForEach%601> . Varsayılan değer ForEach ' dir<\> . <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. Ayarlamak için <xref:System.Activities.Statements.ForEach%601.Values%2A> , **foreach<T \>** Etkinlik tasarımcısında veya özellik kılavuzunda **değerler** kutusuna bir Visual Basic ifadesi yazın.|
|*TypeArgument*|Doğru|<xref:System.Activities.Statements.ForEach%601.Values%2A>Genel parametre *T* tarafından belirtilen koleksiyondaki öğelerin türü. Varsayılan olarak, *TypeArgument* değeri **Int32** olarak ayarlanır. Türü değiştirmek için, özellik kılavuzunda *TypeArgument* Birleşik giriş kutusunun değerini değiştirin.|

Varsayılan olarak, döngü yineleyicisi **öğe** olarak adlandırılır. Etkinlik tasarımcısında Yineleyici değişkeninin adını değiştirebilirsiniz <xref:System.Activities.Statements.ForEach%601> . Döngü yineleyicisi etkinliğin alt öğelerindeki ifadelerde kullanılabilir <xref:System.Activities.Statements.ForEach%601> .

## <a name="see-also"></a>Ayrıca bkz.

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)
