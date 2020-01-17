---
title: İş Akışı Tasarımcısı-TerminateWorkflow etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 078dfb43b5960580327448627a30eec20297d9f3
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111771"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow Etkinlik Tasarımcısı

**TerminateWorkflow** etkinlik Tasarımcısı <xref:System.Activities.Statements.TerminateWorkflow> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow etkinliği

<xref:System.Activities.Statements.TerminateWorkflow> etkinliği bir iş akışının yürütülmesini sonlandırır.

### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow etkinlik tasarımcısını kullanma

**TerminateWorkflow** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek), **araç kutusunun** **çalışma zamanı** kategorisinde bulunabilir.

**TerminateWorkflow** etkinlik Tasarımcısı **araç kutusundan** sürüklenip İş Akışı Tasarımcısı yüzeyine, örneğin <xref:System.Activities.Statements.Sequence>içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, TerminateWorkflow varsayılan **DisplayName** 'i olan bir <xref:System.Activities.Statements.TerminateWorkflow> etkinliği oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, **TerminateWorkflow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.TerminateWorkflow> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> etkinliğinin kolay adı. Varsayılan değer TerminateWorkflow ' dır. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|İş akışı sonlandırıldığı zaman throw özel durumu. Özellik kılavuzunda bu özelliği ayarlayın.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|İş akışının neden sonlandırıldığını açıklayan neden. Özellik kılavuzunda bu özelliği ayarlayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
