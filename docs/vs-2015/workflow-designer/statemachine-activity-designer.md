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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660113"
---
# <a name="statemachine-activity-designer"></a>StateMachine Etkinlik Tasarımcısı
@No__t_0 etkinliği, bilinen durum makinesi paradigmasını kullanan bir durum koleksiyonu ve iş akışları içerir.

## <a name="using-the-statemachine-activity-designer"></a>StateMachine etkinlik tasarımcısını kullanma
 @No__t_0 etkinlik eklemek için, **araç kutusunun** **durum makinesi** bölümünden **StateMachine** etkinlik tasarımcısını sürükleyin ve [!INCLUDE[wfd1](../includes/wfd1-md.md)] yüzeyine bırakın. Bu <xref:System.Activities.Statements.StateMachine> etkinliğine bir alt durum eklemek için, **araç kutusundan** bir <xref:System.Activities.Statements.State> veya <xref:System.Activities.Core.Presentation.FinalState> sürükleyin ve **StateMachine**üzerine bırakın.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı StateMachine etkinlik özellikleri
 Aşağıdaki tabloda, iş akışı Tasarımcısı kullanılarak ayarlayabilecekleri <xref:System.Activities.Statements.StateMachine> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları tasarımcı yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide <xref:System.Activities.Statements.StateMachine> etkinlik tasarımcısının kolay adını belirtir. Varsayılan değer **StateMachine**' dir. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. @No__t_0, iş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)