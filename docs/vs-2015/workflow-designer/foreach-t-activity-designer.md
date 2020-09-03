---
title: ForEach &lt; &gt; etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d41451ada0e37f953e9d611a4e3733815a9d347b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656653"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt; &gt; etkinlik Tasarımcısı
<xref:System.Activities.Statements.ForEach%601>Etkinlik, <xref:System.Activities.Statements.ForEach%601.Body%2A> belirtilen koleksiyondaki her öğe için içinde bulunan etkinliği yürütür <xref:System.Activities.Statements.ForEach%601.Values%2A> .

## <a name="foreacht-properties-in-the-workflow-designer"></a>\<T>İş akışı Tasarımcısı foreach özellikleri
 Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.ForEach%601> . Varsayılan değer ForEach ' dir \<Int32> . <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. Öğesini ayarlamak için <xref:System.Activities.Statements.ForEach%601.Values%2A> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ** \<T> foreach** Etkinlik tasarımcısında veya özellik kılavuzunda **değerler** kutusuna bir ifade yazın.|
|*TypeArgument*|Doğru|<xref:System.Activities.Statements.ForEach%601.Values%2A>Genel parametre *T*tarafından belirtilen koleksiyondaki öğelerin türü. Varsayılan olarak, *TypeArgument* değeri **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzunda *TypeArgument* Birleşik giriş kutusunun değerini değiştirin.|

 Varsayılan olarak, döngü yineleyicisi **öğe**olarak adlandırılır. Etkinlik tasarımcısında Yineleyici değişkeninin adını değiştirebilirsiniz <xref:System.Activities.Statements.ForEach%601> . Döngü yineleyicisi etkinliğin alt öğelerindeki ifadelerde kullanılabilir <xref:System.Activities.Statements.ForEach%601> .

## <a name="see-also"></a>Ayrıca Bkz.
 [ParallelForEach \<T> ](../workflow-designer/parallelforeach-t-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)