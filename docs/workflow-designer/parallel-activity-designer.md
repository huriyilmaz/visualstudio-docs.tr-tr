---
title: İş Akışı Tasarımcısı-paralel etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0c1ea74c1cf64252bdae201e8cc3dd529adb7cb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650097"
---
# <a name="parallel-activity-designer"></a>Parallel Etkinlik Tasarımcısı

@No__t_0 etkinliği alt etkinliklerin bir koleksiyonunu eşzamanlı olarak yürütür.

## <a name="the-parallel-activity"></a>Paralel etkinlik

@No__t_0 etkinliği kendi alt etkinliklerini bir <xref:System.Activities.Statements.Parallel.Branches%2A> koleksiyonunda depolar. Alt etkinliklerin bazıları boşta kalabileceğini <xref:System.Activities.Statements.Sequence> etkinlik yerine <xref:System.Activities.Statements.Parallel> etkinliğini kullanın.

@No__t_0 etkinliği, Kullanıcı tarafından belirtilen Visual Basic ifadesi içeren bir <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> özelliğine sahiptir. @No__t_0 etkinliği her bir dal tamamlandıktan sonra bu özelliği değerlendirir. **True**olarak değerlendirilirse <xref:System.Activities.Statements.Parallel> etkinlik diğer dalları yürütmeden tamamlanır. @No__t_0 **true**olarak değerlendirilmiyorsa, tüm alt etkinlikleri tamamlandığında <xref:System.Activities.Statements.Parallel> etkinlik tamamlanır.

### <a name="using-the-parallel-activity-designer"></a>Paralel etkinlik tasarımcısını kullanma

**Araç kutusunun** **Denetim akışı** kategorisindeki **paralel** etkinlik tasarımcısına erişin.

**Paralel** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin bir **sıra** etkinliği Tasarımcısı içinde olan etkinlik tasarımcılarının normalde yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. İş Akışı Tasarımcısı, bir <xref:System.Activities.Statements.Parallel> etkinliği oluşturur ve bu, varsayılan olarak **paralel** bir <xref:System.Activities.Activity.DisplayName%2A> içerir

Paralel etkinliğin <xref:System.Activities.Statements.Parallel.Branches%2A> koleksiyonuna etkinlik eklemek için, başka bir etkinlik tasarımcısını **araç kutusundan** sürükleyin ve **paralel** etkinlik Tasarımcısı içindeki üçgende bırakın. Üçgenler, dallarda bulunan etkinlikleri Flank. Bu yordam tekrarlayarak ek etkinlikler eklenebilir. Etkinlikler, **paralel** etkinlik Tasarımcısı içinde sürükleyip bırakarak yeniden sıralanabilir.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı paralel etkinlik özellikleri

Aşağıdaki tabloda, paralel etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide etkinlik tasarımcısının kolay görünen adını belirtir. Varsayılan değer **paraleldir**. Değer, isteğe bağlı olarak **Özellikler** kılavuzunda veya doğrudan etkinlik Tasarımcısı üstbilgisinde düzenlenebilir.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Doğru|Yürütülecek alt etkinliklerin koleksiyonunu içerir.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Bir dal tamamlandıktan sonra değerlendirilir. **True**olarak değerlendirilirse, zamanlanan bekleyen dallar iptal edilir. Bu özellik ayarlanmamışsa veya **false**olarak değerlendirilirse, tüm alt etkinlikleri tamamlandığında etkinlik tamamlanır. Varsayılan değer **null**.|

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)