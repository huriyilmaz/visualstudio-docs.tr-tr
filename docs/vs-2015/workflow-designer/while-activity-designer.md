---
title: While etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fae1b4905d66a5162591fd7c720ba81ed7ffda82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72606617"
---
# <a name="while-activity-designer"></a>While Etkinlik Tasarımcısı

<xref:System.Activities.Statements.While>Etkinlik, <xref:System.Activities.Statements.While.Body%2A> belirtilen koşul **doğru**olarak değerlendirilirken içinde içerilen etkinliği yürütür. İçerilen etkinlik hiçbir şekilde yürütülemeyebilir. İçerilen etkinliğin en az bir kez yürütülmesini istiyorsanız <xref:System.Activities.Statements.DoWhile> bunun yerine etkinliğini kullanın.

## <a name="while-properties-in-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.While> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.While> . Varsayılan değer while değeridir. Değer, **Özellikler** penceresinde veya doğrudan etkinlik Tasarımcısı üst bilgisinde düzenlenebilir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.While.Body%2A>|Yanlış|<xref:System.Activities.Statements.While.Condition%2A> **Doğru**olarak değerlendirilirken yürütülecek etkinliği içerir.|
|<xref:System.Activities.Statements.While.Condition%2A>|Doğru|[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]İçindeki etkinliğin yürütülüp yürütülmeyeceğini belirlemekte değerlendirilen ifadeyi içerir <xref:System.Activities.Statements.While.Body%2A> .|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)