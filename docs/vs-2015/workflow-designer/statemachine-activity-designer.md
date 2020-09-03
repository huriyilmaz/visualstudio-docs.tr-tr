---
title: StateMachine etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fc9d34e06ca443b39a1a57aa88fee1155f47a8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660113"
---
# <a name="statemachine-activity-designer"></a>StateMachine Etkinlik Tasarımcısı
<xref:System.Activities.Statements.StateMachine>Etkinlik, bilinen durum makinesi paradigmasını kullanan bir durumlar koleksiyonu ve iş akışları içerir.

## <a name="using-the-statemachine-activity-designer"></a>StateMachine etkinlik tasarımcısını kullanma
 Etkinlik eklemek için <xref:System.Activities.Statements.StateMachine> , **araç kutusu** 'nun **durum makinesi** bölümünde **StateMachine** etkinlik tasarımcısını sürükleyin ve [!INCLUDE[wfd1](../includes/wfd1-md.md)] yüzeyine bırakın. Bu etkinliğe bir alt durum eklemek için <xref:System.Activities.Statements.StateMachine> , <xref:System.Activities.Statements.State> <xref:System.Activities.Core.Presentation.FinalState> **araç kutusundan** bir veya sürükleyip **StateMachine**üzerine bırakın.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı StateMachine etkinlik özellikleri
 Aşağıdaki tabloda, <xref:System.Activities.Statements.StateMachine> iş akışı Tasarımcısı kullanılarak ayarlanmakta olabilecek özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.StateMachine> . Varsayılan değer **StateMachine**' dir. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. , <xref:System.Activities.Activity.DisplayName%2A> İş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)