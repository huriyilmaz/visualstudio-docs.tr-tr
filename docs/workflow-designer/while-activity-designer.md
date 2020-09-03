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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115174"
---
# <a name="while-activity-designer"></a>While Etkinlik Tasarımcısı

<xref:System.Activities.Statements.While>Etkinlik, içinde bulunan etkinliği <xref:System.Activities.Statements.While.Body%2A> belirtilen sırada yürütür <xref:System.Activities.Statements.While.Condition%2A> . **true** İçerilen etkinlik hiçbir şekilde yürütülemeyebilir. İçerilen etkinliğin en az bir kez yürütülmesini istiyorsanız <xref:System.Activities.Statements.DoWhile> bunun yerine etkinliğini kullanın.

## <a name="while-properties-in-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.While> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.While> . Varsayılan değer while değeridir. Değer, **Özellikler** penceresinde veya doğrudan etkinlik Tasarımcısı üst bilgisinde düzenlenebilir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.While.Body%2A>|Yanlış|<xref:System.Activities.Statements.While.Condition%2A> **Doğru**olarak değerlendirilirken yürütülecek etkinliği içerir.|
|<xref:System.Activities.Statements.While.Condition%2A>|Doğru|İçindeki etkinliğin yürütülüp yürütülmeyeceğini belirlemekte değerlendirilen Visual Basic ifadesini içerir <xref:System.Activities.Statements.While.Body%2A> .|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
