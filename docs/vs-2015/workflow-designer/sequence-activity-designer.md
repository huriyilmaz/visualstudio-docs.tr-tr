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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663256"
---
# <a name="sequence-activity-designer"></a>Sequence Etkinlik Tasarımcısı
<xref:System.Activities.Statements.Sequence>Etkinlik, sırayla çalıştırdığı alt etkinliklerin sıralı bir koleksiyonunu içerir.

 Bir etkinlik kümesini sırayla yürütmeye yönelik başka bir yöntem de bir <xref:System.Activities.Statements.Flowchart> etkinlik kullanmaktır. Diagram, modellemek istediğiniz basit bir dallandırma veya döngü programı akışınız varsa, [akış çizelgesini](../workflow-designer/flowchart-activity-designer.md) kullanmayı düşünün.

## <a name="using-the-sequence-activity-designer"></a>Sıra etkinliği tasarımcısını kullanma
 Etkinlik eklemek için <xref:System.Activities.Statements.Sequence> , **dizi** etkinlik tasarımcısını **araç kutusundan** sürükleyin ve [!INCLUDE[wfd1](../includes/wfd1-md.md)] yüzeyine bırakın. Bu etkinliğe bir alt etkinlik eklemek için <xref:System.Activities.Statements.Sequence> , başka bir etkinliği **araç** kutusundan sürükleyin ve kutuya "etkinliği buraya bırak" ipucu metni ile kutudaki üçgeni bırakın.

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı dizi etkinliği özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Sequence> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda veya tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.Sequence> . Varsayılan değer dizidir. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Akış çizelgesi](../workflow-designer/flowchart-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)