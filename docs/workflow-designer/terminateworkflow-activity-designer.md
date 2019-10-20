---
title: İş Akışı Tasarımcısı-TerminateWorkflow etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01003005e9f73138e5a430b21e538c5c241e7f9f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649877"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow Etkinlik Tasarımcısı

**TerminateWorkflow** etkinlik Tasarımcısı <xref:System.Activities.Statements.TerminateWorkflow> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow etkinliği

@No__t_0 etkinliği bir iş akışının yürütülmesini sonlandırır.

### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow etkinlik tasarımcısını kullanma

**TerminateWorkflow** etkinlik Tasarımcısı **, araç kutusu**sekmesine tıklanarak erişilen (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + alt + X.)

**TerminateWorkflow** etkinlik Tasarımcısı **araç kutusundan** sürüklenip İş Akışı Tasarımcısı yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, TerminateWorkflow varsayılan **DisplayName** 'i olan bir <xref:System.Activities.Statements.TerminateWorkflow> etkinliği oluşturur. @No__t_0, **TerminateWorkflow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.TerminateWorkflow> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer TerminateWorkflow ' dır. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|İş akışı sonlandırıldığı zaman throw özel durumu. Özellik kılavuzunda bu özelliği ayarlayın.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|İş akışının neden sonlandırıldığını açıklayan neden. Özellik kılavuzunda bu özelliği ayarlayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)