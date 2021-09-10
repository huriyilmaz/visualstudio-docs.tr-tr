---
title: TerminateWorkflow etkinlik Tasarımcısı
description: İş Akışı Tasarımcısı, bir TerminateWorkflow etkinliği oluşturmak ve yapılandırmak için TerminateWorkflow etkinlik Tasarımcısı 'nı nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: 5d4fe0b77c91b36440cbb760b3e192af453c4f58
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963723"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow Etkinlik Tasarımcısı

**TerminateWorkflow** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.TerminateWorkflow> .

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow etkinliği

<xref:System.Activities.Statements.TerminateWorkflow>Etkinlik, bir iş akışının yürütülmesini sonlandırır.

### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow etkinlik tasarımcısını kullanma

**TerminateWorkflow** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek), **araç kutusunun** **çalışma zamanı** kategorisinde bulunabilir.

**TerminateWorkflow** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, örneğin içinde olduğu gibi etkinliklerin genellikle yerleştirildiği iş akışı Tasarımcısı yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.TerminateWorkflow> , TerminateWorkflow varsayılan **DisplayName** 'i olan bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **TerminateWorkflow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow özellikleri

Aşağıdaki tabloda <xref:System.Activities.Statements.TerminateWorkflow> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.TerminateWorkflow> . Varsayılan değer TerminateWorkflow ' dır. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Yanlış|İş akışı sonlandırıldığı zaman throw özel durumu. Özellik kılavuzunda bu özelliği ayarlayın.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Yanlış|İş akışının neden sonlandırıldığını açıklayan neden. Özellik kılavuzunda bu özelliği ayarlayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
