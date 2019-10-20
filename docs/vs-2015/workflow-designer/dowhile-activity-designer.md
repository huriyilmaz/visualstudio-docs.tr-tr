---
title: DoWhile etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656776"
---
# <a name="dowhile-activity-designer"></a>DoWhile Etkinlik Tasarımcısı
@No__t_0 etkinliği, belirtilen koşul **false**olarak değerlendirilene kadar en az bir kez <xref:System.Activities.Statements.DoWhile.Body%2A> içerilen etkinliği yürütür. Döngü gövdesinde içerilen etkinliğin sıfır veya daha fazla kez yürütülmesi gerekiyorsa, bunun yerine <xref:System.Activities.Statements.While> etkinliğini kullanın.

## <a name="dowhile-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler DoWhile
 Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.DoWhile> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Koşul **doğru**olduğunda yürütülecek etkinlik. @No__t_0 etkinliğini eklemek için, araç kutusundan bir etkinliği **DoWhile** etkinlik Tasarımcısı ' nın "Ipucu" etkinliği buraya bırak "ipucu metnini içeren **gövde** kutusuna bırakın.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Doğru|Döngünün her yinelemesinden sonra değerlendirilecek koşul. @No__t_0 ayarlamak için, **DoWhile** etkinlik Tasarımcısı 'nda veya özellik kılavuzunda **koşul** kutusuna bir [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ifadesi yazın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [](../workflow-designer/while-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md) sırasında