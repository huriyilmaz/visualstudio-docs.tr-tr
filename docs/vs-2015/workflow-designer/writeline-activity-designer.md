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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657526"
---
# <a name="writeline-activity-designer"></a>WriteLine Etkinlik Tasarımcısı
**WriteLine** etkinlik Tasarımcısı <xref:System.Activities.Statements.WriteLine> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-writeline-activity"></a>WriteLine etkinliği
 @No__t_0 etkinliği, belirtilen bir <xref:System.IO.TextWriter> nesnesine metin yazar. @No__t_0 belirtilmemişse, <xref:System.Activities.Statements.WriteLine> metni konsola yazar.

### <a name="using-the-writeline-activity-designer"></a>WriteLine etkinlik tasarımcısını kullanma
 **WriteLine** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] araç **kutusu** sekmesine tıklanarak erişilen **araç kutusu**' ndan bulunabilir (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** ' nu seçin veya CTRL + ALT + X.)

 **WriteLine** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, WriteLine 'ın varsayılan <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.WriteLine> etkinlik oluşturur. @No__t_0, **WriteLine** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-writeline-properties"></a>WriteLine özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.WriteLine> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer WriteLine ' dır. @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Yazılacak metin. Özelliği ayarlamak için, **WriteLine** etkinlik Tasarımcısı ' nın veya özellik kılavuzundaki **metin** kutusuna bir Visual Basic ifadesi yazın.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|@No__t_1 <xref:System.Activities.Statements.WriteLine.Text%2A> yazdığı <xref:System.IO.TextWriter>. Varsayılan, konsoldur.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Temel elemanlar](../workflow-designer/primitives-activity-designers.md) [atama](../workflow-designer/assign-activity-designer.md) [gecikmesi](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)