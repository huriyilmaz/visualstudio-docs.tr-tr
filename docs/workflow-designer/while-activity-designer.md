---
title: İş Akışı Tasarımcısı - While Etkinlik Tasarımcısı
description: While etkinliğinin, belirtilen Koşul true olarak değerlendirilirken Gövdesinde yer alan etkinliği nasıl yürütür?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: f7d5859ae9841eff105b7a18f5f4730d440df94f
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963729"
---
# <a name="while-activity-designer"></a>While Etkinlik Tasarımcısı

Etkinlik içinde yer alan etkinliği yürütürken belirtilen true <xref:System.Activities.Statements.While> olarak <xref:System.Activities.Statements.While.Body%2A> <xref:System.Activities.Statements.While.Condition%2A> **değerlendirilir.** Söz edilen etkinlik hiçbir zaman yürütülmez. Içerdiği etkinliğin en az bir kez yürütültülürse, bunun yerine <xref:System.Activities.Statements.DoWhile> etkinliğini kullanın.

## <a name="while-properties-in-workflow-designer"></a>Özellikler İş Akışı Tasarımcısı

Aşağıdaki tabloda en kullanışlı etkinlik <xref:System.Activities.Statements.While> özellikleri ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik <xref:System.Activities.Statements.While> tasarımcısının kolay adını belirtir. Varsayılan değer While'dır. Değer, Özellikler penceresinde veya **doğrudan** etkinlik tasarımcısı üst bilgisinde düzenlenebilir.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.While.Body%2A>|Yanlış|true olarak değerlendirilirken <xref:System.Activities.Statements.While.Condition%2A> yürütülecek etkinliği **içerir.**|
|<xref:System.Activities.Statements.While.Condition%2A>|Doğru|içinde Visual Basic yürütülecek olup olmadığını belirlemek için değerlendirilen bir <xref:System.Activities.Statements.While.Body%2A> Visual Basic ifadesini içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
- [Dowhile](../workflow-designer/dowhile-activity-designer.md)
