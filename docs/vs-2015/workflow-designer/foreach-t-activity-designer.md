---
title: ForEach &lt;T &gt; etkinlik Tasarımcısı | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656653"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach &lt;T &gt; etkinlik Tasarımcısı
@No__t_0 etkinliği, belirtilen <xref:System.Activities.Statements.ForEach%601.Values%2A> koleksiyonundaki her öğe için <xref:System.Activities.Statements.ForEach%601.Body%2A> içerilen etkinliği yürütür.

## <a name="foreacht-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı > Özellikleri \<T ForEach
 Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.ForEach%601> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer ForEach \<Int32 >. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|Doğru|Yinelecek öğelerin koleksiyonu. @No__t_0 ayarlamak için, **ForEach \<T >** etkinlik Tasarımcısı veya özellik kılavuzunda **değerler** kutusuna bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifadesi yazın.|
|*TypeArgument*|Doğru|Genel parametre *t*tarafından belirtilen <xref:System.Activities.Statements.ForEach%601.Values%2A> koleksiyonundaki öğelerin türü. Varsayılan olarak, *TypeArgument* değeri **Int32**olarak ayarlanır. Türü değiştirmek için, özellik kılavuzunda *TypeArgument* Birleşik giriş kutusunun değerini değiştirin.|

 Varsayılan olarak, döngü yineleyicisi **öğe**olarak adlandırılır. @No__t_0 Etkinlik tasarımcısında Yineleyici değişkeninin adını değiştirebilirsiniz. Döngü yineleyicisi, <xref:System.Activities.Statements.ForEach%601> etkinliğinin alt öğelerindeki ifadelerde kullanılabilir.

## <a name="see-also"></a>Ayrıca Bkz.
 [ParallelForEach \<T >](../workflow-designer/parallelforeach-t-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)