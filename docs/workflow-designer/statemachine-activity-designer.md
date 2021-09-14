---
title: İş Akışı Tasarımcısı-StateMachine etkinlik Tasarımcısı
description: StateMachine etkinliğinin bilinen durum makine paradigmasını kullanarak bir durum koleksiyonu ve modeller iş akışlarını nasıl içerdiğini öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: b6982a3875bc09e95b6f33dd30010adf029b3a91
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726073"
---
# <a name="statemachine-activity-designer"></a>StateMachine Etkinlik Tasarımcısı

<xref:System.Activities.Statements.StateMachine>Etkinlik, bilinen durum makinesi paradigmasını kullanan bir durumlar koleksiyonu ve iş akışları içerir.

## <a name="using-the-statemachine-activity-designer"></a>StateMachine etkinlik tasarımcısını kullanma

Etkinlik eklemek için <xref:System.Activities.Statements.StateMachine> , **araç kutusunun** **durum makinesi** bölümünde **StateMachine** etkinlik tasarımcısını sürükleyin ve iş akışı Tasarımcısı yüzeyine bırakın. Bu etkinliğe bir alt durum eklemek için <xref:System.Activities.Statements.StateMachine> , <xref:System.Activities.Statements.State> <xref:System.Activities.Core.Presentation.FinalState> **araç kutusundan** bir veya sürükleyip **StateMachine** üzerine bırakın.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı StateMachine etkinlik özellikleri

Aşağıdaki tabloda, <xref:System.Activities.Statements.StateMachine> iş akışı Tasarımcısı kullanılarak ayarlanmakta olabilecek özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.StateMachine> . Varsayılan değer **StateMachine**' dir. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. , <xref:System.Activities.Activity.DisplayName%2A> İş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
