---
title: TerminateWorkflow etkinlik tasarımcısı
description: Bu İş Akışı Tasarımcısı, terminateWorkflow etkinlik tasarımcısını kullanarak bir TerminateWorkflow etkinliği oluşturma ve yapılandırma hakkında bilgi öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025413"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow Etkinlik Tasarımcısı

**TerminateWorkflow etkinlik** tasarımcısı, etkinlik oluşturmak ve yapılandırmak için <xref:System.Activities.Statements.TerminateWorkflow> kullanılır.

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow Etkinliği

Etkinlik, <xref:System.Activities.Statements.TerminateWorkflow> bir iş akışının yürütülmesini sonlandırılır.

### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow Etkinlik Tasarımcısını Kullanma

**TerminateWorkflow** etkinlik tasarımcısı, **Araç**  Kutusu sekmesine tıklayarak erişilen Araç Kutusunun  Çalışma Zamanı kategorisinde bulunabilir (Alternatif  olarak, Görünüm menüsünden Araç Kutusu'nı veya CTRL+ALT+X'i seçin.) 

**TerminateWorkflow** etkinlik tasarımcısı Araç Kutusundan  sürüklenip bir içinde olduğu gibi İş Akışı Tasarımcısı yerleştirildiği her yerde bu veri yüzeyine <xref:System.Activities.Statements.Sequence> bırakılır. Bu, varsayılan <xref:System.Activities.Statements.TerminateWorkflow> TerminateWorkflow **DisplayName değerine** sahip bir etkinlik oluşturur. <xref:System.Activities.Activity.DisplayName%2A>, **TerminateWorkflow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzundaki **DisplayName** kutusunda düzenlenebilir.

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow Özellikleri

Aşağıdaki tablo, <xref:System.Activities.Statements.TerminateWorkflow> özellikleri gösterir ve tasarımcıda nasıl kullanıldıklarını açıklar. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazı özellikler yüzeyde İş Akışı Tasarımcısı düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay <xref:System.Activities.Statements.TerminateWorkflow> adı. Varsayılan değer TerminateWorkflow'dır. Görünen ad kesinlikle gerekli değildir ancak görünen ad kullanmak en iyi yöntemdir.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Yanlış|İş akışı sonlandırıldı olduğunda atılacak özel durum. Özellik kılavuzunda bu özelliği ayarlayın.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Yanlış|İş akışının neden sonlandırılma nedenini açıklar. Özellik kılavuzunda bu özelliği ayarlayın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)
