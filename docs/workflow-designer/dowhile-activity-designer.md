---
title: İş Akışı Tasarımcısı - DoWhile Etkinlik Tasarımcısı
description: Belirtilen bir koşul false olarak değerlendirilene kadar DoWhile etkinliğinin Gövdesinde yer alan etkinliği nasıl en az bir kez yürüttülür?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 942552f127cebaff4c0f923118fb8be0ac9b141a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633689"
---
# <a name="dowhile-activity-designer"></a>DoWhile Etkinlik Tasarımcısı

Etkinlik, belirtilen koşul false olarak değerlendirilene kadar en az bir kez içinde <xref:System.Activities.Statements.DoWhile> <xref:System.Activities.Statements.DoWhile.Body%2A> yer alan etkinliği **yürütür.** Döngü gövdesinde yer alan etkinliğin sıfır veya daha fazla kez yürütülecek olması gerekirse, bunun yerine <xref:System.Activities.Statements.While> etkinliğini kullanın.

## <a name="dowhile-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'da DoWhile Özellikleri

Aşağıdaki tabloda en kullanışlı etkinlik <xref:System.Activities.Statements.DoWhile> özellikleri ve bunların tasarımcıda nasıl kullanılaları açıkmektedir:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Yanlış|Koşul doğruyken yürütülecek **etkinlik.** Etkinliği eklemek <xref:System.Activities.Statements.DoWhile.Body%2A> için araç kutusundan **DoWhile**  etkinlik tasarımcısında "Etkinliği Buraya Bırak" ipucu metniyle Gövde kutusuna bir etkinlik bırakın.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Doğru|Döngü her yinelemeden sonra değerlendirilecek koşul. ayarlamak <xref:System.Activities.Statements.DoWhile.Condition%2A> için, **DoWhile** Visual Basic tasarımcısının **Koşul** kutusuna veya özellik kılavuzuna bir Visual Basic ifadesi yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Süre](../workflow-designer/while-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)