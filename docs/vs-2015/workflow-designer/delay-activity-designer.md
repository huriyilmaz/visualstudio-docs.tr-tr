---
title: Gecikme etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a47279bc68503ba645fea3ef23a04ce9d5ef4c41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656794"
---
# <a name="delay-activity-designer"></a>Delay Etkinlik Tasarımcısı
**Gecikme** etkinliği Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Delay> .

## <a name="the-delay-activity"></a>Gecikme etkinliği
 <xref:System.Activities.Statements.Delay>Etkinlik, bir iş akışının belirli bir süre boyunca yürütülmesini geciktirir.

### <a name="using-the-delay-activity-designer"></a>Delay etkinliği tasarımcısını kullanma
 **Gecikme** etkinlik Tasarımcısı **, araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak **Toolbox**, **Primitives** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.) araç çubuğunun temel elemanlar kategorisinde bulunabilir.

 **Gecikme** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeyine bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Delay> , varsayılan gecikmeyle bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **Gecikme** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-delay-properties"></a>Gecikme özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Delay> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] Tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.Delay> . Varsayılan değer gecikmede yapılır. <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Doğru|İş akışını geciktirmek için geçen süre. Bu özellik, özellik kılavuzunda ayarlanır. <xref:System.TimeSpan>Süreyi belirtmek için 00:00:00 biçiminde veya Visual Basic ifadesinde bir sabit değer yazın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Temel elemanlar](../workflow-designer/primitives-activity-designers.md) [atama](../workflow-designer/assign-activity-designer.md) [gecikmesi etkinlik Tasarımcısı](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)