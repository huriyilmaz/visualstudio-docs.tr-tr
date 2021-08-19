---
title: İş Akışı Tasarımcısı - Paralel Etkinlik Tasarımcısı
description: Paralel etkinlik hakkında bilgi edinmek ve Paralel etkinlik tasarımcısını kullanarak bir alt etkinlik koleksiyonunu eşzamanlı olarak yürütmeyi öğrenin.
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
ms.openlocfilehash: d4b1c5315933e2e29e29774b94804846d5317723
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114699"
---
# <a name="parallel-activity-designer"></a>Parallel Etkinlik Tasarımcısı

Etkinlik, <xref:System.Activities.Statements.Parallel> bir alt etkinlik koleksiyonunu eşzamanlı olarak yürütür.

## <a name="the-parallel-activity"></a>Paralel Etkinlik

Etkinlik, <xref:System.Activities.Statements.Parallel> alt etkinliklerini bir koleksiyonda  <xref:System.Activities.Statements.Parallel.Branches%2A> depolar. Alt <xref:System.Activities.Statements.Parallel> etkinliklerden bazıları <xref:System.Activities.Statements.Sequence> boşta kaldıktan sonra etkinlik yerine etkinliği kullanın.

<xref:System.Activities.Statements.Parallel>Etkinliğin, kullanıcı tarafından belirtilen bir <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ifadeyi içeren Visual Basic vardır. Etkinlik, <xref:System.Activities.Statements.Parallel> her dal tamamlandıktan sonra bu özelliği değerlendirir. True olarak **değerlendirilirse,** etkinlik <xref:System.Activities.Statements.Parallel> diğer dalları yürütmeden tamamlanır. true <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> olarak değerlendirilmezse, tüm alt etkinlikleri tamamlandığında etkinlik  <xref:System.Activities.Statements.Parallel> tamamlanır.

### <a name="using-the-parallel-activity-designer"></a>Paralel Etkinlik Tasarımcısını Kullanma

Araç Kutusunun **Denetim** Denetimi **Flow** Paralel etkinlik tasarımcısına **erişin.**

Paralel **etkinlik** tasarımcısı Araç Kutusundan  sürüklenip etkinlik tasarımcılarının normalde yerleştirilmelerinin (örneğin, bir Sıra etkinlik  tasarımcısının içine) İş Akışı Tasarımcısı yüzeyine bırakılır. Bunu bir İş Akışı Tasarımcısı sonra, varsayılan olarak Paralel <xref:System.Activities.Statements.Parallel> içeren bir etkinlik <xref:System.Activities.Activity.DisplayName%2A> **oluşturur**

Paralel etkinliğin koleksiyonuna etkinlik eklemek için Araç Kutusundan başka bir etkinlik tasarımcısını sürükleyin ve Paralel etkinlik tasarımcısının içindeki <xref:System.Activities.Statements.Parallel.Branches%2A> **üçgene**  bırakın. Üçgenler, dallarda bulunan etkinlikleri doğrular. Bu yordam tekrarlayarak ek etkinlikler eklenebilir. Etkinlikler, Paralel etkinlik tasarımcısında sürükleyip bırakarak **yeniden sıralandır** olabilir.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'de Paralel Etkinlik Özellikleri

Aşağıdaki tabloda Paralel etkinlik özellikleri ve bunların tasarımcıda nasıl kullanıldıkları açıkmektedir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik tasarımcısının kolay görünen adını belirtir. Varsayılan değer **Paralel'tir.** Değer isteğe bağlı olarak Özellikler kılavuzunda **veya** doğrudan etkinlik tasarımcısı üst bilgisinde düzenlenebilir.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Doğru|Yürütülecek alt etkinliklerin koleksiyonunu içerir.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Yanlış|Dal tamamlandıktan sonra değerlendirilir. True olarak **değerlendirilirse,** zamanlanmış bekleyen dallar iptal edilir. Bu özellik ayarlanmazsa veya **False** olarak değerlendirilirse, tüm alt etkinlikleri tamamlandığında etkinlik tamamlanır. Varsayılan değer **null'tır.**|

## <a name="see-also"></a>Ayrıca bkz.

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
