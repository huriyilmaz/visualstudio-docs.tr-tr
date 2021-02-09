---
title: İş Akışı Tasarımcısı-DoWhile etkinlik Tasarımcısı
description: Belirtilen koşul false olarak değerlendirilene kadar DoWhile etkinliğinin gövdesinde en az bir kez yer aldığı etkinliği nasıl yürüttüğünü öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e117fcbea0488c4b6a42125971984b86cf78251
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894263"
---
# <a name="dowhile-activity-designer"></a>DoWhile Etkinlik Tasarımcısı

<xref:System.Activities.Statements.DoWhile>Etkinlik, <xref:System.Activities.Statements.DoWhile.Body%2A> belirtilen bir koşul **false** olarak değerlendirilene kadar en az bir kez içerilen etkinliği yürütür. Döngü gövdesinde içerilen etkinliğin sıfır veya daha fazla kez yürütülmesi gerekiyorsa, <xref:System.Activities.Statements.While> bunun yerine etkinliğini kullanın.

## <a name="dowhile-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler DoWhile

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.DoWhile> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır:

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Yanlış|Koşul **doğru** olduğunda yürütülecek etkinlik. Etkinliği eklemek için <xref:System.Activities.Statements.DoWhile.Body%2A> , araç kutusundan bir etkinliği **DoWhile** etkinlik Tasarımcısı ' nın "Ipucu" etkinliği buraya bırak "Ipucu metnini içeren **gövde** kutusuna bırakın.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Doğru|Döngünün her yinelemesinden sonra değerlendirilecek koşul. Ayarlamak için, <xref:System.Activities.Statements.DoWhile.Condition%2A> **DoWhile** etkinlik Tasarımcısı ' nın **koşul** kutusuna veya özellik kılavuzunda bir Visual Basic ifadesi yazın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Edilirken](../workflow-designer/while-activity-designer.md)
- [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)