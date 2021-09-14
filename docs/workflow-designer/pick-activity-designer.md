---
title: İş Akışı Tasarımcısı - Etkinlik Tasarımcısı seçme
description: Pick etkinliğinin olay tabanlı denetim akışını nasıl sağladığını ve bir tetikleyici olayına yanıt olarak birkaç daldan birini nasıl yürüttülür?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: e871e38cb9f675e1a76edae0410cbd5ac45aee10
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725522"
---
# <a name="pick-activity-designer"></a>Pick Etkinlik Tasarımcısı

Etkinlik, <xref:System.Activities.Statements.Pick> olay tabanlı denetim akışı sağlar. Etkinlik, bir tetikleme olayına yanıt olarak birkaç daldan birini yürütür.

## <a name="the-pick-activity"></a>Seçme Etkinliği

Bir etkinlik, tetikleyici olarak görev alan bazı gelen olaylardan dolayı <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> etkinliğin yürütüle bir nesne koleksiyonu içerir. Bu şekilde İş Akışı Tasarımcısı tabanlı denetim akışı modellemesi sağlar. Her <xref:System.Activities.Statements.PickBranch> biri bir ve <xref:System.Activities.Statements.PickBranch.Trigger%2A> <xref:System.Activities.Statements.PickBranch.Action%2A> içerir. Bir etkinliğin <xref:System.Activities.Statements.Pick> yürütülmesinin başlangıcında öğelerin tüm tetikleyici etkinlikleri <xref:System.Activities.Statements.PickBranch> zamanlanmış olur. İlk etkinlik tamamlandığında ilgili eylem etkinliği zamanlanır ve diğer tüm tetikleyici etkinlikleri iptal edilir.

### <a name="how-to-use-the-pick-activity-designer"></a>Etkinlik Tasarımcısını Seçmeyi Kullanma

Araç Kutusunun **Denetim** Denetimi **Flow** etkinlik tasarımcısına **erişin.** Seçim **etkinliği** tasarımcısı Araç Kutusundan  sürüklenip etkinlik tasarımcılarının normalde yerleştirilmeleri (örneğin, bir Sıra etkinlik tasarımcısının içine) İş Akışı Tasarımcısı **yüzeyine** bırakılır. Bunu bir İş Akışı Tasarımcısı sonra, varsayılan olarak Branch1 ve Branch2 görünen adlarına sahip öğeler olarak iki boş etkinlik içeren bir <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.PickBranch> etkinlik oluşturur. Bu <xref:System.Activities.Statements.PickBranch.DisplayName%2A> ilgili özellik değerleri **PickBranch** etkinlik tasarımcısı üst bilgisinde veya her dalın **Özellikler** penceresinde düzenlenebilir.

Bir nesnenin koleksiyonuna etkinlik eklemenin iki yolu <xref:System.Activities.Statements.PickBranch> <xref:System.Activities.Statements.Pick> vardır: **PickBranch**  tasarımcısını **Araç** Kutusundan sürükleyip bırakma veya Tasarım seçin yüzeyinin içindeki sağ tıklama menüsünü kullanma. Ayrıntılar için [PickBranch konu başlığına](../workflow-designer/pickbranch-activity-designer.md) bakın. Bir Pick etkinlik tasarımcısına yerleştiril **pickbranch** **etkinlik** tasarımcısının tek öğe olduğunu fark vardır.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>Etkinlik Özelliklerini seçin İş Akışı Tasarımcısı

Aşağıdaki tablo, <xref:System.Activities.Statements.Pick> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik <xref:System.Activities.Statements.Pick> tasarımcısının kolay adını belirtir. Varsayılan değer Seç'tir. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
- [Pick Etkinliği](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick Etkinliği Kullanma](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)