---
title: TerminateWorkflow etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c204c14818a9c6e6fb0a46e6234b550838f3b1a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72607089"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow Etkinlik Tasarımcısı
**TerminateWorkflow** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.TerminateWorkflow> .

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow etkinliği
 <xref:System.Activities.Statements.TerminateWorkflow>Etkinlik, bir iş akışının yürütülmesini sonlandırır.

### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow etkinlik tasarımcısını kullanma
 **TerminateWorkflow** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek), **araç kutusunun** **çalışma zamanı** kategorisinde bulunabilir.

 **TerminateWorkflow** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.TerminateWorkflow> , TerminateWorkflow varsayılan **DisplayName** 'i olan bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **TerminateWorkflow** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.TerminateWorkflow> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.TerminateWorkflow> . Varsayılan değer TerminateWorkflow ' dır. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|Yanlış|İş akışı sonlandırıldığı zaman throw özel durumu. Özellik kılavuzunda bu özelliği ayarlayın.|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|Yanlış|İş akışının neden sonlandırıldığını açıklayan neden. Özellik kılavuzunda bu özelliği ayarlayın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Çalışma zamanı](../workflow-designer/runtime-activity-designers.md) [kalıcı](../workflow-designer/persist-activity-designer.md)