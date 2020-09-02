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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656776"
---
# <a name="dowhile-activity-designer"></a>DoWhile Etkinlik Tasarımcısı
<xref:System.Activities.Statements.DoWhile>Etkinlik, <xref:System.Activities.Statements.DoWhile.Body%2A> belirtilen bir koşul **false**olarak değerlendirilene kadar en az bir kez içerilen etkinliği yürütür. Döngü gövdesinde içerilen etkinliğin sıfır veya daha fazla kez yürütülmesi gerekiyorsa, <xref:System.Activities.Statements.While> bunun yerine etkinliğini kullanın.

## <a name="dowhile-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı Özellikler DoWhile
 Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.DoWhile> etkinlik özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanılacağı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Yanlış|Koşul **doğru**olduğunda yürütülecek etkinlik. Etkinliği eklemek için <xref:System.Activities.Statements.DoWhile.Body%2A> , araç kutusundan bir etkinliği **DoWhile** etkinlik Tasarımcısı ' nın "Ipucu" etkinliği buraya bırak "Ipucu metnini içeren **gövde** kutusuna bırakın.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Doğru|Döngünün her yinelemesinden sonra değerlendirilecek koşul. Ayarlamak için, <xref:System.Activities.Statements.DoWhile.Condition%2A> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] **DoWhile** etkinlik Tasarımcısı 'Nda veya özellik kılavuzunda **koşul** kutusuna bir ifade yazın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [While](../workflow-designer/while-activity-designer.md) [Denetim akışı](../workflow-designer/control-flow-activity-designers.md) sırasında