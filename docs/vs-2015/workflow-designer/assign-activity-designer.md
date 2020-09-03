---
title: Etkinlik Tasarımcısı ata | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40ebe465d5eeb12a956d285a8313b0acdbcfb8d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659186"
---
# <a name="assign-activity-designer"></a>Assign Etkinlik Tasarımcısı
Etkinlik oluşturma ve yapılandırma etkinliği için **atama** etkinliği Tasarımcısı kullanılır <xref:System.Activities.Statements.Assign> .

## <a name="the-assign-activity"></a>Atama etkinliği
 <xref:System.Activities.Statements.Assign>Etkinlik bir değişkene veya bağımsız değişkene bir değer atar.

### <a name="using-the-assign-activity-designer"></a>Atama etkinliği tasarımcısını kullanma
 **Ata** etkinlik Tasarımcısı **, araç kutusu sekmesine** tıklanarak **erişilen araç kutusu**' nda (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek) bulunan **temel öğeler** kategorisinde bulunabilir.

 **Atama** etkinliği Tasarımcısı **araç kutusundan** sürüklenip, [!INCLUDE[wfd2](../includes/wfd2-md.md)] her zaman etkinliklerin genellikle yerleştirildiği yüzey üzerinde bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.Assign> , ata 'nın varsayılan **DisplayName** değeriyle bir etkinlik oluşturur. , <xref:System.Activities.Activity.DisplayName%2A> **Atama** etkinliğinin üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-assign-properties"></a>Atama özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Assign> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.Assign> . Varsayılan değer atama ' dır. <xref:System.Activities.Activity.DisplayName%2A>Değer kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Assign.To%2A>|Doğru|Atandığı değişken veya bağımsız değişken <xref:System.Activities.Statements.Assign.Value%2A> . Bu geçerli bir Visual Basic tanımlayıcısı olmalıdır. Özelliği ayarlamak için, **assign** Activity Designer 'daki **to** kutusuna veya özellik kılavuzunda bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.Assign.Value%2A>|Doğru|Değişkene atanan değer. <xref:System.Activities.Statements.Assign.Value%2A>' I ayarlamak için, bir Visual Basic ifadesi ' ni **ata** veya özellik kılavuzunda **değer** kutusuna yazın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [İlkel](../workflow-designer/primitives-activity-designers.md) [gecikme](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)