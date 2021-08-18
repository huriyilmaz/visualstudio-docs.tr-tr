---
title: İş Akışı Tasarımcısı-paralel etkinlik Tasarımcısı
description: Paralel etkinlik ve bir alt etkinlik koleksiyonunu eşzamanlı olarak yürütmek için paralel etkinlik tasarımcısının nasıl kullanılacağı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 9d3f3efb6a35a87dadb1b2f70fdf59cdfb3d61691975091b2f9f7f58d557e133
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440480"
---
# <a name="parallel-activity-designer"></a>Parallel Etkinlik Tasarımcısı

<xref:System.Activities.Statements.Parallel>Etkinlik, alt etkinliklerin bir koleksiyonunu eşzamanlı olarak yürütür.

## <a name="the-parallel-activity"></a>Paralel etkinlik

<xref:System.Activities.Statements.Parallel>Etkinlik, alt etkinliklerini bir <xref:System.Activities.Statements.Parallel.Branches%2A> koleksiyonda depolar. <xref:System.Activities.Statements.Parallel> <xref:System.Activities.Statements.Sequence> Alt etkinliklerin bazıları boşta kalabileceğini etkinlik yerine etkinliğini kullanın.

<xref:System.Activities.Statements.Parallel>etkinlik, kullanıcı tarafından <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> belirtilen Visual Basic ifadesi içeren bir özelliğe sahiptir. <xref:System.Activities.Statements.Parallel>Etkinlik her bir dal tamamlandıktan sonra bu özelliği değerlendirir. **True** olarak değerlendirilirse, <xref:System.Activities.Statements.Parallel> etkinlik diğer dalları yürütmeden tamamlanır. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> **Doğru** olarak değerlendirilmiyorsa, <xref:System.Activities.Statements.Parallel> tüm alt etkinlikleri tamamlandığında etkinlik tamamlanır.

### <a name="using-the-parallel-activity-designer"></a>Paralel etkinlik tasarımcısını kullanma

**araç kutusunun** **denetim Flow** kategorisindeki **paralel** etkinlik tasarımcısına erişin.

**Paralel** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin bir **sıra** etkinliği Tasarımcısı içinde olan etkinlik tasarımcılarının normalde yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. İş Akışı Tasarımcısı, bir <xref:System.Activities.Statements.Parallel> etkinlik oluşturur, varsayılan olarak bir <xref:System.Activities.Activity.DisplayName%2A> **paralel** içerir

Paralel etkinliğin koleksiyonuna bir etkinlik eklemek için <xref:System.Activities.Statements.Parallel.Branches%2A> , başka bir etkinlik tasarımcısını **araç kutusundan** sürükleyin ve **paralel** etkinlik Tasarımcısı içindeki üçgende bırakın. Üçgenler, dallarda bulunan etkinlikleri Flank. Bu yordam tekrarlayarak ek etkinlikler eklenebilir. Etkinlikler, **paralel** etkinlik Tasarımcısı içinde sürükleyip bırakarak yeniden sıralanabilir.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı paralel etkinlik özellikleri

Aşağıdaki tabloda, paralel etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik tasarımcısının kolay görünen adını belirtir. Varsayılan değer **paraleldir**. Değer, isteğe bağlı olarak **Özellikler** kılavuzunda veya doğrudan etkinlik Tasarımcısı üstbilgisinde düzenlenebilir.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Doğru|Yürütülecek alt etkinliklerin koleksiyonunu içerir.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Yanlış|Bir dal tamamlandıktan sonra değerlendirilir. **True** olarak değerlendirilirse, zamanlanan bekleyen dallar iptal edilir. Bu özellik ayarlanmamışsa veya **false** olarak değerlendirilirse, tüm alt etkinlikleri tamamlandığında etkinlik tamamlanır. Varsayılan değer **null**.|

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
