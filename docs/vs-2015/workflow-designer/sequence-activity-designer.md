---
title: Sequence etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3acf02ab478eee244557e04f19f78ba2d5f0b950
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663256"
---
# <a name="sequence-activity-designer"></a>Sequence Etkinlik Tasarımcısı
@No__t_0 etkinliği sırayla çalıştırdığı alt etkinliklerin sıralı bir koleksiyonunu içerir.

 Bir etkinlik kümesini sırayla yürütmeye yönelik başka bir yöntem de <xref:System.Activities.Statements.Flowchart> etkinlik kullanmaktır. Diagram, modellemek istediğiniz basit bir dallandırma veya döngü programı akışınız varsa, [akış çizelgesini](../workflow-designer/flowchart-activity-designer.md) kullanmayı düşünün.

## <a name="using-the-sequence-activity-designer"></a>Sıra etkinliği tasarımcısını kullanma
 @No__t_0 etkinlik eklemek için, **dizi** etkinlik tasarımcısını **araç kutusundan** sürükleyin ve [!INCLUDE[wfd1](../includes/wfd1-md.md)] yüzeyine bırakın. Bu <xref:System.Activities.Statements.Sequence> etkinliğine bir alt etkinlik eklemek için, başka bir etkinliği **araç** kutusundan sürükleyin ve kutuya "etkinliği buraya bırak" ipucu metni ile kutudaki üçgeni bırakın.

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı dizi etkinliği özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Sequence> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Üst bilgide <xref:System.Activities.Statements.Sequence> etkinlik tasarımcısının kolay adını belirtir. Varsayılan değer dizidir. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)