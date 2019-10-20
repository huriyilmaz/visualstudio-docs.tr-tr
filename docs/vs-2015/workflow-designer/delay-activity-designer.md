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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656794"
---
# <a name="delay-activity-designer"></a>Delay Etkinlik Tasarımcısı
**Gecikme** etkinliği Tasarımcısı, bir <xref:System.Activities.Statements.Delay> etkinliği oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-delay-activity"></a>Gecikme etkinliği
 @No__t_0 etkinliği, belirli bir süre için iş akışının yürütülmesini geciktirir.

### <a name="using-the-delay-activity-designer"></a>Delay etkinliği tasarımcısını kullanma
 **Gecikme** etkinlik tasarımcısı, [!INCLUDE[wfd2](../includes/wfd2-md.md)] araç **kutusu** sekmesine tıklanarak erişilen **araç kutusu**' nu **temel** alan ' de bulunabilir (alternatif olarak, **Görünüm** menüsünden **araç çubuğu** ' nu seçin veya CTRL + ALT + X.)

 **Gecikme** etkinlik Tasarımcısı **araç kutusundan** sürüklenip [!INCLUDE[wfd2](../includes/wfd2-md.md)] yüzeyine, örneğin <xref:System.Activities.Statements.Sequence> içinde olduğu gibi, her yerde bırakılmış olarak bırakılabilir. Bu, varsayılan gecikme <xref:System.Activities.Activity.DisplayName%2A> bir <xref:System.Activities.Statements.Delay> etkinliği oluşturur. @No__t_0, **gecikme** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-delay-properties"></a>Gecikme özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Statements.Delay> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer gecikmede yapılır. @No__t_0 değeri kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Delay.Duration%2A>|Doğru|İş akışını geciktirmek için geçen süre. Bu özellik, özellik kılavuzunda ayarlanır. 00:00:00 biçiminde bir sabit değer <xref:System.TimeSpan> ya da süreyi belirtmek için bir Visual Basic ifadesi yazın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Temel elemanlar](../workflow-designer/primitives-activity-designers.md) [atama](../workflow-designer/assign-activity-designer.md) [gecikmesi etkinlik Tasarımcısı](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)