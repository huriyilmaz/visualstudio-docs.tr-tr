---
title: Paralel etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a46a340ccdeacacb8f04b962313db18975447a67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672631"
---
# <a name="parallel-activity-designer"></a>Parallel Etkinlik Tasarımcısı
<xref:System.Activities.Statements.Parallel>Etkinlik, alt etkinliklerin bir koleksiyonunu eşzamanlı olarak yürütür.

## <a name="the-parallel-activity"></a>Paralel etkinlik
 <xref:System.Activities.Statements.Parallel>Etkinlik, alt etkinliklerini bir <xref:System.Activities.Statements.Parallel.Branches%2A> koleksiyonda depolar. <xref:System.Activities.Statements.Parallel> <xref:System.Activities.Statements.Sequence> Alt etkinliklerin bazıları boşta kalabileceğini etkinlik yerine etkinliğini kullanın.

 <xref:System.Activities.Statements.Parallel>Etkinlik, Kullanıcı tarafından <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> belirtilen bir ifade içeren bir özelliğe sahiptir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . <xref:System.Activities.Statements.Parallel>Etkinlik her bir dal tamamlandıktan sonra bu özelliği değerlendirir. **True**olarak değerlendirilirse, <xref:System.Activities.Statements.Parallel> etkinlik diğer dalları yürütmeden tamamlanır. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> **Doğru**olarak değerlendirilmiyorsa, <xref:System.Activities.Statements.Parallel> tüm alt etkinlikleri tamamlandığında etkinlik tamamlanır.

### <a name="using-the-parallel-activity-designer"></a>Paralel etkinlik tasarımcısını kullanma
 **Paralel** etkinlik Tasarımcısı, **araç kutusu**' nın sol tarafındaki araç **kutusu** sekmesine tıklanarak erişilen (alternatif olarak, **Control Flow** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.) denetim akış kategorisinde bulunabilir.

 **Paralel** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Örneğin bir **sıra** etkinliği Tasarımcısı içinde olan etkinlik tasarımcılarının normalde yerleştirildiği yüzey üzerinde bırakılmış olabilir. İçine kaldırıldıktan sonra [!INCLUDE[wfd2](../includes/wfd2-md.md)] , <xref:System.Activities.Statements.Parallel> Varsayılan olarak bir <xref:System.Activities.Activity.DisplayName%2A> **paralel** içeren bir etkinlik oluşturur

 Paralel etkinliğin koleksiyonuna bir etkinlik eklemek için <xref:System.Activities.Statements.Parallel.Branches%2A> , başka bir etkinlik tasarımcısını **araç kutusundan** sürükleyin ve **paralel** etkinlik Tasarımcısı içindeki üçgende bırakın. Üçgenler, dallarda bulunan etkinlikleri Flank. Bu yordam tekrarlayarak ek etkinlikler eklenebilir. Etkinlikler, **paralel** etkinlik Tasarımcısı içinde sürükleyip bırakarak yeniden sıralanabilir.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı paralel etkinlik özellikleri
 Aşağıdaki tabloda, paralel etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik tasarımcısının kolay görünen adını belirtir. Varsayılan değer **paraleldir**. Değer, isteğe bağlı olarak **Özellikler** kılavuzunda veya doğrudan etkinlik Tasarımcısı üstbilgisinde düzenlenebilir.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Doğru|Yürütülecek alt etkinliklerin koleksiyonunu içerir.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|Yanlış|Bir dal tamamlandıktan sonra değerlendirilir. **True**olarak değerlendirilirse, zamanlanan bekleyen dallar iptal edilir. Bu özellik ayarlanmamışsa veya **false**olarak değerlendirilirse, tüm alt etkinlikleri tamamlandığında etkinlik tamamlanır. Varsayılan değer **null**.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Sequence](../workflow-designer/sequence-activity-designer.md) [ParallelForEach \<T> ](../workflow-designer/parallelforeach-t-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)