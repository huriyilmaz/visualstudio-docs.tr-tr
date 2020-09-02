---
title: WriteLine etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4f656578526879774e698523239d5a9b2b14ccd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657526"
---
# <a name="writeline-activity-designer"></a>WriteLine Etkinlik Tasarımcısı
**WriteLine** etkinlik Tasarımcısı, etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.WriteLine> .

## <a name="the-writeline-activity"></a>WriteLine etkinliği
 <xref:System.Activities.Statements.WriteLine>Etkinlik, belirtilen bir nesneye metin yazar <xref:System.IO.TextWriter> . Hayır <xref:System.IO.TextWriter> belirtilmişse, <xref:System.Activities.Statements.WriteLine> metni konsola yazar.

### <a name="using-the-writeline-activity-designer"></a>WriteLine etkinlik tasarımcısını kullanma
 **WriteLine** etkinlik Tasarımcısı **, araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak **Toolbox**, **Primitives** [!INCLUDE[wfd2](../includes/wfd2-md.md)] **Görünüm** menüsünden **araç çubuğu** ' nu veya Ctrl + Alt + X ' i seçin.) araç çubuğunun temel elemanlar kategorisinde bulunabilir.

 **WriteLine** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, ancak [!INCLUDE[wfd2](../includes/wfd2-md.md)] içinde olduğu gibi etkinliklerin genellikle yerleştirildiği yüzeye bırakılabilir <xref:System.Activities.Statements.Sequence> . Bu <xref:System.Activities.Statements.WriteLine> , varsayılan olarak WriteLine olan bir etkinlik oluşturur <xref:System.Activities.Activity.DisplayName%2A> . , <xref:System.Activities.Activity.DisplayName%2A> **WriteLine** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-writeline-properties"></a>WriteLine özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.WriteLine> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler, özellik kılavuzunda düzenlenebilir ve bunlardan bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)] Tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinliğin kolay adı <xref:System.Activities.Statements.WriteLine> . Varsayılan değer WriteLine ' dır. <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Yanlış|Yazılacak metin. Özelliği ayarlamak için, **WriteLine** etkinlik Tasarımcısı ' nın veya özellik kılavuzundaki **metin** kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Yanlış|' A <xref:System.IO.TextWriter> <xref:System.Activities.Statements.WriteLine> Yazar <xref:System.Activities.Statements.WriteLine.Text%2A> . Varsayılan, konsoldur.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Temel elemanlar](../workflow-designer/primitives-activity-designers.md) [atama](../workflow-designer/assign-activity-designer.md) [gecikmesi](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)