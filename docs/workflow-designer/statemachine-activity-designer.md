---
title: İş Akışı Tasarımcısı - StateMachine Etkinlik Tasarımcısı
description: StateMachine etkinliğinin tanıdık durum makinesi paradigmasını kullanarak bir durum ve model iş akışı koleksiyonu içerdiğini öğrenin.
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
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963732"
---
# <a name="statemachine-activity-designer"></a>StateMachine Etkinlik Tasarımcısı

Etkinlik, <xref:System.Activities.Statements.StateMachine> tanıdık durum makinesi paradigmasını kullanan durum ve model iş akışlarının bir koleksiyonunu içerir.

## <a name="using-the-statemachine-activity-designer"></a>StateMachine Etkinlik Tasarımcısını Kullanma

Etkinlik eklemek için, Araç Kutusunun State Machine bölümünden <xref:System.Activities.Statements.StateMachine> **StateMachine**  etkinlik tasarımcısını sürükleyin ve etkinlik tasarımcısının İş Akışı Tasarımcısı  bırakın. Bu etkinlike bir alt durum eklemek için, Araç Kutusundan bir veya sürükleyin ve <xref:System.Activities.Statements.StateMachine> <xref:System.Activities.Statements.State> <xref:System.Activities.Core.Presentation.FinalState> **StateMachine üzerine bırakın.** 

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'daki StateMachine Etkinlik Özellikleri

Aşağıdaki tabloda iş <xref:System.Activities.Statements.StateMachine> akışı tasarımcısı kullanılarak ayarlanacak özellikler ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Üst bilgide etkinlik <xref:System.Activities.Statements.StateMachine> tasarımcısının kolay adını belirtir. Varsayılan değer **StateMachine'dır.** Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. <xref:System.Activities.Activity.DisplayName%2A>, iş akışı tasarımcısının üst kısmında görüntülenen içerik harita gezintisinde kullanılır.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi](../workflow-designer/flowchart-activity-designer.md)
- [Denetim Flow](../workflow-designer/control-flow-activity-designers.md)
