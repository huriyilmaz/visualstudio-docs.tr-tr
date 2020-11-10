---
title: İş Akışı Tasarımcısı-seçim etkinliği Tasarımcısı
description: Seçme etkinliğinin olay tabanlı denetim akışı sağladığını ve tetikleme olayına yanıt olarak çeşitli dallardan birini yürüttüğünü öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9968a00a1e4530e22abe25819c9e3d5188bcefa
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434252"
---
# <a name="pick-activity-designer"></a>Pick Etkinlik Tasarımcısı

<xref:System.Activities.Statements.Pick>Etkinlik, olay tabanlı denetim akışı sağlar. Etkinlik, bir tetikleme olayına yanıt olarak çeşitli dallardan birini yürütür.

## <a name="the-pick-activity"></a>Seçim etkinliği

Bir <xref:System.Activities.Statements.Pick> etkinlik <xref:System.Activities.Statements.PickBranch> , bir <xref:System.Activities.Statements.Pick> tetikleyici görevi gören bazı gelen olayları nedeniyle etkinliğin yürütebileceği bir nesne koleksiyonu içerir. Bu şekilde İş Akışı Tasarımcısı olay tabanlı denetim akışı modelleme sağlar. Her biri <xref:System.Activities.Statements.PickBranch> bir <xref:System.Activities.Statements.PickBranch.Trigger%2A> ve içerir <xref:System.Activities.Statements.PickBranch.Action%2A> . <xref:System.Activities.Statements.Pick>Etkinliğin çalışmasının başlangıcında, öğelerin tüm tetikleme etkinlikleri <xref:System.Activities.Statements.PickBranch> zamanlanır. İlk etkinlik tamamlandığında, ilgili eylem etkinliği zamanlanır ve diğer tüm tetikleyici etkinlikleri iptal edilir.

### <a name="how-to-use-the-pick-activity-designer"></a>Seçme etkinliği tasarımcısını kullanma

**Araç kutusunun** **Denetim akışı** kategorisindeki **seçim** etkinliği tasarımcısına erişin. **Seçim** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, örneğin bir **dizi** etkinlik tasarımcısı gibi etkinlik tasarımcılarının normalde yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir. İş Akışı Tasarımcısı ' a geçirdikten sonra, <xref:System.Activities.Statements.Pick> Varsayılan olarak iki boş <xref:System.Activities.Statements.PickBranch> etkinliği Branch1 ve branch2 görünen adlarına sahip öğeler olarak içeren bir etkinlik oluşturur. Bu ilgili <xref:System.Activities.Statements.PickBranch.DisplayName%2A> özellik değerleri, **PickBranch** etkinlik Tasarımcısı üst bilgisinde veya her dala ait **Özellikler** penceresinde düzenlenebilir.

<xref:System.Activities.Statements.PickBranch>Bir nesne koleksiyonuna etkinlik eklemenin iki yolu vardır <xref:System.Activities.Statements.Pick> : **araç kutusundan** **PickBranch** tasarımcısını sürükleyip bırakarak veya **seçme** tasarım yüzeyi içinden sağ tıklama menüsünü kullanarak. Ayrıntılar için bkz. [PickBranch](../workflow-designer/pickbranch-activity-designer.md) konusu. Bir **seçim** etkinliği tasarımcısının içine yerleştirilebilecek tek öğenin bir **PickBranch** etkinlik Tasarımcısı olduğunu fark edersiniz.

### <a name="pick-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı etkinlik özelliklerini seçme

Aşağıdaki tabloda <xref:System.Activities.Statements.Pick> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.Pick> . Varsayılan değer, seçer. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)
- [Pick Etkinliği](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick Etkinliği Kullanma](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)