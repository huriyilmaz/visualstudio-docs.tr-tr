---
title: İş Akışı Tasarımcısı-While etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77954925533c51885a056f7156121e68851ad769
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115174"
---
# <a name="while-activity-designer"></a>While Etkinlik Tasarımcısı

<xref:System.Activities.Statements.While> etkinliği, belirtilen <xref:System.Activities.Statements.While.Condition%2A> **true**olarak değerlendirirken <xref:System.Activities.Statements.While.Body%2A> içerilen etkinliği yürütür. İçerilen etkinlik hiçbir şekilde yürütülemeyebilir. İçerilen etkinliğin en az bir kez yürütülmesini istiyorsanız bunun yerine <xref:System.Activities.Statements.DoWhile> etkinliğini kullanın.

## <a name="while-properties-in-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.While> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide <xref:System.Activities.Statements.While> etkinlik tasarımcısının kolay adını belirtir. Varsayılan değer while değeridir. Değer, **Özellikler** penceresinde veya doğrudan etkinlik Tasarımcısı üst bilgisinde düzenlenebilir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.While.Body%2A>|False|<xref:System.Activities.Statements.While.Condition%2A> **true**olarak değerlendirirken yürütülecek etkinliği içerir.|
|<xref:System.Activities.Statements.While.Condition%2A>|Doğru|<xref:System.Activities.Statements.While.Body%2A> etkinliğin yürütülüp yürütülmeyeceğini belirlemekte değerlendirilen Visual Basic ifadesini içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
