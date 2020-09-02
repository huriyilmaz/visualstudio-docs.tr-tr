---
title: 'Nasıl yapılır: belgelerde program aracılığıyla yazımı denetleme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93ba9d9907135952f7408652bfb36f440d23138d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537858"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Nasıl yapılır: belgelerde program aracılığıyla yazımı denetleme
  Belgedeki Yazımı denetlemek için <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> yöntemini kullanın. Bu yöntem, sağlanan parametrenin doğru yazıldığını belirten bir Boole değeri döndürür.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Yazımı denetlemek ve sonuçları bir ileti kutusunda göstermek için

1. Yöntemi çağırın <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> ve yazım hatalarını denetlemek için bir metin aralığı geçirin. Bu kod örneğini kullanmak için, `ThisDocument` `ThisAddIn` projenizdeki veya sınıfından çalıştırın.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
