---
title: İş Akışı Tasarımcısı - Sıra Etkinliği Tasarımcısı
description: Sıra etkinliğinin sıralı bir alt etkinlik koleksiyonu içerdiğini ve bu koleksiyonun sırayla yürütülür olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 7980e01f23dab3ddb927af207e4e2ce67ab515a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099002"
---
# <a name="sequence-activity-designer"></a>Sequence Etkinlik Tasarımcısı

Etkinlik, <xref:System.Activities.Statements.Sequence> sırayla yürütülen bir alt etkinlik koleksiyonu içerir.

Bir etkinlik kümesi yürütmenin bir diğer yolu da etkinlik <xref:System.Activities.Statements.Flowchart> kullanmaktır. Diyagram aracılığıyla modellemek istediğiniz basit bir dal oluşturma veya döngü programı akışınız olduğunda [Flowchart'ı](../workflow-designer/flowchart-activity-designer.md) kullanmayı göz önünde bulundurabilirsiniz.

## <a name="using-the-sequence-activity-designer"></a>Sıra Etkinliği Tasarımcısını Kullanma

Etkinlik eklemek <xref:System.Activities.Statements.Sequence> için, Sıra **etkinliği** tasarımcısını **Araç** Kutusundan sürükleyip İş Akışı Tasarımcısı bırakın. Bu etkinlike bir alt etkinlik eklemek için Araç Kutusundan başka bir etkinlik sürükleyin ve kutu içinde "Etkinliği buraya bırak" ipucu metniyle birlikte <xref:System.Activities.Statements.Sequence> üçgenin üzerine  bırakın.

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>Etkinlik Özelliklerini İş Akışı Tasarımcısı

Aşağıdaki tablo, <xref:System.Activities.Statements.Sequence> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik <xref:System.Activities.Statements.Sequence> tasarımcısının kolay adını belirtir. Varsayılan değer Sıra'dır. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)